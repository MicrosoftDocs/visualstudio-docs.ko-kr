---
title: 프로젝트 모델링 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706549"
---
# <a name="project-modeling"></a>프로젝트 모델링
프로젝트에 대 한 자동화를 제공 하는 다음 단계는 표준 프로젝트 개체 ( <xref:EnvDTE.Projects> 및 `ProjectItems` 컬렉션, `Project` 및 <xref:EnvDTE.ProjectItem> 개체) 및 구현에 고유한 나머지 개체를 구현 하는 것입니다. 이러한 표준 개체는 Dteinternal .h 파일에 정의 되어 있습니다. 표준 개체의 구현은 BscPrj 샘플에서 제공 됩니다. 이러한 클래스를 모델로 사용 하 여 다른 프로젝트 형식의 project 개체와 나란히 있는 고유한 표준 프로젝트 개체를 만들 수 있습니다.

 Automation 소비자는 <xref:EnvDTE.Solution> ("및 ()를 호출할 수 있다고 가정 `<UniqueProjName>")` <xref:EnvDTE.ProjectItems> `n` 합니다. 여기서 n은 솔루션에서 특정 프로젝트를 가져오기 위한 인덱스 번호입니다. 이 자동화 호출로 인해 환경에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> 적절 한 프로젝트 계층 구조에 대해를 호출 하 여 VSITEMID_ROOT를 ItemID 매개 변수로 전달 하 고 VSHPROPID_ExtObject을 VSHPROPID 매개 변수로 전달 합니다. `IVsHierarchy::GetProperty``IDispatch`구현한 핵심 인터페이스를 제공 하는 자동화 개체에 대 한 포인터를 반환 `Project` 합니다.

 다음은의 구문입니다 `IVsHierarchy::GetProperty` .

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 프로젝트는 중첩을 수용 하 고 컬렉션을 사용 하 여 프로젝트 항목 그룹을 만듭니다. 계층 구조는 다음과 같습니다.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 중첩은 <xref:EnvDTE.ProjectItem> <xref:EnvDTE.ProjectItems> 컬렉션이 중첩 된 개체를 포함할 수 있기 때문에 개체를 동시에 수집할 수 있음을 의미 합니다 `ProjectItems` . 기본 프로젝트 샘플에서는 이러한 중첩을 보여 주지 않습니다. 개체를 구현 하 여 `Project` 전체 자동화 모델의 디자인에 대 한 특징을 나타내는 트리 형식의 구조에 참여 합니다.

 프로젝트 자동화는 다음 다이어그램의 경로를 따릅니다.

 ![Visual Studio 프로젝트 개체](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") 프로젝트 자동화

 개체를 구현 하지 않는 경우 `Project` 환경에서 `Project` 프로젝트 이름만 포함 하는 제네릭 개체를 반환 합니다.

## <a name="see-also"></a>추가 정보
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
