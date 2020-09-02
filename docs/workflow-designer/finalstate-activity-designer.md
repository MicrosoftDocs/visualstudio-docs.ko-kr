---
title: 워크플로 디자이너-전체 상태 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23e8973de1deba610a90e21edb870000abbb03e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86875594"
---
# <a name="finalstate-activity-designer"></a>FinalState 활동 디자이너

<xref:System.Activities.Core.Presentation.FinalState> 디자이너는 상태 시스템 인스턴스를 종료하는 <xref:System.Activities.Statements.State>를 만드는 데 사용됩니다.

## <a name="using-the-finalstate-activity-designer"></a>FinalState 활동 디자이너 사용

**FinalState** <xref:System.Activities.Statements.State> 상태 시스템에서 종료 상태로 미리 구성 된를 만드는 데는 상태 디자이너가 사용 됩니다. <xref:System.Activities.Statements.State>활동 디자이너를 사용 하 여 만든은 <xref:System.Activities.Core.Presentation.FinalState> 해당 <xref:System.Activities.Statements.State.IsFinal%2A> 속성을 **true**로 설정 하 고, 활동이 없으며, 해당에서 발생 하는 <xref:System.Activities.Statements.State.Exit%2A> 전환이 없습니다. 활동 디자이너를 사용 하 여 <xref:System.Activities.Core.Presentation.FinalState> <xref:System.Activities.Statements.State> 상태 시스템에서 종료 상태로 미리 구성 된 활동을 추가 하려면 **도구 상자** 의 **상태 시스템** 섹션에서 상태 활동 디자이너 **를** 끌어 workflow designer에 놓습니다. <xref:System.Activities.Core.Presentation.FinalState> 활동 디자이너를 <xref:System.Activities.Statements.StateMachine>에 끌어 놓고 나중에 전환을 추가하거나 <xref:System.Activities.Core.Presentation.FinalState> 활동 디자이너를 끌어 놓을 때 전환을 만들 수 있습니다. 전환 만들기에 대 한 자세한 내용은 [전환](../workflow-designer/transition-activity-designer.md)을 참조 하세요.

### <a name="state-activity-properties-in-the-workflow-designer"></a>Workflow Designer의 State 활동 속성

다음 표에서는 <xref:System.Activities.Core.Presentation.FinalState> 디자이너를 사용하여 설정할 수 있는 속성을 보여 주고 디자이너에서 이러한 속성을 사용하는 방법을 설명합니다. 이러한 일부 속성은 속성 표에서 편집할 수 있으며 일부 속성은 디자이너 화면에서 편집할 수 있습니다.

|속성 이름|필수|사용량|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|머리글에 <xref:System.Activities.Statements.State> 활동 디자이너의 이름을 지정합니다. 기본값은 **State**입니다. 속성 표에서 또는 활동 디자이너의 머리글에서 직접 값을 편집할 수 있습니다. <xref:System.Activities.Statements.State.DisplayName%2A>은 워크플로 디자이너 상단에 표시되는 이동 경로 탐색에 사용됩니다.<br /><br /> <xref:System.Activities.Statements.State.DisplayName%2A>은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.State.Entry%2A>|False|이 상태가 전환될 때 발생하는 동작을 지정합니다. **도구 상자** 에서 활동을 끌어 상태 섹션에 놓으면이 값을 설정할 수 있습니다 <xref:System.Activities.Statements.State.Entry%2A> .|

## <a name="see-also"></a>추가 정보

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [State](../workflow-designer/state-activity-designer.md)
- [전환](../workflow-designer/transition-activity-designer.md)