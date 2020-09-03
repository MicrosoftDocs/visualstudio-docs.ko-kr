---
title: While 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fae1b4905d66a5162591fd7c720ba81ed7ffda82
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72606615"
---
# <a name="while-activity-designer"></a>While 활동 디자이너

<xref:System.Activities.Statements.While>활동은에 포함 된 활동을 실행 <xref:System.Activities.Statements.While.Body%2A> 하는 반면 지정 된 조건은 **true**로 평가 됩니다. 포함된 활동이 실행되지 않을 수도 있습니다. 포함된 활동이 적어도 한 번은 실행되도록 하려면 그 대신 <xref:System.Activities.Statements.DoWhile> 활동을 사용하세요.

## <a name="while-properties-in-workflow-designer"></a>Workflow Designer의 While 속성

다음 표에서는 가장 유용한 <xref:System.Activities.Statements.While> 활동 속성을 보여 주고 디자이너에서 이러한 속성을 사용하는 방법을 설명합니다.

|속성 이름|필수|사용량|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|머리글에 <xref:System.Activities.Statements.While> 활동 디자이너의 이름을 지정합니다. 기본값은 While입니다. 값은 **속성** 창에서 편집 하거나 activity designer 헤더에서 직접 편집할 수 있습니다.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.While.Body%2A>|False|이 true로 평가 되는 동안 실행할 활동을 포함 <xref:System.Activities.Statements.While.Condition%2A> 합니다. **true**|
|<xref:System.Activities.Statements.While.Condition%2A>|True|[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]의 활동을 실행할지 여부를 결정하기 위해 평가하는 <xref:System.Activities.Statements.While.Body%2A> 식을 포함합니다.|

## <a name="see-also"></a>추가 정보

- [제어 흐름](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)