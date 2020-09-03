---
title: Pick 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: daefc48cfff2c5c73d9ecf14316777becf4d83c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672591"
---
# <a name="pick-activity-designer"></a>Pick 활동 디자이너
<xref:System.Activities.Statements.Pick> 활동은 이벤트 기반의 제어 흐름을 제공합니다. 이 활동은 트리거를 시작하는 이벤트에 대해 몇 가지 분기 중 하나를 실행합니다.

## <a name="the-pick-activity"></a>Pick 활동
 <xref:System.Activities.Statements.Pick> 활동에는 <xref:System.Activities.Statements.PickBranch> 개체 컬렉션이 포함되어 있는데, <xref:System.Activities.Statements.Pick> 활동은 트리거 역할을 하는 들어오는 이벤트로 이러한 개체 중 하나를 실행할 수 있습니다. 이러한 방식으로 [!INCLUDE[wfd1](../includes/wfd1-md.md)]는 이벤트 기반 제어 흐름 모델링을 제공합니다. 각 <xref:System.Activities.Statements.PickBranch>에는 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 및 <xref:System.Activities.Statements.PickBranch.Action%2A>이 포함되어 있습니다. <xref:System.Activities.Statements.Pick> 활동을 실행하기 시작할 때 <xref:System.Activities.Statements.PickBranch> 요소의 트리거 활동이 모두 예약됩니다. 첫 번째 활동이 완료되면 해당 동작 작업이 예약되고 다른 트리거 활동은 모두 취소됩니다.

### <a name="how-to-use-the-pick-activity-designer"></a>Pick 활동 디자이너를 사용하는 방법
 **Pick** 활동 디자이너는 **도구 상자**의 **제어 흐름** 범주에 있습니다 .이 범주에 액세스 하려면의 **도구 상자** 탭을 클릭 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 하거나, **보기** 메뉴에서 **도구 모음** 을 선택 하거나, CTRL + ALT + X를 선택 합니다.

 **도구 상자** 에서 **Pick** 활동 디자이너를 끌어 활동 디자이너가 일반적으로 배치 되는 아무 곳에 나 놓을 수 있습니다. 예를 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 들어 **시퀀스** 활동 디자이너의 내부에 있습니다. [!INCLUDE[wfd2](../includes/wfd2-md.md)]에 끌어 놓으면 <xref:System.Activities.Statements.Pick> 활동이 만들어집니다. 이 활동에는 기본적으로 빈 <xref:System.Activities.Statements.PickBranch> 활동 두 개가 요소(표시 이름 Branch1 및 Bracnh2)로 포함되어 있습니다. 이러한 각 <xref:System.Activities.Statements.PickBranch.DisplayName%2A> 속성 값은 **PickBranch** activity designer 헤더 또는 각 분기의 **속성** 창에서 편집할 수 있습니다.

 개체의 컬렉션에 활동을 추가 하는 방법에는 <xref:System.Activities.Statements.PickBranch> <xref:System.Activities.Statements.Pick> **도구 상자** 에서 **PickBranch** 디자이너를 끌어서 놓거나 **뚝딱** 디자인 화면에서 상황에 맞는 메뉴를 사용 하는 두 가지 방법이 있습니다. 자세한 내용은 [PickBranch](../workflow-designer/pickbranch-activity-designer.md) 항목을 참조 하세요. **Pick** 활동 디자이너 내부에 배치할 수 있는 유일한 항목은 **PickBranch** activity designer입니다.

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Workflow Designer의 Pick 활동 속성
 다음 표에서는 <xref:System.Activities.Statements.Pick> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표 또는 디자이너 화면에서 편집할 수 있습니다.

|속성 이름|필수|사용량|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|머리글에 <xref:System.Activities.Statements.Pick> 활동 디자이너의 이름을 지정합니다. 기본값은 Pick입니다. 속성 표에서 또는 활동 디자이너의 머리글에서 직접 값을 편집할 수 있습니다.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|

## <a name="see-also"></a>관련 항목
 [Pick 활동을 사용 하 여](https://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6) [제어 흐름](../workflow-designer/control-flow-activity-designers.md) [선택 활동](https://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e)