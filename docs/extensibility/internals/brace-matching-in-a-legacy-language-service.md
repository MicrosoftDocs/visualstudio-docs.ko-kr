---
title: 레거시 언어 서비스에서 중괄호 매칭 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0081be3e3ab5a53f7d85f77475d4288aa5c87092
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709813"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>레거시 언어 서비스에서 중괄호 일치
중괄호 일치는 개발자가 괄호 및 중괄호와 같이 함께 발생해야 하는 언어 요소를 추적하는 데 도움이 됩니다. 개발자가 닫는 중괄호를 입력하면 열기 중괄호가 강조 표시됩니다.

 쌍과 트리플이라는 두 개 또는 세 개의 공동 발생 요소를 일치시킬 수 있습니다. 트리플은 세 가지 공동 발생 요소집합입니다. 예를 들어 C#에서 `foreach` 문은 세 개의 `foreach()` `{`를 `}`형성합니다. 닫는 중괄호를 입력하면 세 요소가 모두 강조 표시됩니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현되지만 언어 서비스 기능을 구현하는 최신 방법은 MEF 확장을 사용하는 것입니다. 중괄호 일치를 구현하는 새로운 방법에 대한 자세한 내용은 [연습: 일치하는 중괄호 표시를](../../extensibility/walkthrough-displaying-matching-braces.md)참조하십시오.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상되고 새로운 편집기 기능을 활용할 수 있습니다.

 클래스는 <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> 쌍과 <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> 메서드를 모두 지원합니다.

## <a name="implementation"></a>구현
 언어 서비스는 언어에서 일치하는 모든 요소를 식별한 다음 일치하는 모든 쌍을 찾아야 합니다. 이는 일반적으로 일치하는 언어를 <xref:Microsoft.VisualStudio.Package.IScanner> 검색하도록 구현한 다음 메서드를 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 사용하여 요소와 일치하도록 구현하여 수행됩니다.

 메서드는 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> 줄을 토큰화 하 고 바로 전에 토큰을 반환 하는 스캐너를 호출 합니다. 스캐너는 현재 토큰에 토큰 트리거 값을 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 설정하여 언어 요소 쌍이 발견되었음을 나타냅니다. 메서드는 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> 일치하는 <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> 언어 요소를 찾기 <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> <xref:Microsoft.VisualStudio.Package.ParseReason> 위해 구문 분석 이유 값으로 메서드를 호출하는 메서드를 호출합니다. 일치하는 언어 요소가 발견되면 두 요소가 모두 강조 표시됩니다.

 중괄호를 입력하면 중괄호 강조 표시가 트리거되는 방법에 대한 자세한 설명은 [레거시 언어 서비스 파서 및 스캐너](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)문서의 예제 *구문 분석 작업* 섹션을 참조하십시오.

## <a name="enable-support-for-brace-matching"></a>중괄호 일치 지원 사용
 특성은 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 클래스의 해당 속성을 설정하는 **MatchBraces,** **MatchBracesAtCaret**및 **ShowMatchingBrace** 레지스트리 항목을 설정할 수 있습니다. 언어 기본 설정 속성은 사용자가 설정할 수도 있습니다.

|레지스트리 항목|속성|설명|
|--------------------|--------------|-----------------|
|매치브레이스|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|중괄호 일치를 활성화합니다.|
|매치브레이스애트케어|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|카를트가 움직일 때 중괄호 일치를 활성화합니다.|
|쇼매칭브레이스|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|일치하는 중괄호를 강조 표시됩니다.|

## <a name="match-conditional-statements"></a>조건문 일치
 조건문(예: `if`" `else if`및 `else`, 및 `#if` `#elif`) `#else`" `#endif`및 및 S . 클래스를 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 하위 클래스로 분류하고 일치하는 요소의 내부 배열에 텍스트 범위와 구분 기호를 추가할 수 있는 메서드를 제공할 수 있습니다.

## <a name="set-the-trigger"></a>트리거 설정
 다음 예제에서는 일치하는 괄호, 중괄호 및 사각형 중괄호를 검색하고 스캐너에서 괄호에 대한 트리거를 설정하는 방법을 보여 주습니다. 클래스의 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> <xref:Microsoft.VisualStudio.Package.Source> 메서드는 트리거를 감지하고 파서를 호출하여 일치하는 쌍을 찾습니다(이 문서의 *일치 찾기* 섹션 참조). 이 예제는 설명용으로만 사용됩니다. 스캐너에 텍스트 줄에서 토큰을 식별하고 반환하는 메서드가 `GetNextToken` 포함되어 있다고 가정합니다.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private const string braces = "()[]{}";
        private Lexer lex;

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false;
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char firstChar = token[0];
                if (Char.IsPunctuation(firstChar) && token.Length > 0)
                {
                    if (braces.IndexOf(firstChar) != -1)
                    {
                        tokenInfo.Trigger = TokenTriggers.MatchBraces;
                    }
                }
            }
            return foundToken;
        }
```

## <a name="match-the-braces"></a>중괄호 일치
 다음은 `{ }`언어 요소 및 `( )` `[ ]`및 에 해당 범위를 개체에 추가하는 간단한 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 예제입니다. 이 방법은 소스 코드를 구문 분석하는 데 권장되지 않습니다. 이는 설명목적으로만 사용됩니다.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class Parser
    {
         private IList<TextSpan[]> m_braces;
         public IList<TextSpan[]> Braces
         {
             get { return m_braces; }
         }
         private void AddMatchingBraces(TextSpan braceSpan1, TextSpan braceSpan2)
         {
             if IsMatch(braceSpan1, braceSpan2)
                 m_braces.Add(new TextSpan[] { braceSpan1, braceSpan2 });
         }

         private bool IsMatch(TextSpan braceSpan1, TextSpan braceSpan2)
         {
             //definition for matching here
          }
    }

    public class TestLanguageService : LanguageService
    {
         Parser parser = new Parser();
         Source source = (Source) this.GetSource(req.FileName);

         private AuthoringScope ParseSource(ParseRequest req)
         {
             if (req.Sink.BraceMatching)
             {
                 if (req.Reason==ParseReason.MatchBraces)
                 {
                     foreach (TextSpan[] brace in parser.Braces)
                     {
                         req.Sink.MatchPair(brace[0], brace[1], 1);
                     }
                 }
             }
             return new TestAuthoringScope();
         }
    }
}
```

## <a name="see-also"></a>참조
- [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)
- [레거시 언어 서비스 파서 및 스캐너](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
