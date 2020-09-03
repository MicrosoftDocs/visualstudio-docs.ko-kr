---
title: UML 시퀀스 다이어그램 요소의 속성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.properties
- vs.teamarch.sequencediagram.shapes.properties
helpviewer_keywords:
- UML sequence diagrams, properties
- sequence diagrams, properties
ms.assetid: 475c10f3-a2d2-4a1e-b366-dc28997d437e
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4d0753ea7396c9f21addcbb01ab7b90be066356a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671420"
---
# <a name="properties-of-elements-on-uml-sequence-diagrams"></a>UML 시퀀스 다이어그램 요소의 속성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML 시퀀스 다이어그램에서 다이어그램의 각 요소에는 속성이 있습니다. 요소의 속성을 보려면 다이어그램 또는 **UML 모델 탐색기** 에서 요소를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다. 속성은 **속성** 창에 표시 됩니다.

> [!NOTE]
> 이 항목은 UML 시퀀스 다이어그램 요소의 속성에 대한 것입니다. UML 시퀀스 다이어그램을 읽는 방법에 대 한 자세한 내용은 [Uml 시퀀스 다이어그램: 참조](../modeling/uml-sequence-diagrams-reference.md)를 참조 하세요. UML 시퀀스 다이어그램을 그리는 방법에 대한 자세한 내용은 [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md)을 참조하세요.

## <a name="properties-of-elements"></a>요소의 속성

|속성|기본값|요소|설명|
|--------------|-------------|-------------|-----------------|
|**이름**|기본 이름|모두|요소를 식별합니다.|
|**정규화된 이름**|패키지 :: 이름|모두|요소를 고유하게 식별합니다. 요소를 포함하는 패키지의 정규화된 이름이 접두사로 추가됩니다.|
|**작업 항목**|0 associated|모두|이 요소와 연결된 작업 항목 수입니다. 작업 항목을 연결 하려면 [모델 요소 및 작업 항목 연결](../modeling/link-model-elements-and-work-items.md)을 참조 하세요.|
|**설명**|(비어 있음)|모두|여기서 항목에 대한 일반적인 메모를 만들 수 있습니다.|
|**색상**|(요소 형식에 대한 기본값)|수명선, 메시지|도형의 색입니다. 이 속성은 모양이 표시하는 요소가 아니라 모양의 속성입니다.|
|**유형**|(비어 있음)|수명선|수명선이 나타내는 인스턴스 형식입니다.<br /><br /> 수명선의 머리글에 표시되는 참조 기호가 있는 경우 이 클래스 또는 인터페이스가 UML 모델 탐색기에 별도로 존재하며 클래스 다이어그램에 표시될 수 있습니다.|
|**배우**|False|수명선|수명선이 다이어그램과 관련된 구성 요소 외부에 있는 사용자, 디바이스 또는 소프트웨어 구성 요소를 나타내는지 여부를 표시합니다.|
|**종류**|**Complete** -발신자와 수신자가 모두 있는 메시지입니다.<br /><br /> **Found** -지정 되지 않은 보낸 사람이 있는 메시지입니다.<br /><br /> **손실** -수신기가 지정 되지 않은 메시지입니다.|메시지|수명선에 연결된 메시지의 끝을 나타냅니다.<br /><br /> 이 속성은 변경할 수 없습니다. 메시지를 만들 때 설정됩니다.|
|**Sort**|**AsynchCall** -비동기 메시지입니다.<br /><br /> **SynchCall** -동기 메시지입니다.<br /><br /> **Reply** -동기 메시지의 반환 부분입니다.<br /><br /> **CreateMessage** -인스턴스 생성 메시지입니다.|메시지|메시지의 형식입니다. 이 속성은 변경할 수 없습니다. 메시지를 만드는 데 사용하는 도구에 의해 결정됩니다.|
|**연산**|(비어 있음)|메시지|받는 수명선에서 메시지에 의해 호출되는 메서드입니다.<br /><br /> 받는 수명선이 인터페이스 또는 클래스에 연결된 경우에만 표시됩니다.|
|**참조 대상**|시퀀스 다이어그램|상호 작용 사용|이 상호 작용 사용에서 호출되는 시퀀스 다이어그램입니다.|
|**상호 작용 연산자**|**코드 감싸기** 명령을 사용 하는 경우 설정|결합 조각|이 조각 또는 조각 컬렉션이 나타내는 연산자입니다.|
|**호위**|(비어 있음)|결합 조각의 상호 작용 피연산자|가드가 true가 아니면 조각의 시퀀스가 발생하지 않습니다.<br /><br /> 결합된 조각의 최상위 조각을 선택하려면 조각 제목 아래를 클릭합니다.|
|**최소, 최대**|(제한 없음)|루프 결합 조각|루프가 실행되는 최소 및 최대 횟수입니다.|
|**메시지**|(비어 있음)|결합 조각 고려 및<br /><br /> 무시|이 조각에서 고려되거나 무시되는 메시지입니다.|

## <a name="see-also"></a>관련 항목
 [Uml 시퀀스 다이어그램: 참조](../modeling/uml-sequence-diagrams-reference.md) [uml 시퀀스 다이어그램: 지침은](../modeling/uml-sequence-diagrams-guidelines.md) [uml 시퀀스 다이어그램의 조각으로 제어 흐름을 설명](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md) 합니다.
