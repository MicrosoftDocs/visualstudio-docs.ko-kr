---
title: 워크플로 디자이너 Receive 활동 디자이너
description: Receive 활동 디자이너를 사용 하 여 receive 활동을 만들고 구성 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Receive.UI
ms.assetid: f58d3c70-944d-4bb4-90a7-e68c103caddc
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ceff7d40ffd0d7c961f07dd65a8070a8f11a1b4b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899383"
---
# <a name="receive-activity-designer"></a>Receive 활동 디자이너

**Receive** 활동 디자이너는 활동을 만들고 구성 하는 데 사용 됩니다 <xref:System.ServiceModel.Activities.Receive> . <xref:System.ServiceModel.Activities.Receive> 활동은 기본 제공 형식(예:  <xref:System.ServiceModel.Channels.Message>, <xref:System.IO.Stream> 또는 <xref:System.Xml.Linq.XElement>)이거나 serialize될 수 있는 애플리케이션 정의 데이터 계약, 메시지 계약 또는 XML 클래스 중 하나인 메시지를 수신하는 활동입니다.

## <a name="the-receive-activity"></a>Receive 활동

<xref:System.ServiceModel.Activities.Receive>활동은 사용 되는 수신 콘텐츠 유형에 따라 단일 항목 또는 여러 항목을 받을 수 있습니다. <xref:System.ServiceModel.Activities.SendReply> 활동은 서비스에 대한 요청/응답 메시지 교환 패턴 중 메시지를 받는 <xref:System.ServiceModel.Activities.Receive> 활동에 바인딩될 수 있습니다.

### <a name="using-the-receive-activity-designer"></a>Receive 활동 디자이너 사용

**도구 상자** 의 **메시징** 범주에서 **Receive** 활동 디자이너에 액세스 합니다. **Receive** 활동 디자이너를 **도구 상자** 에서 끌어다가 일반적으로 활동을 배치 하는 워크플로 디자이너 화면에 놓을 수 있습니다. 그러면 기본 <xref:System.ServiceModel.Activities.Receive>인 Receive라는 이름의 <xref:System.Activities.Activity.DisplayName%2A> 활동이 만들어집니다. <xref:System.Activities.Activity.DisplayName%2A> **Receive** 활동 디자이너의 머리글 또는 속성 표의 **DisplayName** 상자에서을 편집할 수 있습니다.

활동을 만들고 <xref:System.ServiceModel.Activities.SendReply> 선택한 활동에 바인딩하려면 <xref:System.ServiceModel.Activities.Receive> **receive** 활동 디자이너를 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 **SendReply 항목 만들기** 를 클릭 합니다. 그러면 **SendReplyToReceive** 디자이너가 **수신** 디자이너 아래에 나타납니다. <xref:System.ServiceModel.Activities.SendReply> 활동은 서비스측에 대한 요청/응답 메시지 교환 패턴 중 응답 메시지를 보내는 활동입니다. **SendReplyToReceive** designer를 사용 하 여 구성할 수 있습니다.

또는 **도구 상자** 의 **메시징** 범주에 있는 **ReceiveAndSendReply** 템플릿 디자이너를 사용 하 여 미리 구성 된 및 활동 쌍을 만들 수 <xref:System.ServiceModel.Activities.Receive> 있습니다 <xref:System.ServiceModel.Activities.SendReply> . **ReceiveAndSendReply** 및 **SendReplyToReceive** 템플릿 사용에 대 한 자세한 내용은 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) 항목을 참조 하세요.

### <a name="the-receive-activity-properties"></a>Receive 활동 속성

다음 표에서는 <xref:System.ServiceModel.Activities.Receive> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표 또는 워크플로 디자이너 화면에서 편집할 수 있습니다. 필수 속성은 <xref:System.ServiceModel.Activities.Receive.OperationName%2A> 속성뿐입니다.

| 속성 이름 | 필수 | 사용량 |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | <xref:System.ServiceModel.Activities.Receive> 활동의 이름을 지정합니다. 기본값은 Receive입니다.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>에 꼭 기본값 이외의 값을 사용할 필요는 없지만 그런 값을 사용하는 것이 좋습니다. |
| <xref:System.ServiceModel.Activities.Receive.OperationName%2A> | True | 이 <xref:System.ServiceModel.Activities.Receive> 활동에 의해 구현되는 서비스 작업의 이름을 지정합니다. **작업** 속성이 명시적으로 설정 되지 않은 경우이 속성은 **작업** 속성의 기본값을 생성 하는 데 사용 됩니다. |
| <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> | False | 서비스 계약의 이름을 지정합니다. 이 속성은 서비스 작업을 개별 서비스 계약으로 그룹화 하는 데 사용 됩니다. 동일한 <xref:System.ServiceModel.Activities.Receive>을 가진 모든 <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> 활동은 동일한 서비스 계약(WSDL 포트 형식)으로 그룹화됩니다. 기본값은 최상위 (루트) 활동의 정규화 된 CLR 이름입니다. |
| <xref:System.ServiceModel.Activities.Receive.Content%2A> | False | 받을 메시지 또는 매개 변수 콘텐츠를 지정합니다. <xref:System.ServiceModel.Activities.ReceiveMessageContent> 활동이거나 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 활동일 수 있습니다. 속성 표에서 **콘텐츠** 필드 옆에 있는 줄임표 단추를 선택 하거나 **Receive** Activity designer 화면에서 **콘텐츠** 레이블 옆에 있는 **정의 ...** 단추를 클릭 하 여이 속성을 편집 합니다. 둘 다 **콘텐츠 정의** 대화 상자를 표시 합니다. 이 상자를 사용 하는 방법에 대 한 자세한 내용은 [콘텐츠 정의 대화 상자](../workflow-designer/content-definition-dialog-box.md) 항목을 참조 하세요. |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> | False | <xref:System.ServiceModel.Activities.Receive> 개체가 있는 워크플로의 서비스 작업에 포함된 <xref:System.ServiceModel.MessageQuerySet> 활동 간의 상관 관계를 지정합니다. 속성 표에서 속성 옆의 줄임표 단추를 클릭 <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> 하 여 **CorrelatesOn 정의** 대화 상자를 엽니다. 이 대화 상자를 사용 하는 방법에 대 한 자세한 내용은 [콘텐츠 정의 대화 상자](../workflow-designer/content-definition-dialog-box.md) 항목을 참조 하세요. |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> | False | 메시지를 적절한 워크플로 인스턴스로 라우팅하는 데 사용되는 <xref:System.ServiceModel.Activities.CorrelationHandle>을 지정합니다.<br /><br /> 속성 표에서 속성 옆의 줄임표 단추를 클릭 <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> 하 여 **식 편집기** 대화 상자를 엽니다. 이 대화 상자를 사용 하는 방법에 대 한 자세한 내용은 [방법: 식 편집기 사용](../workflow-designer/how-to-use-the-expression-editor.md) 항목을 참조 하세요. |
| <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> | False | 워크플로 내에서 이 <xref:System.ServiceModel.Activities.CorrelationInitializer> 활동을 구성하는 <xref:System.ServiceModel.Activities.CorrelationHandle> 개체를 여러 개 초기화하는 <xref:System.ServiceModel.Activities.Receive> 개체 컬렉션을 지정합니다. 속성 표에서 속성 옆의 줄임표 단추를 클릭 <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> 하 여 **상관 관계 이니셜라이저 추가** 대화 상자를 엽니다. 이 상자를 사용 하는 방법에 대 한 자세한 내용은 [CorrelationInitializers 추가 대화 상자](../workflow-designer/add-correlationinitializers-dialog-box.md) 항목을 참조 하세요. |
| <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> | False | 메시지가 기존 워크플로 인스턴스와 연관되지 않은 경우 메시지를 처리하기 위해 새 워크플로 인스턴스를 만들지 여부를 결정하는 값을 지정합니다. 값을 **true** 로 설정 하면 메시지가 기존 워크플로 인스턴스와 연관 되지 않은 경우 메시지를 처리 하기 위해 새 워크플로 인스턴스가 만들어집니다. |
| <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> | False | 이 <xref:System.ServiceModel.Activities.Receive> 활동에 의해 구현되는 서비스 작업의 알려진 형식 컬렉션을 지정합니다. 이 속성은 <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>로 설정된 <xref:System.Runtime.Serialization.DataContractSerializer> 속성과 함께 사용해야 합니다. 을 사용 하는 경우 무시 됩니다 <xref:System.Xml.Serialization.XmlSerializer> .<br /><br /> 속성 표의 **Knowntypes** 필드 옆에 있는 줄임표 단추를 선택 하 여 관련 형식을 추가할 수 있는 **형식 컬렉션 편집기** 대화 상자를 표시 합니다. 이 상자를 사용 하는 방법에 대 한 자세한 내용은 [형식 컬렉션 편집기 대화 상자](../workflow-designer/type-collection-editor-dialog-box.md) 항목을 참조 하세요. |
| <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A> | False | 메시지의 <xref:System.Net.Security.ProtectionLevel>을 지정합니다.<br /><br /> 1.  <xref:System.Net.Security.ProtectionLevel> 인증만을 의미 합니다.<br />2.  <xref:System.Net.Security.ProtectionLevel> 전송 된 데이터의 무결성을 보장 하기 위해 데이터에 서명 하는 것을 의미 합니다.<br />3.  <xref:System.Net.Security.ProtectionLevel> 전송 된 데이터의 기밀성 및 무결성을 보장 하기 위해 데이터를 암호화 하 고 서명 하는 것을 의미 합니다. |
| <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> | False | <xref:System.ServiceModel.Activities.Receive> 활동에 의해 구현되는 서비스 작업에 사용할 serializer의 형식을 지정합니다. 기본값은 <xref:System.Runtime.Serialization.DataContractSerializer>이며, 제공된 데이터 계약을 사용하는 XML 스트림 또는 문서에 형식 인스턴스를 직렬화 및 역직렬화합니다. XML에 대한 제어를 강화해야 하는 경우에도 <xref:System.Xml.Serialization.XmlSerializer>를 사용할 수 있습니다. |
| <xref:System.ServiceModel.Activities.Receive.Action%2A> | False | 메시지의 동작 헤더를 지정합니다. 명시적으로 설정 되지 않은 경우 해당 값의 기본값은 `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` 입니다. |

## <a name="see-also"></a>참고 항목

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [보내기](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)
