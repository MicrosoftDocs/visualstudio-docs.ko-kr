---
title: 워크플로 디자이너 TerminateWorkflow 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 078dfb43b5960580327448627a30eec20297d9f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "76111770"
---
# <a name="terminateworkflow-activity-designer"></a>TerminateWorkflow 활동 디자이너

**TerminateWorkflow** 활동 디자이너는 활동을 만들고 구성 하는 데 사용 됩니다 <xref:System.Activities.Statements.TerminateWorkflow> .

## <a name="the-terminateworkflow-activity"></a>TerminateWorkflow 활동

<xref:System.Activities.Statements.TerminateWorkflow> 활동은 워크플로의 실행을 종료합니다.

### <a name="using-the-terminateworkflow-activity-designer"></a>TerminateWorkflow 활동 디자이너 사용

**TerminateWorkflow** 활동 디자이너 **는 도구 상자**의 **런타임** 범주에 있습니다 .이 범주에 액세스 하려면 **도구 상자** 탭을 클릭 하거나, **보기** 메뉴에서 **도구 상자** 를 선택 하거나, CTRL + ALT + X를 선택 합니다.

**TerminateWorkflow** 활동 디자이너를 **도구 상자** 에서 끌어다가 등 일반적으로 활동을 배치 하는 워크플로 디자이너 화면에 놓을 수 있습니다 <xref:System.Activities.Statements.Sequence> . 그러면 <xref:System.Activities.Statements.TerminateWorkflow> 기본 **DisplayName** 이 TerminateWorkflow 인 활동이 만들어집니다. <xref:System.Activities.Activity.DisplayName%2A> **TerminateWorkflow** 활동 디자이너의 머리글 또는 속성 표의 **DisplayName** 상자에서을 편집할 수 있습니다.

### <a name="the-terminateworkflow-properties"></a>TerminateWorkflow 속성

다음 표에서는 <xref:System.Activities.Statements.TerminateWorkflow> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표에서 편집할 수 있으며 일부 속성은 워크플로 디자이너 화면에서 편집할 수 있습니다.

|속성 이름|필수|사용량|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.TerminateWorkflow> 활동의 이름입니다. 기본값은 TerminateWorkflow입니다. 표시 이름이 꼭 필요하지 않더라도 표시 이름을 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|워크플로가 종료될 때 throw할 예외입니다. 이 속성은 속성 표에서 설정합니다.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|워크플로가 왜 종료되었는지 설명하는 이유입니다. 이 속성은 속성 표에서 설정합니다.|

## <a name="see-also"></a>추가 정보

- [런타임](../workflow-designer/runtime-activity-designers.md)
- [유지할](../workflow-designer/persist-activity-designer.md)
