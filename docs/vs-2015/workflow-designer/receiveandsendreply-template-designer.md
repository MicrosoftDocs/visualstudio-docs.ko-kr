---
title: ReceiveAndSendReply 템플릿 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4c00eed244867cfd38b20f6a8f065fc6da006801
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395385"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply 템플릿 디자이너
**ReceiveAndSendReply** 템플릿은 <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> <xref:System.Activities.Statements.Sequence> 서버에서 요청/응답 메시지 교환 패턴의 일부로 상관 관계가 지정 된 활동 내에 미리 구성 된 및 활동 쌍을 만드는 데 사용 됩니다.

## <a name="the-receiveandsendreply-template"></a>ReceiveAndSendReply 템플릿
 **ReceiveAndSendReply** 템플릿 추가는 활동을 사용 하 여 <xref:System.ServiceModel.Activities.Receive> 및 활동을 만드는 것 외에도 세 가지 작업을 수행 합니다 <xref:System.ServiceModel.Activities.SendReply> <xref:System.Activities.Statements.Sequence> .

1. <xref:System.ServiceModel.Activities.Receive.OperationName%2A> 활동의 <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>, <xref:System.ServiceModel.Activities.Receive> 속성이 구성됩니다.

2. <xref:System.ServiceModel.Activities.SendReply.Request%2A> 활동의 <xref:System.ServiceModel.Activities.Receive> 속성이 <xref:System.ServiceModel.Activities.Send> 활동에 바인딩됩니다.

3. 부모 활동의 변수로 <xref:System.ServiceModel.Activities.CorrelationHandle>이 만들어집니다.

### <a name="using-the-receiveandsendreply-template-designer"></a>ReceiveAndSendReply 템플릿 디자이너 사용
 **ReceiveAndSendReply** 활동 디자이너는 **도구 상자**의 **메시징** 범주에 있습니다 .이 범주에 액세스 하려면의 **도구 상자** 탭을 클릭 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 하거나, **보기** 메뉴에서 **도구 모음** 을 선택 하거나, CTRL + ALT + X를 클릭 합니다.

 **ReceiveAndSendReply** 활동 디자이너를 **도구 상자** 에서 끌어다가 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 일반적으로 활동을 배치 하는 화면의 아무 곳에 나 놓을 수 있습니다. 이렇게 하면 <xref:System.ServiceModel.Activities.Receive> SendReplyToReceive designer를 사용 하 여 구성할 수 있는 상관 관계와 **Send** activity designer를 사용 하 여 구성할 수 있는 활동이 만들어집니다 <xref:System.ServiceModel.Activities.SendReply> .

 [!INCLUDE[crabout](../includes/crabout-md.md)]**수신** 디자이너를 사용 하 여 작업을 구성 하려면 <xref:System.ServiceModel.Activities.Receive> [수신](../workflow-designer/receive-activity-designer.md) 항목을 참조 하세요.

 [!INCLUDE[crabout](../includes/crabout-md.md)]**SendReplyToReceive** 디자이너를 사용 하 여 작업을 구성 하려면 <xref:System.ServiceModel.Activities.SendReply> 다음 섹션을 참조 하세요.

### <a name="properties-of-sendreply"></a>SendReply 속성
 다음 표에서는 <xref:System.ServiceModel.Activities.SendReply> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표에서 편집할 수 있으며 일부 속성은 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 디자이너 화면에서 편집할 수 있습니다.

|                               속성 이름                                | 필수 |                                                                                                                                                                                                                                                                                                                                                      사용량                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <xref:System.Activities.Activity.DisplayName%2A>              |  False   |                                                                                                                                                                                            <xref:System.ServiceModel.Activities.SendReply> 활동의 선택적 이름입니다. 기본값은 SendReplyToReceive입니다.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>에 꼭 기본값 이외의 값을 사용할 필요는 없지만 그런 값을 사용하는 것이 좋습니다.                                                                                                                                                                                             |
|         <xref:System.ServiceModel.Activities.SendReply.Request%2A>         |   True   | 이 <xref:System.ServiceModel.Activities.Receive> 활동과 한 쌍을 이루는 <xref:System.ServiceModel.Activities.SendReply> 활동에 대한 참조입니다. 이 속성은 **null**이 아니어야 합니다. <xref:System.ServiceModel.Activities.Receive><xref:System.ServiceModel.Activities.SendReply>서버에서 및 활동을 함께 사용 하 여 요청/응답 메시징 패턴을 모델링할 수 있습니다. 이 속성 <xref:System.ServiceModel.Activities.Send> 은 쌍을 이루는 활동을 지정 합니다. 이 속성은 <xref:System.ServiceModel.Activities.Send> 활동을 만들었던 <xref:System.ServiceModel.Activities.SendReply> 활동에 자동으로 바인딩되기 때문에 디자이너에서 편집할 수 없습니다. |
|         <xref:System.ServiceModel.Activities.SendReply.Content%2A>         |  False   |                       받을 메시지 또는 매개 변수 콘텐츠를 지정합니다. <xref:System.ServiceModel.Activities.ReceiveMessageContent> 활동이거나 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 활동일 수 있습니다. 속성 표에서 **내용** 필드 옆에 있는 줄임표 단추를 클릭 하거나 **정의 ...** 를 클릭 하 여이 속성을 편집 합니다. **Receive** activity Designer 화면의 **콘텐츠** 레이블 옆에 있는 단추입니다. 둘 다 **콘텐츠 정의** 대화 상자를 표시 합니다. [!INCLUDE[crabout](../includes/crabout-md.md)] 이 상자를 사용 하는 방법 [콘텐츠 정의 대화 상자](../workflow-designer/content-definition-dialog-box.md) 항목을 참조 하세요.                       |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> |  False   |            워크플로 내에서 이 <xref:System.ServiceModel.Activities.CorrelationInitializer> 활동을 구성하는 <xref:System.ServiceModel.Activities.CorrelationHandle> 개체를 여러 개 초기화하는 <xref:System.ServiceModel.Activities.Receive> 개체 컬렉션을 지정합니다. 속성 표에서 속성 옆의 줄임표 단추를 클릭 <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> 하 여 **상관 관계 이니셜라이저 추가** 대화 상자를 엽니다. [!INCLUDE[crabout](../includes/crabout-md.md)] 이 상자를 사용 하 여 [CorrelationInitializers 추가 대화 상자](../workflow-designer/add-correlationinitializers-dialog-box.md) 항목을 참조 하세요.            |
|         <xref:System.ServiceModel.Activities.SendReply.Action%2A>          |  False   |                                                                                                                                                                                                                                              메시지의 동작 헤더를 지정합니다. 동작 헤더가 명시적으로 설정되어 있지 않으면 기본값인<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`                                                                                                                                                                                                                                              |
|    <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>    |  False   |                                                                                                                                                                                                                                                                                          회신 메시지를 보내기 전에 워크플로 인스턴스를 유지할지 여부를 지정합니다. 기본 값은 **false**입니다.                                                                                                                                                                                                                                                                                           |

## <a name="see-also"></a>관련 항목
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [Send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)