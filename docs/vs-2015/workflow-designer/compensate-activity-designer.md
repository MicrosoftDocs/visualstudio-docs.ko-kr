---
title: 보정 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 706cd446e931d6a3a065a3e8abfb58b5a90e9152
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656984"
---
# <a name="compensate-activity-designer"></a>Compensate 활동 디자이너
**보정** 활동 디자이너는 활동을 만들고 구성 하는 데 사용 됩니다 <xref:System.Activities.Statements.Compensate> .

## <a name="the-compensate-activity"></a>Compensate 활동
 <xref:System.Activities.Statements.Compensate> 활동은 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>에 포함된 활동에 대해 <xref:System.Activities.Statements.CompensableActivity>를 명시적으로 호출합니다. <xref:System.Activities.Statements.Compensate>, <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 또는 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>의 <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>에서 <xref:System.Activities.Statements.CompensableActivity> 활동을 사용하지 않는 경우 <xref:System.Activities.Statements.Compensate.Target%2A> 속성을 지정해야 합니다.

 <xref:System.Activities.Statements.CompensationToken>에 의해 지정된 <xref:System.Activities.Statements.Compensate.Target%2A>은 <xref:System.Activities.Statements.CompensableActivity>의 <xref:System.Activities.Statements.CompensableActivity.Body%2A>가 성공적으로 완료된 후 <xref:System.Activities.Statements.CompensableActivity>를 명시적으로 확인하거나 보정하는 수단을 제공합니다.

### <a name="using-the-compensate-activity-designer"></a>Compensate 활동 디자이너 사용
 **보정** 활동 디자이너는 **도구 상자**의 **트랜잭션** 범주에 있습니다 .이 범주에 액세스 하려면의 왼쪽에 있는 **도구 상자** 탭을 클릭 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 하거나, **보기** 메뉴에서 **도구 모음** 을 선택 하거나, CTRL + ALT + X를 선택 합니다.

 **보정** 활동 디자이너를 **도구 상자** 에서 끌어다가 등 일반적으로 활동을 배치 하는 아무 곳에 나 놓을 수 있습니다 [!INCLUDE[wfd2](../includes/wfd2-md.md)] <xref:System.Activities.Statements.Sequence> . 그러면 기본 <xref:System.Activities.Statements.Compensate>인 Compensate라는 이름의 <xref:System.Activities.Activity.DisplayName%2A> 활동이 만들어집니다. <xref:System.Activities.Activity.DisplayName%2A> **보정** 활동 디자이너의 머리글 또는 속성 표의 **DisplayName** 상자에서 값을 편집할 수 있습니다.

### <a name="the-compensate-properties"></a>보정 속성
 다음 표에서는 <xref:System.Activities.Statements.CancellationScope> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. <xref:System.Activities.Activity.DisplayName%2A> 속성은 속성 표 또는 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면에서 편집할 수 있지만 <xref:System.Activities.Statements.Compensate.Target%2A> 속성은 반드시 속성 표에서 편집해야 합니다.

|속성 이름|필수|사용량|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Compensate> 활동의 선택적 이름을 지정합니다. 기본값은 Compensate입니다.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|이 <xref:System.Activities.InArgument%601> 활동의 <xref:System.Activities.Statements.CompensationToken>이 들어 있는 <xref:System.Activities.Statements.Compensate>을 지정합니다.|

## <a name="see-also"></a>관련 항목
 [Transaction](../workflow-designer/transaction-activity-designers.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [보정 활동 디자이너](../workflow-designer/compensate-activity-designer.md) [확인](../workflow-designer/confirm-activity-designer.md) [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)