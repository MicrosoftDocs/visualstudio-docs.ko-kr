---
title: 워크플로 디자이너-ForEach &lt; T &gt; 활동 디자이너
description: ForEach <T> 작업이 지정 된 값 컬렉션의 각 항목에 대 한 본문에 포함 된 활동을 실행 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d4c594e613d1160794e8310695d61bcc97902caa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876461"
---
# <a name="foreachlttgt-activity-designer"></a>ForEach &lt; T &gt; 활동 디자이너

<xref:System.Activities.Statements.ForEach%601> 활동은 지정된 <xref:System.Activities.Statements.ForEach%601.Body%2A> 컬렉션의 각 항목에 대해 <xref:System.Activities.Statements.ForEach%601.Values%2A>에 포함된 활동을 실행합니다.

## <a name="foreacht-properties-in-the-workflow-designer"></a>워크플로 디자이너의 ForEach<T \> 속성

다음 표에서는 가장 유용한 <xref:System.Activities.Statements.ForEach%601> 활동 속성을 보여 주고 디자이너에서 이러한 속성을 사용하는 방법을 설명합니다.

|속성 이름|필수|사용량|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.ForEach%601> 활동의 이름입니다. 기본값은 ForEach<Int32 \> 입니다. <xref:System.Activities.Activity.DisplayName%2A> 값은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|반복할 항목의 컬렉션입니다. 을 설정 하려면 <xref:System.Activities.Statements.ForEach%601.Values%2A> **ForEach<T \>** 활동 디자이너의 **값** 상자 또는 속성 표에 Visual Basic 식을 입력 합니다.|
|*TypeArgument*|True|<xref:System.Activities.Statements.ForEach%601.Values%2A>제네릭 매개 변수 *T* 로 지정 된 컬렉션에 있는 항목의 형식입니다. 기본적으로 *Typeargument* 는 **Int32** 로 설정 됩니다. 유형을 변경 하려면 속성 표에서 *Typeargument* 콤보 상자의 값을 변경 합니다.|

기본적으로 루프 반복기는 **항목** 으로 명명 됩니다. <xref:System.Activities.Statements.ForEach%601> 활동 디자이너에서 반복기 변수의 이름을 변경할 수 있습니다. 루프 반복기는 <xref:System.Activities.Statements.ForEach%601> 활동의 자식에 포함된 식에서 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [제어 흐름](../workflow-designer/control-flow-activity-designers.md)
