---
title: 메시징 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 897e63cf-a42f-4edd-876f-c4ccfffaf6d6
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a6fb06bea4cebf2558990d23f7ece5b4f8db5b95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658926"
---
# <a name="messaging-activity-designers"></a>메시징 활동 디자이너
메시징 활동 디자이너는 [!INCLUDE[indigo1](../includes/indigo1-md.md)] 애플리케이션에서 [!INCLUDE[wf](../includes/wf-md.md)] 메시지를 보내고 받는 메시징 활동을 만들고 구성하는 데 사용됩니다. [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)]에는 다섯 가지 메시징 활동이 도입되었으며, [!INCLUDE[wfd1](../includes/wfd1-md.md)]에는 두 가지 새로운 템플릿 디자이너가 있어 워크플로 내의 메시징을 관리할 수 있습니다. 이 단원의 항목 및 아래 표의 항목에서는 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 활동 및 템플릿 디자이너의 사용 방법에 대한 지침을 제공합니다.

## <a name="in-this-section"></a>섹션 내용

|메시지 활동|설명|
|----------------------|-----------------|
|[CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)|<xref:System.ServiceModel.Activities.CorrelationScope> 개체로 자식 메시징 활동을 암시적으로 관리하는 <xref:System.ServiceModel.Activities.CorrelationHandle> 활동을 만들고 구성합니다.|
|[InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)|메시지를 보내거나 받지 않고 상관 관계를 초기화하는 데 사용되는 <xref:System.ServiceModel.Activities.InitializeCorrelation> 활동을 만들고 구성합니다.|
|[받습니다](../workflow-designer/receive-activity-designer.md)|서비스로부터 메시지를 받는 <xref:System.ServiceModel.Activities.Receive> 활동을 만들고 구성합니다.|
|[ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)|<xref:System.ServiceModel.Activities.Send> 활동 내부에 사전 구성된 <xref:System.ServiceModel.Activities.ReceiveReply> 및 <xref:System.Activities.Statements.Sequence> 활동 쌍을 만듭니다.|
|[보내기](../workflow-designer/send-activity-designer.md)|서비스로 메시지를 보내는 <xref:System.ServiceModel.Activities.Send> 활동을 만들고 구성합니다.|
|[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)|<xref:System.ServiceModel.Activities.Receive> 활동 내부에 사전 구성된 <xref:System.ServiceModel.Activities.SendReply> 및 <xref:System.Activities.Statements.Sequence> 활동 쌍을 만듭니다.|
|[TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)|워크플로에 대한 트랜잭션의 흐름을 가능하게 하는 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 활동을 만들고 구성합니다.|

## <a name="reference"></a>참고
 <xref:System.Activities.Activity>

 <xref:System.ServiceModel.Activities.CorrelationScope>

 <xref:System.ServiceModel.Activities.Receive>

 <xref:System.ServiceModel.Activities.Send>

 <xref:System.ServiceModel.Activities.ReceiveReply>

 <xref:System.ServiceModel.Activities.SendReply>

 <xref:System.ServiceModel.Activities.TransactedReceiveScope>

## <a name="related-sections"></a>관련 단원
 그 밖의 활동 디자이너 형식에 대해서는 다음 항목을 참조하세요.

 [제어 흐름](../workflow-designer/control-flow-activity-designers.md)

 [활동 디자이너 사용](../workflow-designer/using-the-activity-designers.md)

 [순서도](../workflow-designer/flowchart-activity-designers.md)

 [런타임](../workflow-designer/runtime-activity-designers.md)

 [기본 요소](../workflow-designer/primitives-activity-designers.md)

 [트랜잭션](../workflow-designer/transaction-activity-designers.md)

 [컬렉션](../workflow-designer/collection-activity-designers.md)

 [오류 처리](../workflow-designer/error-handling-activity-designers.md)

## <a name="external-resources"></a>외부 리소스
 [활동 디자이너 사용](../workflow-designer/using-the-activity-designers.md)