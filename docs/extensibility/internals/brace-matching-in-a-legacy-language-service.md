---
title: 레거시 언어 서비스의 중괄호 일치 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709813"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>레거시 언어 서비스의 중괄호 일치
중괄호 일치는 괄호 및 중괄호와 같이 함께 발생 해야 하는 언어 요소를 개발자가 추적 하는 데 도움이 됩니다. 개발자가 닫는 중괄호를 입력 하면 여는 중괄호가 강조 표시 됩니다.

 쌍 및 삼중 쌍 라는 두 개 또는 세 개의 공동 발생 요소를 일치 시킬 수 있습니다. 삼중 쌍는 세 개의 공동 발생 요소 집합입니다. 예를 들어 c #에서 `foreach` 문은 삼중: `foreach()` , 및를 형성 `{` `}` 합니다. 닫는 중괄호가 입력 되 면 세 요소가 모두 강조 표시 됩니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현 되지만 언어 서비스 기능을 구현 하는 최신 방법은 MEF 확장을 사용 하는 것입니다. 중괄호 일치를 구현 하는 새로운 방법에 대해 자세히 알아보려면 [연습: 일치 하는 중괄호 표시](../../extensibility/walkthrough-displaying-matching-braces.md)를 참조 하세요.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용 하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.

 <xref:Microsoft.VisualStudio.Package.AuthoringSink>클래스는 및 메서드를 사용 하 여 쌍과 삼중 쌍을 모두 지원 <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> 합니다.

## <a name="implementation"></a>구현
 언어 서비스는 언어에서 일치 하는 모든 요소를 식별 한 다음 일치 하는 모든 쌍을 찾아야 합니다. 이는 일반적으로를 구현 하 여 <xref:Microsoft.VisualStudio.Package.IScanner> 일치 하는 언어를 검색 한 다음 메서드를 사용 하 여 요소를 일치 시키는 방법으로 수행 됩니다 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> .

 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>메서드는 스캐너를 호출 하 여 줄을 토큰화 하 고 캐럿 바로 앞에 토큰을 반환 합니다. 스캐너는 현재 토큰에서 토큰 트리거 값을 설정 하 여 언어 요소 쌍이 발견 되었음을 나타냅니다 <xref:Microsoft.VisualStudio.Package.TokenTriggers> . 메서드는 메서드 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> 를 호출 합니다 <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> .이 메서드는 구문 분석 이유 값을 사용 하 여 메서드를 호출 하 여 일치 하는 <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> <xref:Microsoft.VisualStudio.Package.ParseReason> 언어 요소를 찾습니다. 일치 하는 언어 요소가 발견 되 면 두 요소가 모두 강조 표시 됩니다.

 중괄호를 입력 하는 방법에 대 한 자세한 설명은 중괄호를 입력 하는 방법에 대 한 자세한 내용은 [레거시 언어 서비스 파서 및 스캐너](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)문서에서 *예제 구문 분석 작업* 섹션을 참조 하세요.

## <a name="enable-support-for-brace-matching"></a>중괄호 일치 지원 사용
 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>특성은 클래스의 해당 속성을 설정 하는 **matchbraces**, **MatchBracesAtCaret**및 **ShowMatchingBrace** 레지스트리 항목을 설정할 수 있습니다 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> . 사용자가 언어 기본 설정 속성을 설정할 수도 있습니다.

|레지스트리 항목|속성|설명|
|--------------------|--------------|-----------------|
|MatchBraces|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|중괄호 일치를 사용 합니다.|
|MatchBracesAtCaret|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|캐럿이 이동할 때 중괄호 일치를 사용 하도록 설정 합니다.|
|ShowMatchingBrace|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|짝이 되는 중괄호를 강조 표시 합니다.|

## <a name="match-conditional-statements"></a>조건문 일치
 `if` `else if` `else` `#if` `#elif` `#else` `#endif` 일치 하는 구분 기호와 같은 방식으로,,,,,,, 등의 조건문을 일치 시킬 수 있습니다. 클래스의 서브 클래스를 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 지정 하 고 일치 하는 요소의 내부 배열에 구분 기호 뿐만 아니라 텍스트 범위를 추가할 수 있는 메서드를 제공할 수 있습니다.

## <a name="set-the-trigger"></a>트리거 설정
 다음 예제에서는 일치 하는 괄호, 중괄호 및 대괄호를 검색 하 고 스캐너에서 트리거를 설정 하는 방법을 보여 줍니다. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>클래스의 메서드는 <xref:Microsoft.VisualStudio.Package.Source> 트리거를 검색 하 고 파서를 호출 하 여 일치 하는 쌍을 찾습니다 (이 문서의 *일치 항목 찾기* 섹션 참조). 이 예는 설명을 위한 목적 으로만 사용 됩니다. 스캐너에는 `GetNextToken` 텍스트 줄에서 토큰을 식별 하 고 반환 하는 메서드가 포함 되어 있다고 가정 합니다.

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
 다음은 언어 요소, `{ }` `( )` 및를 일치 하 `[ ]` 고 해당 범위를 개체에 추가 하는 간단한 예제입니다 <xref:Microsoft.VisualStudio.Package.AuthoringSink> . 이 방법은 소스 코드를 구문 분석 하는 데 권장 되는 방법이 아닙니다. 설명 목적 으로만 사용 됩니다.

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

## <a name="see-also"></a>추가 정보
- [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)
- [레거시 언어 서비스 파서 및 스캐너](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
