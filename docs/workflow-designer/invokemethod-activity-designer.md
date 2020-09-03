---
title: 워크플로 디자이너 InvokeMethod 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8660cd82f9d671da3b535ac228e8ce62c875dc07
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75593202"
---
# <a name="invokemethod-activity-designer"></a>InvokeMethod 활동 디자이너

**InvokeMethod** 디자이너는 활동을 만들고 구성 하는 데 사용 됩니다 <xref:System.Activities.Statements.InvokeMethod> .

## <a name="the-invokemethod-activity"></a>InvokeMethod 활동

<xref:System.Activities.Statements.InvokeMethod>는 지정한 개체 또는 형식의 public 메서드를 호출합니다.

### <a name="use-the-invokemethod-activity-designer"></a>InvokeMethod 활동 디자이너 사용

**도구 상자**의 **기본 형식** 범주에서 **InvokeMethod** activity 디자이너에 액세스 합니다. **InvokeMethod** 활동 디자이너를 **도구 상자** 에서 끌어다가 등 일반적으로 활동을 배치 하는 워크플로 디자이너 화면에 놓을 수 있습니다 <xref:System.Activities.Statements.Sequence> . 활동 디자이너를 삭제 하면 <xref:System.Activities.Statements.InvokeMethod> InvokeMethod의 기본이 포함 된 활동이 만들어집니다 <xref:System.Activities.Activity.DisplayName%2A> . <xref:System.Activities.Activity.DisplayName%2A> **InvokeMethod** 활동 디자이너의 머리글 또는 속성 표의 **DisplayName** 상자에서을 편집할 수 있습니다.

### <a name="the-invokemethod-properties"></a>InvokeMethod 속성

다음 표에서는 속성을 보여 주고 <xref:System.Activities.Statements.InvokeMethod> 디자이너에서 이러한 속성을 사용 하는 방법을 설명 합니다. 이러한 속성은 속성 표에서 편집할 수 있으며 일부 속성은 워크플로 디자이너 화면에서 편집할 수 있습니다.

|속성 이름|필수|사용량|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.InvokeMethod> 활동의 이름입니다. 기본값은 InvokeMethod입니다.<br /><br /> 는 반드시 <xref:System.Activities.Activity.DisplayName%2A> 필요한 것은 아니지만 하나를 사용 하는 것이 좋습니다.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|작업이 실행될 때 호출할 메서드의 이름입니다. 호출 된 메서드를 **public**으로 선언 해야 합니다. 이 속성은 디자이너 화면에서 편집할 수 있으며 필수 항목입니다.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|호출되는 메서드의 매개 변수 컬렉션입니다. 메서드 시그니처에 표시되는 것과 동일한 순서대로 컬렉션에 매개 변수를 추가해야 합니다. 이 속성을 설정할 수 있는 **매개 변수** 대화 상자를 표시 하려면 속성 표의 **매개 변수** 필드에서 줄임표 단추를 클릭 합니다. **인수 만들기** 단추를 클릭 하 여 매개 변수를 추가 합니다.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|메서드 호출의 반환 값입니다.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|메서드가 비동기적으로 호출되는지 여부를 지정합니다. 기본값은 **False**입니다.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|호출할 메서드가 포함된 개체입니다. 이 속성은 디자이너 화면에서 편집할 수 있습니다.<br /><br /> <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 또는 <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>을 설정해야 합니다.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>의 형식입니다. 이 속성은 디자이너 화면에서 편집할 수 있습니다. 이 속성은 호출된 메서드가 정적인 경우에만 설정해야 합니다.|

C # **out** 매개 변수로 매개 변수를 전달 하려면 (예:) `Method1(out myParam))` **InOutArgument** 대신 **outargument<int>** 를 사용 합니다.

**TargetObject** 또는 **Result** 라는 인수를 사용 하는 메서드는 활동을 사용 하 여 호출할 수 없습니다 <xref:System.Activities.Statements.InvokeMethod> . 그 이유는 <xref:System.Activities.Statements.InvokeMethod> 활동이 <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 및 <xref:System.Activities.Statements.InvokeMethod.Result%2A>를 <xref:System.Activities.Activity.CacheMetadata%2A>에 등록하기 때문입니다.

<xref:System.Activities.Activity.CacheMetadata%2A>에 매개 변수를 등록하는 알고리즘이 다음 목록에 나와 있습니다.

1. <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 인수를 등록합니다.

2. <xref:System.Activities.Statements.InvokeMethod.Result%2A> 인수를 등록합니다.

3. <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> 컬렉션을 반복하고 각 인수를 등록합니다.

다음과 같은 메시지와 함께 <xref:System.Activities.InvalidWorkflowException> 형식의 예외가 발생합니다. 'InvokeMethod': 이름이 'TargetObject'인 변수(RuntimeArgument 또는 DelegateArgument) 변수가 이미 있습니다. 이름은 환경 범위 내에서 고유해야 합니다.

이 제한은 및에 적용 되지 않습니다 <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A> . 워크플로 인수가 아니므로 <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> 메서드의 활동 컬렉션에 등록 되지 않습니다 <xref:System.Activities.Statements.InvokeMethod> <xref:System.Activities.Activity.CacheMetadata%2A> .

## <a name="see-also"></a>추가 정보

- [기본 요소](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)
