---
title: 레거시 언어 서비스에서 색지정 구문 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704701"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>레거시 언어 서비스의 구문 색 지정
구문 색지정은 프로그래밍 언어의 다른 요소를 서로 다른 색상과 스타일로 소스 파일에 표시하도록 하는 기능입니다. 이 기능을 지원하려면 파일의 어휘 요소 또는 토큰 유형을 식별할 수 있는 파서 또는 스캐너를 제공해야 합니다. 많은 언어는 키워드, 구분기호(예: 괄호 또는 중괄호) 및 주석을 다른 방식으로 색칠하여 구분합니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현되지만 언어 서비스 기능을 구현하는 최신 방법은 MEF 확장을 사용하는 것입니다. 자세한 내용은 [편집기 및 언어 서비스 확장을](../../extensibility/extending-the-editor-and-language-services.md)참조하십시오.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상되고 새로운 편집기 기능을 활용할 수 있습니다.

## <a name="implementation"></a>구현
 색상화를 지원하기 위해 관리되는 패키지 프레임워크(MPF)에는 <xref:Microsoft.VisualStudio.Package.Colorizer> 인터페이스를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 구현하는 클래스가 포함됩니다. 이 클래스는 토큰 <xref:Microsoft.VisualStudio.Package.IScanner> 및 색상을 결정하기 위해 a와 상호 작용합니다. 스캐너에 대한 자세한 내용은 [레거시 언어 서비스 파서 및 스캐너를](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)참조하십시오. 그런 <xref:Microsoft.VisualStudio.Package.Colorizer> 다음 클래스는 토큰의 각 문자를 색상 정보로 표시하고 해당 정보를 원본 파일을 표시하는 편집기로 반환합니다.

 편집기로 반환되는 색상 정보는 색 항목 목록으로 의한 인덱스입니다. 각 색 항목은 색상 값과 굵게 또는 스트라이크스루와 같은 글꼴 속성 집합을 지정합니다. 편집기는 언어 서비스에서 사용할 수 있는 기본 색상 항목 집합을 제공합니다. 각 토큰 유형에 적합한 색상 인덱스를 지정하기만 하면 됩니다. 그러나 사용자 지정 색상 항목 집합과 토큰에 대해 제공하는 인덱스를 제공하고 기본 목록 대신 고유한 색 항목 목록을 참조할 수 있습니다. 또한 사용자 지정 `RequestStockColors` 색상을 지원하려면 레지스트리 항목을 0으로 설정하거나 `RequestStockColors` 항목을 전혀 지정하지 않아야 합니다. 명명된 매개 변수를 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 사용하여 이 레지스트리 항목을 사용자 정의 특성으로 설정할 수 있습니다. 언어 서비스 등록 및 옵션 설정에 대한 자세한 내용은 [레거시 언어 서비스 등록을](../../extensibility/internals/registering-a-legacy-language-service1.md)참조하십시오.

## <a name="custom-colorable-items"></a>사용자 지정 색 항목
 사용자 지정 색상 항목을 제공하려면 클래스의 <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> 메서드와 <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> 메서드를 <xref:Microsoft.VisualStudio.Package.LanguageService> 재정의해야 합니다. 첫 번째 메서드는 언어 서비스가 지원하는 사용자 지정 색상 항목 수를 반환하고 두 번째 방법은 인덱스별로 사용자 지정 색상 항목을 가져옵니다. 사용자 지정 색상 항목의 기본 목록을 만듭니다. 언어 서비스의 생성자에서 각 색 항목에 이름을 제공하기만 하면 됩니다. Visual Studio는 사용자가 다른 색 항목 집합을 선택하는 경우를 자동으로 처리합니다. 이 이름은 **옵션** 대화 상자의 **글꼴 및 색상** 속성 페이지에 표시되는 이름입니다(Visual Studio **도구** 메뉴에서 사용 가능)이 이름은 사용자가 재정의한 색상을 결정합니다. 사용자의 선택 사항은 레지스트리의 캐시에 저장되고 색상 이름으로 액세스됩니다. **글꼴 및 색상** 속성 페이지에는 모든 색상 이름이 알파벳 순으로 나열되므로 언어 이름과 함께 각 색상 이름 앞에 지정 색상을 그룹화할 수 있습니다. 예를 들어,**"testLanguage- 코멘트"** 및 **"testLanguage- 키워드**". 또는 유형별로 색 항목을 그룹화할**Comment (TestLanguage)** 수 있습니다.**Keyword (TestLanguage)** 언어 이름으로 그룹화하는 것이 좋습니다.

> [!CAUTION]
> 기존 색상 항목 이름과 충돌하지 않도록 색상 항목 이름에 언어 이름을 포함하는 것이 좋습니다.

> [!NOTE]
> 개발 중에 색상 중 하나의 이름을 변경하는 경우 Visual Studio에서 처음 색상에 액세스할 때 만든 캐시를 다시 설정해야 합니다. Visual Studio SDK 프로그램 메뉴에서 **실험 하이브 재설정** 명령을 실행하여 수행할 수 있습니다.

 색상 항목 목록의 첫 번째 항목은 참조되지 않습니다. Visual Studio는 항상 해당 항목에 대한 기본 텍스트 색상 및 속성을 제공합니다. 이 문제를 처리하는 가장 쉬운 방법은 자리 표시자 색상 항목을 첫 번째 항목으로 제공하는 것입니다.

### <a name="high-color-colorable-items"></a>높은 색상 색상 항목
 색상 항목은 인터페이스를 통해 24비트 또는 높은 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 색상 값을 지원할 수도 있습니다. MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> 클래스는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 인터페이스를 지원하며 24비트 색상은 일반 색상과 함께 생성자에서 지정됩니다. 자세한 내용은 <xref:Microsoft.VisualStudio.Package.ColorableItem> 클래스를 참조하십시오. 아래 예제에서는 키워드 및 댓글의 24비트 색상을 설정하는 방법을 보여 주며, 이 에 대한 24비트 색상을 보여 주시면 됩니다. 24비트 색상은 사용자의 바탕 화면에서 24비트 색상을 지원할 때 사용됩니다. 그렇지 않으면 일반 텍스트 색상이 사용됩니다.

 이러한 색상은 해당 언어의 기본 색상입니다. 사용자는 이러한 색상을 원하는 색상으로 변경할 수 있습니다.

### <a name="example"></a>예제
 이 예제에서는 클래스를 사용하여 사용자 지정 색상 항목의 <xref:Microsoft.VisualStudio.Package.ColorableItem> 배열을 선언하고 채우는 한 가지 방법을 보여 주며 있습니다. 이 예제는 24비트 색상을 사용하여 키워드 및 주석 색상을 설정합니다.

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

## <a name="the-colorizer-class-and-the-scanner"></a>컬러라이저 클래스와 스캐너
 기본 <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스에는 <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> 클래스를 인스턴스화하는 <xref:Microsoft.VisualStudio.Package.Colorizer> 메서드가 있습니다. <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 메서드에서 반환되는 스캐너는 <xref:Microsoft.VisualStudio.Package.Colorizer> 클래스 생성자에게 전달됩니다.

 메서드를 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 고유한 <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스 버전에서 구현해야 합니다. 클래스는 <xref:Microsoft.VisualStudio.Package.Colorizer> 스캐너를 사용하여 모든 토큰 색상 정보를 가져옵니다.

 스캐너는 찾은 모든 <xref:Microsoft.VisualStudio.Package.TokenInfo> 토큰에 대한 구조를 채워야 합니다. 이 구조에는 토큰이 차지하는 범위, 사용할 색상 인덱스, 토큰유형 및 토큰 트리거와 같은 <xref:Microsoft.VisualStudio.Package.TokenTriggers>정보가 포함됩니다(참조). <xref:Microsoft.VisualStudio.Package.Colorizer> 클래스별로 색상화에는 범위와 색상 인덱스만 필요합니다.

 <xref:Microsoft.VisualStudio.Package.TokenInfo> 구조에 저장된 색상 인덱스는 일반적으로 키워드 <xref:Microsoft.VisualStudio.Package.TokenColor> 및 연산자와 같은 다양한 언어 요소에 해당하는 명명된 인덱스를 제공하는 열거형의 값입니다. 사용자 지정 색상 항목 목록이 <xref:Microsoft.VisualStudio.Package.TokenColor> 열거형에 표시되는 항목과 일치하는 경우 열거형항목을 각 토큰의 색상으로 사용할 수 있습니다. 그러나 추가 색 항목이 있거나 해당 순서로 기존 값을 사용하지 않으려면 필요에 맞게 사용자 지정 색상 항목 목록을 정렬하고 해당 목록에 적절한 인덱스를 반환할 수 있습니다. 구조에 저장할 때 인덱스를 <xref:Microsoft.VisualStudio.Package.TokenColor> a로 캐스팅하십시오. <xref:Microsoft.VisualStudio.Package.TokenInfo> [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] 인덱스만 볼 수 있습니다.

### <a name="example"></a>예제
 다음 예제에서는 스캐너가 숫자, 문장 부호 및 식별자(숫자나 문장 부호가 아닌 모든 것)의 세 가지 토큰 유형을 식별하는 방법을 보여 주며, 이 두 가지 토큰 유형을 식별합니다. 이 예제는 설명용으로만 사용되며 포괄적인 파서 및 스캐너 구현을 나타내지 않습니다. 문자열을 반환 하는 `Lexer` 메서드가 `GetNextToken()` 있는 클래스가 있다고 가정 합니다.

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

## <a name="see-also"></a>참조
- [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)
- [레거시 언어 서비스 파서 및 검사기](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
- [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)
