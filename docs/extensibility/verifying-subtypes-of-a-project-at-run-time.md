---
title: 런타임에 프로젝트의 하위 형식 확인 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0d739a9f8734dd8941e3254d03364cbf4c77350
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698179"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>런타임에 프로젝트의 하위 형식 확인
사용자 지정 프로젝트 하위 유형에 따라 달라 지는 VSPackage는 하위 유형이 없는 경우 정상적으로 실패할 수 있도록 해당 하위 유형을 찾는 논리를 포함 해야 합니다. 다음 절차에서는 지정 된 하위 형식이 있는지 확인 하는 방법을 보여 줍니다.

### <a name="to-verify-the-presence-of-a-subtype"></a>하위 형식이 있는지 확인 하려면

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>VSPackage에 다음 코드를 추가 하 여 프로젝트 및 솔루션 개체에서 개체로 프로젝트 계층 구조를 가져옵니다.

    ```csharp
    EnvDTE.DTE dte;
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));

    EnvDTE.Project project;
    project = dte.Solution.Projects.Item(1);

    IVsSolution solution;
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));

    IVsHierarchy hierarchy;
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);

    ```

2. 계층을 <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> 인터페이스로 캐스팅 합니다.

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. 을 호출 하 여 프로젝트 형식 Guid 목록을 가져옵니다 <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A> .

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. 목록에서 지정 된 하위 형식의 GUID를 확인 합니다.

    ```csharp
    // Replace the string "MyGUID" with the GUID of the subtype.
    string guidMySubtype = "MyGUID";
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)
    {
        // The specified subtype is present.
    }
    ```

## <a name="see-also"></a>추가 정보
- [프로젝트 하위 형식](../extensibility/internals/project-subtypes.md)
- [프로젝트 하위 형식 디자인](../extensibility/internals/project-subtypes-design.md)
- [프로젝트 하위 형식에 의해 확장 된 속성 및 메서드](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
