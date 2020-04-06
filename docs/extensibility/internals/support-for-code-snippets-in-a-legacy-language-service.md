---
title: 레거시 언어 서비스의 코드 조각 지원 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704917"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>레거시 언어 서비스의 코드 조각 지원
코드 코드 조각은 소스 파일에 삽입되는 코드 조각입니다. 스니펫 자체는 필드 집합이 있는 XML 기반 템플릿입니다. 이러한 필드는 스니펫이 삽입된 후 강조 표시되며 코드 조각이 삽입되는 컨텍스트에 따라 다른 값을 가질 수 있습니다. 코드 조각이 삽입된 직후 언어 서비스는 코드 조각을 포맷할 수 있습니다.

 코드 조각은 TAB 키를 사용하여 스니펫의 필드를 탐색할 수 있는 특수 편집 모드에 삽입됩니다. 필드는 IntelliSense 스타일의 드롭다운 메뉴를 지원할 수 있습니다. 사용자는 ENTER 또는 ESC 키를 입력하여 소스 파일에 스니펫을 커밋합니다. 코드 조각에 대한 자세한 내용은 [코드 조각](../../ide/code-snippets.md)을 참조하십시오.

 레거시 언어 서비스는 VSPackage의 일부로 구현되지만 언어 서비스 기능을 구현하는 최신 방법은 MEF 확장을 사용하는 것입니다. 자세한 내용은 [연습: 코드 조각 구현](../../extensibility/walkthrough-implementing-code-snippets.md)을 참조하십시오.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상되고 새로운 편집기 기능을 활용할 수 있습니다.

## <a name="managed-package-framework-support-for-code-snippets"></a>코드 스니펫에 대한 관리되는 패키지 프레임워크 지원
 관리되는 패키지 프레임워크(MPF)는 템플릿 읽기부터 코드 삽입 및 특수 편집 모드 활성화에 이르기까지 대부분의 코드 조각 기능을 지원합니다. 지원은 클래스를 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 통해 관리됩니다.

 클래스가 <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> 인스턴스화되면 <xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 클래스의 메서드가 개체를 가져오도록 호출됩니다(기본 <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스는 항상 각 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> <xref:Microsoft.VisualStudio.Package.Source> 개체에 대해 새 개체를 반환합니다).

 MPF는 확장 기능을 지원하지 않습니다. 확장 함수는 코드 조각 템플릿에 포함되고 필드에 배치할 하나 이상의 값을 반환하는 명명된 함수입니다. 값은 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 개체를 통해 언어 서비스 자체에 의해 반환 됩니다. <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 확장 기능을 지원하려면 언어 서비스에서 개체를 구현해야 합니다.

## <a name="providing-support-for-code-snippets"></a>코드 스니펫 지원 제공
 코드 조각에 대한 지원을 사용하려면 코드 조각을 제공하거나 설치해야 하며 사용자가 해당 스니펫을 삽입할 수 있는 수단을 제공해야 합니다. 코드 조각에 대한 지원을 활성화하는 세 가지 단계가 있습니다.

1. 스니펫 파일 설치.

2. 언어 서비스에 대한 코드 조각 을 사용하도록 설정합니다.

3. 개체를 호출합니다. <xref:Microsoft.VisualStudio.Package.ExpansionProvider>

### <a name="installing-the-snippet-files"></a>스니펫 파일 설치
 언어에 대한 모든 코드 조각은 XML 파일에 템플릿으로 저장되며 일반적으로 파일당 하나의 스니펫 템플릿으로 저장됩니다. 코드 조각 템플릿에 사용되는 XML 스키마에 대한 자세한 내용은 [코드 조각 스키마 참조를](../../ide/code-snippets-schema-reference.md)참조하십시오. 각 코드 조각 템플릿은 언어 ID로 식별됩니다. 이 언어 ID는 레지스트리에 지정되며 템플릿의 `Language` \<코드> 태그의 특성에 입력됩니다.

 일반적으로 스니펫 템플릿 파일이 저장되는 위치는 1) 언어가 설치된 위치와 2) 사용자의 폴더에 있습니다. 이러한 위치는 비주얼 스튜디오 **코드 조각 관리자가** 스니펫을 찾을 수 있도록 레지스트리에 추가됩니다. 사용자의 폴더는 사용자가 만든 스니펫이 저장되는 곳입니다.

 설치된 스니펫 템플릿 파일의 일반적인 폴더 레이아웃은 다음과 같습니다: *[InstallRoot]*\\\\ *[TestLanguage]* \스니펫 *[LCID]* \스니펫.

 *[InstallRoot]는* 언어가 설치된 폴더입니다.

 *[TestLanguage]는* 폴더 이름으로 언어의 이름입니다.

 *[LCID]는* 로캘 ID입니다. 이렇게 하면 지역화된 버전의 스니펫이 저장됩니다. 예를 들어 영어의 로캘 ID는 1033이므로 *[LCID]는* 1033으로 바뀝습니다.

 하나의 추가 파일을 제공해야 하며 일반적으로 SnippetsIndex.xml 또는 ExpansionsIndex.xml(.xml로 끝나는 유효한 파일 이름을 사용할 수 있음)이라고 하는 인덱스 파일입니다. 이 파일은 일반적으로 *[InstallRoot]*\\ *[TestLanguage]* 폴더에 저장되며 코드 조각 폴더의 정확한 위치와 스니펫을 사용하는 언어 서비스의 언어 ID 및 GUID를 지정합니다. 인덱스 파일의 정확한 경로는 "레지스트리 항목 설치"의 설명과 같이 레지스트리에 배치됩니다. 다음은 SnippetsIndex.xml 파일의 예입니다.

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

 언어 \<> 태그는 언어 `Lang` ID(특성) 및 언어 서비스 GUID를 지정합니다.

 이 예제에서는 Visual Studio 설치 폴더에 언어 서비스를 설치했다고 가정합니다. %LCID%는 사용자의 현재 로캘 ID로 대체됩니다. 각 \<디렉터리 및 로캘마다 여러 개의 SnippetDir> 태그를 추가할 수 있습니다. 또한 스니펫 폴더에는 하위 폴더가 포함될 수 있으며, 각 폴더는 \< \<SnippetSubDir> 태그에 포함된 SnippetSubDir> 태그가 있는 인덱스 파일에서 식별됩니다.

 사용자는 사용자의 언어에 대한 자신의 스니펫을 만들 수도 있습니다. 이러한 도구는 일반적으로 사용자의 설정 폴더에 저장됩니다(예: *[TestDocs]* \코드 조각\\ *[TestLanguage]* \Test Code 코드 조각, 여기서 *[TestDocs]는* Visual Studio용 사용자의 설정 폴더의 위치입니다.

 다음 대체 요소는 인덱스 파일의 \<DirPath> 태그에 저장된 경로에 배치할 수 있습니다.

|요소|Description|
|-------------|-----------------|
|%LCID%|로케일 ID.|
|%설치루트%|비주얼 스튜디오에 대한 루트 설치 폴더, 예를 들어, C :\프로그램 파일 \마이크로 소프트 비주얼 스튜디오 8.|
|%프로디르%|현재 프로젝트를 포함하는 폴더입니다.|
|%프로즈아이템%|현재 프로젝트 항목이 포함된 폴더입니다.|
|%TestDocs%|사용자의 설정 폴더에 있는 폴더(예: C:\문서\\및 설정 *[사용자 이름]* \내 문서\Visual Studio\8)|

### <a name="enabling-code-snippets-for-your-language-service"></a>언어 서비스에 대한 코드 조각 사용
 VSPackage에 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> 특성을 추가하여 언어 서비스에 대한 코드 조각을 활성화할 수 있습니다(자세한 내용은 [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md) 참조). <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> 및 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> 매개 변수는 선택 사항이지만 `SearchPaths` **코드 조각 관리자에게** 코드 조각의 위치를 알려주려면 명명된 매개 변수를 포함해야 합니다.

 다음은 이 특성을 사용하는 방법의 예입니다.

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
 언어 서비스는 삽입이 호출되는 방식뿐만 아니라 모든 코드 조각의 삽입을 제어합니다.

## <a name="calling-the-expansion-provider-for-code-snippets"></a>코드 스니펫에 대한 확장 공급자 호출
 확장 공급자를 호출하는 방법에는 메뉴 명령을 사용하거나 완료 목록의 바로 가기를 사용하는 두 가지 방법이 있습니다.

### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>메뉴 명령을 사용하여 코드 조각 삽입
 메뉴 명령을 사용하여 코드 조각을 표시하려면 메뉴 명령을 추가한 다음 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> 해당 메뉴 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 명령에 대한 응답으로 인터페이스에서 메서드를 호출합니다.

1. .vsct 파일에 명령과 단추를 추가합니다. 메뉴 명령을 사용 하 고 [확장 만들기에서](../../extensibility/creating-an-extension-with-a-menu-command.md)이렇게 하는 방법에 대 한 지침을 찾을 수 있습니다.

2. 클래스에서 클래스를 <xref:Microsoft.VisualStudio.Package.ViewFilter> 파생 하 <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> 고 새 메뉴 명령에 대 한 지원을 나타내는 메서드를 재정의 합니다. 이 예제는 항상 메뉴 명령을 사용할 수 있습니다.

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

3. 클래스에서 <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> 메서드를 <xref:Microsoft.VisualStudio.Package.ViewFilter> 재정의하여 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 개체를 가져오고 해당 개체에서 메서드를 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> 호출합니다.

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

     클래스의 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 다음 메서드는 코드 조각을 삽입하는 동안 지정된 순서로 Visual Studio에서 호출됩니다.

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     메서드가 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> 호출된 후 스니펫이 삽입되고 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 개체가 방금 삽입된 스니펫을 수정하는 데 사용되는 특수 편집 모드에 있습니다.

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>바로 가기를 사용하여 코드 조각 삽입
 완료 목록에서 바로 가기를 구현하는 것은 메뉴 명령을 구현하는 것보다 훨씬 더 많이 관련됩니다. 먼저 IntelliSense 단어 완성 목록에 코드 바로 가기를 추가해야 합니다. 그런 다음 완료 결과로 코드 조각 바로 가기 이름이 삽입된 시기를 감지해야 합니다. 마지막으로 바로 가기 이름을 사용하여 코드 조각 제목과 경로를 가져오고 해당 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> 정보를 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 메서드의 메서드에 전달해야 합니다.

 단어 완성 목록에 코드 바로 가기를 추가하려면 클래스의 <xref:Microsoft.VisualStudio.Package.Declarations> 개체에 추가합니다. <xref:Microsoft.VisualStudio.Package.AuthoringScope> 바로 가기를 코드 조각 이름으로 식별할 수 있는지 확인해야 합니다. 예를 들어 [연습: 설치된 코드 조각 목록(레거시 구현) 을](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)참조하십시오.

 클래스의 메서드에서 코드 조각 바로 가기의 삽입을 <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> 검색할 <xref:Microsoft.VisualStudio.Package.Declarations> 수 있습니다. 코드 조각 이름이 원본 파일에 이미 삽입되었기 때문에 확장을 삽입할 때 제거해야 합니다. 메서드는 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> 코드 조각에 대 한 삽입 지점을 설명 하는 범위를 사용 합니다. 범위원본 파일에 전체 코드 조각 이름이 포함된 경우 해당 이름은 코드 조각으로 바뀝니다.

 다음은 바로 가기 <xref:Microsoft.VisualStudio.Package.Declarations> 이름이 지정된 코드 삽입을 처리하는 클래스 의 버전입니다. 명확성을 위해 <xref:Microsoft.VisualStudio.Package.Declarations> 클래스의 다른 메서드가 생략되었습니다. 이 클래스의 생성자는 개체를 <xref:Microsoft.VisualStudio.Package.LanguageService> 취합니다. 이 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 개체의 버전에서 전달할 수 있습니다 (예를 들어, <xref:Microsoft.VisualStudio.Package.AuthoringScope> 클래스의 <xref:Microsoft.VisualStudio.Package.LanguageService> 구현은 해당 생성자에서 개체를 `TestDeclarations` 받아 클래스 생성자에 해당 개체를 전달할 수 있습니다).

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

 언어 서비스가 바로 가기 이름을 가져오면 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> 파일 이름 및 코드 코드 조각 제목을 가져오는 메서드를 호출합니다. 그런 다음 언어 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> 서비스는 클래스의 메서드를 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 호출하여 코드 조각을 삽입합니다. 다음 메서드는 코드 조각을 삽입 하는 동안 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 클래스에서 지정된 순서로 Visual Studio에서 호출 됩니다.

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   언어 서비스에 대해 설치된 코드 조각 목록을 가져오는 방법에 대한 자세한 내용은 [연습: 설치된 코드 조각 목록 얻기(레거시 구현)를](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)참조하십시오.

## <a name="implementing-the-expansionfunction-class"></a>확장기능 클래스 구현
 확장 함수는 코드 조각 템플릿에 포함되고 필드에 배치할 하나 이상의 값을 반환하는 명명된 함수입니다. 언어 서비스에서 확장 함수를 지원하려면 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 클래스에서 클래스를 파생하고 메서드를 <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> 구현해야 합니다. 그런 다음 클래스의 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> 메서드를 <xref:Microsoft.VisualStudio.Package.LanguageService> 재정의하여 지원하는 각 확장 함수에 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 대해 클래스 버전의 새 인스턴스화를 반환해야 합니다. 확장 함수에서 가능한 값 목록을 지원하는 경우 <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 클래스의 메서드를 재정의하여 해당 값 목록을 반환해야 합니다.

 확장 함수가 호출될 때까지 확장 공급자가 완전히 초기화되지 않을 수 있으므로 인수를 사용하거나 다른 필드에 액세스해야 하는 확장 함수는 편집 가능한 필드와 연결되어서는 안 됩니다. 따라서 확장 함수는 인수 또는 다른 필드의 값을 가져올 수 없습니다.

### <a name="example"></a>예제
 다음은 호출된 `GetName` 간단한 확장 함수를 구현하는 방법의 예입니다. 이 확장 함수는 확장 함수가 인스턴스화될 때마다 기본 클래스 이름에 숫자를 더합니다(연결된 코드 조각이 삽입될 때마다 해당).

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

## <a name="see-also"></a>참조
- [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)
- [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [코드 조각](../../ide/code-snippets.md)
- [연습: 설치된 코드 조각 목록 가져오기(레거시 구현)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)
