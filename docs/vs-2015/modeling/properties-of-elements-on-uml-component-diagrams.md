---
title: UML 구성 요소 다이어그램 요소의 속성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.componentdiagram.shapes.properties
helpviewer_keywords:
- component diagrams, properties
- UML, element properties
ms.assetid: fa0a9460-6675-4642-aa00-50f8719a892d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 39350a9e1d340651f8e15de109ecf61eb98996bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671458"
---
# <a name="properties-of-elements-on-uml-component-diagrams"></a>UML 구성 요소 다이어그램 요소의 속성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML 구성 요소 다이어그램에서 다이어그램의 각 요소에는 속성이 있습니다. 요소의 속성을 보려면 다이어그램 또는 **UML 모델 탐색기** 에서 요소를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다. 속성은 **속성** 창에 표시 됩니다.

> [!NOTE]
> 이 항목은 UML 구성 요소 다이어그램 요소의 속성에 대한 것입니다. UML 구성 요소 다이어그램을 읽는 방법에 대 한 자세한 내용은 [Uml 구성 요소 다이어그램: 참조](../modeling/uml-component-diagrams-reference.md)를 참조 하세요. UML 구성 요소 다이어그램을 그리는 방법에 대 한 자세한 내용은 [Uml 구성 요소 다이어그램: 지침](../modeling/uml-component-diagrams-guidelines.md)을 참조 하세요.

## <a name="properties-of-elements"></a>요소의 속성

|속성|기본값|요소|설명|
|--------------|-------------|-------------|-----------------|
|**이름**|기본 이름|모두|요소를 식별합니다.|
|**정규화된 이름**|네임스페이스 :: 이름|모두|요소를 고유하게 식별합니다.<br /><br /> 구성 요소 또는 형식의 이름에는 요소를 포함하는 패키지의 정규화된 이름이 접두사로 추가됩니다.<br /><br /> 파트 또는 포트의 이름에는 요소를 소유하는 구성 요소의 정규화된 이름이 접두사로 추가됩니다.|
|**작업 항목**|0 associated|모두|이 요소와 연결된 작업 항목 수입니다. 작업 항목을 연결 하려면 [모델 요소 및 작업 항목 연결](../modeling/link-model-elements-and-work-items.md)을 참조 하세요.|
|**설명**|(없음)|모두|여기서 요소에 대한 일반적인 메모를 만들 수 있습니다.|
|**색상**|(형식 기본값)|구성 요소, 파트, 위임 및 파트 어셈블리|도형의 색입니다. 다른 속성과 달리, 모양이 표시하는 모델 요소가 아닌 모양의 색입니다.|
|**간접 인스턴스화됨**|True|구성 요소|구성 요소는 디자인 아티팩트로만 존재합니다. 런타임에는 해당 파트만 존재합니다.|
|**추상**|False|구성 요소|구성 요소 정의는 다른 구성 요소가 특수화될 수 있는 일반화로만 사용할 수 있습니다.|
|**표시 유형**|공용|구성 요소, 파트, 포트|**공용** -전역적으로 표시 됩니다.<br /><br /> **Package** -패키지 내에 표시 됩니다.<br /><br /> **Private** -소유 하는 구성 요소 내에 표시 됩니다.<br /><br /> **Protected** -소유자 로부터 파생 된 구성 요소에 표시 됩니다.|
|**유형**|생성 시 형식|부분<br /><br /> 포트|파트 형식은 구성 요소 또는 클래스입니다.<br /><br /> 포트 형식은 인터페이스입니다.|
|**다중성**|1|부분<br /><br /> 포트|부모 구성 요소의 파트를 구성하는 지정된 형식 인스턴스 수를 나타냅니다.<br /><br /> `1` -정확히 한 개<br /><br /> `0..1` -one 또는 none입니다.<br /><br /> `*` -임의의 수의 컬렉션입니다.<br /><br /> `n..m` -n 개에서 m 개의 인스턴스로의 컬렉션입니다.|
|**동작**|False|포트|True이면 이 포트에 대한 메시지는 해당 파트가 아니라 구성 요소 파트로 설명된 동작 또는 작업에 의해 처리됩니다.|
|**서비스**|False|포트|True이면 이 포트는 이 구성 요소의 게시된 인터페이스 파트입니다.|
|**LinkedPackage**|모델|다이어그램|이 다이어그램에 추가된 요소에 대한 기본 네임스페이스입니다.|

## <a name="see-also"></a>관련 항목
 [Uml 사용 사례 다이어그램: 참조](../modeling/uml-use-case-diagrams-reference.md) [Uml 사용 사례 다이어그램: 지침](../modeling/uml-use-case-diagrams-guidelines.md)
