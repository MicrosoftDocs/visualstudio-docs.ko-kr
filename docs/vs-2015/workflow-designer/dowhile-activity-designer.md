---
title: DoWhile 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b63c3e2e0907bcaf13ada4cbb20ce5527a240fe3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656777"
---
# <a name="dowhile-activity-designer"></a>DoWhile 활동 디자이너
<xref:System.Activities.Statements.DoWhile>활동은 <xref:System.Activities.Statements.DoWhile.Body%2A> 지정 된 조건이 **false**로 평가 될 때까지 한 번 이상 포함 된 활동을 실행 합니다. 루프 본문에 포함된 활동을 0번 이상 실행해야 할 경우 <xref:System.Activities.Statements.While> 활동을 대신 사용하세요.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Workflow Designer의 DoWhile 속성
 다음 표에서는 가장 유용한 <xref:System.Activities.Statements.DoWhile> 활동 속성을 보여 주고 디자이너에서 이러한 속성을 사용하는 방법을 설명합니다.

|속성 이름|필수|사용량|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|조건이 **true**인 동안 실행할 작업입니다. 활동을 추가 하려면 <xref:System.Activities.Statements.DoWhile.Body%2A> 도구 상자의 활동을 "여기에 작업 놓기" 힌트 텍스트가 있는 **DoWhile** 활동 디자이너의 **본문** 상자로 끌어 놓습니다.|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|루프를 반복할 때마다 평가할 조건입니다. 을 설정 하려면 <xref:System.Activities.Statements.DoWhile.Condition%2A> [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] **DoWhile** activity 디자이너의 **조건** 상자 또는 속성 표에 식을 입력 합니다.|

## <a name="see-also"></a>관련 항목
 [While](../workflow-designer/while-activity-designer.md) [제어 흐름](../workflow-designer/control-flow-activity-designers.md)