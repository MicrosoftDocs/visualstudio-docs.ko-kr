---
title: 런타임에 프로젝트의 하위 유형 확인 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698179"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>런타임에 프로젝트의 하위 유형 확인
사용자 지정 프로젝트 하위 형식에 종속된 VSPackage에는 하위 형식이 없는 경우 정상적으로 실패할 수 있도록 해당 하위 형식을 찾는 논리가 포함되어야 합니다. 다음 절차에서는 지정된 하위 형식의 존재를 확인하는 방법을 보여 주며

### <a name="to-verify-the-presence-of-a-subtype"></a>하위 형식의 존재를 확인하려면

1. VSPackage에 다음 코드를 추가하여 프로젝트 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 및 솔루션 개체에서 프로젝트 계층 구조를 개체로 가져옵니다.

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

2. 계층을 인터페이스에 <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> 캐스팅합니다.

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. 을 호출하여 프로젝트 유형 GUID 목록을 <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>가져옵니다.

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. 지정된 하위 유형의 GUID 목록을 확인합니다.

    ```csharp
    // Replace the string "MyGUID" with the GUID of the subtype.
    string guidMySubtype = "MyGUID";
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)
    {
        // The specified subtype is present.
    }
    ```

## <a name="see-also"></a>참조
- [프로젝트 하위 유형](../extensibility/internals/project-subtypes.md)
- [프로젝트 하위 유형 설계](../extensibility/internals/project-subtypes-design.md)
- [프로젝트 하위 유형으로 확장된 속성 및 메서드](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
