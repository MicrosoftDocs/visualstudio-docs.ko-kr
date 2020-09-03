---
title: FlowSwitch &lt; T &gt; 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 27abb660766a7c04742eca221432af19f05f0d28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656639"
---
# <a name="flowswitchlttgt-activity-designer"></a>FlowSwitch &lt; T &gt; 활동 디자이너
<xref:System.Activities.Statements.FlowSwitch%601> 활동은 두 개 이상의 대안 분기가 필요할 때 일치 기준에 따라 제어 흐름에 대한 분기를 제공하는 조건 노드입니다. 흐름 분기에 두 경로만 필요한 경우 <xref:System.Activities.Statements.FlowDecision> 활동을 대신 사용합니다.

## <a name="the-flowswitcht-activity"></a>FlowSwitch \<T> 활동
 활동에는 <xref:System.Activities.Statements.FlowSwitch%601> <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 평가할 때 제네릭 매개 변수로 지정 된 *T* 형식의 값을 반환 하는가 포함 되어 있습니다. 또한 이 활동에는 가능한 계산 결과와 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> 개체 집합 간의 고유 매핑을 지정하는 <xref:System.Activities.Statements.FlowNode> 집합도 포함되어 있습니다. 실행 된는 <xref:System.Activities.Statements.FlowNode> *T* 형식의 개체가 계산 된의 값과 일치 하는 항목입니다 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> . 일치하는 항목이 없는 case에 대해 선택적으로 <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> case를 제공할 수 있습니다.

### <a name="using-the-flowswitcht-activity-designer"></a>FlowSwitch \<T> 활동 디자이너 사용
 **FlowSwitch \<T> ** 활동 디자이너는 **도구 상자**의 **순서도** 범주에 있습니다 .이 범주에 액세스 하려면의 왼쪽에 있는 **도구 상자** 탭을 클릭 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 하거나, **보기** 메뉴에서 **도구 모음** 을 선택 하거나, CTRL + ALT + X를 선택 합니다.

 ** \<T> FlowSwitch** 활동 디자이너를 **도구 상자** 에서 끌어다 [!INCLUDE[wfd2](../includes/wfd2-md.md)] **순서도** 활동 디자이너 내의 화면에 놓을 수 있습니다. 를 평가 하 여 얻은 형식 (제네릭 매개 변수를 사용 하 여 코드에 연결 됨)을 지정 하려면 표시 되는 **형식 선택** 창을 사용 합니다 <xref:System.Activities.Statements.FlowSwitch%601> <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> . 이 프로시저는 <xref:System.Activities.Statements.FlowSwitch%601> 활동 내에서 **Switch** 라는 활동을 만듭니다 <xref:System.Activities.Statements.Flowchart> . <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>"VB 식 입력" 이라는 힌트 텍스트가 표시 되는 위치를 클릭 하 여 **속성** 창의 **식** 상자에를 입력할 수 있습니다.

 **FlowSwitch \<T> ** 활동 디자이너 위로 마우스를 가져가면 연결 하는 데 사용 되는 사각형 핸들이 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> 가장자리 주위에 표시 됩니다. **FlowSwitch<T \> ** 활동 디자이너와 기타 활동 디자이너를 **순서도**로 끌어 오면 표시 되는 <xref:System.Activities.Activity> 개체를 함께 연결 하 여 실행 순서를 지정할 수 있습니다. 와 연결 된 중 하나를 만들려면 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> <xref:System.Activities.Statements.FlowSwitch%601> **FlowSwitch \<T> ** 경계에 있는 square case 핸들 중 하나를 클릭 하 고 마우스 단추를 누른 상태에서 마우스 단추를 누른 상태에서 해당 디자이너 위로 마우스를 가져가면 대상 활동 주변에 비슷한 방식으로 나타나는 핸들 중 하나로 끕니다 마우스 단추를 놓으면 **FlowSwitch \<T> ** 에서 대상 디자이너에 대 한 화살표가 표시 되어이 경우를 나타냅니다. 이 경우의 기본값은 화살표에 표시 되며 **속성** 창의 **case** 상자에서 편집할 수 있습니다.

### <a name="the-flowswitcht-properties"></a>FlowSwitch \<T> 속성
 다음 표에서는 <xref:System.Activities.Statements.FlowSwitch%601> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표 또는 디자이너 화면에서 편집할 수 있습니다.

|속성 이름|필수|사용량|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|실행 경로에서 전환할 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>를 결정하기 위해 계산할 식을 지정합니다.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 계산으로 얻은 가능한 결과와 <xref:System.Activities.Statements.FlowNode> 개체 집합 간의 고유 매핑을 지정합니다.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 계산이 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> 개체에 포함된 값 중 하나와 일치하지 않을 경우의 매핑을 지정합니다.|

## <a name="see-also"></a>관련 항목
 [순서도](../workflow-designer/flowchart-activity-designers.md) [흐름도](../workflow-designer/flowchart-activity-designer.md) [flowdecision 결정](../workflow-designer/flowdecision-activity-designer.md)