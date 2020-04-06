---
title: 레거시 언어 서비스 회원 완료 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6445aec4954590e4d361189f053592eebe7767e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707188"
---
# <a name="member-completion-in-a-legacy-language-service"></a>레거시 언어 서비스의 멤버 완성

IntelliSense 멤버 완료는 클래스, 구조체, 열거형 또는 네임스페이스와 같은 특정 범위의 가능한 멤버 목록을 표시하는 도구 설명입니다. 예를 들어 C#에서 사용자가 "this"를 입력한 다음 마침표가 있으면 현재 범위의 클래스 또는 구조체의 모든 구성원 목록이 사용자가 선택할 수 있는 목록에 표시됩니다.

MPF(관리되는 패키지 프레임워크)는 도구 설명및 도구 설명에서 목록을 관리하는 지원을 제공합니다. 필요한 것은 목록에 나타나는 데이터를 제공하는 파서의 협력입니다.

레거시 언어 서비스는 VSPackage의 일부로 구현되지만 언어 서비스 기능을 구현하는 최신 방법은 MEF 확장을 사용하는 것입니다. 자세한 내용은 [편집기 및 언어 서비스 확장을](../../extensibility/extending-the-editor-and-language-services.md)참조하십시오.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상되고 새로운 편집기 기능을 활용할 수 있습니다.

## <a name="how-it-works"></a>작동 방법

다음은 MPF 클래스를 사용하여 멤버 목록이 표시되는 두 가지 방법입니다.

- 식별자 또는 멤버 완료 문자 후에 캐러티를 배치하고 **IntelliSense** 메뉴에서 **목록 멤버를** 선택합니다.

- 스캐너는 <xref:Microsoft.VisualStudio.Package.IScanner> 멤버 완료 문자를 검색하고 해당 문자에 대해 [TokenTriggers.MemberSelect의 토큰 트리거를 설정합니다.](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)

멤버 완성 문자는 클래스, 구조체 또는 열거형의 멤버가 따라야 한다는 것을 나타냅니다. 예를 들어 C# 또는 Visual Basic에서 멤버 `.`완료 문자는 ". `.` `->` 트리거 값은 멤버 선택 문자를 검색할 때 설정됩니다.

### <a name="the-intellisense-member-list-command"></a>인텔리센스 멤버 목록 명령

명령은 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> <xref:Microsoft.VisualStudio.Package.Source> 클래스의 메서드에 대한 호출을 시작하고 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 메서드는 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> [ParseReason.DisplayMemberList의](<xref:Microsoft.VisualStudio.Package.ParseReason.DisplayMemberList>)구문 분석 이유를 사용하여 메서드 파서를 호출합니다.

파서는 현재 위치 아래 또는 바로 앞에 토큰뿐만 아니라 현재 위치의 컨텍스트를 결정합니다. 이 토큰을 기반으로 선언 목록이 표시됩니다. 예를 들어 C#에서 클래스 멤버에 caret를 배치하고 **구성원 목록(List Member)을**선택하면 클래스의 모든 구성원 목록이 표시됩니다. 개체 변수 다음에 오는 기간 다음에 캐번을 배치하면 개체가 나타내는 클래스의 모든 멤버 목록이 표시됩니다. 멤버 목록이 표시될 때 카포트가 멤버에 배치되면 목록에서 멤버를 선택하면 해당 멤버가 목록에 있는 멤버와 대체됩니다.

### <a name="the-token-trigger"></a>토큰 트리거

[TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 트리거는 <xref:Microsoft.VisualStudio.Package.Source> 클래스의 메서드에 대한 호출을 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 시작하고 메서드는 [ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>)의 구문 분석 이유를 사용하여 파서를 호출합니다. 토큰 트리거에 [TokenTriggers.MatchBraces](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MatchBraces>) 플래그도 포함된 경우 구문 분석 이유는 멤버 선택과 중괄호 강조 표시를 결합한 [ParseReason.MemberSelectAndHighlightBraces입니다.](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>)

파서는 현재 위치의 컨텍스트와 멤버 선택 문자 앞에 입력된 컨텍스트를 결정합니다. 이 정보에서 파서는 요청된 범위의 모든 구성원 목록을 만듭니다. 이 선언 목록은 메서드에서 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 반환되는 개체에 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 저장됩니다. 선언이 반환되면 멤버 완료 도구 설명이 표시됩니다. 도구 설명은 <xref:Microsoft.VisualStudio.Package.CompletionSet> 클래스의 인스턴스에 의해 관리됩니다.

## <a name="enable-support-for-member-completion"></a>회원 완료지원 활성화

IntelliSense `CodeSense` 작업을 지원하려면 레지스트리 항목을 1로 설정해야 합니다. 이 레지스트리 항목은 언어 패키지와 연결된 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 사용자 특성에 전달된 명명된 매개 변수로 설정할 수 있습니다. 언어 서비스 클래스는 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 클래스의 속성에서 이 레지스트리 항목의 값을 읽습니다.

스캐너가 [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)의 토큰 트리거를 반환하고 파서가 선언 목록을 반환하면 멤버 완료 목록이 표시됩니다.

## <a name="support-member-completion-in-the-scanner"></a>스캐너에서 지원 회원 완료

스캐너는 멤버 완료 문자를 감지하고 해당 문자가 구문 분석될 때 [TokenTriggers.MemberSelect의](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) 토큰 트리거를 설정할 수 있어야 합니다.

### <a name="scanner-example"></a>스캐너 예제

다음은 멤버 완료 문자를 검색하고 적절한 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 플래그를 설정하는 간단한 예입니다. 이 예제는 설명용으로만 사용됩니다. 스캐너에 텍스트 줄에서 토큰을 식별하고 반환하는 메서드가 `GetNextToken` 포함되어 있다고 가정합니다. 예제 코드는 올바른 종류의 문자를 볼 때마다 트리거를 설정하기만 하면 됩니다.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private Lexer lex;
        private const char memberSelectChar = '.';

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char c = token[0];
                if (c == memberSelectChar)
                {
                        tokenInfo.Trigger |= TokenTriggers.MemberSelect;
                }
            }
            return foundToken;
        }
    }
}
```

## <a name="support-member-completion-in-the-parser"></a>파서에서 지원 회원 완료

멤버 완료를 <xref:Microsoft.VisualStudio.Package.Source> 위해 클래스는 메서드를 호출합니다. <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> 클래스에서 파생 된 클래스에서 <xref:Microsoft.VisualStudio.Package.Declarations> 목록을 구현 해야 합니다. 구현해야 <xref:Microsoft.VisualStudio.Package.Declarations> 하는 방법에 대한 자세한 내용은 클래스를 참조하십시오.

파서는 멤버 선택 문자를 입력할 때 [ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>) 또는 [ParseReason.MemberSelectAndHighlightBraces로 호출됩니다.](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>) 개체에 <xref:Microsoft.VisualStudio.Package.ParseRequest> 지정된 위치는 멤버 선택 문자 바로 다음에 있습니다. 파서는 소스 코드의 특정 지점에서 구성원 목록에 나타날 수 있는 모든 멤버의 이름을 수집해야 합니다. 그런 다음 파서는 현재 줄을 구문 분석하여 사용자가 멤버 선택 문자와 연결하려는 범위를 결정해야 합니다.

이 범위는 멤버 선택 문자 앞에 있는 식별자의 유형을 기반으로 합니다. 예를 들어 C#에서 `languageService` `LanguageService`유형의 **typeing languageService가** 있는 멤버 변수가 있습니다. 을 따르면 모든 클래스 의 `LanguageService` 구성원 목록이 생성됩니다. 또한 C #에서 **이것을 입력합니다.** 을 사용하성으로 현재 범위의 모든 클래스 구성원 목록이 생성됩니다.

### <a name="parser-example"></a>파서 예제

다음 예제에서는 <xref:Microsoft.VisualStudio.Package.Declarations> 목록을 채우는 한 가지 방법을 보여 주며 있습니다. 이 코드는 파서가 선언을 생성하고 `AddDeclaration` `TestAuthoringScope` 클래스에서 메서드를 호출하여 목록에 추가한다고 가정합니다.

```csharp
using System.Collections;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    internal class TestDeclaration
    {
        public string Name;            // Name of declaration
        public int     TypeImageIndex; // Glyph index
        public string Description;     // Description of declaration

        public TestDeclaration(string name, int typeImageIndex, string description)
        {
            this.Name = name;
            this.TypeImageIndex = typeImageIndex;
            this.Description = description;
        }
    }

    //===================================================
    internal class TestDeclarations : Declarations
    {
        private ArrayList declarations;

        public TestDeclarations()
            : base()
        {
            declarations = new ArrayList();
        }

        public void AddDeclaration(TestDeclaration declaration)
        {
            declarations.Add(declaration);
        }

        //////////////////////////////////////////////////////////////////////
        // Declarations of class methods that must be implemented.
        public override int GetCount()
        {
            // Return the number of declarations to show.
            return declarations.Count;
        }

        public override string GetDescription(int index)
        {
            // Return the description of the specified item.
            string description = "";
            if (index >= 0 && index < declarations.Count)
            {
                description = ((TestDeclaration)declarations[index]).Description;
            }
            return description;
        }

        public override string GetDisplayText(int index)
        {
            // Determine what is displayed in the tool tip list.
            string text = null;
            if (index >= 0 && index < declarations.Count)
            {
                text = ((TestDeclaration)declarations[index]).Name;
            }
            return text;
        }

        public override int GetGlyph(int index)
        {
            // Return index of image to display next to the display text.
            int imageIndex = -1;
            if (index >= 0 && index < declarations.Count)
            {
                imageIndex = ((TestDeclaration)declarations[index]).TypeImageIndex;
            }
            return imageIndex;
        }

        public override string GetName(int index)
        {
            string name = null;
            if (index >= 0 && index < declarations.Count)
            {
                name = ((TestDeclaration)declarations[index]).Name;
            }
            return name;
        }
    }

    //===================================================
    public class TestAuthoringScope : AuthoringScope
    {
        private TestDeclarations declarationsList;

        public void AddDeclaration(TestDeclaration declaration)
        {
            if (declaration != null)
            {
                if (declarationsList == null)
                {
                    declarationsList = new TestDeclarations();
                }
                declarationsList.AddDeclaration(declaration);
            }
        }

        public override Declarations GetDeclarations(IVsTextView view,
                                                     int line,
                                                     int col,
                                                     TokenInfo info,
                                                     ParseReason reason)
        {
            return declarationsList;
        }

        /////////////////////////////////////////////////
        // Remainder of AuthoringScope methods not shown.
        /////////////////////////////////////////////////
    }

    //===================================================
    class TestLanguageService : LanguageService
    {
        public override AuthoringScope ParseSource(ParseRequest req)
        {
            TestAuthoringScope scope = new TestAuthoringScope();
            if (req.Reason == ParseReason.MemberSelect ||
                req.Reason == ParseReason.MemberSelectAndHighlightBraces)
            {
                // Gather list of declarations based on what the user
                // has typed so far. In this example, this list is an array of
                // MemberDeclaration objects (a helper class you might implement
                // to hold member declarations).
                // How this list is gathered is dependent on the parser
                // and is not shown here.
                MemberDeclarations memberDeclarations;
                memberDeclarations = GetDeclarationsForScope();

                // Now populate the Declarations list in the authoring scope.
                // GetImageIndexBasedOnType() is a helper method you
                // might implement to convert a member type to an index into
                // the image list returned from the language service.
                foreach (MemberDeclaration dec in memberDeclarations)
                {
                    scope.AddDeclaration(new TestDeclaration(
                                             dec.Name,
                                             GetImageIndexBasedOnType(dec.Type),
                                             dec.Description));
                }
            }
            return scope;
        }
    }
}
```
