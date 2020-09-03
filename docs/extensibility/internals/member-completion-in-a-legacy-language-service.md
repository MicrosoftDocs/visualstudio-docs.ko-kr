---
title: 레거시 언어 서비스의 멤버 완료 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707188"
---
# <a name="member-completion-in-a-legacy-language-service"></a>레거시 언어 서비스의 멤버 완성

IntelliSense 멤버 완성은 클래스, 구조체, 열거형 또는 네임 스페이스와 같은 특정 범위의 가능한 멤버 목록을 표시 하는 도구 설명입니다. 예를 들어 c #에서 사용자가 "this"를 입력 하 고 마침표를 입력 하면 현재 범위에 있는 클래스 또는 구조체의 모든 멤버 목록이 사용자가 선택할 수 있는 목록에 표시 됩니다.

MPF (관리 되는 패키지 프레임 워크)는 도구 설명에 대 한 지원을 제공 하 고 도구 설명의 목록 관리를 제공 합니다. 목록에 표시 되는 데이터를 제공 하는 데 필요한 모든 것이 파서에서 협력 됩니다.

레거시 언어 서비스는 VSPackage의 일부로 구현 되지만 언어 서비스 기능을 구현 하는 최신 방법은 MEF 확장을 사용 하는 것입니다. 자세히 알아보려면 [편집기 및 언어 서비스 확장](../../extensibility/extending-the-editor-and-language-services.md)을 참조 하세요.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용 하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.

## <a name="how-it-works"></a>작동 방법

다음은 MPF 클래스를 사용 하 여 멤버 목록을 표시 하는 두 가지 방법입니다.

- 식별자에 캐럿을 배치 하거나 멤버 완성 문자 뒤에 **IntelliSense** 메뉴에서 **멤버 나열** 을 선택 합니다.

- <xref:Microsoft.VisualStudio.Package.IScanner>스캐너는 구성원 완성 문자를 검색 하 고 해당 문자에 대 한 [TokenTriggers](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) 의 토큰 트리거를 설정 합니다.

멤버 완성 문자는 클래스, 구조체 또는 열거형의 멤버가 따라야 함을 나타냅니다. 예를 들어 c # 또는 Visual Basic 멤버 완성 문자는 이며 `.` c + +에서 문자는 `.` 또는 `->` 입니다. 트리거 값은 멤버 선택 문자를 검색할 때 설정 됩니다.

### <a name="the-intellisense-member-list-command"></a>IntelliSense 멤버 목록 명령

<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>명령은 클래스의 메서드에 대 한 호출을 시작 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> <xref:Microsoft.VisualStudio.Package.Source> 하 고 메서드는 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> [ParseReason](<xref:Microsoft.VisualStudio.Package.ParseReason.DisplayMemberList>)의 구문 분석 이유를 사용 하 여 메서드 파서를 호출 합니다.

파서는 현재 위치의 컨텍스트 및 현재 위치 바로 앞에 있는 토큰을 확인 합니다. 이 토큰을 기반으로 선언 목록이 표시 됩니다. 예를 들어 c #에서 캐럿을 클래스 멤버에 배치 하 고 **멤버 목록**을 선택 하는 경우 클래스의 모든 멤버 목록을 가져옵니다. 개체 변수 다음에 오는 마침표 뒤에 캐럿을 배치 하면 개체가 나타내는 클래스의 모든 멤버 목록이 표시 됩니다. 멤버 목록이 표시 될 때 캐럿이 멤버에 배치 되는 경우 목록에서 멤버를 선택 하면 캐럿이 있는 멤버가 목록에 있는 멤버로 바뀝니다.

### <a name="the-token-trigger"></a>토큰 트리거

[TokenTriggers](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) 트리거는 클래스의 메서드에 대 한 호출을 시작 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> <xref:Microsoft.VisualStudio.Package.Source> 하 고, <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 메서드는 구문 분석 이유를 [ParseReason](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>)로 설정 하 여 파서를 호출 합니다. 토큰 트리거에서 [TokenTriggers](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MatchBraces>) 플래그도 포함 하는 경우 구문 분석 이유는 멤버 선택 및 중괄호 강조 표시를 결합 하는 [MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>)입니다.

파서는 현재 위치의 컨텍스트와 멤버 선택 문자 앞에 입력 된 내용을 확인 합니다. 이 정보를 통해 파서는 요청 된 범위의 모든 멤버 목록을 만듭니다. 이 선언 목록은 메서드에서 반환 되는 개체에 저장 됩니다 <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> . 선언이 반환 되 면 멤버 완료 도구 설명이 표시 됩니다. 도구 설명은 클래스의 인스턴스에 의해 관리 됩니다 <xref:Microsoft.VisualStudio.Package.CompletionSet> .

## <a name="enable-support-for-member-completion"></a>멤버 완성 지원 사용

`CodeSense`IntelliSense 작업을 지원 하려면 레지스트리 항목을 1로 설정 해야 합니다. 이 레지스트리 항목은 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 언어 패키지와 연결 된 사용자 특성에 전달 된 명명 된 매개 변수를 사용 하 여 설정할 수 있습니다. 언어 서비스 클래스는 클래스의 속성에서이 레지스트리 항목의 값을 읽습니다 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .

스캐너가 [TokenTriggers](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)의 토큰 트리거를 반환 하 고 파서가 선언 목록을 반환 하면 멤버 완성 목록이 표시 됩니다.

## <a name="support-member-completion-in-the-scanner"></a>스캐너에서 구성원 완료를 지원 합니다.

스캐너는 구성원 완성 문자를 검색 하 고 해당 문자가 구문 분석 될 때 [TokenTriggers select](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) 의 토큰 트리거를 설정할 수 있어야 합니다.

### <a name="scanner-example"></a>스캐너 예

다음은 멤버 완성 문자를 검색 하 고 적절 한 플래그를 설정 하는 간단한 예입니다 <xref:Microsoft.VisualStudio.Package.TokenTriggers> . 이 예는 설명을 위한 목적 으로만 사용 됩니다. 스캐너에는 `GetNextToken` 텍스트 줄에서 토큰을 식별 하 고 반환 하는 메서드가 포함 되어 있다고 가정 합니다. 예제 코드에서는 올바른 종류의 문자가 표시 될 때마다 트리거를 설정 하기만 하면 됩니다.

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

## <a name="support-member-completion-in-the-parser"></a>파서에서 멤버 완료를 지원 합니다.

멤버 완성을 위해 <xref:Microsoft.VisualStudio.Package.Source> 클래스는 메서드를 호출 합니다 <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> . 클래스에서 파생 된 클래스에서 목록을 구현 해야 합니다 <xref:Microsoft.VisualStudio.Package.Declarations> . <xref:Microsoft.VisualStudio.Package.Declarations>구현 해야 하는 메서드에 대 한 자세한 내용은 클래스를 참조 하세요.

멤버가 select 문자를 입력 하면 [ParseReason](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>) 또는 [ParseReason](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>) 를 사용 하 여 파서가 호출 됩니다. 개체에 지정 된 위치는 <xref:Microsoft.VisualStudio.Package.ParseRequest> 멤버 선택 문자 바로 뒤에 있습니다. 파서는 소스 코드의 특정 지점에서 멤버 목록에 나타날 수 있는 모든 멤버의 이름을 수집 해야 합니다. 그런 다음 파서가 현재 줄을 구문 분석 하 여 사용자가 멤버 select 문자를 연결 하려는 범위를 확인 해야 합니다.

이 범위는 멤버 선택 문자 앞의 식별자 형식을 기반으로 합니다. 예를 들어 c #에서 형식의 멤버 변수를 지정 하 고 `languageService` languageService을 `LanguageService` 입력 **합니다.** 클래스의 모든 멤버 목록을 생성 `LanguageService` 합니다. 또한 c #에서이를 입력 **합니다.** 현재 범위에 있는 클래스의 모든 멤버 목록을 생성 합니다.

### <a name="parser-example"></a>파서 예

다음 예에서는 목록을 채우는 한 가지 방법을 보여 줍니다 <xref:Microsoft.VisualStudio.Package.Declarations> . 이 코드에서는 파서가 선언을 생성 하 고 클래스에서 메서드를 호출 하 여 목록에 추가 한다고 가정 합니다 `AddDeclaration` `TestAuthoringScope` .

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
