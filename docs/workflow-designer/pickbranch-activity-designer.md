---
title: 워크플로 디자이너 PickBranch 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34da9091c0f96b7270678f9b36fe861e4a87418f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86876088"
---
# <a name="pickbranch-activity-designer"></a>PickBranch 활동 디자이너

<xref:System.Activities.Statements.PickBranch>는 들어오는 이벤트에 의해 트리거되는 <xref:System.Activities.Statements.Pick> 활동 내에서 이벤트 기반의 실행 경로를 제공합니다.

## <a name="pickbranch"></a>PickBranch

<xref:System.Activities.Statements.PickBranch> 개체는 <xref:System.Activities.Statements.Pick.Branches%2A> 활동의 <xref:System.Activities.Statements.Pick> 컬렉션에 포함되어 있습니다. 각 <xref:System.Activities.Statements.PickBranch>는 <xref:System.Activities.Statements.Pick> 활동의 분기에 포함되며 트리거 역할을 하는 일부 들어오는 이벤트에 따라 실행될 수 있습니다. 이러한 방식으로 워크플로 디자이너는 이벤트 기반 제어 흐름 모델링을 제공 합니다. 각 <xref:System.Activities.Statements.PickBranch>에는 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 및 <xref:System.Activities.Statements.PickBranch.Action%2A>이 포함되어 있습니다.

### <a name="how-to-use-the-pick-activity-designer"></a>Pick 활동 디자이너를 사용하는 방법

**도구 상자**의 **제어 흐름** 범주에 있는 **PickBranch** 디자이너에 액세스 합니다.

<xref:System.Activities.Statements.PickBranch> **Branch1** 및 **Branch2** 의 표시 이름을 사용 하는 두 개의 빈 개체는 기본적으로 <xref:System.Activities.Statements.Pick> **Pick** 활동 디자이너를 워크플로 디자이너에 처음 놓을 때 활동의 요소로 만들어집니다. 이러한 <xref:System.Activities.Statements.PickBranch.DisplayName%2A> 각 속성 값은 **PickBranch** designer 헤더 또는 각 분기의 **속성** 창에서 편집할 수 있습니다.

개체의 컬렉션에 개체를 추가 하는 방법은 두 가지입니다 <xref:System.Activities.Statements.PickBranch> <xref:System.Activities.Statements.Pick> . **도구 상자**에서 **PickBranch** 디자이너를 끌어서 놓거나 **뚝딱** 디자인 화면에서 오른쪽 클릭 메뉴를 사용 합니다.

- **PickBranch** 디자이너는 <xref:System.Activities.Statements.PickBranch> **도구 상자** 에서 끌고 워크플로 디자이너 표면의 **Pick** 활동 디자이너 분기 중 하나로 끌어 놓으면를 만듭니다. 새 <xref:System.Activities.Statements.PickBranch> 개체는 <xref:System.Activities.Statements.Pick> 디자이너 내에서 컬렉션에 이미 포함되어 있는 기존 <xref:System.Activities.Statements.PickBranch> 요소의 왼쪽 또는 오른쪽에 배치됩니다. **PickBranch** 디자이너를 마우스를 사용 하 여 **뚝딱** 디자이너에 끌어다 놓으면 **뚝딱** 디자이너는 파란색 세로 띠를 사용 하 여 <xref:System.Activities.Statements.PickBranch> 지정 된 마우스 배치에 대해가 추가 된 위치를 표시 합니다.

- **PickBranch** designer 내부가 아닌 **뚝딱** 활동 디자이너를 마우스 오른쪽 단추로 클릭 하 여 상황에 맞는 메뉴를 가져오고 **분기 만들기** 를 선택 하 여 새를 추가 <xref:System.Activities.Statements.PickBranch> 합니다. 새 <xref:System.Activities.Statements.PickBranch> 가 <xref:System.Activities.Statements.PickBranch> **뚝딱** 디자이너에서 기존 개체의 오른쪽에 추가 됩니다.

**PickBranch** 디자이너를 확장 하 여 **트리거** 및 **작업** 상자를 표시 하거나 머리글의 오른쪽에 있는 이중 캐럿을 클릭 하 여 축소할 수 있습니다. 활동을 <xref:System.Activities.Statements.PickBranch.Trigger%2A> <xref:System.Activities.Statements.PickBranch.Action%2A> <xref:System.Activities.Statements.PickBranch> 디자이너의 **트리거** 및 **작업** 상자로 끌어 각의 및를 편집 합니다.

<xref:System.Activities.Statements.PickBranch> <xref:System.Activities.Statements.Pick.Branches%2A> 개체의 컬렉션에 있는 개체는 <xref:System.Activities.Statements.Pick> **뚝딱** 디자이너 내의 새 위치로 끌어서 다시 정렬할 수 있습니다. **뚝딱** 디자이너는 가로 파랑-회색 띠를 사용 하 여 지정 된 <xref:System.Activities.Statements.PickBranch> 마우스 배치에 대해가 추가 된 위치를 표시 합니다.

<xref:System.Activities.Statements.PickBranch>를 삭제하는 방법은 두 가지입니다.

- **PickBranch** 디자이너를 선택 하 고 삭제 합니다.
- **PickBranch** 디자이너를 선택 하 고 마우스 오른쪽 단추를 클릭 하 여 상황에 맞는 메뉴를 가져온 다음 **삭제**를 선택 합니다.

**PickBranch** 디자이너를 선택 해야 합니다. **트리거** 또는 **작업** 상자 내에서 작업 중 하나를 실수로 선택 하면 개체가 아닌 이러한 작업 중 하나를 삭제 합니다 <xref:System.Activities.Statements.PickBranch> .

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Workflow Designer의 PickBranch 속성

다음 표에서는 가장 유용한 속성을 보여 주고 <xref:System.Activities.Statements.PickBranch> 워크플로 디자이너에서 사용 하는 방법을 설명 합니다.

|속성 이름|필수|사용량|
|-|--------------|-|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|**PickBranch** 디자이너의 헤더에 표시 되는 이름입니다. 기본값은 분기입니다.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|각 <xref:System.Activities.Statements.PickBranch>에는 <xref:System.Activities.Statements.PickBranch.Trigger%2A>을 호출할 수 있는 <xref:System.Activities.Statements.PickBranch.Action%2A> 활동이 포함되어 있습니다.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|각 <xref:System.Activities.Statements.PickBranch>에는 트리거될 경우 실행되는 <xref:System.Activities.Statements.PickBranch.Action%2A>이 포함되어 있습니다.|

## <a name="see-also"></a>추가 정보

- [제어 흐름](../workflow-designer/control-flow-activity-designers.md)
- [선택 활동](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Pick 작업 사용](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)