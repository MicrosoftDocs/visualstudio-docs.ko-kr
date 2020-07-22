---
title: 워크플로 디자이너 InitializeCorrelation 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aadb526e50351c8344c8b265dca3364637d1ff0c
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86875568"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation 활동 디자이너

**InitializeCorrelation** 활동 디자이너는 활동을 만들고 구성 하는 데 사용 됩니다 <xref:System.ServiceModel.Activities.InitializeCorrelation> . <xref:System.ServiceModel.Activities.InitializeCorrelation>활동은 메시지를 보내거나 받기 전에 메시지 간의 상관 관계를 설정 합니다.

## <a name="the-initializecorrelation-activity"></a>InitializeCorrelation 활동

<xref:System.ServiceModel.Activities.InitializeCorrelation> 활동은 메시지를 보내거나 받지 않고 상관 관계를 초기화하는 데 사용됩니다. 일반적으로 상관 관계는 메시지를 보내거나 받을 때 초기화됩니다. 메시지를 보내거나 받기 전에 상관 관계를 설정해야 하는 경우 <xref:System.ServiceModel.Activities.InitializeCorrelation>을 사용하여 상관 관계를 초기화합니다.

### <a name="using-the-initializecorrelation-activity-designer"></a>InitializeCorrelation 활동 디자이너 사용

**도구 상자**의 **메시징** 범주에서 **InitializeCorrelation** 활동 디자이너에 액세스 합니다.

**InitializeCorrelation** 활동 디자이너를 **도구 상자** 에서 끌어서 워크플로 디자이너 화면에 놓을 수 있습니다. 활동 디자이너를 삭제 하면 <xref:System.ServiceModel.Activities.InitializeCorrelation> InitializeCorrelation의 기본이 포함 된 활동이 만들어집니다 <xref:System.Activities.Activity.DisplayName%2A> . <xref:System.Activities.Activity.DisplayName%2A> **InitializeCorrelation** 활동 디자이너의 머리글 또는 **속성** 창의 **DisplayName** 상자에서을 편집할 수 있습니다.

는 <xref:System.ServiceModel.Activities.CorrelationHandle> **InitializeCorrelation** Activity designer 화면의 **속성** 창에 있는 **상관 관계** 필드에서 지정할 수 있습니다.

상관 관계 **초기화** 대화 상자를 표시 하려면 상관 관계 핸들 및이를 초기화 하는 데 사용 되는 키-값 쌍을 지정할 수 있습니다. 그런 다음 **속성** 창에서 **CorrelationData** 필드 옆에 있는 줄임표 단추를 선택 합니다. 또는 "보기 ..."를 선택 합니다. **InitializeCorrelation** activity designer 화면의 힌트 텍스트입니다. 이 대화 상자를 사용 하는 방법에 대 한 자세한 내용은 [형식 컬렉션 편집기 대화 상자](../workflow-designer/type-collection-editor-dialog-box.md) 문서를 참조 하세요.

### <a name="the-initializecorrelation-properties"></a>InitializeCorrelation 속성

다음 표에서는 속성을 보여 주고 <xref:System.ServiceModel.Activities.InitializeCorrelation> 디자이너에서 이러한 속성을 사용 하는 방법을 설명 합니다. 이러한 속성은 **속성** 창이 나 워크플로 디자이너 화면에서 편집할 수 있습니다.

|속성 이름|필수|사용량|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|거짓|<xref:System.ServiceModel.Activities.InitializeCorrelation> 활동의 이름입니다. 기본값은 InitializeCorrelation입니다.<br /><br /> 친숙 한에 기본값이 아닌 값을 사용 하는 것은 반드시 필요한 것은 아니지만 <xref:System.Activities.Activity.DisplayName%2A> 권장 됩니다.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|거짓|상관 관계에서 워크플로 활동을 연결하는 데 사용되는 <xref:System.ServiceModel.Activities.CorrelationHandle>입니다.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|거짓|메시지를 워크플로 인스턴스와 연결하는 상관 관계 데이터의 사전입니다.<br /><br /> **상관 관계 초기화** 대화 상자를 사용 하 여를 구성할 수 <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> 있습니다. 이 대화 상자 사용에 대 한 자세한 내용은 [형식 컬렉션 편집기 대화 상자](../workflow-designer/type-collection-editor-dialog-box.md) 문서를 참조 하세요.|

## <a name="see-also"></a>추가 정보

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [받습니다](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [보내기](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)