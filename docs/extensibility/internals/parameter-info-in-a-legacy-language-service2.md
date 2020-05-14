---
title: 레거시 언어 서비스의 매개 변수 정보2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e2c40c9ca5c038a70714545f4133db0c0dd686d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706744"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>레거시 언어 서비스의 매개 변수 정보
IntelliSense 매개 변수 정보는 사용자가 메서드 매개 변수 목록에 대한 매개 변수 목록 시작 문자(일반적으로 열린 괄호)를 입력할 때 메서드의 서명을 표시하는 도구 설명입니다. 각 매개 변수를 입력하고 매개 변수 구분 기호(일반적으로 쉼표)를 입력하면 도구 설명이 업데이트되어 다음 매개 변수를 굵게 표시합니다.

 MPF(관리되는 패키지 프레임워크) 클래스는 매개 변수 정보 도구 설명 관리를 지원합니다. 파서는 매개 변수 시작, 매개 변수 다음 및 매개 변수 끝 문자를 검색해야 하며 메서드 서명 및 관련 매개 변수 목록을 제공해야 합니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현되지만 언어 서비스 기능을 구현하는 최신 방법은 MEF 확장을 사용하는 것입니다. 자세한 내용은 [편집기 및 언어 서비스 확장을](../../extensibility/extending-the-editor-and-language-services.md)참조하십시오.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상되고 새로운 편집기 기능을 활용할 수 있습니다.

## <a name="implementation"></a>구현
 파서는 매개 변수 목록 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 시작 문자(종종 열린 괄호)를 찾을 때 트리거 값이 설정됩니다. 매개 변수 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 구분 기호(종종 쉼표)를 찾을 때 트리거를 설정해야 합니다. 이렇게 하면 매개 변수 정보 도구 설명이 업데이트되고 다음 매개 변수가 굵게 표시됩니다. 파서는 매개 변수 목록 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 끝 문자(종종 가까운 괄호)를 찾을 때 트리거 값을 설정해야 합니다.

 트리거 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 값은 <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> 메서드에 대한 호출을 시작하며, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 메서드파서는 <xref:Microsoft.VisualStudio.Package.ParseReason>의 구문 분석 이유를 사용하여 메서드 파서를 호출합니다. 파서가 매개 변수 목록 시작 문자 이전의 식별자가 인식된 메서드 이름이라고 판단하면 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 개체에서 일치하는 메서드 시그니처 목록을 반환합니다. 메서드 서명이 발견되면 매개 변수 정보 도구 설명이 목록의 첫 번째 서명과 함께 표시됩니다. 그런 다음 더 많은 서명이 입력되면 이 도구 설명이 업데이트됩니다. 매개 변수 목록 끝 문자를 입력하면 매개 변수 정보 도구 설명이 보기에서 제거됩니다.

> [!NOTE]
> 매개 변수 정보 도구 설명의 서식이 제대로 지정되도록 하려면 <xref:Microsoft.VisualStudio.Package.Methods> 클래스의 속성을 재정의하여 적절한 문자를 제공해야 합니다. 기본 <xref:Microsoft.VisualStudio.Package.Methods> 클래스는 C#스타일 메서드 서명을 가정합니다. 이 <xref:Microsoft.VisualStudio.Package.Methods> 작업을 수행하는 방법에 대한 자세한 내용은 클래스를 참조하십시오.

## <a name="enabling-support-for-the-parameter-info"></a>매개 변수 정보에 대한 지원 사용
 매개 변수 정보 도구 설명을 `ShowCompletion` 지원하려면 의 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> `true`명명된 매개 변수를 으로 설정해야 합니다. 언어 서비스는 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> 속성에서 이 레지스트리 항목의 값을 읽습니다.

 또한 매개 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> 변수 정보 도구 `true` 설명이 표시되려면 속성을 설정해야 합니다.

### <a name="example"></a>예제
 다음은 매개 변수 목록 문자를 검색하고 적절한 트리거를 설정하는 간단한 예입니다. 이 예제는 설명용으로만 사용됩니다. 스캐너에 텍스트 줄에서 토큰을 식별하고 반환하는 메서드가 `GetNextToken` 포함되어 있다고 가정합니다. 예제 코드는 올바른 종류의 문자를 볼 때마다 트리거를 설정하기만 하면 됩니다.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private Lexer lex;
        private const char parameterListStartChar = '(';
        private const char parameterListEndChar   = ')';
        private const char parameterNextChar      = ',';

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char c = token[0];
                if (Char.IsPunctuation(c))
                {
                    tokenInfo.Type = TokenType.Operator;
                    tokenInfo.Color = TokenColor.Keyword;
                    tokenInfo.EndIndex = index;

                    if (c == parameterListStartChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterStart;
                    }
                    else if (c == parameterListNextChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterNext;
                    else if (c == parameterListEndChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterEnd;
                    }
                }
            return foundToken;
        }
    }
}
```

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>파서에서 매개 변수 정보 도구 팁 지원
 클래스는 <xref:Microsoft.VisualStudio.Package.Source> 매개 변수 정보 도구 설명이 표시되고 업데이트될 때 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 및 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 클래스의 내용에 대해 몇 가지 가정을 합니다.

- 파서는 매개 <xref:Microsoft.VisualStudio.Package.ParseReason> 변수 목록 시작 문자를 입력할 때 지정됩니다.

- 개체에 <xref:Microsoft.VisualStudio.Package.ParseRequest> 지정된 위치는 매개 변수 목록 시작 문자 바로 입니다. 파서는 해당 위치에서 사용할 수 있는 모든 메서드 선언의 서명을 수집하고 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 개체 버전의 목록에 저장해야 합니다. 이 목록에는 메서드 이름, 메서드 유형(또는 반환 형식) 및 가능한 매개 변수 목록이 포함됩니다. 이 목록은 나중에 매개 변수 정보 도구 설명에 표시할 메서드 서명 또는 서명을 검색합니다.

  그런 다음 파서는 <xref:Microsoft.VisualStudio.Package.ParseRequest> 개체가 지정한 줄을 구문 분석하여 입력할 메서드의 이름과 사용자가 매개 변수를 입력하는 정도를 수집해야 합니다. 이 <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> 작업은 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 메서드의 이름을 개체의 메서드에 전달한 다음 매개 <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> 변수 목록 시작 문자가 구문 분석될 때 메서드를 호출하고 매개 변수 목록 다음 문자가 구문 분석될 때 <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> 메서드를 호출하고 매개 변수 목록 끝 문자가 구문 분석될 때 메서드를 호출하여 <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> 수행됩니다. 이러한 메서드 호출의 결과는 클래스에서 <xref:Microsoft.VisualStudio.Package.Source> 매개 변수 정보 도구 설명을 적절하게 업데이트하는 데 사용됩니다.

### <a name="example"></a>예제
 다음은 사용자가 입력할 수 있는 텍스트 줄입니다. 줄 아래의 숫자는 줄의 해당 위치에서 파서가 취한 단계를 나타냅니다(구문 분석이 왼쪽에서 오른쪽으로 이동한다고 가정). 여기서 가정은 "testfunc" 메서드 시그니처를 포함하여 줄 이전의 모든 것이 메서드 시그니처에 대해 구문 분석되었다는 것입니다.

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 파서가 취하는 단계는 다음과 같습니다.

1. 파서는 텍스트 <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> "testfunc"와 함께 호출합니다.

2. 파서는 을 <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>호출합니다.

3. 파서는 을 <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>호출합니다.

4. 파서는 을 <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>호출합니다.
