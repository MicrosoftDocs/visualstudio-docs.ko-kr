---
title: SendAndReceiveReply 템플릿 디자이너 | 마이크로 소프트 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1bfe43f410709a924b0ebdb0cf6afbb8d30a8fcf
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395333"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply 템플릿 디자이너
**SendAndReceiveReply** 템플릿은 클라이언트에서 요청/응답 메시지 <xref:System.ServiceModel.Activities.Send> 교환 <xref:System.ServiceModel.Activities.ReceiveReply> 패턴의 <xref:System.Activities.Statements.Sequence> 일부로 상관 관계가 있는 활동 내에서 미리 구성된 활동 과 활동 쌍을 만드는 데 사용됩니다.

## <a name="the-sendandreceivereply-template"></a>SendAndReceiveReply 템플릿
 **SendAndReceiveReply** 템플릿을 추가하면 활동 <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> 내에서 및 <xref:System.Activities.Statements.Sequence> 활동을 만드는 것 외에 세 가지 작업을 수행합니다.

1. <xref:System.ServiceModel.Activities.Send.OperationName%2A> 활동의 <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A>, <xref:System.ServiceModel.Activities.Send> 속성이 구성됩니다.

2. <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> 활동의 <xref:System.ServiceModel.Activities.ReceiveReply> 속성이 <xref:System.ServiceModel.Activities.Send> 활동에 바인딩됩니다.

3. 부모 활동의 변수로 <xref:System.ServiceModel.Activities.CorrelationHandle>이 만들어집니다.

### <a name="using-the-sendandreceivereply-template-designer"></a>SendAndReceiveReply 템플릿 디자이너 사용
 **SendAndReceiveReply** 활동 디자이너는 **도구 상자의** **메시징** 범주에서 찾을 수 있습니다., 도구 [!INCLUDE[wfd2](../includes/wfd2-md.md)] **상자** 탭을 클릭 하 여 액세스 (또는, **보기** 메뉴에서 **도구 모음을** 선택, 또는 CTRL +ALT+X.)

 **SendAndReceiveReply** 활동 디자이너는 도구 **상자에서** 드래그하여 활동이 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 일반적으로 배치되는 모든 위치에 놓일 수 있습니다. 이렇게 하면 <xref:System.ServiceModel.Activities.Send> **보내기** 활동 디자이너와 **ReceiveReplyForSend** 디자이너로 <xref:System.ServiceModel.Activities.ReceiveReply> 구성할 수 있는 상관 관계로 구성할 수 있는 활동을 만듭니다.

 [!INCLUDE[crabout](../includes/crabout-md.md)]**보내기** 디자이너를 사용하여 <xref:System.ServiceModel.Activities.Send> 활동을 구성하려면 [보내기](../workflow-designer/send-activity-designer.md) 항목을 참조하십시오.

 [!INCLUDE[crabout](../includes/crabout-md.md)]**수신응답ForSend** 디자이너를 사용하여 <xref:System.ServiceModel.Activities.ReceiveReply> 활동을 구성하려면 다음 섹션을 참조하십시오.

### <a name="properties-of-receivereply"></a>ReceiveReply의 속성
 다음 표에서는 <xref:System.ServiceModel.Activities.ReceiveReply> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표에서 편집할 수 있으며 일부 속성은 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 디자이너 화면에서 편집할 수 있습니다.

|                                 속성 이름                                 | 필수 |                                                                                                                                                                                                                                                                                                                                                        사용                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  False   |                                                                                                                                                                                            <xref:System.ServiceModel.Activities.ReceiveReply> 활동의 선택적 이름입니다. 기본값은 ReceiveReplyForSend입니다.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>에 꼭 기본값 이외의 값을 사용할 필요는 없지만 그런 값을 사용하는 것이 좋습니다.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   True   | 이 <xref:System.ServiceModel.Activities.Send> 활동과 한 쌍을 이루는 <xref:System.ServiceModel.Activities.ReceiveReply> 활동에 대한 참조입니다. 이 속성은 **null이**아니어야 합니다. <xref:System.ServiceModel.Activities.Send> 및 <xref:System.ServiceModel.Activities.ReceiveReply> 활동은 클라이언트에서 요청/응답 메시징 패턴을 모델링하는 데 함께 사용됩니다. 이 속성은 페어링되는 <xref:System.ServiceModel.Activities.Send> 활동을 지정합니다. 이 속성은 <xref:System.ServiceModel.Activities.Send> 활동을 만들었던 <xref:System.ServiceModel.Activities.ReceiveReply> 활동에 자동으로 바인딩되기 때문에 디자이너에서 편집할 수 없습니다. |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  False   |                        받을 메시지 또는 매개 변수 콘텐츠를 지정합니다. <xref:System.ServiceModel.Activities.ReceiveMessageContent> 활동이거나 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 활동일 수 있습니다. 속성 표의 **콘텐츠** 필드 옆에 있는 타원 단추를 클릭하거나 정의 정의를 클릭하여 이 속성을 **편집합니다.** [수신 활동 디자이너] **Receive** 표면의 **콘텐츠** 레이블 옆에 있는 단추를 누를 수 있습니다. 둘 다 **콘텐츠 정의** 대화 상자를 표시합니다. [!INCLUDE[crabout](../includes/crabout-md.md)]이 상자를 사용하는 방법은 [콘텐츠 정의 대화 상자](../workflow-designer/content-definition-dialog-box.md) 항목을 참조하십시오.                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  False   |              워크플로 내에서 이 <xref:System.ServiceModel.Activities.CorrelationInitializer> 활동을 구성하는 <xref:System.ServiceModel.Activities.CorrelationHandle> 개체를 여러 개 초기화하는 <xref:System.ServiceModel.Activities.Receive> 개체 컬렉션을 지정합니다. 속성 그리드의 속성 옆에 <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> 있는 타원 단추를 클릭하여 **상관 관계 초기화자 추가** 대화 상자를 엽니다. [!INCLUDE[crabout](../includes/crabout-md.md)]이 상자를 사용하여 [상관 관계 초기화자 대화 상자 추가](../workflow-designer/add-correlationinitializers-dialog-box.md) 항목을 참조하십시오.               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  False   |                                                                                                                                                                                                                                               메시지의 동작 헤더를 지정합니다. 동작 헤더가 명시적으로 설정되어 있지 않으면 기본값인<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`.                                                                                                                                                                                                                                              |

## <a name="see-also"></a>관련 항목
 [상관 관계 스코프](../workflow-designer/correlationscope-activity-designer.md) [초기화상관](../workflow-designer/initializecorrelation-activity-designer.md) [수신AndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [전송](../workflow-designer/send-activity-designer.md) [트랜잭션 수신스코프](../workflow-designer/transactedreceivescope-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md)