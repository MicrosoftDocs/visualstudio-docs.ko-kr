---
title: 워크플로 디자이너 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 099be38c5585fe19c00b31c00ac3a7ddcd3d7fe2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "76111466"
---
# <a name="if-activity-designer"></a>If 활동 디자이너

<xref:System.Activities.Statements.If> 활동은 조건을 평가하고 그 결과에 따라 활동을 실행합니다. 이 활동은 절차적 모델링 스타일의 프로그래밍을 사용하는 경우에 가장 유용합니다. 예를 들어 <xref:System.Activities.Statements.If> 활동 또는 <xref:System.Activities.Statements.Sequence> 활동 안에 <xref:System.Activities.Statements.Parallel> 활동이 중첩될 수 있습니다. <xref:System.Activities.Statements.Flowchart> 활동을 사용 중인 경우 <xref:System.Activities.Statements.FlowDecision> 활동을 대신 사용해 보세요.

## <a name="if-properties-in-the-workflow-designer"></a>워크플로 디자이너의 If 속성

다음 표에서는 가장 유용한 <xref:System.Activities.Statements.If> 활동 속성을 보여 주고 디자이너에서 이러한 속성을 사용하는 방법을 설명합니다.

|속성 이름|필수|사용량|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|True|실행할 자식 활동을 결정하는 조건입니다. 을 설정 하려면 <xref:System.Activities.Statements.If.Condition%2A> **If** 활동 디자이너의 **조건** 상자 또는 속성 표에 Visual Basic 식을 입력 합니다.|
|<xref:System.Activities.Statements.If.Else%2A>|False|이 false 인 경우 실행할 작업 <xref:System.Activities.Statements.If.Condition%2A> 입니다 **false**. 분기에 의해 실행 되는 활동을 추가 하려면 <xref:System.Activities.Statements.If.Else%2A> **도구 상자** 의 활동을 "여기에 작업 놓기" 힌트 텍스트가 있는 **If** 활동 디자이너의 **Else** 상자로 끌어 놓습니다.|
|<xref:System.Activities.Statements.If.Then%2A>|False|이 true 인 경우 실행할 작업 <xref:System.Activities.Statements.If.Condition%2A> 입니다 **true**. 분기에 의해 실행 되는 활동을 추가 하려면 <xref:System.Activities.Statements.If.Then%2A> **도구 상자** 의 활동을 "여기에 작업 놓기" 힌트 텍스트가 있는 **If** 활동 디자이너의 **Then** 상자로 끌어 놓습니다.|

## <a name="see-also"></a>추가 정보

- [시퀀스](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [제어 흐름](../workflow-designer/control-flow-activity-designers.md)
