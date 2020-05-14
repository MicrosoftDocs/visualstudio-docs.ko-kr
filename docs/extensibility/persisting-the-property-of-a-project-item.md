---
title: 프로젝트 항목의 속성 유지 | 마이크로 소프트 문서
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15c280f15436a5e27bcc0dcc4d2fb9e9bdd82933
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702205"
---
# <a name="persist-the-property-of-a-project-item"></a>프로젝트 항목의 속성 유지
원본 파일의 작성자등 프로젝트 항목에 추가하는 속성을 유지/할 수 있습니다. 프로젝트 파일에 속성을 저장하여 이 작업을 수행할 수 있습니다.

 프로젝트 파일에 속성을 유지하는 첫 번째 단계는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 프로젝트의 계층 구조를 인터페이스로 가져오는 것입니다. 자동화를 사용하거나 을 사용하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>이 인터페이스를 가져올 수 있습니다. 인터페이스를 가져오면 이 인터페이스를 사용하여 현재 선택된 프로젝트 항목을 결정할 수 있습니다. 프로젝트 항목 ID가 있으면 속성을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> 추가하는 데 사용할 수 있습니다.

 다음 절차에서는 프로젝트 파일의 *VsPkg.cs* 값으로 `Author` `Tom` VsPkg.cs 속성을 유지합니다.

## <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>DTE 개체를 사용하여 프로젝트 계층구조를 가져오려면

1. VSPackage에 다음 코드를 추가합니다.

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

## <a name="to-persist-the-project-item-property-with-the-dte-object"></a>DTE 개체를 사용하여 프로젝트 항목 속성을 유지하려면

1. 이전 프로시저의 메서드에 지정된 코드에 다음 코드를 추가합니다.

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        uint itemId;
        string fullPath = (string)project.ProjectItems.Item(
            "VsPkg.cs").Properties.Item("FullPath").Value;
        hierarchy.ParseCanonicalName(fullPath, out itemId);
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>IVsMonitor선택을 사용하여 프로젝트 계층구조를 가져오려면

1. VSPackage에 다음 코드를 추가합니다.

    ```csharp
    IVsHierarchy hierarchy = null;
    IntPtr hierarchyPtr = IntPtr.Zero;
    IntPtr selectionContainer = IntPtr.Zero;
    uint itemid;

    // Retrieve shell interface in order to get current selection
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;
    if (monitorSelection == null)
        throw new InvalidOperationException();

    try
    {
        // Get the current project hierarchy, project item, and selection container for the current selection
        // If the selection spans multiple hierachies, hierarchyPtr is Zero
        IVsMultiItemSelect multiItemSelect = null;
        ErrorHandler.ThrowOnFailure(
            monitorSelection.GetCurrentSelection(
                out hierarchyPtr, out itemid,
                out multiItemSelect, out selectionContainer));

        // We only care if there is only one node selected in the tree
        if (!(itemid == VSConstants.VSITEMID_NIL ||
            hierarchyPtr == IntPtr.Zero ||
            multiItemSelect != null ||
            itemid == VSConstants.VSITEMID_SELECTION))
        {
            hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr)
                as IVsHierarchy;
        }
    }
    finally
    {
        if (hierarchyPtr != IntPtr.Zero)
            Marshal.Release(hierarchyPtr);
        if (selectionContainer != IntPtr.Zero)
            Marshal.Release(selectionContainer);
    }
    ```

## <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>프로젝트 계층 구조가 지정된 선택한 프로젝트 항목 속성을 유지하려면

1. 이전 프로시저의 메서드에 지정된 코드에 다음 코드를 추가합니다.

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-verify-that-the-property-is-persisted"></a>속성이 유지되는지 확인하려면

1. 먼저 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 솔루션을 열고 만들 수 있습니다.

2. **솔루션 탐색기에서**VsPkg.cs 프로젝트 항목을 선택합니다.

3. 중단점을 사용하거나 VSPackage가 로드되고 SetItemAttribute가 실행되는지 확인합니다.

   > [!NOTE]
   > UI 컨텍스트에서 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>VSPackage를 자동 로드할 수 있습니다. 자세한 내용은 [VS패키지 로드 를](../extensibility/loading-vspackages.md)참조하십시오.

4. 메모장에서 프로젝트 파일을 닫고 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 엽니다. \<다음과 같이 Tom 값이 있는 작성자> 태그가 표시됩니다.

   ```xml
   <Compile Include="VsPkg.cs">
       <Author>Tom</Author>
   </Compile>
   ```

## <a name="see-also"></a>참조

- [사용자 지정 도구](../extensibility/internals/custom-tools.md)
