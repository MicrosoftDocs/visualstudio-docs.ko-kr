---
title: 레거시 언어 서비스의 구문 색상화 Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02723a09254255b98291cb921ae5ec091d8b9859
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704701"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>레거시 언어 서비스의 구문 색 지정
구문 색 지정은 프로그래밍 언어의 여러 요소가 다른 색 및 스타일의 소스 파일에 표시 되도록 하는 기능입니다. 이 기능을 지원 하려면 파일의 어휘 요소나 토큰 형식을 식별할 수 있는 파서 또는 스캐너를 제공 해야 합니다. 여러 언어에서 키워드, 구분 기호 (예: 괄호 또는 중괄호) 및 주석을 다른 방식으로 색을 구분 하 여 구분 합니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현 되지만 언어 서비스 기능을 구현 하는 최신 방법은 MEF 확장을 사용 하는 것입니다. 자세히 알아보려면 [편집기 및 언어 서비스 확장](../../extensibility/extending-the-editor-and-language-services.md)을 참조 하세요.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용 하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.

## <a name="implementation"></a>구현
 색 지정을 지원 하기 위해 MPF (관리 패키지 프레임 워크)는 인터페이스를 구현 하는 <xref:Microsoft.VisualStudio.Package.Colorizer> 클래스를 포함 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> . 이 클래스는와 상호 작용 <xref:Microsoft.VisualStudio.Package.IScanner> 하 여 토큰 및 색을 결정 합니다. 스캐너에 대 한 자세한 내용은 [레거시 언어 서비스 파서 및 스캐너](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)를 참조 하세요. <xref:Microsoft.VisualStudio.Package.Colorizer>그런 다음 클래스는 토큰의 각 문자를 색 정보로 표시 하 고 소스 파일을 표시 하는 편집기에 해당 정보를 반환 합니다.

 편집기에 반환 되는 색 정보는 색 항목 목록에 대 한 인덱스입니다. 각 색 항목은 색 값과 굵은 글꼴, 취소선 등의 글꼴 특성 집합을 지정 합니다. 편집기는 언어 서비스에서 사용할 수 있는 기본 색 항목 집합을 제공 합니다. 각 토큰 유형에 적절 한 색 인덱스를 지정 하기만 하면 됩니다. 그러나 사용자 지정 색 항목 집합 및 토큰에 대해 제공 하는 인덱스를 제공 하 고 기본 목록 대신 고유한 색 항목 목록을 참조할 수 있습니다. 또한 `RequestStockColors` `RequestStockColors` 사용자 지정 색을 지원 하려면 레지스트리 항목을 0 (또는 항목을 지정 하지 않음)으로 설정 해야 합니다. 사용자 정의 특성에 대 한 명명 된 매개 변수를 사용 하 여이 레지스트리 항목을 설정할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . 언어 서비스를 등록 하 고 해당 옵션을 설정 하는 방법에 대 한 자세한 내용은 [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)을 참조 하세요.

## <a name="custom-colorable-items"></a>사용자 지정 색 항목
 사용자 고유의 사용자 지정 색 항목을 제공 하려면 <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> 클래스에서 및 메서드를 재정의 해야 합니다 <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> . 첫 번째 메서드는 언어 서비스가 지 원하는 사용자 지정 색 항목의 수를 반환 하 고, 두 번째 메서드는 인덱스 별로 사용자 지정 색 항목을 가져옵니다. 사용자 지정 색 항목의 기본 목록을 만듭니다. 언어 서비스의 생성자에서 각 색 항목에 이름을 제공 하기만 하면 됩니다. Visual Studio는 사용자가 다른 색 항목 집합을 선택 하는 경우를 자동으로 처리 합니다. 이 이름은 **옵션** 대화 상자의 **글꼴 및 색** 속성 페이지 (Visual Studio **도구** 메뉴에서 사용 가능)에 표시 되며,이 이름에 따라 사용자가 재정의 한 색이 결정 됩니다. 사용자의 선택 항목은 레지스트리의 캐시에 저장 되 고 색 이름에 의해 액세스 됩니다. **글꼴 및 색** 속성 페이지에는 모든 색 이름이 알파벳 순서로 나열 되어 있으므로 각 색 이름 앞에 언어 이름을 사용 하 여 사용자 지정 색을 그룹화 할 수 있습니다. 예를 들면 "**testlanguage-Comment**" 및 "**Testlanguage-Keyword**"입니다. 또는 형식, "**주석 (TestLanguage)**" 및 "**키워드 (testlanguage)**"를 기준으로 색 항목을 그룹화 할 수 있습니다. 언어 이름을 기준으로 그룹화 하는 것이 좋습니다.

> [!CAUTION]
> 기존 색 항목 이름과의 충돌을 피하기 위해 언어 이름을 색 항목 이름에 포함 하는 것이 좋습니다.

> [!NOTE]
> 개발 하는 동안 색 중 하나의 이름을 변경 하는 경우 색에 처음 액세스할 때 Visual Studio에서 만든 캐시를 다시 설정 해야 합니다. Visual Studio SDK 프로그램 메뉴에서 **실험적 Hive 다시 설정** 명령을 실행 하 여이 작업을 수행할 수 있습니다.

 색 항목 목록의 첫 번째 항목은 참조 되지 않습니다. Visual Studio는 항상 해당 항목에 대 한 기본 텍스트 색과 특성을 제공 합니다. 이를 처리 하는 가장 쉬운 방법은 자리 표시자 색 항목을 첫 번째 항목으로 제공 하는 것입니다.

### <a name="high-color-colorable-items"></a>높은 색 색 항목
 색 항목은 인터페이스를 통해 24 비트 또는 높은 색의 값도 지원할 수 있습니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> . MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> 클래스는 인터페이스를 지원 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 하 고 24 비트 색은 일반 색과 함께 생성자에 지정 됩니다. 자세한 내용은 <xref:Microsoft.VisualStudio.Package.ColorableItem> 클래스를 참조하십시오. 아래 예제에서는 키워드 및 주석에 대 한 24 비트 색을 설정 하는 방법을 보여 줍니다. 24 비트 색은 사용자의 데스크톱에서 24 비트 색이 지원 되는 경우에 사용 됩니다. 그렇지 않으면 일반 텍스트 색이 사용 됩니다.

 해당 언어에 대 한 기본 색을 염두에 두어야 합니다. 사용자는 원하는 대로 색을 변경할 수 있습니다.

### <a name="example"></a>예
 이 예제에서는 클래스를 사용 하 여 사용자 지정 색 항목의 배열을 선언 하 고 채우는 한 가지 방법을 보여 줍니다 <xref:Microsoft.VisualStudio.Package.ColorableItem> . 이 예제에서는 24 비트 색을 사용 하 여 키워드 및 주석 색을 설정 합니다.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private ColorableItem[] m_colorableItems;

        TestLanguageService() : base()
        {
            m_colorableItems = new ColorableItem[] {
                new ColorableItem("TestLanguage - Text",
                                  "Text",
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,
                                  System.Drawing.Color.Empty,
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_DEFAULT),
                new ColorableItem("TestLanguage - Keyword",
                                  "Keyword",
                                  COLORINDEX.CI_MAROON,
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,
                                  System.Drawing.Color.FromArgb(192,32,32),
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_BOLD),
                new ColorableItem("TestLanguage - Comment",
                                  "Comment",
                                  COLORINDEX.CI_DARKGREEN,
                                  COLORINDEX.CI_LIGHTGRAY,
                                  System.Drawing.Color.FromArgb(32,128,32),
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_DEFAULT)
                // ...
                // Add as many colorable items as you want to support.
            };
        }
    }
}
```

## <a name="the-colorizer-class-and-the-scanner"></a>Svc 클래스 및 스캐너
 기본 클래스에는 <xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> 클래스를 instantiantes 하는 메서드가 있습니다 <xref:Microsoft.VisualStudio.Package.Colorizer> . 메서드에서 반환 된 스캐너가 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 클래스 생성자에 전달 됩니다 <xref:Microsoft.VisualStudio.Package.Colorizer> .

 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>클래스의 고유한 버전에서 메서드를 구현 해야 합니다 <xref:Microsoft.VisualStudio.Package.LanguageService> . 클래스는 스캐너를 사용 하 여 <xref:Microsoft.VisualStudio.Package.Colorizer> 모든 토큰 색 정보를 가져옵니다.

 스캐너는 <xref:Microsoft.VisualStudio.Package.TokenInfo> 찾은 모든 토큰에 대 한 구조를 채워야 합니다. 이 구조에는 토큰이 차지 하는 범위, 사용할 색 인덱스, 토큰 유형 및 토큰 트리거와 같은 정보가 포함 됩니다 (참조 <xref:Microsoft.VisualStudio.Package.TokenTriggers> ). 범위 및 색 인덱스만 클래스에서 색 지정을 수행 하는 데 필요 합니다 <xref:Microsoft.VisualStudio.Package.Colorizer> .

 구조체에 저장 된 색 인덱스는 <xref:Microsoft.VisualStudio.Package.TokenInfo> 일반적으로 열거형의 값으로 <xref:Microsoft.VisualStudio.Package.TokenColor> , 키워드 및 연산자와 같은 다양 한 언어 요소에 해당 하는 명명 된 많은 인덱스를 제공 합니다. 사용자 지정 색 항목 목록이 열거형에 표시 된 항목과 일치 하는 경우 <xref:Microsoft.VisualStudio.Package.TokenColor> 각 토큰의 색으로 열거를 사용 하면 됩니다. 그러나 추가 색 항목이 있거나 해당 순서로 기존 값을 사용 하지 않으려는 경우 사용자의 요구에 맞게 사용자 지정 색 항목 목록을 정렬 하 고 해당 목록에 적절 한 인덱스를 반환할 수 있습니다. 구조에 인덱스를 저장할 때 인덱스를로 캐스팅 해야 <xref:Microsoft.VisualStudio.Package.TokenColor> 합니다 .는 <xref:Microsoft.VisualStudio.Package.TokenInfo> [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] 인덱스만 볼 수 있습니다.

### <a name="example"></a>예
 다음 예제에서는 스캐너가 숫자, 문장 부호 및 식별자 (숫자 또는 문장 부호가 아닌 모든 항목)의 세 가지 토큰 형식을 식별 하는 방법을 보여 줍니다. 이 예제는 설명 목적 으로만 사용 되며 포괄적인 파서 및 스캐너 구현을 나타내지는 않습니다. 이 예제에서는 `Lexer` `GetNextToken()` 문자열을 반환 하는 메서드가 있는 클래스가 있다고 가정 합니다.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    private Lexer lex;

    public class TestScanner : IScanner
    {
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false;
            string token = lex.GetNextToken();
            if (token != null)
            {
                char firstChar = token[0];
                if (Char.IsPunctuation(firstChar))
                {
                    tokenInfo.Type = TokenType.Operator;
                    tokenInfo.Color = TokenColor.Keyword;
                }
                else if (Char.IsNumber(firstChar))
                {
                    tokenInfo.Type = TokenType.Literal;
                    tokenInfo.Color = TokenColor.Number;
                }
                else
                {
                    tokenInfo.Type = TokenType.Identifier;
                    tokenInfo.Color = TokenColor.Identifier;
                }
            }
            return foundToken;
        }
```

## <a name="see-also"></a>추가 정보
- [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)
- [레거시 언어 서비스 파서 및 검사기](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
- [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)
