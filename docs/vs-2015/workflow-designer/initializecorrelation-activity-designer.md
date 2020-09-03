---
title: InitializeCorrelation 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 145b67574169696771f4102b29e9dc8f6a9d1575
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659017"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation 활동 디자이너
**InitializeCorrelation** 활동 디자이너는 <xref:System.ServiceModel.Activities.InitializeCorrelation> 메시지를 보내거나 받기 전에 메시지 간의 상관 관계를 설정 하는 데 사용 되는 활동을 만들고 구성 하는 데 사용 됩니다.

## <a name="the-initializecorrelation-activity"></a>InitializeCorrelation 활동
 <xref:System.ServiceModel.Activities.InitializeCorrelation> 활동은 메시지를 보내거나 받지 않고 상관 관계를 초기화하는 데 사용됩니다. 일반적으로 상관 관계는 메시지를 보내거나 받을 때 초기화됩니다. 메시지를 보내거나 받기 전에 상관 관계를 설정해야 하는 경우 <xref:System.ServiceModel.Activities.InitializeCorrelation>을 사용하여 상관 관계를 초기화합니다.

### <a name="using-the-initializecorrelation-activity-designer"></a>InitializeCorrelation 활동 디자이너 사용
 **InitializeCorrelation** 활동 디자이너는 **도구 상자**의 **메시징** 범주에 있습니다 .이 범주에 액세스 하려면의 **도구 상자** 탭을 클릭 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 하거나, **보기** 메뉴에서 **도구 모음** 을 선택 하거나, CTRL + ALT + X를 눌러 액세스 합니다.

 **InitializeCorrelation** 활동 디자이너를 **도구 상자** 에서 끌어다 화면에 놓을 수 있습니다 [!INCLUDE[wfd2](../includes/wfd2-md.md)] . 그러면 <xref:System.ServiceModel.Activities.InitializeCorrelation> InitializeCorrelation의 기본값을 사용 하 여 활동이 생성 <xref:System.Activities.Activity.DisplayName%2A> 됩니다. <xref:System.Activities.Activity.DisplayName%2A> **InitializeCorrelation** 활동 디자이너의 머리글 또는 **속성** 창의 **DisplayName** 상자에서을 편집할 수 있습니다.

 는 <xref:System.ServiceModel.Activities.CorrelationHandle> **InitializeCorrelation** Activity designer 화면의 **속성** 창에 있는 **상관 관계** 필드에서 지정할 수 있습니다.

 **속성** 창에서 **CorrelationData** 필드 외에 줄임표 단추를 클릭 하거나 "보기 ..."를 클릭 합니다. **InitializeCorrelation** 활동 디자이너 화면의 힌트 텍스트 상관 관계 **초기화** 대화 상자를 표시 합니다 .이 대화 상자에서 상관 관계 핸들 및이를 초기화 하는 데 사용 되는 키-값 쌍을 지정할 수 있습니다. [!INCLUDE[crabout](../includes/crabout-md.md)] 이 대화 상자를 사용 하 여 [형식 컬렉션 편집기 대화 상자](../workflow-designer/type-collection-editor-dialog-box.md) 항목을 참조 하세요.

### <a name="the-initializecorrelation-properties"></a>InitializeCorrelation 속성
 다음 표에서는 <xref:System.ServiceModel.Activities.InitializeCorrelation> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 **속성** 창이 나 화면에서 편집할 수 있습니다 [!INCLUDE[wfd2](../includes/wfd2-md.md)] .

|속성 이름|필수|사용량|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.InitializeCorrelation> 활동의 이름입니다. 기본값은 InitializeCorrelation입니다.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>에 꼭 기본값 이외의 값을 사용할 필요는 없지만 그런 값을 사용하는 것이 좋습니다.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|상관 관계에서 워크플로 활동을 연결하는 데 사용되는 <xref:System.ServiceModel.Activities.CorrelationHandle>입니다.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|메시지를 워크플로 인스턴스와 연결하는 상관 관계 데이터의 사전입니다.<br /><br /> **상관 관계 초기화** 대화 상자를 사용 하 여를 구성할 수 <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> 있습니다. [!INCLUDE[crabout](../includes/crabout-md.md)] 이 대화 상자를 사용 하 여 [형식 컬렉션 편집기 대화 상자](../workflow-designer/type-collection-editor-dialog-box.md) 항목을 참조 하세요.|

## <a name="see-also"></a>관련 항목
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)