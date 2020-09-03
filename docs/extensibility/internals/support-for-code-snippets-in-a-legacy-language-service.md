---
title: 레거시 언어 서비스의 코드 조각 지원 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad871eb73341f6ab87229687e2a6df898ffda32d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704917"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>레거시 언어 서비스의 코드 조각 지원
코드 조각은 소스 파일에 삽입 되는 코드 조각입니다. 코드 조각은 필드 집합을 사용 하는 XML 기반 템플릿입니다. 이러한 필드는 코드 조각이 삽입 된 후 강조 표시 되며 조각이 삽입 된 컨텍스트에 따라 다른 값을 가질 수 있습니다. 코드 조각이 삽입 된 직후에 언어 서비스는 코드 조각의 서식을 지정할 수 있습니다.

 코드 조각은 TAB 키를 사용 하 여 코드 조각의 필드를 탐색할 수 있도록 하는 특수 편집 모드에서 삽입 됩니다. 필드는 IntelliSense 스타일 드롭다운 메뉴를 지원할 수 있습니다. 사용자는 ENTER 키 또는 ESC 키를 입력 하 여 소스 파일에 코드 조각을 커밋합니다. 코드 조각에 대 한 자세한 내용은 [코드 조각](../../ide/code-snippets.md)을 참조 하세요.

 레거시 언어 서비스는 VSPackage의 일부로 구현 되지만 언어 서비스 기능을 구현 하는 최신 방법은 MEF 확장을 사용 하는 것입니다. 자세히 알아보려면 [연습: 코드 조각 구현](../../extensibility/walkthrough-implementing-code-snippets.md)을 참조 하세요.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용 하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.

## <a name="managed-package-framework-support-for-code-snippets"></a>코드 조각에 대 한 관리 되는 패키지 프레임 워크 지원
 MPF (관리 되는 패키지 프레임 워크)는 템플릿을 읽어 코드 조각을 삽입 하 고 특수 편집 모드를 사용 하는 것부터 대부분의 조각 기능을 지원 합니다. 지원은 클래스를 통해 관리 됩니다 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> .

 <xref:Microsoft.VisualStudio.Package.Source>클래스가 인스턴스화되면 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> 클래스의 메서드를 <xref:Microsoft.VisualStudio.Package.LanguageService> 호출 하 여 개체를 가져옵니다 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> <xref:Microsoft.VisualStudio.Package.LanguageService> . 기본 클래스는 항상 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 각 개체에 대 한 새 개체를 반환 합니다 <xref:Microsoft.VisualStudio.Package.Source> .

 MPF는 확장 기능을 지원 하지 않습니다. 확장 함수는 코드 조각 템플릿에 포함 된 명명 된 함수 이며 필드에 배치할 하나 이상의 값을 반환 합니다. 값은 언어 서비스 자체에서 개체를 통해 반환 됩니다 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> . <xref:Microsoft.VisualStudio.Package.ExpansionFunction>확장 함수를 지원 하려면 언어 서비스에서 개체를 구현 해야 합니다.

## <a name="providing-support-for-code-snippets"></a>코드 조각에 대 한 지원 제공
 코드 조각에 대 한 지원을 사용 하도록 설정 하려면 코드 조각을 제공 하거나 설치 해야 하며 사용자가 코드 조각을 삽입할 수 있는 방법을 제공 해야 합니다. 코드 조각에 대 한 지원을 사용 하도록 설정 하는 세 가지 단계가 있습니다.

1. 조각 파일을 설치 합니다.

2. 언어 서비스에 코드 조각을 사용 하도록 설정 합니다.

3. 개체를 호출 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 합니다.

### <a name="installing-the-snippet-files"></a>조각 파일 설치
 언어에 대 한 모든 코드 조각은 XML 파일에 템플릿으로 저장 됩니다. 일반적으로 파일 별로 하나의 코드 조각 템플릿을 저장 합니다. 코드 조각 템플릿에 사용 되는 XML 스키마에 대 한 자세한 내용은 [코드 조각 스키마 참조](../../ide/code-snippets-schema-reference.md)를 참조 하세요. 각 코드 조각 템플릿은 언어 ID로 식별 됩니다. 이 언어 ID는 레지스트리에 지정 되어 있으며 `Language` 템플릿에서 태그의 특성에 포함 됩니다 \<Code> .

 일반적으로 코드 조각 템플릿 파일을 저장 하는 위치는 1) 사용자의 폴더에 저장 됩니다. 이러한 위치는 Visual Studio **코드 조각 관리자** 가 코드 조각을 찾을 수 있도록 레지스트리에 추가 됩니다. 사용자의 폴더는 사용자가 만든 코드 조각이 저장 되는 위치입니다.

 설치 된 코드 조각 템플릿 파일의 일반적인 폴더 레이아웃은 다음과 같습니다. *[installroot]* \\ *[testlanguage]* \snippets \\ *[LCID]* \snippets)

 *[Installroot]* 는 언어가 설치 된 폴더입니다.

 *[Testlanguage]* 은 (는) 폴더 이름으로 서의 언어 이름입니다.

 *[LCID]* 는 로캘 ID입니다. 이는 지역화 된 버전의 코드 조각을 저장 하는 방법입니다. 예를 들어 영어에 대 한 로캘 ID는 1033 이므로 *[LCID]* 는 1033로 바뀝니다.

 추가 파일 하나를 제공 해야 하며, 인덱스 파일 (일반적으로 SnippetsIndex.xml 또는 ExpansionsIndex.xml 이라고 함)입니다. xml로 끝나는 유효한 파일 이름을 사용할 수 있습니다. 이 파일은 일반적으로 *[installroot]* \\ *[testlanguage]* 폴더에 저장 되며, 코드 조각을 사용 하는 언어 서비스의 언어 ID 및 GUID 뿐만 아니라 코드 조각 폴더의 정확한 위치를 지정 합니다. 인덱스 파일의 정확한 경로는 나중에 "레지스트리 항목 설치"의 설명에 따라 레지스트리에 저장 됩니다. SnippetsIndex.xml 파일의 예는 다음과 같습니다.

```
<?xml version="1.0" encoding="utf-8" ?>
<SnippetCollection>
    <Language Lang="Testlanguage" Guid="{b614a40a-80d9-4fac-a6ad-fc2868fff7cd}">
        <SnippetDir>
            <OnOff>On</OnOff>
            <Installed>true</Installed>
            <Locale>1033</Locale>
            <DirPath>%InstallRoot%\TestLanguage\Snippets\%LCID%\Snippets\</DirPath>
            <LocalizedName>Snippets</LocalizedName>
        </SnippetDir>
    </Language>
</SnippetCollection>
```

 \<Language>태그는 언어 ID ( `Lang` 특성)와 언어 서비스 GUID를 지정 합니다.

 이 예제에서는 Visual Studio 설치 폴더에 언어 서비스를 설치 했다고 가정 합니다. % LCID%는 사용자의 현재 로캘 ID로 바뀝니다. \<SnippetDir>서로 다른 디렉터리와 로캘에 대해 하나씩 여러 태그를 추가할 수 있습니다. 또한 조각 폴더에는 하위 폴더가 포함 될 수 있으며, 각 하위 폴더는 태그에 포함 된 태그를 사용 하 여 인덱스 파일에서 식별 됩니다 \<SnippetSubDir> \<SnippetDir> .

 사용자는 해당 언어에 대 한 고유한 코드 조각을 만들 수도 있습니다. 일반적으로 사용자의 settings 폴더에 저장 됩니다 (예: *[testdocs]* \Code 코드 조각 \\ *[testdocs]* \test 코드 조각). 여기서 *[testdocs]* 는 Visual Studio에 대 한 사용자 설정 폴더의 위치입니다.

 인덱스 파일의 태그에 저장 된 경로에 다음 대체 요소를 배치할 수 있습니다 \<DirPath> .

|요소|설명|
|-------------|-----------------|
|LCID|로캘 ID입니다.|
|InstallRoot|Visual Studio의 루트 설치 폴더 (예: C:\Program Files\Microsoft Visual Studio 8).|
|%ProjDir%|현재 프로젝트를 포함 하는 폴더입니다.|
|%ProjItem%|현재 프로젝트 항목을 포함 하는 폴더입니다.|
|% TestDocs%|사용자의 settings 폴더에 있는 폴더 (예: C:\Documents \\ *[username]* \My Documents\visual Studio\8.|

### <a name="enabling-code-snippets-for-your-language-service"></a>언어 서비스에 코드 조각 사용
 VSPackage에 특성을 추가 하 여 언어 서비스에 코드 조각을 사용 하도록 설정할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> (자세한 내용은 [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md) 참조). <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A>및 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> 매개 변수는 선택 사항 이지만 `SearchPaths` **코드 조각 관리자에 코드** 조각 위치를 알리기 위해 명명 된 매개 변수를 포함 해야 합니다.

 다음은이 특성을 사용 하는 방법의 예입니다.

```
[ProvideLanguageCodeExpansion(
         typeof(TestSnippetLanguageService),
         "Test Snippet Language",          // Name of language used as registry key
         0,                               // Resource ID of localized name of language service
         "Test Snippet Language",        // Name of Language attribute in snippet template
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets
```

### <a name="calling-the-expansion-provider"></a>확장 공급자 호출
 언어 서비스는 삽입이 호출 되는 방식 뿐만 아니라 모든 코드 조각의 삽입을 제어 합니다.

## <a name="calling-the-expansion-provider-for-code-snippets"></a>코드 조각에 대 한 확장 공급자 호출
 확장 공급자를 호출 하는 방법에는 메뉴 명령을 사용 하거나 완성 목록의 바로 가기를 사용 하는 두 가지 방법이 있습니다.

### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>메뉴 명령을 사용 하 여 코드 조각 삽입
 메뉴 명령을 사용 하 여 코드 조각 브라우저를 표시 하려면 메뉴 명령을 추가한 다음 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 해당 메뉴 명령에 대 한 응답으로 인터페이스에서 메서드를 호출 합니다.

1. 명령 및 단추를 vsct 파일에 추가 합니다. [메뉴 명령을 사용 하 여 확장을 만드는](../../extensibility/creating-an-extension-with-a-menu-command.md)방법에 대 한 지침을 찾을 수 있습니다.

2. 클래스에서 클래스를 파생 시키고 <xref:Microsoft.VisualStudio.Package.ViewFilter> 메서드를 재정의 <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> 하 여 새 메뉴 명령에 대 한 지원을 표시 합니다. 이 예에서는 항상 메뉴 명령을 사용 하도록 설정 합니다.

    ```csharp
    using Microsoft.VisualStudio.Package;

    namespace TestLanguagePackage
    {
        class TestViewFilter : ViewFilter
        {
            public TestViewFilter(CodeWindowManager mgr, IVsTextView view)
                : base(mgr, view)
            {
            }

            protected override int QueryCommandStatus(ref Guid guidCmdGroup,
                                                      uint nCmdId)
            {
                int hr = base.QueryCommandStatus(ref guidCmdGroup, nCmdId);
                // If the base class did not recognize the command then
                // see if we can handle the command.
                if (hr == (int)Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP)
                {
                    if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)
                    {
                        if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)
                        {
                            hr = (int)(OLECMDF.OLECMDF_SUPPORTED | OLECMDF.OLECMDF_ENABLED);
                        }
                    }
                }
                return hr;
            }
        }
    }
    ```

3. <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A>클래스의 메서드를 재정의 <xref:Microsoft.VisualStudio.Package.ViewFilter> 하 여 개체를 가져오고 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> 해당 개체에 대해 메서드를 호출 합니다.

    ```csharp
    using Microsoft.VisualStudio.Package;

    namespace TestLanguagePackage
    {
        class TestViewFilter : ViewFilter
        {
            public override bool HandlePreExec(ref Guid guidCmdGroup,
                                               uint nCmdId,
                                               uint nCmdexecopt,
                                               IntPtr pvaIn,
                                               IntPtr pvaOut)
            {
                if (base.HandlePreExec(ref guidCmdGroup,
                                       nCmdId,
                                       nCmdexecopt,
                                       pvaIn,
                                       pvaOut))
                {
                    // Base class handled the command.  Do nothing more here.
                    return true;
                }

                if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)
                {
                    if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)
                    {
                        ExpansionProvider ep = this.GetExpansionProvider();
                        if (this.TextView != null && ep != null)
                        {
                            bool bDisplayed = ep.DisplayExpansionBrowser(
                                this.TextView,
                                "TestLanguagePackage Snippet:",
                                null,
                                false,
                                null,
                                false);
                        }
                        return true;   // Handled the command.
                    }
                }
                return false;   // Did not handle the command.
            }
        }
    }

    ```

     클래스의 다음 메서드는 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 코드 조각을 삽입 하는 과정에서 지정 된 순서에 따라 Visual Studio에 의해 호출 됩니다.

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>메서드가 호출 되 면 코드 조각이 삽입 되 고 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 개체가 방금 삽입 된 코드 조각을 수정 하는 데 사용 되는 특수 편집 모드로 사용 됩니다.

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>바로 가기를 사용 하 여 코드 조각 삽입
 완성 목록에서 바로 가기를 구현 하는 것은 메뉴 명령을 구현 하는 것 보다 훨씬 더 복잡 합니다. 먼저 IntelliSense 단어 완성 목록에 코드 조각 바로 가기를 추가 해야 합니다. 그런 다음 완성 된 결과로 조각 바로 가기 이름이 삽입 된 시기를 감지 해야 합니다. 마지막으로 바로 가기 이름을 사용 하 여 코드 조각 제목과 경로를 가져온 다음이 정보를 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> 메서드의 메서드에 전달 해야 합니다 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> .

 단어 완성 목록에 코드 조각 바로 가기를 추가 하려면 <xref:Microsoft.VisualStudio.Package.Declarations> 클래스의 개체에 추가 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 합니다. 바로 가기를 코드 조각 이름으로 식별할 수 있는지 확인 해야 합니다. 예제는 [연습: 설치 된 코드 조각 목록 가져오기 (레거시 구현)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)를 참조 하세요.

 클래스의 메서드에서 코드 조각 바로 가기 삽입을 검색할 수 있습니다 <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> <xref:Microsoft.VisualStudio.Package.Declarations> . 소스 파일에 코드 조각 이름이 이미 삽입 되었으므로 확장이 삽입 될 때 해당 이름이 제거 되어야 합니다. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A>메서드는 코드 조각의 삽입 지점을 설명 하는 범위를 사용 합니다. 범위에 소스 파일의 전체 코드 조각 이름이 포함 된 경우 해당 이름이 조각으로 바뀝니다.

 다음은 <xref:Microsoft.VisualStudio.Package.Declarations> 바로 가기 이름이 지정 된 경우 코드 조각 삽입을 처리 하는 클래스 버전입니다. 클래스의 다른 메서드 <xref:Microsoft.VisualStudio.Package.Declarations> 는 명확 하 게 나타내기 위해 생략 되었습니다. 이 클래스의 생성자는 개체를 사용 <xref:Microsoft.VisualStudio.Package.LanguageService> 합니다. 이는 개체의 버전에서 전달 될 수 있습니다 <xref:Microsoft.VisualStudio.Package.AuthoringScope> . 예를 들어 클래스의 구현이 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 생성자에서 개체를 사용 하 <xref:Microsoft.VisualStudio.Package.LanguageService> 고 해당 개체를 클래스 생성자에 전달할 수 있습니다 `TestDeclarations` .

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    internal class TestDeclarations : Declarations
    {
        private ArrayList       declarations;
        private LanguageService languageService;
        private TextSpan        commitSpan;

        public TestDeclarations(LanguageService langService)
            : base()
        {
            languageService = langService;
            declarations = new ArrayList();
        }

        // This method is used to add declarations to the internal list.
        public void AddDeclaration(TestDeclaration declaration)
        {
            declarations.Add(declaration);
        }

        // This method is called to get the string to commit to the source buffer.
        // Note that the initial extent is only what the user has typed so far.
        public override string OnCommit(IVsTextView textView,
                                        string textSoFar,
                                        char commitCharacter,
                                        int index,
                                        ref TextSpan initialExtent)
        {
            // We intercept this call only to get the initial extent
            // of what was committed to the source buffer.
            commitSpan = initialExtent;

            return base.OnCommit(textView,
                                 textSoFar,
                                 commitCharacter,
                                 index,
                                 ref initialExtent);
        }

        // This method is called after the string has been committed to the source buffer.
        public override char OnAutoComplete(IVsTextView textView,
                                            string committedText,
                                            char commitCharacter,
                                            int index)
        {
            TestDeclaration item = declarations[index] as TestDeclaration;
            if (item != null)
            {
                // In this example, TestDeclaration identifies types with a string.
                // You can choose a different approach.
                if (item.Type == "snippet")
                {
                    Source src = languageService.GetSource(textView);
                    if (src != null)
                    {
                        ExpansionProvider ep = src.GetExpansionProvider();
                        if (ep != null)
                        {
                            string title;
                            string path;
                            int commitLength = commitSpan.iEndIndex - commitSpan.iStartIndex;
                            if (commitLength < committedText.Length)
                            {
                                // Replace everything that was inserted
                                // so calculate the span of the full
                                // insertion, taking into account what
                                // was inserted when the commitSpan
                                // was obtained in the first place.
                                commitSpan.iEndIndex += (committedText.Length - commitLength);
                            }

                            if (ep.FindExpansionByShortcut(textView,
                                                           committedText,
                                                           commitSpan,
                                                           true,
                                                           out title,
                                                           out path))
                            {
                                ep.InsertNamedExpansion(textView,
                                                        title,
                                                        path,
                                                        commitSpan,
                                                        false);
                            }
                        }
                    }
                }
            }
            return '\0';
        }
    }
}
```

 언어 서비스에서 바로 가기 이름을 가져올 때 메서드를 호출 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> 하 여 파일 이름 및 코드 조각 제목을 가져옵니다. 그런 다음 언어 서비스는 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> 클래스의 메서드를 호출 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 하 여 코드 조각을 삽입 합니다. 다음 메서드는 코드 조각을 삽입 하는 과정에서 클래스의 지정 된 순서에 따라 Visual Studio에서 호출 됩니다 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> .

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   언어 서비스에 대해 설치 된 코드 조각 목록을 가져오는 방법에 대 한 자세한 내용은 [연습: 설치 된 코드 조각 목록 가져오기 (레거시 구현)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)를 참조 하세요.

## <a name="implementing-the-expansionfunction-class"></a>ExpansionFunction 클래스 구현
 확장 함수는 코드 조각 템플릿에 포함 된 명명 된 함수 이며 필드에 배치할 하나 이상의 값을 반환 합니다. 언어 서비스에서 확장 함수를 지원 하려면 클래스에서 클래스를 파생 시키고 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 메서드를 구현 해야 합니다 <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> . 그런 다음 클래스의 메서드를 재정의 하 여 지원 되는 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 각 확장 함수에 대해 클래스 버전의 새 인스턴스를 반환 해야 합니다. 확장 함수에서 사용할 수 있는 값 목록을 지 원하는 경우 <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> 클래스의 메서드를 재정의 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 하 여 해당 값의 목록을 반환 해야 합니다.

 확장 공급자가 확장 함수가 호출 될 때까지 완전히 초기화 되지 않았을 수 있으므로 인수를 사용 하거나 다른 필드에 액세스 해야 하는 확장 함수를 편집 가능한 필드와 연결 해서는 안 됩니다. 따라서 확장 함수는 해당 인수 또는 다른 필드의 값을 가져올 수 없습니다.

### <a name="example"></a>예
 다음은 라는 간단한 확장 함수를 구현할 수 있는 방법의 예입니다 `GetName` . 이 확장 함수는 확장 함수가 인스턴스화될 때마다 기본 클래스 이름에 숫자를 추가 합니다 .이는 연결 된 코드 조각이 삽입 될 때마다 해당 됩니다.

```csharp
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private int classNameCounter = 0;

        public override ExpansionFunction CreateExpansionFunction(
            ExpansionProvider provider,
            string functionName)
        {
            ExpansionFunction function = null;
            if (functionName == "GetName")
            {
                ++classNameCounter;
                function = new TestGetNameExpansionFunction(provider, classNameCounter);
            }
            return function;
        }
    }

    internal class TestGetNameExpansionFunction : ExpansionFunction
    {
        private int nameCount;

        TestGetNameExpansionFunction(ExpansionProvider provider, int counter)
            : base(provider)
        {
            nameCount = counter;
        }

        public override string GetCurrentValue()
        {
            string name = "TestClass";
            name += nameCount.ToString();
            return name;
        }
    }
}
```

## <a name="see-also"></a>추가 정보
- [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)
- [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [코드 조각](../../ide/code-snippets.md)
- [연습: 설치된 코드 조각 목록 가져오기(레거시 구현)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)
