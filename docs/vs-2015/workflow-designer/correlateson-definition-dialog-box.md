---
title: CorrelatesOn 정의 대화 상자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e2a9a6f7ec6b8bf246ebfc03c166780b229e1aee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656946"
---
# <a name="correlateson-definition-dialog-box"></a>CorrelatesOn 정의 대화 상자
**CorrelatesOn** 대화 상자는에서 [!INCLUDE[wfd1](../includes/wfd1-md.md)] <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> 활동의 속성을 편집 하는 데 사용 됩니다 <xref:System.ServiceModel.Activities.Receive> . [!INCLUDE[crdefault](../includes/crdefault-md.md)][수신](../workflow-designer/receive-activity-designer.md) 항목입니다.

 <xref:System.ServiceModel.Activities.Receive> 활동 간의 상관 관계는 워크플로에서 서비스 작업 간의 다양한 상호 연결 방식을 지정합니다.

 다음 표에서는 **CorrelatesOn** 대화 상자의 UI (사용자 인터페이스) 요소에 대해 설명 합니다.

|UI 요소|설명|
|----------------|-----------------|
|**CorrelatesWith**|메시지를 적절한 워크플로 인스턴스로 라우팅하는 데 사용되는 <xref:System.ServiceModel.Activities.CorrelationHandle>입니다.|
|**XPath 쿼리**|받은 메시지에서 상관 관계 데이터를 추출하는 데 사용되는 쿼리가 포함된 키/값 쌍입니다. 이것은 <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> 속성에 해당합니다. XPath 쿼리는 <xref:System.ServiceModel.MessageQuerySet> 개체에 포함되어 있습니다.|

## <a name="to-launch-the-correlateson-dialog-box"></a>CorrelatesOn 대화 상자를 시작하려면
 **Receive** 활동 디자이너를 **도구 상자** 에서 끌어다가 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 일반적으로 활동을 배치 하는 화면의 아무 곳에 나 놓을 수 있습니다. 그러면 기본 <xref:System.ServiceModel.Activities.Receive>인 Receive라는 이름의 <xref:System.Activities.Activity.DisplayName%2A> 활동이 만들어집니다. **Receive** 활동 디자이너를 선택 하 고 속성 표에서 **CorrelatesOn** 속성의 (컬렉션) 텍스트 옆에 있는 줄임표 단추를 클릭 하 여 **CorrelatesOn 정의** 대화 상자를 표시 합니다.

## <a name="see-also"></a>관련 항목
 <xref:System.ServiceModel.Activities.Receive>[CorrelationInitializers 추가 대화 상자](../workflow-designer/add-correlationinitializers-dialog-box.md) [상관 관계 초기화 대화 상자](../workflow-designer/initialize-correlation-dialog-box.md)