---
title: UML 사용 사례 다이어그램 요소의 속성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties
- vs.teamarch.usecasediagram.shapes.properties
helpviewer_keywords:
- use case diagrams, properties
ms.assetid: 2728fb26-a275-4fce-8a2c-5a78af6bee04
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: db3dc649d979c87960a42d38ffa211e352be175b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671408"
---
# <a name="properties-of-elements-on-uml-use-case-diagrams"></a>UML 사용 사례 다이어그램 요소의 속성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML 사용 사례 다이어그램에서 다이어그램의 각 요소에는 속성이 있습니다. 요소의 속성을 보려면 다이어그램 또는 **UML 모델 탐색기** 에서 요소를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다. 속성은 **속성** 창에 표시 됩니다.

> [!NOTE]
> 이 항목은 UML 사용 사례 다이어그램 요소의 속성에 대한 것입니다. UML 동작 다이어그램을 읽는 방법에 대 한 자세한 내용은 [Uml 사용 사례 다이어그램: 참조](../modeling/uml-use-case-diagrams-reference.md)를 참조 하세요. UML 동작 다이어그램을 그리는 방법에 대 한 자세한 내용은 [Uml 사용 사례 다이어그램: 지침](../modeling/uml-use-case-diagrams-guidelines.md)을 참조 하세요.

## <a name="properties-of-elements"></a>요소의 속성

|속성|기본값|요소|설명|
|--------------|-------------|-------------|-----------------|
|**이름**|기본 이름|모두|요소를 식별합니다.|
|**정규화된 이름**|패키지 :: 이름|모두|요소를 고유하게 식별합니다. 요소를 포함하는 패키지의 정규화된 이름이 접두사로 추가됩니다.|
|**작업 항목**|0 associated|모두|이 요소와 연결된 작업 항목 수입니다. 작업 항목을 연결 하려면 [모델 요소 및 작업 항목 연결](../modeling/link-model-elements-and-work-items.md)을 참조 하세요.|
|**설명**|(없음)|모두|여기서 요소에 대한 일반적인 메모를 만들 수 있습니다.|
|**색상**|(기본값)|모두|도형의 색입니다. 다른 속성과 달리, 모양이 표시하는 요소의 속성이 아닙니다.|
|**이미지 경로**|(없음)|행위자|기본 행위자 아이콘 대신 사용해야 하는 이미지의 파일 경로입니다. 아이콘은 Visual Studio 프로젝트 내의 리소스 파일이어야 합니다.|
|**제목**|(없음)|사용 사례|사용 사례를 소유하는 하위 시스템 또는 다른 형식입니다.<br /><br /> 다이어그램의 하위 시스템에 사용 사례를 배치하여 설정할 수 있습니다.|
|**표시 유형**|공용|사용 사례, 행위자, 하위 시스템|**공용** -전역적으로 표시 됩니다.<br /><br /> **Package** -패키지 내에 표시 됩니다.|
|**IsAbstract**|False|사용 사례, 행위자, 하위 시스템|true이면 형식을 인스턴스화할 수 없으며, 다른 정의에서 특수화 기초로 사용됩니다.|
|**간접 인스턴스화됨**|True|하위 시스템|하위 시스템이 디자인 아티팩트로만 존재합니다. 런타임에는 해당 파트만 존재합니다.|
|**하이퍼링크**|(없음)|아티팩트|아티팩트가 링크를 제공하는 다이어그램 또는 문서의 URL 또는 파일 경로입니다.|

 연결 속성 목록은 [UML 클래스 다이어그램 연결의 속성](../modeling/properties-of-associations-on-uml-class-diagrams.md)을 참조 하세요.

## <a name="see-also"></a>관련 항목
 [Uml 사용 사례 다이어그램: 참조](../modeling/uml-use-case-diagrams-reference.md) [Uml 사용 사례 다이어그램: 지침](../modeling/uml-use-case-diagrams-guidelines.md)
