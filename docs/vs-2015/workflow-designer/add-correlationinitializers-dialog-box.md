---
title: CorrelationInitializers 추가 대화 상자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e1402b90dfc78068546b510ce6b85379b1695f47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672032"
---
# <a name="add-correlationinitializers-dialog-box"></a>상관 관계 이니셜라이저 추가 대화 상자
**상관 관계 이니셜라이저 추가** 대화 상자는에서 [!INCLUDE[wfd1](../includes/wfd1-md.md)] ,, **CorrelationInitializers** <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> 및 <xref:System.ServiceModel.Activities.ReceiveReply> 활동의 CorrelationInitializers 속성을 구성 하는 데 사용 됩니다. [!INCLUDE[crabout](../includes/crabout-md.md)] 이 상자를 사용 하는 activity designer는 [Send](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)및 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) 항목을 참조 하세요.

 이 대화 상자에서 지정한 컬렉션의 상관 관계 이니셜라이저는 쿼리 기반, 컨텍스트, 콜백 컨텍스트 또는 메시징 활동 간의 요청-회신 상관 관계를 초기화할 수 있습니다.

 다음 표에서는 **상관 관계 이니셜라이저 추가** 대화 상자의 UI (사용자 인터페이스) 요소에 대해 설명 합니다.

|UI 요소|설명|
|----------------|-----------------|
|**이니셜라이저 추가**|**초기화 추가** 상자를 클릭 하 여 컬렉션에 이니셜라이저를 추가 합니다.|
|**상관 관계 유형**|상관 관계 이니셜라이저의 형식을 지정합니다. 다음 네 가지 형식 중에서 선택할 수 있습니다.<br /><br /> 1 .를 지정 하는 콜백 상관 관계 이니셜라이저 <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> 입니다.<br />2. 컨텍스트 상관 관계 이니셜라이저를 지정 하 여를 지정 <xref:System.ServiceModel.Activities.CorrelationInitializer> 합니다.<br />3. 요청-회신 상관 관계 이니셜라이저를 지정 하 여를 지정 <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> 합니다.<br />4. 쿼리 상관 관계 이니셜라이저를 지정 하 여를 지정 <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> 합니다.<br /><br /> **CorrelationType** 를 편집 하려면<br /><br /> 1. **Add 이니셜라이저** DataGrid의 특정 행에 대 한 탭입니다.<br />2. Ctrl + Tab을 눌러 포커스를 **눌러 correlationtypecombobox** 로 설정 합니다.<br />3. **콤보 상자** 를 표시 하 고 편집 하려면 Alt + 아래쪽 화살표를 누릅니다.|
|**XPath 쿼리**|들어오는 메시지와 나가는 메시지에서 상관 관계 데이터를 추출하는 데 사용되는 쿼리가 포함된 키/값 쌍입니다. 이 목록은 <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> 형식을 사용하는 경우에만 유효합니다.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>상관 관계 이니셜라이저 추가 대화 상자를 시작하려면
 **상관 관계 이니셜라이저 추가** 대화 상자는 **Send**, **Receive**, **ReceiveAndSendReply**및 **SendAndReceiveReply** 디자이너에서 사용 됩니다. 이러한 항목에 액세스 하는 것은 각 사례에서 유사 하며 **수신** 디자이너를 포함 하는 사례에서 절차를 설명 하는 데 사용 됩니다.

 **Receive** 활동 디자이너를 **도구 상자** 에서 끌어다가 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 일반적으로 활동을 배치 하는 화면의 아무 곳에 나 놓을 수 있습니다. 그러면 기본 <xref:System.ServiceModel.Activities.Receive>인 Receive라는 이름의 <xref:System.Activities.Activity.DisplayName%2A> 활동이 만들어집니다. **Receive** 활동 디자이너를 선택 하 고 속성 표에서 **CorrelationInitializers** 속성의 (컬렉션) 텍스트 옆에 있는 줄임표 단추를 클릭 하 여 **상관 관계 이니셜라이저 추가** 대화 상자를 표시 합니다.

## <a name="see-also"></a>관련 항목
 [상관 관계 초기화 대화 상자](../workflow-designer/initialize-correlation-dialog-box.md)