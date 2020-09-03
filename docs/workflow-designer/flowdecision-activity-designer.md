---
title: 워크플로 디자이너 FlowDecision 결정 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79e405f82bcf33bc01ad07f1092879c17dec5849
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "76111442"
---
# <a name="flowdecision-activity-designer"></a>FlowDecision 활동 디자이너

<xref:System.Activities.Statements.FlowDecision> 노드는 지정된 조건이 충족되었는지 여부에 따라 제어 흐름을 두 가지 대안 중 하나로 보내는 분기를 제공하는 조건 노드입니다. 흐름에 두 개 이상의 분기가 필요하면 <xref:System.Activities.Statements.FlowSwitch%601>을 대신 사용합니다.

## <a name="the-flowdecision-node"></a>FlowDecision 노드

흐름이 두 경로로 분기될 수 있는 경우 <xref:System.Activities.Statements.FlowDecision>을 사용합니다. <xref:System.Activities.Statements.FlowDecision> 노드에는 <xref:System.Activities.Statements.FlowDecision.Condition%2A> 또는 <xref:System.Activities.Statements.FlowNode>의 두 가지 결과와 각각 연결된 <xref:System.Activities.Statements.FlowDecision.True%2A>와 <xref:System.Activities.Statements.FlowDecision.False%2A>이 있습니다. <xref:System.Activities.Statements.FlowDecision.Condition%2A>을 평가하고 이 평가의 값으로 <xref:System.Activities.Statements.FlowNode>에서 처리할 다음 번 <xref:System.Activities.Statements.Flowchart>를 결정합니다.

### <a name="using-the-flowdecision-designer"></a>FlowDecision 디자이너 사용

**Flowdecision 결정** 디자이너는 **도구**상자의 **순서도** 범주에 있습니다 .이 범주에 액세스 하려면 워크플로 디자이너의 **도구 상자** 탭을 클릭 합니다. 또는 **보기** 메뉴에서 **도구 상자** 를 선택 하거나 **ctrl** + **Alt** + **X**를 누릅니다.

**Flowdecision 결정** 디자이너를 **도구 상자** 에서 끌어다 **순서도** 활동 디자이너 내의 워크플로 디자이너 화면에 놓을 수 있습니다. 그러면 <xref:System.Activities.Statements.FlowDecision> 활동 내에서 레이블이 지정 된 **의사 결정** 을 만듭니다 <xref:System.Activities.Statements.Flowchart> . 디자이너 위에 마우스를 놓고 두 분기에 대 한 **True** 및 **False** 제곱 핸들을 표시 합니다.

**Flowdecision 결정** 디자이너와 기타 디자이너를 **순서도**로 끌어 온 후에는 노드를 함께 연결 하 여 실행 순서를 지정할 수 있습니다. 원본 노드 ( **Flowdecision 결정**의 **True** 및 **False** 분기 포함)와 대상 노드의 링크를 만들려면 소스 노드의 디자이너 위에 마우스를 놓고 사각형 핸들이 양쪽에 나타납니다. 정사각형 핸들 중 하나를 클릭한 후 마우스 단추를 누른 상태에서 핸들 중 하나로 끕니다. 대상 노드 위로 마우스를 가져가면 대상 노드 주변에도 이 핸들이 비슷한 방식으로 나타납니다. 마우스 단추를 놓으면 두 노드 간 연결이 만들어지고 소스 디자이너에서 대상 디자이너를 향하는 화살표로 표시됩니다.

<xref:System.Activities.Statements.FlowDecision.Condition%2A>"VB 식 입력" 이라는 힌트 텍스트가 표시 되는 위치를 클릭 하 여 **속성** 창의 **조건** 상자에를 나타내는 식을 입력할 수 있습니다.

### <a name="the-flowdecision-properties"></a>FlowDecision 속성

다음 표에서는 <xref:System.Activities.Statements.FlowDecision> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표 또는 디자이너 화면에서 편집할 수 있습니다.

|속성 이름|필수|사용량|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|True|흐름 제어의 경로를 결정하는 조건입니다.|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|<xref:System.Activities.Statements.FlowDecision.Condition%2A>이 충족되는 경우의 흐름 제어 경로입니다.|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|<xref:System.Activities.Statements.FlowDecision.Condition%2A>이 충족되지 않는 경우의 흐름 제어 경로입니다.|

## <a name="see-also"></a>추가 정보

- [순서도](../workflow-designer/flowchart-activity-designers.md)
- [순서도](../workflow-designer/flowchart-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)
