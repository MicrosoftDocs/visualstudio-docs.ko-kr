---
title: 프로젝트 항목에 특성 추가 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 059eef0b6a215f1f02c77df63f777fbfda5dff19
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80740194"
---
# <a name="add-an-attribute-to-a-project-item"></a>프로젝트 항목에 특성 추가
메서드 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> 및는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> 프로젝트 항목의 특성 값을 가져오고 설정 합니다. SetItemAttribute가 아직 없는 경우 특성을 만들어 프로젝트 항목 메타 데이터에 추가 합니다.

## <a name="add-an-attribute-to-a-project-item"></a>프로젝트 항목에 특성 추가

- 다음 코드에서는 <xref:EnvDTE.DTE> automation 개체와 메서드를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> 프로젝트 항목에 특성을 추가 합니다. 프로젝트 항목 ID는 프로젝트 항목 이름 "program.cs"에서 가져옵니다. "MyAttribute" 특성은이 프로젝트 항목에 추가 되 고 "MyValue" 값이 지정 됩니다.

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        uint itemId;
        string fullPath = (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;
        hierarchy.ParseCanonicalName(fullPath, out itemId);
        buildPropertyStorage.SetItemAttribute(itemId, "MyAttribute", "MyValue");
    }

    ```

## <a name="see-also"></a>추가 정보
- [MSBuild 프로젝트 파일에 데이터 보관](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
