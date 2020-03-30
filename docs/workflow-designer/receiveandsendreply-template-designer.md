---
title: 워크플로 디자이너 - 수신AndSendReply 템플릿 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 042032efe745a9cb38bbf4e362cb5ad8440129ba
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395295"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply 템플릿 디자이너

**ReceiveAndSendReply** 템플릿은 미리 구성된 활동 <xref:System.ServiceModel.Activities.Receive> 과 <xref:System.ServiceModel.Activities.SendReply> 활동 쌍을 만드는 데 사용됩니다. 활동은 <xref:System.Activities.Statements.Sequence> 활동의 일부이며 서버의 요청/응답 메시지 교환 패턴의 일부로 상호 관련됩니다.

## <a name="the-receiveandsendreply-template"></a>ReceiveAndSendReply 템플릿

**ReceiveAndSendReply** 템플릿을 추가하면 활동 <xref:System.ServiceModel.Activities.Receive> 및 <xref:System.ServiceModel.Activities.SendReply> 활동을 <xref:System.Activities.Statements.Sequence> 만드는 것 외에 세 가지 작업을 수행합니다.

- 활동의 <xref:System.ServiceModel.Activities.Receive.OperationName%2A> 및 <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> 속성을 구성합니다. <xref:System.ServiceModel.Activities.Receive>

- <xref:System.ServiceModel.Activities.SendReply.Request%2A> 활동의 <xref:System.ServiceModel.Activities.Receive> 속성이 <xref:System.ServiceModel.Activities.Send> 활동에 바인딩됩니다.

- 부모 활동의 변수로 <xref:System.ServiceModel.Activities.CorrelationHandle>이 만들어집니다.

### <a name="use-the-receiveandsendreply-template-designer"></a>ReceiveAndSendReply 템플릿 디자이너 사용

**도구 상자의** **메시징** 범주에서 **ReceiveAndSendReply** 활동 디자이너에 액세스합니다. **ReceiveAndSendReply** 활동 디자이너는 도구 **상자에서** 드래그하여 활동이 일반적으로 배치되는 모든 위치에서 워크플로 디자이너 표면으로 놓을 수 있습니다. 활동 디자이너를 삭제하면 **보내기** 활동 디자이너로 구성할 수 있는 <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.Receive> 활동과 SendReplyToReceive 디자이너로 구성할 수 있는 상관 관계가 만들어집니다.

수신 디자이너를 사용하여 활동을 구성하는 자세한 내용은 [활동 받기 디자이너를](../workflow-designer/receive-activity-designer.md)참조하십시오. **Receive** <xref:System.ServiceModel.Activities.Receive>

### <a name="properties-of-sendreply"></a>SendReply 속성

다음 표에서는 <xref:System.ServiceModel.Activities.SendReply> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표에서 편집할 수 있으며 일부는 워크플로 디자이너 표면에서 편집할 수 있습니다.

| 속성 이름 | 필수 | 사용 |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | <xref:System.ServiceModel.Activities.SendReply> 활동의 선택적 이름입니다. 기본값은 SendReplyToReceive입니다.<br /><br /> 친용에 <xref:System.Activities.Activity.DisplayName%2A> 대해 기본값이 아닌 값을 사용해야 하는 것은 아니지만 이러한 값을 사용하는 것이 가장 좋습니다. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | True | 이 <xref:System.ServiceModel.Activities.Receive> 활동과 한 쌍을 이루는 <xref:System.ServiceModel.Activities.SendReply> 활동에 대한 참조입니다. 이 속성은 **null이**아니어야 합니다. <xref:System.ServiceModel.Activities.Receive>활동은 <xref:System.ServiceModel.Activities.SendReply> 서버에서 함께 사용되어 요청/응답 메시징 패턴을 모델링합니다. 이 속성은 페어링되는 <xref:System.ServiceModel.Activities.Send> 활동을 지정합니다. 디자이너에서는 활동을 만든 <xref:System.ServiceModel.Activities.Send> 활동에 자동으로 바인딩되므로 이 속성을 편집할 <xref:System.ServiceModel.Activities.SendReply> 수 없습니다. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | 받을 메시지 또는 매개 변수 콘텐츠를 지정합니다. <xref:System.ServiceModel.Activities.ReceiveMessageContent> 활동이거나 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 활동일 수 있습니다. 속성 표의 **콘텐츠** 필드 옆에 있는 타원 단추를 클릭하거나 **활동 받기** 디자이너 표면의 콘텐츠 레이블 옆에 있는 **정의** 단추를 클릭하여 이 속성을 편집합니다. **Content** 둘 다 **콘텐츠 정의** 대화 상자를 표시합니다. 이 상자를 사용하는 방법에 대한 자세한 내용은 [콘텐츠 정의 대화 상자](../workflow-designer/content-definition-dialog-box.md) 항목을 참조하세요. |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | 워크플로 내에서 이 <xref:System.ServiceModel.Activities.CorrelationInitializer> 활동을 구성하는 <xref:System.ServiceModel.Activities.CorrelationHandle> 개체를 여러 개 초기화하는 <xref:System.ServiceModel.Activities.Receive> 개체 컬렉션을 지정합니다. 속성 그리드의 속성 옆에 <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> 있는 타원 단추를 클릭하여 **상관 관계 초기화자 추가** 대화 상자를 엽니다. 이 상자에 대한 자세한 내용은 [상관 관계 초기화 추가 대화 상자](../workflow-designer/add-correlationinitializers-dialog-box.md) 항목을 참조하십시오. |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | 메시지의 동작 헤더를 지정합니다. 명시적으로 설정되지 않은 경우 해당 값은 기본값을 다음과 같은 값으로 설정합니다.<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | 회신 메시지를 보내기 전에 워크플로 인스턴스를 유지할지 여부를 지정합니다. 기본값은 **false**입니다. |

## <a name="see-also"></a>참고 항목

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [수신](../workflow-designer/receive-activity-designer.md)
- [보내기](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)