---
title: 프로젝트 모델링 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1ac89baf5bc7582d3430532938a5e5a0c35a4c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706549"
---
# <a name="project-modeling"></a>프로젝트 모델링
프로젝트에 자동화를 제공하는 다음 단계는 표준 프로젝트 개체를 <xref:EnvDTE.Projects> `ProjectItems` 구현하는 것입니다. `Project` 및 <xref:EnvDTE.ProjectItem> 개체; 구현에 고유한 나머지 개체입니다. 이러한 표준 객체는 Dteinternal.h 파일에 정의되어 있습니다. 표준 개체의 구현은 BscPrj 샘플에 제공됩니다. 이러한 클래스를 모델로 사용하여 다른 프로젝트 형식의 프로젝트 개체와 나란히 서 있는 고유한 표준 프로젝트 객체를 만들 수 있습니다.

 자동화 소비자는 n이 솔루션에서 <xref:EnvDTE.Solution>특정`<UniqueProjName>")` 프로젝트를 <xref:EnvDTE.ProjectItems> `n`얻기 위한 인덱스 번호인 경우 호출("및 )을 호출할 수 있을 것으로 가정합니다. 이 자동화 호출을 하면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> 환경이 적절한 프로젝트 계층 구조를 호출하여 VSITEMID_ROOT ItemID 매개 변수로 전달하고 VSHPROPID_ExtObject VSHPROPID 매개 변수로 전달합니다. `IVsHierarchy::GetProperty`은 `IDispatch` 구현한 핵심 `Project` 인터페이스를 제공하는 자동화 개체에 대한 포인터를 반환합니다.

 다음은 의 `IVsHierarchy::GetProperty`구문입니다.

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

 중첩은 <xref:EnvDTE.ProjectItem> `ProjectItems` 컬렉션에 중첩된 개체를 포함할 <xref:EnvDTE.ProjectItems> 수 있으므로 개체를 동시에 컬렉션으로 만들 수 있음을 의미합니다. 기본 프로젝트 샘플에서는 이 중첩을 보여 줍니다. 개체를 `Project` 구현하면 전체 자동화 모델의 설계를 특징짓는 트리와 같은 구조에 참여합니다.

 프로젝트 자동화는 다음 다이어그램의 경로를 따릅니다.

 ![비주얼 스튜디오 프로젝트 개체](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") 프로젝트 자동화

 개체를 `Project` 구현하지 않으면 환경은 프로젝트 이름만 `Project` 포함하는 제네릭 개체를 반환합니다.

## <a name="see-also"></a>참조
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
