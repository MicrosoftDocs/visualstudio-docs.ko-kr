---
title: Sequence 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3acf02ab478eee244557e04f19f78ba2d5f0b950
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663255"
---
# <a name="sequence-activity-designer"></a>Sequence 활동 디자이너
<xref:System.Activities.Statements.Sequence> 활동에는 순서대로 실행되는 정렬된 자식 활동 컬렉션이 들어 있습니다.

 활동 집합을 순서대로 실행하는 또 다른 방법은 <xref:System.Activities.Statements.Flowchart> 활동을 사용하는 것입니다. Diagrammatically 모델링 하려는 간단한 분기 또는 반복 프로그램 흐름이 있는 경우 [순서도](../workflow-designer/flowchart-activity-designer.md) 를 사용 하는 것이 좋습니다.

## <a name="using-the-sequence-activity-designer"></a>Sequence 활동 디자이너 사용
 활동을 추가 하려면 <xref:System.Activities.Statements.Sequence> **도구 상자** 에서 **시퀀스** 활동 디자이너를 끌어 화면에 놓습니다 [!INCLUDE[wfd1](../includes/wfd1-md.md)] . 이 활동에 자식 활동을 추가 하려면 <xref:System.Activities.Statements.Sequence> **도구 상자** 의 다른 활동을 "여기에 작업 놓기" 힌트 텍스트가 있는 상자의 삼각형 위에 놓습니다.

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>워크플로 디자이너의 Sequence 활동 속성
 다음 표에서는 <xref:System.Activities.Statements.Sequence> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표 또는 디자이너 화면에서 편집할 수 있습니다.

|속성 이름|필수|사용량|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|머리글에 <xref:System.Activities.Statements.Sequence> 활동 디자이너의 이름을 지정합니다. 기본값은 Sequence입니다. 속성 표에서 또는 활동 디자이너의 머리글에서 직접 값을 편집할 수 있습니다.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|

## <a name="see-also"></a>관련 항목
 [순서도](../workflow-designer/flowchart-activity-designer.md) [제어 흐름](../workflow-designer/control-flow-activity-designers.md)