---
title: 프로젝트 항목의 속성 유지 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4adcf0f5c5770f5d3ffc0e0ed9bffdb108869c7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841583"
---
# <a name="persisting-the-property-of-a-project-item"></a>프로젝트 항목의 속성 유지
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로젝트 항목에 추가 하는 속성 (예: 소스 파일의 작성자)을 유지 하려고 할 수 있습니다. 프로젝트 파일에 속성을 저장 하 여이 작업을 수행할 수 있습니다.  
  
 프로젝트 파일에서 속성을 유지 하는 첫 번째 단계는 프로젝트의 계층 구조를 인터페이스로 가져오는 것입니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> . 자동화를 사용 하거나를 사용 하 여이 인터페이스를 가져올 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> . 인터페이스를 가져온 후에는이 인터페이스를 사용 하 여 현재 선택 된 프로젝트 항목을 확인할 수 있습니다. 프로젝트 항목 ID가 있으면를 사용 하 여 속성을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> 추가할 수 있습니다.  
  
 다음 절차에서는 `Author` 프로젝트 파일의 값을 사용 하 여 VsPkg.cs 속성을 유지 합니다 `Tom` .  
  
### <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>DTE 개체를 사용 하 여 프로젝트 계층 구조를 가져오려면  
  
1. VSPackage에 다음 코드를 추가 합니다.  
  
    ```csharp  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    ```  
  
### <a name="to-persist-the-project-item-property-with-the-dte-object"></a>DTE 개체를 사용 하 여 프로젝트 항목 속성을 유지 하려면  
  
1. 이전 절차의 메서드에 지정 된 코드에 다음 코드를 추가 합니다.  
  
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
  
### <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>IVsMonitorSelection을 사용 하 여 프로젝트 계층 구조를 가져오려면  
  
1. VSPackage에 다음 코드를 추가 합니다.  
  
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
  
2. 
  
### <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>프로젝트 계층 구조가 지정 된 경우 선택한 프로젝트 항목 속성을 유지 하려면  
  
1. 이전 절차의 메서드에 지정 된 코드에 다음 코드를 추가 합니다.  
  
    ```  
    IVsBuildPropertyStorage buildPropertyStorage =   
        hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");  
    }  
    ```  
  
### <a name="to-verify-that-the-property-is-persisted"></a>속성이 유지 되는지 확인 하려면  
  
1. 를 시작 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 하 고 솔루션을 열거나 만듭니다.  
  
2. **솔루션 탐색기**에서 프로젝트 항목 VsPkg.cs를 선택 합니다.  
  
3. 중단점을 사용 하거나, VSPackage가 로드 되 고 SetItemAttribute가 실행 되는지 확인 합니다.  
  
    > [!NOTE]
    > UI 컨텍스트에서 VSPackage을 autoload 수 있습니다 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid> . 자세한 내용은 [Vspackage 로드](../extensibility/loading-vspackages.md)를 참조 하세요.  
  
4. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]메모장에서 프로젝트 파일을 닫았다가 엽니다. 다음과 \<Author> 같이 Tom 값을 가진 태그가 표시 됩니다.  
  
    ```  
    <Compile Include="VsPkg.cs">  
        <Author>Tom</Author>  
    </Compile>  
    ```  
  
## <a name="see-also"></a>참고 항목  
 [사용자 지정 도구](../extensibility/internals/custom-tools.md)
