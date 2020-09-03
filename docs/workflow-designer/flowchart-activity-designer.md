---
title: 워크플로 디자이너-Flowchart 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Flowchart.UI
- System.Activities.Statements.FlowStep.UI
- System.Activities.Core.Presentation.FlowStart.UI
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d786e9acfa99d2b106b72822a0106e2161724790
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75597037"
---
# <a name="flowchart-activity-designer"></a>순서도 활동 디자이너

<xref:System.Activities.Statements.Flowchart> 활동은 복잡한 흐름 제어를 정의하고 관리하는 워크플로를 만드는 데 사용됩니다. 는 <xref:System.Activities.Statements.Flowchart> 코드에서 또는 워크플로 디자이너를 사용 하 여 작성할 수 있습니다. 이 항목에서는 워크플로 디자이너 환경에 대해 설명 합니다. 개발자는 워크플로 디자이너 워크플로 활동 디자이너를 사용 하 여 워크플로를 자연스럽 게 작성할 수 있습니다.

## <a name="the-flowchart-activity"></a>Flowchart 활동

<xref:System.Activities.Statements.Flowchart>는 워크플로를 시작할 때 실행되는 고유한 <xref:System.Activities.Statements.Flowchart.StartNode%2A>이며, 연결된 <xref:System.Activities.Statements.Flowchart.Nodes%2A> 네트워크를 사용하여 임의의 루프를 만들거나 정해진 시간에 실행 흐름을 워크플로의 다른 곳으로 전환합니다.

### <a name="using-the-flowchart-activity-designer"></a>Flowchart 활동 디자이너 사용

**Flowchart** 활동 디자이너는 **도구**상자의 **순서도** 범주에 있습니다 .이 범주에 액세스 하려면 워크플로 디자이너의 **도구 상자** 탭을 클릭 합니다. 또는 **보기** 메뉴에서 **도구 상자** 를 선택 하거나 **ctrl** + **Alt** + **X**를 누릅니다.

**Flowchart** 활동 디자이너를 **도구 상자** 에서 끌어 활동 디자이너가 일반적으로 루트 활동 또는 다른 제어 흐름 활동의 자식으로 배치 되는 워크플로 디자이너 화면에 놓을 수 있습니다. **Flowchart** 활동 디자이너를 빈 워크플로 디자이너 표면에 놓으면 활동을 만듭니다 .이 활동은 <xref:System.Activities.Statements.Flowchart> 기본적으로 실행을 시작 하는 시작 노드가 녹색 공을 나타내는 확장 된 뷰에 표시 됩니다. **Flowchart** 활동 디자이너를 다른 제어 흐름 활동으로 끌어 놓는 경우 해당 활동 디자이너는 **flowchart** 활동 디자이너를 두 번 클릭 하 여 확장할 수 있는 최소화 된 뷰로 표시 됩니다. **도구 상자** 의 모든 작업은 다른 제어 흐름 작업을 포함 하 여 **Flowchart** activity designer로 직접 끌어 올 수 있습니다.

다양 한 활동 디자이너를 워크플로 디자이너 캔버스로 끌어온 후 <xref:System.Activities.Activity> 에 표시 되는 개체를 함께 연결 하 여 실행 순서를 지정할 수 있습니다. 소스 활동과 대상 활동 사이에 연결을 만들려면 소스 활동 디자이너 위로 마우스를 가져갑니다. 그러면 정사각형 핸들이 양쪽에 나타납니다. 정사각형 핸들 중 하나를 클릭한 후 마우스 단추를 누른 상태에서 핸들 중 하나로 끌어 놓습니다. 대상 활동 위로 마우스를 가져가면 대상 활동 주변에도 이 핸들이 비슷한 방식으로 나타납니다. 마우스 단추를 놓으면 두 활동 간 연결이 만들어지고 소스 디자이너에서 대상 디자이너를 향하는 화살표로 표시됩니다.

### <a name="flowchart-activity-properties"></a>Flowchart 활동 속성

다음 표에서는 <xref:System.Activities.Statements.Flowchart> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표 또는 디자이너 화면에서 편집할 수 있습니다.

|속성 이름|필수|사용량|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|머리글에 활동 디자이너의 표시 이름을 지정합니다. 기본값은 Flowchart입니다. 값은 **속성** 창에서 편집 하거나 activity designer 헤더에서 직접 편집할 수 있습니다.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|False|자식 활동 간에 상태를 공유하기 위해 이 <xref:System.Activities.Statements.Flowchart> 내로 범위가 지정된 변수 컬렉션입니다.|
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|False|<xref:System.Activities.Statements.FlowNode>를 시작할 때 실행되는 <xref:System.Activities.Statements.Flowchart>입니다.|
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|False|<xref:System.Activities.Statements.FlowNode>에 있는 <xref:System.Activities.Statements.Flowchart> 개체 컬렉션을 포함합니다.|

## <a name="see-also"></a>추가 정보

- [순서도](../workflow-designer/flowchart-activity-designers.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)
