---
title: 워크플로 디자이너-StateMachine 활동 디자이너
description: 상태 시스템 패러다임을 사용 하 여 상태 및 모델 워크플로 컬렉션을 StateMachine 활동에 포함 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 7fe26f8d0ea127189d115692bd01fa538bf8fb33
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873504"
---
# <a name="statemachine-activity-designer"></a>StateMachine 활동 디자이너

<xref:System.Activities.Statements.StateMachine> 활동에는 익숙한 상태 시스템 패러다임을 사용하여 상태와 모델 워크플로의 컬렉션이 포함되어 있습니다.

## <a name="using-the-statemachine-activity-designer"></a>StateMachine 활동 디자이너 사용

활동을 추가 하려면 <xref:System.Activities.Statements.StateMachine> **도구 상자** 의 **상태 시스템** 섹션에서 **StateMachine** 활동 디자이너를 끌어 워크플로 디자이너 화면에 놓습니다. 이 작업에 자식 상태를 추가 하려면 <xref:System.Activities.Statements.StateMachine> <xref:System.Activities.Statements.State> <xref:System.Activities.Core.Presentation.FinalState> **도구 상자** 에서 또는를 **StateMachine** 에 놓습니다.

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>Workflow Designer의 StateMachine 활동 속성

다음 표에서는 워크플로 디자이너를 사용하여 설정할 수 있는 <xref:System.Activities.Statements.StateMachine> 속성을 보여 주고 디자이너에서 이러한 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표에서 편집할 수 있으며 일부 속성은 디자이너 화면에서 편집할 수 있습니다.

|속성 이름|필수|사용량|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|머리글에 <xref:System.Activities.Statements.StateMachine> 활동 디자이너의 이름을 지정합니다. 기본값은 **StateMachine** 입니다. 속성 표에서 또는 활동 디자이너의 머리글에서 직접 값을 편집할 수 있습니다. <xref:System.Activities.Activity.DisplayName%2A>은 워크플로 디자이너 상단에 표시되는 이동 경로 탐색에 사용됩니다.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|

## <a name="see-also"></a>참고 항목

- [Flowchart](../workflow-designer/flowchart-activity-designer.md)
- [제어 흐름](../workflow-designer/control-flow-activity-designers.md)
