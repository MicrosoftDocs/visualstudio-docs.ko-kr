---
title: Delay 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a47279bc68503ba645fea3ef23a04ce9d5ef4c41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656793"
---
# <a name="delay-activity-designer"></a>Delay 활동 디자이너
**Delay** 활동 디자이너는 활동을 만들고 구성 하는 데 사용 됩니다 <xref:System.Activities.Statements.Delay> .

## <a name="the-delay-activity"></a>Delay 활동
 <xref:System.Activities.Statements.Delay> 활동은 지정된 시간 동안 워크플로 실행을 지연시킵니다.

### <a name="using-the-delay-activity-designer"></a>Delay 활동 디자이너 사용
 **Delay** 활동 디자이너는 **도구 상자**의 **기본 형식** 범주에 있습니다 .이 범주에 액세스 하려면의 **도구 상자** 탭을 클릭 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 하거나, **보기** 메뉴에서 **도구 모음** 을 선택 하거나, CTRL + ALT + X를 선택 합니다.

 **Delay** 활동 디자이너를 **도구 상자** 에서 끌어다가 등 일반적으로 활동을 배치 하는 아무 곳에 나 놓을 수 있습니다 [!INCLUDE[wfd2](../includes/wfd2-md.md)] <xref:System.Activities.Statements.Sequence> . 그러면 기본 <xref:System.Activities.Statements.Delay>인 Delay라는 이름의 <xref:System.Activities.Activity.DisplayName%2A> 활동이 만들어집니다. <xref:System.Activities.Activity.DisplayName%2A> **Delay** 활동 디자이너의 머리글 또는 속성 표의 **DisplayName** 상자에서을 편집할 수 있습니다.

### <a name="the-delay-properties"></a>Delay 속성
 다음 표에서는 <xref:System.Activities.Statements.Delay> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표에서 편집할 수 있으며 일부 속성은 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 디자이너 화면에서 편집할 수 있습니다.

|속성 이름|필수|사용량|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Delay> 활동의 이름입니다. 기본값은 Delay입니다. <xref:System.Activities.Activity.DisplayName%2A> 값은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|워크플로를 지연할 시간입니다. 이 속성은 속성 표에서 설정합니다. 리터럴 <xref:System.TimeSpan>을 00:00:00 형식으로 입력하거나 Visual Basic 식을 입력하여 시간을 지정합니다.|

## <a name="see-also"></a>관련 항목
 [기본 형식](../workflow-designer/primitives-activity-designers.md) [할당](../workflow-designer/assign-activity-designer.md) [지연 활동 디자이너](../workflow-designer/delay-activity-designer.md) [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md) [WriteLine](../workflow-designer/writeline-activity-designer.md)