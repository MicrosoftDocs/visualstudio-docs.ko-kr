---
title: 워크플로 디자이너 TransactedReceiveScope 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75fb1da392bce7dbd0cd7849d83b3b452521e0c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86875932"
---
# <a name="transactedreceivescope-activity-designer"></a>TransactedReceiveScope 활동 디자이너

**TransactedReceiveScope** 디자이너는 활동을 만들고 구성 하는 데 사용 됩니다 <xref:System.ServiceModel.Activities.TransactedReceiveScope> .

## <a name="the-transactedreceivescope-activity"></a>TransactedReceiveScope 활동

<xref:System.ServiceModel.Activities.TransactedReceiveScope> 활동을 통해 트랜잭션을 워크플로 또는 디스패처에 의해 만들어진 서버 트랜잭션으로 이동할 수 있습니다.

### <a name="using-the-transactedreceivescope-activity-designer"></a>TransactedReceiveScope 활동 디자이너 사용

**도구 상자**의 **메시징** 범주에서 **TransactedReceiveScope** 활동 디자이너에 액세스 합니다. **TransactedReceiveScope** 활동 디자이너를 **도구 상자** 에서 끌어다가 일반적으로 활동을 배치 하는 워크플로 디자이너 화면에 놓을 수 있습니다. 그러면 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 기본 **DisplayName** 이 TransactedReceiveScope 인 활동이 만들어집니다. <xref:System.Activities.Activity.DisplayName%2A> **TransactedReceiveScope** 활동 디자이너의 머리글 또는 속성 표의 **DisplayName** 상자에서을 편집할 수 있습니다.

**TransactedReceiveScope** 디자이너에는 **요청** 및 **본문** 상자가 포함 되어 있습니다. 이 상자는 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> 속성을 구성하는 데 사용되고, 이 속성은 <xref:System.ServiceModel.Activities.Receive> 활동과 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> 속성을 지정하며, 이 속성은 다시 몇 가지 다른 <xref:System.Activities.Activity>를 지정합니다. <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>는 트랜잭션을 만듭니다. 그러면 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> 범위의 트랜잭션이 앰비언트 트랜잭션이 되어 이 범위의 모든 활동이 이 트랜잭션 내에서 실행됩니다.

### <a name="the-transactedreceivescope-properties"></a>TransactedReceiveScope 속성

다음 표에서는 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 <xref:System.Activities.Activity.DisplayName%2A> 속성은 속성 표 또는 워크플로 디자이너 화면에서 편집할 수 있지만 다른 속성은 디자인 화면에서 편집 해야 합니다.

|속성 이름|필수|사용량|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.TransactedReceiveScope> 활동의 선택적 이름입니다. 기본값은 TransactedReceiveScope입니다.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> 이름이 꼭 필요하지 않더라도 표시 이름을 사용하는 것이 좋습니다.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|활동 <xref:System.ServiceModel.Activities.Receive> 디자이너 화면의 **요청** 블록에 활동을 놓습니다.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|<xref:System.Activities.Activity>활동 디자이너 화면의 **본문** 블록에를 놓습니다.|

## <a name="see-also"></a>추가 정보

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [받습니다](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [보내기](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)