---
title: 워크플로 디자이너 ReceiveAndSendReply 템플릿 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66822664766ac64e466882fda27906f56ebb4aad
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86876010"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply 템플릿 디자이너

**ReceiveAndSendReply** 템플릿은 미리 구성 된 및 작업 쌍을 만드는 데 사용 됩니다 <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> . 활동은 활동의 일부 <xref:System.Activities.Statements.Sequence> 이며 서버에서 요청/응답 메시지 교환 패턴의 일부로 상관 관계가 지정 됩니다.

## <a name="the-receiveandsendreply-template"></a>ReceiveAndSendReply 템플릿

**ReceiveAndSendReply** 템플릿 추가는 활동을 사용 하 여 및 활동을 만드는 것 외에도 다음 세 가지 작업을 수행 합니다 <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> <xref:System.Activities.Statements.Sequence> .

- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>활동의 및 속성을 구성 합니다 <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> <xref:System.ServiceModel.Activities.Receive> .

- <xref:System.ServiceModel.Activities.SendReply.Request%2A> 활동의 <xref:System.ServiceModel.Activities.Receive> 속성이 <xref:System.ServiceModel.Activities.Send> 활동에 바인딩됩니다.

- 부모 활동의 변수로 <xref:System.ServiceModel.Activities.CorrelationHandle>이 만들어집니다.

### <a name="use-the-receiveandsendreply-template-designer"></a>ReceiveAndSendReply 템플릿 디자이너 사용

**도구 상자**의 **메시징** 범주에서 **ReceiveAndSendReply** 활동 디자이너에 액세스 합니다. **ReceiveAndSendReply** 활동 디자이너를 **도구 상자** 에서 끌어다가 일반적으로 활동을 배치 하는 워크플로 디자이너 화면에 놓을 수 있습니다. 활동 디자이너를 삭제 하면 <xref:System.ServiceModel.Activities.Receive> SendReplyToReceive designer를 사용 하 여 구성할 수 있는 상관 관계와 **Send** activity designer를 사용 하 여 구성할 수 있는 활동이 만들어집니다 <xref:System.ServiceModel.Activities.SendReply> .

**수신** 디자이너를 사용 하 여 작업을 구성 하는 방법에 대 한 자세한 내용은 <xref:System.ServiceModel.Activities.Receive> [receive activity designer](../workflow-designer/receive-activity-designer.md)를 참조 하세요.

### <a name="properties-of-sendreply"></a>SendReply 속성

다음 표에서는 <xref:System.ServiceModel.Activities.SendReply> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표에서 편집할 수 있으며 일부 속성은 워크플로 디자이너 화면에서 편집할 수 있습니다.

| 속성 이름 | 필수 | 사용량 |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | 거짓 | <xref:System.ServiceModel.Activities.SendReply> 활동의 선택적 이름입니다. 기본값은 SendReplyToReceive입니다.<br /><br /> 친숙 한에 기본값이 아닌 값을 사용 하는 것은 반드시 <xref:System.Activities.Activity.DisplayName%2A> 필요한 것은 아니지만 이러한 값을 사용 하는 것이 가장 좋습니다. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | True | 이 <xref:System.ServiceModel.Activities.Receive> 활동과 한 쌍을 이루는 <xref:System.ServiceModel.Activities.SendReply> 활동에 대한 참조입니다. 이 속성은 **null**이 아니어야 합니다. <xref:System.ServiceModel.Activities.Receive><xref:System.ServiceModel.Activities.SendReply>서버에서 및 활동을 함께 사용 하 여 요청/응답 메시징 패턴을 모델링할 수 있습니다. 이 속성 <xref:System.ServiceModel.Activities.Send> 은 쌍을 이루는 활동을 지정 합니다. 디자이너에서는 활동을 만든 활동에 자동으로 바인딩되기 때문에이 속성을 편집할 수 없습니다 <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> . |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | 거짓 | 받을 메시지 또는 매개 변수 콘텐츠를 지정합니다. <xref:System.ServiceModel.Activities.ReceiveMessageContent> 활동이거나 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 활동일 수 있습니다. 속성 그리드에서 **콘텐츠** 필드 옆에 있는 줄임표 단추를 클릭 하거나 **수신** 활동 디자이너 화면에서 **콘텐츠** 레이블 옆에 있는 **정의** 단추를 클릭 하 여이 속성을 편집 합니다. 둘 다 **콘텐츠 정의** 대화 상자를 표시 합니다. 이 상자를 사용 하는 방법에 대 한 자세한 내용은 [콘텐츠 정의 대화 상자](../workflow-designer/content-definition-dialog-box.md) 항목을 참조 하세요. |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | 거짓 | 워크플로 내에서 이 <xref:System.ServiceModel.Activities.CorrelationInitializer> 활동을 구성하는 <xref:System.ServiceModel.Activities.CorrelationHandle> 개체를 여러 개 초기화하는 <xref:System.ServiceModel.Activities.Receive> 개체 컬렉션을 지정합니다. 속성 표에서 속성 옆의 줄임표 단추를 클릭 <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> 하 여 **상관 관계 이니셜라이저 추가** 대화 상자를 엽니다. 이 상자를 사용 하는 방법에 대 한 자세한 내용은 [CorrelationInitializers 추가 대화 상자](../workflow-designer/add-correlationinitializers-dialog-box.md) 항목을 참조 하세요. |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | 거짓 | 메시지의 동작 헤더를 지정합니다. 명시적으로 설정 되지 않은 경우 해당 값의 기본값은 다음과 같습니다.<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | 거짓 | 회신 메시지를 보내기 전에 워크플로 인스턴스를 유지할지 여부를 지정합니다. 기본 값은 **false**입니다. |

## <a name="see-also"></a>추가 정보

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [받습니다](../workflow-designer/receive-activity-designer.md)
- [보내기](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)