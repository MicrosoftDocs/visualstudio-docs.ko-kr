---
title: 프로젝트 항목에 특성 추가 | Microsoft Docs
description: 셸 Interop 메서드 GetItemAttribute 및 SetItemAttribute를 사용하여 Visual Studio 프로젝트 항목에 특성을 추가하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 36fc5905fd2b1423865982a80a6cb2ba6a803cc5
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902022"
---
# <a name="add-an-attribute-to-a-project-item"></a>프로젝트 항목에 특성 추가
메서드 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> 프로젝트 항목의 특성 값을 얻고 설정합니다. SetItemAttribute는 특성이 아직 없는 경우 해당 특성을 만들어 프로젝트 항목 메타데이터에 추가합니다.

## <a name="add-an-attribute-to-a-project-item"></a>프로젝트 항목에 특성 추가

- 다음 코드에서는 <xref:EnvDTE.DTE> 자동화 개체와 메서드를 사용하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> 특성을 프로젝트 항목에 추가합니다. 프로젝트 항목 ID는 프로젝트 항목 이름 "program.cs"에서 가져온 것입니다. "MyAttribute" 특성이 이 프로젝트 항목에 추가되고 "MyValue" 값이 지정됩니다.

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
