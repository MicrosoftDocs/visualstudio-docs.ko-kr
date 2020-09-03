---
title: 설치 된 코드 조각 목록 가져오기 (레거시) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3d5ef857973555c4b2d201f98957bd2c39328b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703647"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>연습: 설치된 코드 조각 목록 가져오기(레거시 구현)
코드 조각은 메뉴 명령 (설치 된 코드 조각 목록 중에서 선택할 수 있음)을 사용 하거나 IntelliSense 완성 목록에서 코드 조각 바로 가기를 선택 하 여 소스 버퍼에 삽입할 수 있는 코드 조각입니다.

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A>메서드는 특정 언어 GUID에 대 한 모든 코드 조각을 가져옵니다. 이러한 조각에 대 한 바로 가기를 IntelliSense 완성 목록에 삽입할 수 있습니다.

 MPF (관리 패키지 프레임 워크) 언어 서비스에서 코드 조각을 구현 하는 방법에 대 한 자세한 내용은 [레거시 언어 서비스의 코드 조각 지원](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md) 을 참조 하세요.

### <a name="to-retrieve-a-list-of-code-snippets"></a>코드 조각의 목록을 검색 하려면

1. 다음 코드에서는 지정 된 언어에 대 한 코드 조각 목록을 가져오는 방법을 보여 줍니다. 결과는 구조체의 배열에 저장 됩니다 <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion> . 이 메서드는 정적 메서드를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> 서비스에서 인터페이스를 가져옵니다 <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> . 그러나 VSPackage에 제공 된 서비스 공급자를 사용 하 고 메서드를 호출할 수도 있습니다 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> .

    ```csharp
    using System;
    using System.Collections;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Package;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.TextManager.Interop;

    [Guid("00000000-0000-0000-0000-000000000000")] //create a new GUID for the language service
    namespace TestLanguage
    {
        class TestLanguageService : LanguageService
        {
            private void GetSnippets(Guid languageGuid,
                                     ref ArrayList expansionsList)
            {
                IVsTextManager textManager = (IVsTextManager)Package.GetGlobalService(typeof(SVsTextManager));
                if (textManager != null)
                {
                    IVsTextManager2 textManager2 = (IVsTextManager2)textManager;
                    if (textManager2 != null)
                    {
                        IVsExpansionManager expansionManager = null;
                        textManager2.GetExpansionManager(out expansionManager);
                        if (expansionManager != null)
                        {
                            // Tell the environment to fetch all of our snippets.
                            IVsExpansionEnumeration expansionEnumerator = null;
                            expansionManager.EnumerateExpansions(languageGuid,
                            0,     // return all info
                            null,    // return all types
                            0,     // return all types
                            1,     // include snippets without types
                            0,     // do not include duplicates
                            out expansionEnumerator);
                            if (expansionEnumerator != null)
                            {
                                // Cache our expansions in a VsExpansion array
                                uint count   = 0;
                                uint fetched = 0;
                                VsExpansion expansionInfo = new VsExpansion();
                                IntPtr[] pExpansionInfo   = new IntPtr[1];

                                // Allocate enough memory for one VSExpansion structure. This memory is filled in by the Next method.
                                pExpansionInfo[0] = Marshal.AllocCoTaskMem(Marshal.SizeOf(expansionInfo));

                                expansionEnumerator.GetCount(out count);
                                for (uint i = 0; i < count; i++)
                                {
                                    expansionEnumerator.Next(1, pExpansionInfo, out fetched);
                                    if (fetched > 0)
                                    {
                                        // Convert the returned blob of data into a structure that can be read in managed code.
                                        expansionInfo = (VsExpansion)Marshal.PtrToStructure(pExpansionInfo[0], typeof(VsExpansion));

                                        if (!String.IsNullOrEmpty(expansionInfo.shortcut))
                                        {
                                            expansionsList.Add(expansionInfo);
                                        }
                                    }
                                }
                                Marshal.FreeCoTaskMem(pExpansionInfo[0]);
                            }
                        }
                    }
                }
            }
        }
    }
    ```

### <a name="to-call-the-getsnippets-method"></a>GetSnippets 메서드를 호출 하려면

1. 다음 메서드는 `GetSnippets` 구문 분석 작업을 완료할 때 메서드를 호출 하는 방법을 보여 줍니다. 이유를 사용 하 여 <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A> 시작 된 구문 분석 작업 후 메서드가 호출 됩니다 <xref:Microsoft.VisualStudio.Package.ParseReason> .

> [!NOTE]
> `expansionsList`배열 목록은 성능상의 이유로 캐시 됩니다. 코드 조각에 대 한 변경 내용은 언어 서비스가 중지 되 고 다시 로드 될 때까지 목록에 반영 되지 않습니다 (예: 중지 및 다시 시작 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ).

```csharp
class TestLanguageService : LanguageService
{
    private ArrayList expansionsList;

    public override void OnParseComplete(ParseRequest req)
    {
        if (this.expansionsList == null)
        {
            this.expansionsList = new ArrayList();
            GetSnippets(this.GetLanguageServiceGuid(),
                ref this.expansionsList);
        }
    }
}
```

### <a name="to-use-the-snippet-information"></a>코드 조각 정보를 사용 하려면

1. 다음 코드에서는 메서드에서 반환 된 코드 조각 정보를 사용 하는 방법을 보여 줍니다 `GetSnippets` . `AddSnippets`메서드는 코드 조각 목록을 채우는 데 사용 되는 구문 분석 이유에 대 한 응답으로 파서에서 호출 됩니다. 전체 구문 분석이 처음으로 수행 된 후에이 작업을 수행 해야 합니다.

     `AddDeclaration`메서드는 나중에 완성 목록에 표시 되는 선언 목록을 작성 합니다.

     클래스에는 `TestDeclaration` 선언 유형 뿐만 아니라 완성 목록에 표시 될 수 있는 모든 정보가 포함 되어 있습니다.

    ```csharp
    class TestAuthoringScope : AuthoringScope
    {
        public void AddDeclarations(TestDeclaration declaration)
        {
            if (m_declarations == null)
                m_declarations = new List<TestDeclaration>();
            m_declarations.Add(declaration);
         }
    }
    class TestDeclaration
    {
        private string m_name;
        private string m_description;
        private string m_type;

        public TestDeclaration(string name, string desc, string type)
        {
            m_name = name;
            m_description = desc;
            m_type = type;
        }

    class TestLanguageService : LanguageService
    {
        internal void AddSnippets(ref TestAuthoringScope scope)
        {
            if (this.expansionsList != null && this.expansionsList.Count > 0)
            {
                int count = this.expansionsList.Count;
                for (int i = 0; i < count; i++)
                {
                    VsExpansion expansionInfo = (VsExpansion)this.expansionsList[i];
                    scope.AddDeclaration(new TestDeclaration(expansionInfo.title,
                         expansionInfo.description,
                         "snippet"));
                }
            }
        }
    }

    ```

## <a name="see-also"></a>추가 정보
- [레거시 언어 서비스의 코드 조각 지원](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)
