---
title: 워크플로 디자이너 - 활동 디자이너 보내기
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8690d5ccf18c752aacb37a71243d9f591fb9ee30
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395216"
---
# <a name="send-activity-designer"></a>Sent 활동 디자이너

**활동 보내기** 디자이너는 <xref:System.ServiceModel.Activities.Send> 활동을 만들고 구성하는 데 사용됩니다.

## <a name="the-send-activity"></a>Send 활동

 <xref:System.ServiceModel.Activities.Send> 활동은 서비스에 메시지를 보내는 데 사용됩니다. <xref:System.ServiceModel.Activities.ReceiveReply> 활동은 클라이언트측에서 요청/응답 메시지 교환 패턴 중 메시지를 받는 <xref:System.ServiceModel.Activities.Send> 활동에 바인딩될 수 있습니다.

### <a name="using-the-send-activity-designer"></a>Send 활동 디자이너 사용

**도구 상자의** **메시징** 범주에서 **활동 보내기** 디자이너에 액세스합니다. **활동 보내기** 디자이너는 도구 **상자에서** 끌어서 활동이 일반적으로 배치되는 모든 위치에서 워크플로 디자이너 표면으로 놓을 수 있습니다. 그러면 기본 <xref:System.ServiceModel.Activities.Send>인 Send라는 이름의 <xref:System.Activities.Activity.DisplayName%2A> 활동이 만들어집니다. 활동 <xref:System.Activities.Activity.DisplayName%2A> **보내기** 디자이너의 헤더 또는 속성 그리드의 **DisplayName** 상자에서 편집할 수 있습니다.

<xref:System.ServiceModel.Activities.ReceiveReply> 활동을 <xref:System.ServiceModel.Activities.Send> 만들고 선택한 활동에 바인딩하려면 활동 **보내기** 디자이너를 마우스 오른쪽 단추로 클릭하고 컨텍스트 메뉴에서 **ReceiveReply 만들기** 항목을 클릭하고 **ReceiveReplyForSend** 디자이너가 **보내기** 디자이너 아래에 나타납니다. <xref:System.ServiceModel.Activities.ReceiveReply> 활동은 요청/응답 메시지 교환 패턴 중 클라이언트에서 메시지를 받는 활동입니다. **ReceiveReplyForSend** 디자이너로 구성할 수 있습니다.

또는 **도구 상자의** **메시징** 범주에 있는 **SendAndReceiveReply** 템플릿 디자이너를 사용하여 미리 구성된 활동 <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> 및 활동 쌍을 만들 수 있습니다. **SendAndReceiveReply** 및 **ReceiveReplyForSend** 템플릿의 사용에 대한 자세한 내용은 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) 참조 항목을 참조하십시오.

### <a name="the-send-activity-properties"></a>Send 활동 속성

다음 표에서는 <xref:System.ServiceModel.Activities.Send> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 그리드 또는 워크플로 디자이너 표면에서 편집할 수 있습니다.

| 속성 이름 | 필수 | 사용 |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | <xref:System.ServiceModel.Activities.Send> 활동의 이름입니다. 기본값은 Send입니다. <xref:System.Activities.Activity.DisplayName%2A>은 꼭 필요하지 않더라도 사용하는 것이 좋습니다. |
| <xref:System.ServiceModel.Activities.Send.OperationName%2A> | True | 이 <xref:System.ServiceModel.Activities.Send> 활동에 의해 호출되는 서비스 작업의 이름입니다. 이 속성은 **Action** 속성이 명시적으로 설정되지 않은 경우 **Action** 속성의 기본값을 생성하는 데 사용됩니다. |
| <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> | True | 호출할 서비스가 구현하는 서비스 계약의 이름입니다. |
| <xref:System.ServiceModel.Activities.Send.Content%2A> | False | 받을 메시지 또는 매개 변수 콘텐츠를 지정합니다. <xref:System.ServiceModel.Activities.ReceiveMessageContent> 활동이거나 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 활동일 수 있습니다. 속성 표의 **콘텐츠** 필드 옆에 있는 타원 단추를 선택하거나 **활동 받기** 디자이너 표면의 **콘텐츠** 레이블 옆에 있는 **정의 단추를** 클릭하여 이 속성을 편집합니다. 둘 다 **콘텐츠 정의** 대화 상자를 표시합니다. 이 상자를 사용하는 방법에 대한 자세한 내용은 [콘텐츠 정의 대화 상자](../workflow-designer/content-definition-dialog-box.md) 항목을 참조하세요. |
| <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> | False | 메시지를 적절한 워크플로 인스턴스로 라우팅하는 데 사용되는 <xref:System.ServiceModel.Activities.CorrelationHandle>을 지정합니다.<br /><br /> 속성 그리드의 속성 옆에 <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> 있는 타원 단추를 클릭하여 **표현식 편집기** 대화 상자를 엽니다. 이 대화 상자의 사용에 대한 자세한 내용은 [표현식 편집기 사용 방법](../workflow-designer/how-to-use-the-expression-editor.md) 항목을 참조하십시오. |
| <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> | False | 워크플로 내에서 이 <xref:System.ServiceModel.Activities.CorrelationInitializer> 활동을 구성하는 <xref:System.ServiceModel.Activities.CorrelationHandle> 개체를 여러 개 초기화하는 <xref:System.ServiceModel.Activities.Send> 개체 컬렉션을 지정합니다. 속성 그리드의 속성 옆에 <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> 있는 타원 단추를 클릭하여 **상관 관계 초기화자 추가** 대화 상자를 엽니다. 이 상자에 대한 자세한 내용은 [상관 관계 초기화 추가 대화 상자](../workflow-designer/add-correlationinitializers-dialog-box.md) 항목을 참조하십시오. |
| <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> | False | 이 <xref:System.ServiceModel.Activities.Send> 활동으로 호출되는 서비스 작업에 대한 알려진 형식의 컬렉션입니다. 이 속성은 <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>로 설정된 <xref:System.Runtime.Serialization.DataContractSerializer> 속성과 함께 사용해야 합니다. 사용 하는 <xref:System.Xml.Serialization.XmlSerializer> 경우 무시 됩니다.<br /><br /> 속성 표의 **KnownTypes** 필드 옆에 있는 타원 단추를 선택하여 관련 형식을 추가할 수 있는 **유형 컬렉션 편집기** 대화 상자를 표시합니다.<br /><br /> 속성 표의 **KnownTypes** 필드 옆에 있는 타원 단추를 선택하여 관련 형식을 추가할 수 있는 **유형 컬렉션 편집기** 대화 상자를 표시합니다. 이 상자 사용에 대한 자세한 내용은 [형식 컬렉션 편집기 대화 상자](../workflow-designer/type-collection-editor-dialog-box.md) 항목을 참조하십시오. |
| <xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A> | True | 메시지의 <xref:System.Net.Security.ProtectionLevel>을 지정합니다.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> 인증만 을 의미합니다.<br />2. <xref:System.Net.Security.ProtectionLevel> 전송된 데이터의 무결성을 보장하기 위해 서명 데이터를 의미합니다.<br />3. <xref:System.Net.Security.ProtectionLevel> 전송된 데이터의 기밀성과 무결성을 보장하기 위해 데이터를 암호화하고 서명하는 것을 의미합니다. |
| <xref:System.ServiceModel.Activities.Send.SerializerOption%2A> | True | <xref:System.ServiceModel.Activities.Send> 활동으로 호출되는 서비스 작업에 사용할 serializer입니다. 기본값은 <xref:System.Runtime.Serialization.DataContractSerializer>이며, 제공된 데이터 계약을 사용하여 형식 인스턴스를 XML 스트림 또는 문서로 직렬화 및 역직렬화합니다. |
| <xref:System.ServiceModel.Activities.Send.Action%2A> | False | 메시지의 동작 헤더를 지정합니다. 명시적으로 설정되지 않은 경우 해당 값은 `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`기본값을 다음과 같은 값으로 설정합니다. <xref:System.ServiceModel.Activities.Send> 활동에 지정하는 경우 메시지를 받는 <xref:System.ServiceModel.Activities.Receive> 활동에 동일한 값이 있어야 메시지가 올바르게 배달됩니다. |
| <xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A> | | 메시지 수신자에게 허용되는 <xref:System.Security.Principal.TokenImpersonationLevel>입니다. 서버 프로세스가 클라이언트 프로세스를 대신하여 작동할 수 있는 정도를 제어하는 보안 가장 수준을 정의합니다.<xref:System.Security.Principal.TokenImpersonationLevel> 은 가장 수준이 지정되지 않았음을 의미합니다. <xref:System.Security.Principal.TokenImpersonationLevel>은 서버 프로세스가 클라이언트에 대한 식별 정보를 가져올 수 없으며 클라이언트를 가장할 수 없음을 나타냅니다. <xref:System.Security.Principal.TokenImpersonationLevel>은 서버 프로세스가 보안 식별자 및 권한과 같은 클라이언트에 대한 정보를 얻을 수 있지만 클라이언트를 가장할 수는 없음을 나타냅니다. 이 멤버는 테이블 및 뷰를 내보내는 데이터베이스 제품과 같이 자체의 개체를 내보내는 서버에 유용합니다. 서버는 검색된 클라이언트 보안 정보를 사용하여 클라이언트의 보안 컨텍스트를 사용하는 다른 서비스를 사용할 수는 없지만 액세스 위반 결정을 내릴 수 있습니다. <xref:System.Security.Principal.TokenImpersonationLevel>은 서버 프로세스가 로컬 시스템에서 클라이언트의 보안 컨텍스트를 가장할 수 있음을 나타냅니다. 원격 시스템에서는 서버가 클라이언트를 가장할 수 없습니다. <xref:System.Security.Principal.TokenImpersonationLevel>은 서버 프로세스가 원격 시스템에서 클라이언트의 보안 컨텍스트를 가장할 수 있음을 나타냅니다. |
| <xref:System.ServiceModel.Activities.Send.Endpoint%2A> | | <xref:System.ServiceModel.Endpoint> 활동에서 메시지를 보내는 <xref:System.ServiceModel.Activities.Send>입니다. 이 속성이 설정된 <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> 경우 속성은 **null이어야**합니다. |
| <xref:System.ServiceModel.Activities.Send.EndpointAddress%2A> | | 메시지가 전달될 <xref:System.ServiceModel.EndpointAddress>입니다. |
| <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> | | 엔드포인트 구성의 이름입니다. 이 속성은 구성 파일에서 엔드포인트를 구성할 때 설정됩니다. 이 속성은 구성 파일의 ** \<끝점>** 요소에 지정된 이름으로 설정되어야 합니다. 이 속성이 설정된 <xref:System.ServiceModel.Activities.Send.Endpoint%2A> 경우 속성은 **null이어야**합니다. |

## <a name="see-also"></a>참고 항목

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [수신](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)