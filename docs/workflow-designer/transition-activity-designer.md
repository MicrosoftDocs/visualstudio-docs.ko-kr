---
title: 워크플로 디자이너 전환 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Transition.UI
ms.assetid: f6e8b5cc-7fb8-4699-9703-f3c9fc7cc316
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: c71f31f4582a60bcfc87e4906a1447e33ffa7bd3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75593085"
---
# <a name="transition-activity-designer"></a>전환 활동 디자이너

<xref:System.Activities.Statements.Transition>은 두 상태 간 전환을 나타냅니다.

## <a name="using-the-transition-activity-designer"></a>전환 활동 디자이너 사용

전환 활동 디자이너를 사용하면 두 상태 간에 전환을 구성할 수 있습니다.

### <a name="transition-properties-in-the-workflow-designer"></a>Workflow Designer의 Transition 속성

다음 표에서는 워크플로 디자이너를 사용하여 설정할 수 있는 <xref:System.Activities.Statements.Transition> 속성을 보여 주고 디자이너에서 이러한 속성을 사용하는 방법을 설명합니다.

|속성 이름|필수|사용량|
|-|--------------|-|
|<xref:System.Activities.Statements.Transition.DisplayName%2A>|False|<xref:System.Activities.Statements.Transition> 활동 디자이너의 이름을 지정합니다. 기본값은 **T1**입니다. 값은 속성 표, 확장된 전환 디자이너의 헤더 및 확장된 전환 디자이너 내에서 작업 섹션의 헤더에서 편집할 수 있습니다. <xref:System.Activities.Activity.DisplayName%2A>은 워크플로 디자이너 상단에 표시되는 이동 경로 탐색에 사용됩니다.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.Transition.Condition%2A>|False|있는 경우 제어를 대상 상태로 전달 하기 전에 **True** 로 평가 해야 하는 식을 지정 합니다. 속성 표 및 확장 전환 디자이너에서 이 조건을 편집할 수 있습니다. 전환 디자이너에 나타나는 순서로 공유 전환의 여러 조건을 평가합니다. **참고:**  <xref:System.Activities.Statements.Transition.Condition%2A> 전환의이 **false** 로 평가 되거나 공유 트리거 전환의 모든 조건이 **false**로 평가 되는 경우에는 전환이 발생 하지 않으며 상태에서 모든 전환에 대 한 모든 트리거가 다시 예약 됩니다. 이 자습서에서는 조건이 구성된 방식(추측이 올바른지 또는 잘못되었는지에 따라 특정 동작이 지정됨) 때문에 이러한 상황이 발생할 수 없습니다.|
|**원본**|True|이 전환이 원래 발생한 상태를 나타냅니다. 소스 상태의 이름을 클릭하면 디자이너 보기가 해당 상태의 확장된 보기로 전환됩니다. 이 값은 전환이 만들어질 때 설정되며 변경될 수 있습니다.|
|<xref:System.Activities.Statements.Transition.Trigger%2A>|False|완료 시 전환을 시작하는 활동을 지정합니다. 이 작업을 설정 하려면 **도구 상자** 에서 활동을 끌어 전환의 **트리거** 섹션에 놓습니다.|
|<xref:System.Activities.Statements.Transition.Action%2A>|False|트리거 작업이 완료 될 때 실행 되는 활동을 지정 하 고 <xref:System.Activities.Statements.Transition.Condition%2A> , 있는 경우 **true**로 평가 됩니다. 이 활동은 소스 상태(있을 경우)에 대한 <xref:System.Activities.Statements.State.Exit%2A> 활동이 실행된 후에 대상 상태로 전환할 때 실행됩니다. 전환 디자이너가 확장 되 면 **도구 상자** 에서 활동을 끌어 전환의 **동작** 섹션에 놓으면이 값을 설정할 수 있습니다. 단일 전환에 여러 작업이 있을 수 있습니다. 개별 작업을 확장하고 수축할 수 있으며 전환 중인 작업이 여러 개 있을 때 작업에 나타나는 위 또는 아래 화살표를 클릭하여 순서를 지정할 수 있습니다.|
|**대상**|True|전환이 완료된 후 상태 시스템이 전환하는 상태를 나타냅니다. 이는 개체 모델에 있는 전환의 <xref:System.Activities.Statements.Transition.To%2A> 속성에 해당합니다. 대상 상태의 이름을 클릭하면 디자이너 보기가 해당 상태의 확장된 보기로 전환됩니다. 이 값은 전환이 만들어지면 설정되고 전환을 디자이너의 대상 상태에 연결하는 화살표를 끌어 변경할 수 있습니다.|

### <a name="creating-transitions"></a>전환 만들기

전환은 한 상태에서 다른 상태로 선을 끌거나 한 상태를 다른 상태 위로 끌어갈 때 나타나는 삼각형에 상태를 놓으면 만들어집니다. 끌어서 전환을 만들려면 소스 상태의 가장자리 위로 마우스를 가져가 소스 상태에서 대상 상태로 선을 끕니다. 놓아서 전환을 만들려면 대상 상태를 끌어 소스 상태 위로 가져가 소스 상태 주변에 나타나는 4개의 삼각형 중 하나에 놓습니다. 대상 상태는 **도구 상자**에서 끌어 온 새 상태 이거나 workflow designer에서 끌어 온 기존 상태일 수 있습니다.

> [!NOTE]
> 상태 시스템에서 하나의 상태는 Workflow Designer를 사용하여 만들어지는 전환을 76개까지 사용할 수 있습니다. 디자이너 밖에서 만들어지는 워크플로 상태의 전환에 대한 제한은 시스템 리소스로만 제한됩니다.

공유 트리거 전환은 같은 트리거 이벤트를 공유하는 전환 집합입니다. 공유 트리거를 사용하면 공통의 트리거 이벤트를 공유하는 여러 전환에 대해 구성된 식의 평가를 기준으로 대상 상태로 조건적 진행이 가능합니다. 전환에 추가 작업을 추가하고 공유 전환을 만들려면 원하는 전환의 시작을 나타내는 원을 클릭하고 원하는 상태로 끕니다. 새 전환은 초기 전환과 동일한 트리거를 공유하지만 고유한 조건과 작업을 사용합니다. 전환 디자이너의 맨 아래에 있는 **공유 트리거 전환 추가** 를 클릭 한 다음 **사용 가능한 상태 드롭다운에서 연결할** 대상 상태를 선택 하 여 전환 디자이너 내에서 공유 전환을 만들 수도 있습니다.

## <a name="see-also"></a>추가 정보

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [FinalState](../workflow-designer/finalstate-activity-designer.md)
- [State](../workflow-designer/state-activity-designer.md)
