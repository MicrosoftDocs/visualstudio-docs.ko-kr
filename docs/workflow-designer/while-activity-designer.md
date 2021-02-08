---
title: 워크플로 디자이너-While 활동 디자이너
description: While 작업이 본문에 포함 된 활동을 실행 하는 방법 및 지정 된 조건이 true로 평가 되는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9447d32f17283e7123e2f99490acc49c1613360d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837998"
---
# <a name="while-activity-designer"></a>While 활동 디자이너

<xref:System.Activities.Statements.While>활동은에 포함 된 활동을 실행 <xref:System.Activities.Statements.While.Body%2A> 하는 반면 지정 된는 <xref:System.Activities.Statements.While.Condition%2A> **true** 로 평가 됩니다. 포함된 활동이 실행되지 않을 수도 있습니다. 포함된 활동이 적어도 한 번은 실행되도록 하려면 그 대신 <xref:System.Activities.Statements.DoWhile> 활동을 사용하세요.

## <a name="while-properties-in-workflow-designer"></a>Workflow Designer의 While 속성

다음 표에서는 가장 유용한 <xref:System.Activities.Statements.While> 활동 속성을 보여 주고 디자이너에서 이러한 속성을 사용하는 방법을 설명합니다.

|속성 이름|필수|사용량|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|머리글에 <xref:System.Activities.Statements.While> 활동 디자이너의 이름을 지정합니다. 기본값은 While입니다. 값은 **속성** 창에서 편집 하거나 activity designer 헤더에서 직접 편집할 수 있습니다.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.While.Body%2A>|False|이 true로 평가 되는 동안 실행할 활동을 포함 <xref:System.Activities.Statements.While.Condition%2A> 합니다. |
|<xref:System.Activities.Statements.While.Condition%2A>|True|의 작업을 실행할지 여부를 결정 하기 위해 평가 되는 Visual Basic 식을 포함 합니다 <xref:System.Activities.Statements.While.Body%2A> .|

## <a name="see-also"></a>참고 항목

- [제어 흐름](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)
