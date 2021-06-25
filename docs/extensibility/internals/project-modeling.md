---
title: 프로젝트 모델링 | Microsoft Docs
description: 새 프로젝트 형식에 대한 자동화를 만드는 데 필요한 표준 프로젝트 개체와 프로젝트 자동화가 따르는 경로에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b90271fcc43c627f2eb7dbb2f318427ad0d9839e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899682"
---
# <a name="project-modeling"></a>프로젝트 모델링
프로젝트에 대한 자동화를 제공하는 다음 단계는 표준 프로젝트 개체( <xref:EnvDTE.Projects> 및 `ProjectItems` 컬렉션, 및 개체 및 `Project` <xref:EnvDTE.ProjectItem> 구현에 고유한 나머지 개체)를 구현하는 것입니다. 이러한 표준 개체는 Dteinternal.h 파일에 정의되어 있습니다. 표준 개체의 구현은 BscPrj 샘플에서 제공됩니다. 이러한 클래스를 모델로 사용하여 다른 프로젝트 형식의 프로젝트 개체와 나란히 서 있는 고유한 표준 프로젝트 개체를 만들 수 있습니다.

 자동화 소비자는 (" 및 ( )를 호출할 수 있다고 <xref:EnvDTE.Solution> `<UniqueProjName>")` 가정합니다. <xref:EnvDTE.ProjectItems> `n` 여기서 n은 솔루션에서 특정 프로젝트를 얻기 위한 인덱스 번호입니다. 이 자동화 호출을 만들면 환경이 적절한 프로젝트 계층에서 를 호출하고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> VSITEMID_ROOT ItemID 매개 변수로 전달하고 VSHPROPID_ExtObject VSHPROPID 매개 변수로 전달합니다. `IVsHierarchy::GetProperty` 는 `IDispatch` 구현한 핵심 인터페이스를 제공하는 자동화 개체에 대한 `Project` 포인터를 반환합니다.

 다음은 의 `IVsHierarchy::GetProperty` 구문입니다.

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 프로젝트는 중첩을 수용하고 컬렉션을 사용하여 프로젝트 항목 그룹을 만듭니다. 계층 구조는 다음과 같습니다.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 중첩은 컬렉션에 <xref:EnvDTE.ProjectItem> 중첩된 개체가 포함될 수 <xref:EnvDTE.ProjectItems> 있으므로 개체가 동시에 수집될 수 있음을 `ProjectItems` 의미합니다. 기본 프로젝트 샘플에서는 이 중첩을 보여 주지 않습니다. 개체를 구현하여 `Project` 전체 자동화 모델의 디자인 특징을 지정하는 트리와 같은 구조체에 참여합니다.

 프로젝트 자동화는 다음 다이어그램의 경로를 따릅니다.

 ![프로젝트 개체 Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") 프로젝트 자동화

 개체를 구현하지 않으면 `Project` 환경은 프로젝트 이름만 포함하는 제네릭 개체를 계속 `Project` 반환합니다.

## <a name="see-also"></a>참조
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
