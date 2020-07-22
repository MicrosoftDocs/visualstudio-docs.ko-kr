---
title: 워크플로 디자이너 CorrelationScope 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 135acfbbaf9fdcbbf219fd50a504cf9262fe4d24
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86876101"
---
# <a name="correlationscope-activity-designer"></a>CorrelationScope 활동 디자이너

**CorrelationScope** 활동 디자이너는 <xref:System.ServiceModel.Activities.CorrelationScope> 개체를 사용 하 여 자식 메시징 활동의 암시적 관리를 제공 하는 활동을 만들고 구성 하는 데 사용 됩니다 <xref:System.ServiceModel.Activities.CorrelationHandle> .

## <a name="the-correlationscope-activity"></a>CorrelationScope 활동

<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> 속성은 자식 메시징 활동을 관리하는 데 사용되는 <xref:System.ServiceModel.Activities.CorrelationHandle>을 지정합니다. <xref:System.ServiceModel.Activities.Send>에 포함된 <xref:System.ServiceModel.Activities.Receive> 및 <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> 활동은 해당 활동을 포함하는 <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> 활동의 <xref:System.ServiceModel.Activities.CorrelationScope> 속성을 사용하여 상호 연결을 수행하도록 구성됩니다.

### <a name="use-the-correlationscope-activity-designer"></a>CorrelationScope 활동 디자이너 사용

**CorrelationScope** 활동 디자이너는 **도구 상자**의 **메시징** 범주에 있습니다 .이 범주에 액세스 하려면 워크플로 디자이너 왼쪽에 있는 **도구 상자** 탭을 클릭 합니다. 또는 **보기** 메뉴에서 **도구 상자** 를 선택 하거나 **ctrl** + **Alt** + **X**를 누릅니다.

**CorrelationScope** 활동 디자이너를 **도구 상자** 에서 끌어서 워크플로 디자이너 화면에 놓을 수 있습니다. 그러면 <xref:System.ServiceModel.Activities.CorrelationScope> 기본 **DisplayName** 이 CorrelationScope 인 활동이 만들어집니다. <xref:System.Activities.Activity.DisplayName%2A> **CorrelationScope** 활동 디자이너의 머리글 또는 **속성** 창의 **DisplayName** 상자에서을 편집할 수 있습니다.

<xref:System.ServiceModel.Activities.CorrelationHandle>자식 메시징 활동에서 사용 되는을 지정 하려면 **속성** 창에서 **CorrelatesWith** 필드 옆에 있는 줄임표 단추를 선택 하 여 **식 편집기** 대화 상자를 표시 합니다. 이 속성은 활동 디자이너 화면에서도 설정할 수 있습니다.

상관 관계 내에서 범위가 지정 된 활동은 **CorrelationScope** 디자이너 내의 **본문** 상자 내에서 해당 디자이너를 삭제 하 여 지정 합니다.

### <a name="the-correlationscope-properties"></a>CorrelationScope 속성

다음 표에서는 <xref:System.ServiceModel.Activities.CorrelationScope> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 **속성** 창이 나 워크플로 디자이너 화면에서 편집할 수 있으며 둘 다에서 편집할 수 있습니다.

|속성 이름|필수|사용량|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|거짓|<xref:System.ServiceModel.Activities.InitializeCorrelation> 활동의 선택적 이름입니다.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|거짓|자식 메시징 활동을 관리하는 데 사용되는 <xref:System.ServiceModel.Activities.CorrelationHandle>을 지정합니다. 이 속성을 설정하지 않으면 <xref:System.ServiceModel.Activities.CorrelationScope>는 자동으로 <xref:System.ServiceModel.Activities.CorrelationHandle>을 만듭니다.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|거짓|상관 관계 범위 내에 활동을 지정합니다.|

## <a name="see-also"></a>추가 정보

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [받습니다](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [보내기](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)