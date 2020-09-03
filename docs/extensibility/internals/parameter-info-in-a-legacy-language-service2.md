---
title: 레거시 언어 Service2의 매개 변수 정보 | Microsoft Docs
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
ms.openlocfilehash: dff6e871320d0727ed2fbec4188e8f7af2e5c5fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88237960"
---
# <a name="parameter-info-in-a-legacy-language-service-2"></a>레거시 언어 서비스의 매개 변수 정보 2
IntelliSense 매개 변수 정보는 사용자가 메서드 매개 변수 목록에 대 한 매개 변수 목록 시작 문자 (일반적으로 여는 괄호)를 입력 하는 경우 메서드의 시그니처를 표시 하는 도구 설명입니다. 각 매개 변수를 입력 하 고 매개 변수 구분 기호 (일반적으로 쉼표)를 입력 하면 도구 설명이 업데이트 되어 다음 매개 변수가 굵게 표시 됩니다.

 MPF (관리 되는 패키지 프레임 워크) 클래스는 매개 변수 정보 도구 설명을 관리 하는 기능을 제공 합니다. 파서는 매개 변수 시작, 매개 변수 다음 및 매개 변수 끝 문자를 검색 해야 하 고 메서드 시그니처와 연결 된 매개 변수 목록을 제공 해야 합니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현 되지만 언어 서비스 기능을 구현 하는 최신 방법은 MEF 확장을 사용 하는 것입니다. 자세히 알아보려면 [편집기 및 언어 서비스 확장](../../extensibility/extending-the-editor-and-language-services.md)을 참조 하세요.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용 하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.

## <a name="implementation"></a>구현
 파서는 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 매개 변수 목록 시작 문자 (종종 여는 괄호)를 찾을 때 설정 되는 트리거 값을 설정 해야 합니다. <xref:Microsoft.VisualStudio.Package.TokenTriggers>매개 변수 구분 기호 (종종 쉼표)를 찾으면 트리거를 설정 해야 합니다. 이렇게 하면 매개 변수 정보 도구 설명이 업데이트 되 고 다음 매개 변수는 굵게 표시 됩니다. <xref:Microsoft.VisualStudio.Package.TokenTriggers>이 매개 변수 목록 끝 문자 (종종 닫는 괄호)를 찾을 때 파서는 트리거 값을 설정 해야 합니다.

 <xref:Microsoft.VisualStudio.Package.TokenTriggers>트리거 값은 메서드에 대 한 호출을 시작 하며 <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> ,이는 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 구문 분석 이유를 사용 하 여 메서드 파서를 호출 합니다 <xref:Microsoft.VisualStudio.Package.ParseReason> . 파서에서 매개 변수 목록 시작 문자 앞의 식별자가 인식 되는 메서드 이름인 것으로 확인 되 면 개체에서 일치 하는 메서드 시그니처의 목록을 반환 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 합니다. 메서드 시그니처를 찾은 경우 목록에 첫 번째 서명이 포함 된 매개 변수 정보 도구 설명이 표시 됩니다. 그러면이 도구 설명이 더 많은 서명이 입력 될 때 업데이트 됩니다. 매개 변수 목록 끝 문자를 입력 하면 매개 변수 정보 도구 설명이 뷰에서 제거 됩니다.

> [!NOTE]
> 매개 변수 정보 도구 설명이 올바른 형식으로 지정 되도록 하려면 클래스의 속성을 재정의 하 여 <xref:Microsoft.VisualStudio.Package.Methods> 적절 한 문자를 제공 해야 합니다. 기본 <xref:Microsoft.VisualStudio.Package.Methods> 클래스는 c # 스타일 메서드 시그니처를 가정 합니다. <xref:Microsoft.VisualStudio.Package.Methods>이 작업을 수행 하는 방법에 대 한 자세한 내용은 클래스를 참조 하십시오.

## <a name="enabling-support-for-the-parameter-info"></a>매개 변수 정보에 대 한 지원 사용
 매개 변수 정보 도구 설명을 지원 하려면 `ShowCompletion` 의 명명 된 매개 변수를로 설정 해야 합니다 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> `true` . 언어 서비스는 속성에서이 레지스트리 항목의 값을 읽습니다 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> .

 또한 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> `true` 매개 변수 정보 도구 설명이 표시 되려면 속성을로 설정 해야 합니다.

### <a name="example"></a>예
 다음은 매개 변수 목록 문자를 검색 하 고 적절 한 트리거를 설정 하는 간단한 예입니다. 이 예는 설명을 위한 목적 으로만 사용 됩니다. 스캐너에는 `GetNextToken` 텍스트 줄에서 토큰을 식별 하 고 반환 하는 메서드가 포함 되어 있다고 가정 합니다. 예제 코드에서는 올바른 종류의 문자가 표시 될 때마다 트리거를 설정 하기만 하면 됩니다.

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

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>파서에서 매개 변수 정보 도구 설명 지원
 <xref:Microsoft.VisualStudio.Package.Source>클래스는 <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.AuthoringSink> 매개 변수 정보 도구 설명이 표시 되 고 업데이트 될 때 및 클래스의 내용에 대해 몇 가지 가정을 합니다.

- <xref:Microsoft.VisualStudio.Package.ParseReason>매개 변수 목록 시작 문자를 입력 하면 파서가 제공 됩니다.

- 개체에 지정 된 위치는 <xref:Microsoft.VisualStudio.Package.ParseRequest> 매개 변수 목록 시작 문자 바로 뒤에 있습니다. 파서는 해당 위치에서 사용할 수 있는 모든 메서드 선언의 서명을 수집 하 여 개체 버전의 목록에 저장 해야 합니다 <xref:Microsoft.VisualStudio.Package.AuthoringScope> . 이 목록에는 메서드 이름, 메서드 형식 (또는 반환 형식) 및 가능한 매개 변수 목록이 포함 됩니다. 이 목록은 나중에 매개 변수 정보 도구 설명에 표시할 메서드 시그니처 또는 서명을 검색 합니다.

  그러면 파서가 개체에서 지정 된 줄을 구문 분석 <xref:Microsoft.VisualStudio.Package.ParseRequest> 하 여 입력 되는 메서드의 이름과 사용자가 매개 변수를 입력 하는 거리를 수집 해야 합니다. 이렇게 하려면 메서드 이름을 <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> 개체의 메서드에 전달 하 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 고 매개 변수 목록 시작 문자를 구문 분석할 때 메서드를 호출 하 고, 매개 변수 목록 다음 문자를 구문 분석할 때 메서드를 호출 하 <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> 고, <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> 매개 변수 목록 끝 문자를 구문 분석할 때 메서드를 호출 하 여 수행 합니다. 이러한 메서드 호출의 결과는 <xref:Microsoft.VisualStudio.Package.Source> 클래스에서 매개 변수 정보 도구 설명을 적절 하 게 업데이트 하는 데 사용 됩니다.

### <a name="example"></a>예
 사용자가 입력할 수 있는 텍스트 줄은 다음과 같습니다. 줄 아래의 숫자는 줄의 해당 위치에서 파서가 수행 하는 단계를 표시 합니다. 구문 분석은 왼쪽에서 오른쪽으로 이동 합니다. 여기서는 줄 앞의 모든 항목이 "testfunc" 메서드 시그니처를 포함 하 여 메서드 시그니처에 대해 이미 구문 분석 되었음을 전제로 합니다.

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 파서에서 사용 하는 단계는 아래에 설명 되어 있습니다.

1. 파서는 <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> "testfunc" 텍스트를 사용 하 여를 호출 합니다.

2. 파서가를 호출 합니다 <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> .

3. 파서가를 호출 합니다 <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> .

4. 파서가를 호출 합니다 <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> .
