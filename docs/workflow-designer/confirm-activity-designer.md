---
title: 워크플로 디자이너-Confirm 활동 디자이너
description: Confirm 활동 디자이너와이 디자이너를 사용 하 여 확인 활동을 만들고 구성 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0227a300160434d0052e81d7c1ccd107c5a11a01
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955660"
---
# <a name="confirm-activity-designer"></a>Confirm 활동 디자이너

**Confirm** 활동 디자이너는 활동을 만들고 구성 하는 데 사용 됩니다 <xref:System.Activities.Statements.Confirm> .

## <a name="the-confirm-activity"></a>Confirm 활동
 <xref:System.Activities.Statements.Confirm> 활동은 <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>에 포함된 활동에 대해 <xref:System.Activities.Statements.CompensableActivity>를 명시적으로 호출합니다. <xref:System.Activities.Statements.Confirm>, <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 또는 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>의 <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>에서 <xref:System.Activities.Statements.CompensableActivity> 활동을 사용하지 않는 경우 <xref:System.Activities.Statements.Confirm.Target%2A> 속성을 지정해야 합니다.

 <xref:System.Activities.Statements.CompensationToken>에 의해 지정된 <xref:System.Activities.Statements.Compensate.Target%2A>은 <xref:System.Activities.Statements.CompensableActivity>의 <xref:System.Activities.Statements.CompensableActivity.Body%2A>가 성공적으로 완료된 후 <xref:System.Activities.Statements.CompensableActivity>를 명시적으로 확인하거나 보정하는 수단을 제공합니다.

### <a name="using-the-confirm-activity-designer"></a>Confirm 활동 디자이너 사용
 **Confirm** 활동 디자이너는 **도구 상자** 의 **트랜잭션** 범주에 있습니다 .이 범주에 액세스 하려면 워크플로 디자이너 왼쪽에 있는 **도구 상자** 탭을 클릭 합니다. 또는 **보기** 메뉴에서 **도구 상자** 를 선택 하거나 **ctrl** + **Alt** + **X** 를 누릅니다.

 **Confirm** 활동 디자이너를 **도구 상자** 에서 끌어다가 등 일반적으로 활동을 배치 하는 아무 곳에 나 워크플로 디자이너 화면에 놓을 수 있습니다 <xref:System.Activities.Statements.Sequence> . 그러면 기본 <xref:System.Activities.Statements.Confirm>인 Confirm이라는 이름의 <xref:System.Activities.Activity.DisplayName%2A> 활동이 만들어집니다. <xref:System.Activities.Activity.DisplayName%2A> **확인** 활동 디자이너의 머리글 또는 속성 표의 **DisplayName** 상자에서 값을 편집할 수 있습니다.

### <a name="the-confirm-properties"></a>Confirm 속성
 다음 표에서는 <xref:System.Activities.Statements.Confirm> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 속성은 속성 <xref:System.Activities.Activity.DisplayName%2A> 표 또는 워크플로 디자이너 화면에서 편집할 수 있지만 속성은 속성 <xref:System.Activities.Statements.Confirm.Target%2A> 표에서 편집 해야 합니다.

|속성 이름|필수|사용량|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CancellationScope> 활동의 선택적 이름을 지정합니다. 기본값은 Confirm입니다.|
|<xref:System.Activities.Statements.Confirm.Target%2A>|True|이 <xref:System.Activities.InArgument%601> 활동의 <xref:System.Activities.Statements.CompensationToken>이 들어 있는 <xref:System.Activities.Statements.Confirm>을 지정합니다.|

## <a name="see-also"></a>참고 항목

- [트랜잭션](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [보정할](../workflow-designer/compensate-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)