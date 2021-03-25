---
title: 프로젝트 항목에 특성 추가 | Microsoft Docs
description: 셸 Interop 메서드 GetItemAttribute 및 SetItemAttribute를 사용 하 여 Visual Studio에서 프로젝트 항목에 특성을 추가 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ee65a22e0a296047f5a401e00495ee25403d64e0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094915"
---
# <a name="add-an-attribute-to-a-project-item"></a>프로젝트 항목에 특성 추가
메서드 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> 및는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> 프로젝트 항목의 특성 값을 가져오고 설정 합니다. SetItemAttribute가 아직 없는 경우 특성을 만들어 프로젝트 항목 메타 데이터에 추가 합니다.

## <a name="add-an-attribute-to-a-project-item"></a>프로젝트 항목에 특성 추가

- 다음 코드에서는 <xref:EnvDTE.DTE> automation 개체와 메서드를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> 프로젝트 항목에 특성을 추가 합니다. 프로젝트 항목 ID는 프로젝트 항목 이름 "program .cs"에서 가져옵니다. "MyAttribute" 특성은이 프로젝트 항목에 추가 되 고 "MyValue" 값이 지정 됩니다.

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
- [MSBuild 프로젝트 파일에 데이터 보관](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
