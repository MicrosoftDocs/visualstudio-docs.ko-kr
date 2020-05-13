---
title: 프로젝트 항목에 특성 추가 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740194"
---
# <a name="add-an-attribute-to-a-project-item"></a>프로젝트 항목에 특성 추가
메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> 얻고 프로젝트 항목의 특성 값을 설정합니다. SetItemAttribute 이 아직 존재하지 않는 경우 특성을 만들어 프로젝트 항목 메타데이터에 추가합니다.

## <a name="add-an-attribute-to-a-project-item"></a>프로젝트 항목에 특성 추가

- 다음 코드는 <xref:EnvDTE.DTE> 자동화 개체와 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> 메서드를 사용하여 프로젝트 항목에 특성을 추가합니다. 프로젝트 항목 ID는 프로젝트 항목 이름 "program.cs"에서 가져옵니다. "MyAttribute" 특성이 이 프로젝트 항목에 추가되고 "MyValue" 값이 주어집니다.

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

## <a name="see-also"></a>참조
- [MSBuild 프로젝트 파일에 데이터 유지](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
