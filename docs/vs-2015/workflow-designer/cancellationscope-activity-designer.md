---
title: CancellationScope 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa41d63fa4f67037a8e98e72abc3e338ad894f70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659172"
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope 활동 디자이너
**CancellationScope** 활동 디자이너는 활동을 만들고 구성 하는 데 사용 됩니다 <xref:System.Activities.Statements.CancellationScope> .

## <a name="the-cancellationscope-activity"></a>CancellationScope 활동
 <xref:System.Activities.Statements.CancellationScope> 활동을 사용하여 실행할 활동과 해당 활동에 대한 취소 논리를 지정할 수 있습니다.

### <a name="using-the-cancellationscope-activity-designer"></a>CancellationScope 활동 디자이너 사용
 **CancellationScope** 활동 디자이너는 **도구 상자**의 **트랜잭션** 범주에 있습니다 .이 범주에 액세스 하려면의 **도구 상자** 탭을 클릭 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 하거나, **보기** 메뉴에서 **도구 모음** 을 선택 하거나, CTRL + ALT + X를 선택 합니다.

 **CancellationScope** 활동 디자이너를 **도구 상자** 에서 끌어다가 등 일반적으로 활동을 배치 하는 아무 곳에 나 놓을 수 있습니다 [!INCLUDE[wfd2](../includes/wfd2-md.md)] <xref:System.Activities.Statements.Sequence> . 이렇게 하면 기본 <xref:System.Activities.Statements.CancellationScope>인 CancellationScope라는 이름의 <xref:System.Activities.Activity.DisplayName%2A> 활동이 만들어집니다. <xref:System.Activities.Activity.DisplayName%2A> **CancellationScope** 활동 디자이너의 머리글 또는 속성 표의 **DisplayName** 상자에서 값을 편집할 수 있습니다.

### <a name="the-cancellationscope-properties"></a>CancellationScope 속성
 다음 표에서는 <xref:System.Activities.Statements.CancellationScope> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. <xref:System.Activities.Activity.DisplayName%2A> 속성은 속성 표에서 편집할 수 있지만 다른 속성은 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면에서 편집해야 합니다.

|속성 이름|필수|사용량|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CancellationScope> 활동의 선택적 이름입니다. 기본값은 CancellationScope입니다. <xref:System.Activities.Activity.DisplayName%2A> 값은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|취소 논리가 제공되는 활동을 지정합니다. 활동을 추가 하려면 <xref:System.Activities.Statements.CancellationScope.Body%2A> **도구 상자** 의 활동을 "여기에 작업 놓기" 힌트 텍스트가 있는 **CancellationScope** 활동 디자이너의 **본문** 상자로 끌어 놓습니다.|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|취소 시 실행할 활동을 지정합니다. 활동을 추가 하려면 <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> **도구 상자** 의 활동을 "여기에 작업 놓기" 힌트 텍스트가 있는 **CancellationScope** 활동 디자이너의 **CancellationHandler** 상자로 끌어 놓습니다.|

## <a name="see-also"></a>관련 항목
 [트랜잭션](../workflow-designer/transaction-activity-designers.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [보정](../workflow-designer/compensate-activity-designer.md) [확인](../workflow-designer/confirm-activity-designer.md) [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)