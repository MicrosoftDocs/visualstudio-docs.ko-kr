---
title: UML 클래스 다이어그램 형식의 속성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 6e1ef2d0-d67a-401a-bd64-d5e034decd2c
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9881393e792cf8bf49dc6d0b9459b18969dea171
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671326"
---
# <a name="properties-of-types-on-uml-class-diagrams"></a>UML 클래스 다이어그램 형식의 속성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML 클래스 다이어그램에서 *형식은* 클래스, 인터페이스 또는 열거형입니다.

> [!NOTE]
> 이 항목은 UML 클래스 다이어그램 형식의 속성에 대한 것입니다. 자세한 내용은 다음 항목을 참조하세요.

- [UML 클래스 다이어그램: 참조](../modeling/uml-class-diagrams-reference.md)

- [UML 클래스 다이어그램: 지침](../modeling/uml-class-diagrams-guidelines.md)

- [UML 클래스 다이어그램 특성의 속성](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [UML 클래스 다이어그램 작업의 속성](../modeling/properties-of-operations-on-uml-class-diagrams.md)

- [UML 클래스 다이어그램 연결의 속성](../modeling/properties-of-associations-on-uml-class-diagrams.md)

## <a name="properties"></a>속성
 클래스, 인터페이스 또는 열거형의 속성입니다.

 형식의 속성을 보려면 다이어그램 또는 **UML 모델 탐색기**에서 형식을 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다. 속성은 **속성** 창에 표시 됩니다.

|**속성**|**기본값**|표시 위치|설명|
|------------------|-----------------|----------------|-----------------|
|**이름**|기본 이름|모든 요소|요소를 식별합니다.|
|**정규화된 이름**|패키지 :: 형식 이름 포함|모든 요소|요소를 고유하게 식별합니다. 요소를 포함하는 패키지의 정규화된 이름이 접두사로 추가됩니다.|
|**색상**|해당 종류의 형식에 대한 기본값|모든 요소|이 모양의 색입니다. 다른 속성과 달리 기본 모델 요소의 속성이 아닙니다. 동일한 형식의 다른 뷰는 서로 다른 색을 가질 수 있습니다.|
|**추상**|False|클래스|true이면 클래스를 인스턴스화할 수 없으며, 기본 클래스로 사용됩니다.|
|**리프**|False|클래스, 인터페이스|true이면 형식이 파생 형식을 가질 수 없습니다.|
|**활성 상태**|False|클래스|true이면 이 형식의 각 인스턴스가 컨트롤의 스레드에 연결됩니다.|
|**표시 유형**|공용|클래스, 인터페이스, 열거형|-Public-전역적으로 표시 됩니다.<br />-Private-이 형식은 해당 형식을 소유 하는 패키지 내에 표시 됩니다.<br />-Package-패키지 내에 표시 됩니다.|
|**작업 항목**|0 associated|모든 요소|이 요소와 연결된 작업 항목 수입니다. 작업 항목을 연결 하려면 [모델 요소 및 작업 항목 연결](../modeling/link-model-elements-and-work-items.md)을 참조 하세요.|
|**설명**|(비어 있음)|모든 요소|여기서 항목에 대한 일반적인 메모를 만들 수 있습니다.|
|**템플릿 바인딩**|(없음)|클래스, 인터페이스, 열거형|비어 있지 않은 경우 이 형식은 이 템플릿 클래스에 매개 변수 값을 바인딩하여 정의됩니다. 템플릿 매개 변수의 바인딩을 보려면 속성을 확장합니다.|
|**템플릿 매개 변수**|(없음)|클래스, 인터페이스, 열거형|비어 있지 않은 경우 여기에 나열된 매개 변수를 포함하는 템플릿 클래스입니다. 매개 변수를 추가 하거나 개별 매개 변수의 속성을 보려면 **[...]** 를 클릭 합니다.|

## <a name="see-also"></a>관련 항목
 [Uml 클래스 다이어그램에 대 한 특성 속성 uml](../modeling/properties-of-attributes-on-uml-class-diagrams.md) [클래스 다이어그램 작업의 속성](../modeling/properties-of-operations-on-uml-class-diagrams.md) uml 클래스 다이어그램 [연결의 속성](../modeling/properties-of-associations-on-uml-class-diagrams.md) [uml 클래스 다이어그램: 지침](../modeling/uml-class-diagrams-guidelines.md)
