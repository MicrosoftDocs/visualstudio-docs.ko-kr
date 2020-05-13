---
title: 설치된 코드 조각 목록 얻기(레거시) | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703647"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>연습: 설치된 코드 조각 목록 가져오기(레거시 구현)
코드 스니펫은 메뉴 명령(설치된 코드 조각 목록 중에서 선택할 수 있음)을 사용하는 또는 IntelliSense 완료 목록에서 코드 바로 가기를 선택하여 소스 버퍼에 삽입할 수 있는 코드 조각입니다.

 메서드는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A> 특정 언어 GUID에 대 한 모든 코드 조각을 가져옵니다. 이러한 코드 조각에 대한 바로 가기를 IntelliSense 완료 목록에 삽입할 수 있습니다.

 관리되는 패키지 프레임워크(MPF) 언어 서비스에서 코드 조각 구현에 대한 자세한 내용은 [레거시 언어 서비스의 코드 조각 지원을](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md) 참조하십시오.

### <a name="to-retrieve-a-list-of-code-snippets"></a>코드 조각 목록을 검색하려면

1. 다음 코드는 지정된 언어에 대한 코드 조각 목록을 얻는 방법을 보여 주었습니다. 결과는 구조의 <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion> 배열에 저장됩니다. 이 메서드는 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 정적 메서드를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> 사용 <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> 하 여 서비스에서 인터페이스를 가져옵니다. 그러나 VSPackage에 제공된 서비스 공급자를 사용하고 메서드를 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> 호출할 수도 있습니다.

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

### <a name="to-call-the-getsnippets-method"></a>GetSnippets 메서드를 호출하려면

1. 다음 메서드는 구문 `GetSnippets` 분석 작업이 완료될 때 메서드를 호출하는 방법을 보여 주며 있습니다. 메서드는 <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A> 원인으로 <xref:Microsoft.VisualStudio.Package.ParseReason>시작된 구문 분석 작업 후에 호출됩니다.

> [!NOTE]
> 성능상의 `expansionsList` 이유로 배열 목록이 캐시됩니다. 언어 서비스가 중지되고 다시 로드될 때까지 코드 조각에 대한 변경 내용은 목록에 반영되지 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]않습니다(예: 중지 및 다시 시작).

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

### <a name="to-use-the-snippet-information"></a>스니펫 정보를 사용하려면

1. 다음 코드는 메서드에서 반환하는 코드 조각 `GetSnippets` 정보를 사용하는 방법을 보여 주며 있습니다. 메서드는 `AddSnippets` 코드 조각 목록을 채우는 데 사용 되는 모든 구문 분석 이유에 대 한 응답으로 파서에서 호출 됩니다. 이것은 전체 구문 분석이 처음으로 수행 된 후에 수행되어야합니다.

     메서드는 `AddDeclaration` 나중에 완료 목록에 표시 되는 선언 목록을 작성 합니다.

     클래스에는 `TestDeclaration` 완료 목록에 표시할 수 있는 모든 정보와 선언 유형이 포함되어 있습니다.

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

## <a name="see-also"></a>참조
- [레거시 언어 서비스의 코드 조각 지원](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)
