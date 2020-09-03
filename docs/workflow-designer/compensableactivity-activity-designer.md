---
title: 워크플로 디자이너 CompensableActivity 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ec70c22ae195dc6dd58aa2cfa893cee35fe6ca8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75597102"
---
# <a name="compensableactivity-activity-designer"></a>CompensableActivity 활동 디자이너

**CompensableActivity** 활동 디자이너는 활동을 만들고 구성 하는 데 사용 됩니다 <xref:System.Activities.Statements.CompensableActivity> .

## <a name="the-compensableactivity-activity"></a>CompensableActivity 활동
 <xref:System.Activities.Statements.CompensableActivity>는 성공적으로 완료한 후 확인 또는 보정할 수 있는 작업 단위를 정의합니다.

### <a name="using-the-compensableactivity-activity-designer"></a>CompensableActivity 활동 디자이너 사용
 **CompensableActivity** 활동 디자이너는 **도구 상자**의 **트랜잭션** 범주에 있습니다. **도구 상자**를 열려면 워크플로 디자이너 왼쪽에 있는 **도구 상자** 탭을 선택 합니다. 또는 **보기** 메뉴에서 **도구 상자** 를 선택 하거나 **ctrl** + **Alt** + **X**를 누릅니다.

 **CompensableActivity** 활동 디자이너를 **도구 상자** 에서 끌어서 워크플로 디자이너 화면에 놓을 수 있습니다. 내에서 activity designer를 삭제할 수 있습니다 <xref:System.Activities.Statements.Sequence> . 활동 디자이너를 삭제 하면 <xref:System.Activities.Statements.CompensableActivity> CompensableActivity의 기본이 포함 된 활동이 만들어집니다 <xref:System.Activities.Activity.DisplayName%2A> . <xref:System.Activities.Activity.DisplayName%2A> **CompensableActivity** activity 디자이너의 헤더에서 값을 편집 합니다. 또한 속성 표의 **DisplayName** 상자에서 편집할 수 있습니다.

### <a name="the-compensableactivity-properties"></a>CompensableActivity 속성
 다음 표에서는 <xref:System.Activities.Statements.CompensableActivity> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. <xref:System.Activities.Activity.DisplayName%2A>및 <xref:System.Activities.Activity%601.Result%2A> 속성은 속성 표에서 편집할 수 있지만 다른 속성은 워크플로 디자이너 화면에서 편집 해야 합니다.

|속성 이름|필수|사용량|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CompensableActivity> 활동의 선택적 이름입니다. 기본값은 CompensableActivity입니다.|
|<xref:System.Activities.Activity%601.Result%2A>|False|<xref:System.Activities.Statements.CompensableActivity>의 반환 값을 지정합니다. 이 속성은 속성 표에서 편집해야 합니다.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|보정, 취소 및 확인 논리를 제공할 활동을 지정합니다. 활동을 추가 하려면 <xref:System.Activities.Statements.CompensableActivity.Body%2A> **도구 상자** 의 활동을 **CompensableActivity** 활동 디자이너의 **본문** 상자로 끌어 놓습니다. "여기에 작업 놓기" 힌트 텍스트를 추가 합니다.|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|취소가 있을 때 실행 되는 작업을 지정 합니다. 활동을 추가 하려면 **도구 상자** 에서 **CompensableActivity** 활동 디자이너의 **CancellationHandler** 상자에 디자이너를 놓습니다. "여기에 작업 놓기" 힌트 텍스트를 추가 합니다.|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|<xref:System.Activities.Statements.CompensableActivity.Body%2A> 활동을 보정할 때 실행할 활동을 지정합니다. <xref:System.Activities.Statements.Compensate> 활동을 사용하여 이 처리기를 명시적으로 호출할 수 있습니다.<br /><br /> 활동을 추가 하려면 **도구 상자** 에서 활동 디자이너를 **CompensableActivity** 활동 디자이너의 **CompensationHandler** 상자로 끌어 놓습니다. "여기에 작업 놓기" 힌트 텍스트를 추가 합니다.|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|<xref:System.Activities.Statements.CompensableActivity.Body%2A> 활동을 확인할 때 실행할 활동을 지정합니다. <xref:System.Activities.Statements.Confirm> 활동을 사용하여 이 처리기를 명시적으로 호출할 수 있습니다.<br /><br /> 활동을 추가 하려면 **도구 상자** 에서 활동 디자이너를 **CompensableActivity** 활동 디자이너의 **ConfirmationHandler** 상자로 끌어 놓습니다. "여기에 작업 놓기" 힌트 텍스트를 추가 합니다.|

## <a name="see-also"></a>추가 정보

- [트랜잭션](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [보정할](../workflow-designer/compensate-activity-designer.md)
- [확인](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
