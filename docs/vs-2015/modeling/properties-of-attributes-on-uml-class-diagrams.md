---
title: UML 클래스 다이어그램 특성의 속성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.attribute.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: ba01e064-7424-4e72-98fa-42fa1c30e153
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: de32eba5fc6e4afc21d62f4432d9317d85408ffd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652060"
---
# <a name="properties-of-attributes-on-uml-class-diagrams"></a>UML 클래스 다이어그램 특성의 속성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML 클래스 다이어그램에서 클래스 및 인터페이스에 *특성* 을 추가할 수 있습니다. 특성은 클래스 또는 인터페이스의 인스턴스에 연결할 수 있는 값을 정의합니다.

 특성을 추가하려면 클래스 또는 인터페이스를 마우스 오른쪽 단추로 클릭하고 **추가**를 가리키고 **특성**을 클릭합니다.

 다이어그램에 클래스 특성이 표시되지 않으면 클래스 또는 인터페이스 위쪽에서 펼침 단추를 클릭하여 확장합니다. **특성** 머리글이 표시되면 **[+]** 를 클릭하여 특성 섹션을 확장합니다.

## <a name="signature-of-an-attribute"></a>특성 서명
 특성 서명은 UML 클래스 다이어그램의 클래스 또는 인터페이스에서 서명을 나타내는 선입니다. 형식은 다음과 같습니다.

```
+ AttributeName : TypeName [*]
```

 \+ 공용 표시 여부를 나타냅니다. 기타 허용되는 값은 -(private), #(protected), ~(package)입니다.

 특성이 static이면 `AttributeName`에 밑줄이 표시됩니다.

 특성에 형식이 없으면 `: TypeName`이 생략됩니다.

 `[*]`는 복합성을 나타냅니다. 복합성이 1이면 생략됩니다.

## <a name="properties"></a>속성
 다음 표에서는 UML 클래스 다이어그램의 클래스 또는 인터페이스에 있는 특성의 속성을 설명합니다.

 특성의 속성을 확인하려면 다이어그램의 클래스 또는 인터페이스에서 특성을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다. 속성은 속성 창에 나타납니다.

 특성의 속성을 보려면 해당 특성을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.

|   **속성**    | **기본값**  |                                                                                                                                                                                                         설명                                                                                                                                                                                                          |
|-------------------|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **기본값** |   (비어 있음)    |                                                                                                                                                                               분류자가 인스턴스화될 때 특성의 값입니다.                                                                                                                                                                                |
| **읽기 전용**  |    False     |                                                                                                                                                                                    true이면 특성 값을 변경할 수 없습니다.                                                                                                                                                                                    |
|   **정적**   |    False     |                                                                                                                    true이면 이 특성의 단일 값이 이 형식의 모든 인스턴스 간에 공유됩니다.<br /><br /> true이면 다이어그램에서 특성 이름에 밑줄이 추가됩니다.                                                                                                                    |
|     **이름**      | (새 이름) |                                                                                                                                                                                        소유하는 분류자 내에서 고유해야 합니다.                                                                                                                                                                                        |
|     **유형**      |    (없음)    |                                                **Integer**와 같은 기본 형식 또는 모델에서 정의된 형식입니다. 값을 메타데이터로 인코딩해야 하므로 **10진수** 와 같이 기본이 아닌 형식은 사용할 수 없습니다. 이 속성에 새 형식의 이름을 입력하면 형식이 UML 모델 탐색기의 **지정되지 않은 형식** 섹션에 추가됩니다.                                                 |
|  **표시 유형**   |    공용    |                                     허용되는 값 및 서명에 나타나는 문자는 다음과 같습니다.<br /><br /> **+ Public** - 전체적으로 표시됩니다.<br /><br /> **- Private** - 소유하는 형식 외부에 표시되지 않습니다.<br /><br /> **# Protected** - 소유자로부터 파생된 형식에 표시됩니다.<br /><br /> **~ Package** - 같은 패키지 내의 다른 형식에 표시됩니다.                                      |
|  **작업 항목**   | 0 associated |                                                                                                                          연결된 작업 항목 개수입니다. 읽기 전용입니다.<br /><br /> 자세한 내용은 [모델 요소 및 작업 항목 연결](../modeling/link-model-elements-and-work-items.md)을 참조 하세요.                                                                                                                           |
|    **리프**    |    False     |                                                                                                                                                                    true이면 이 형식을 파생된 형식으로 다시 정의할 수 없습니다.                                                                                                                                                                     |
|  **파생**   |    False     |                                                                                                              true이면 이 특성이 다른 특성에서 계산됩니다. 예를 들어 대각선은 너비 및 높이에서 계산됩니다. **설명** 또는 연결된 주석에서 세부 정보를 작성해야 합니다.                                                                                                              |
|  **설명**  |   (비어 있음)    |                                                                                                                                                                        일반 참고 사항에 사용되거나 특성 값에 대한 제약 조건을 정의하는 데 사용됩니다.                                                                                                                                                                        |
| **다중성**  |      1       | **1** - 이 특성에는 지정된 형식의 단일 값이 포함됩니다.<br /><br /> **0..1** - 이 특성에는 `null`값이 포함될 수 있습니다.<br /><br /> **\\**\* -이 특성 값은 값의 컬렉션입니다.<br /><br /> **1.. \\ ** \* -이 특성의 값은 하나 이상의 값을 포함 하는 컬렉션입니다.<br /><br /> *n* **..** *m* - 이 특성 값은 *n* ~ *m* 개 값이 포함된 컬렉션입니다. |
|  **순서 지정됨**   |    False     |                                                                                                                                                                    true이면 컬렉션이 순차적 목록을 구성합니다. 두 개 이상의 **복합성** 에 사용됩니다.                                                                                                                                                                     |
|   **고유**   |    False     |                                                                                                                                                                true이면 컬렉션에 중복 값이 없습니다. 두 개 이상의 **복합성** 에 사용됩니다.                                                                                                                                                                |

## <a name="see-also"></a>관련 항목
 [Uml 클래스 다이어그램:](../modeling/uml-class-diagrams-reference.md) [uml 클래스 다이어그램 형식의 참조 속성](../modeling/properties-of-types-on-uml-class-diagrams.md) uml 클래스 다이어그램 [작업의 속성](../modeling/properties-of-operations-on-uml-class-diagrams.md) [Uml 클래스 다이어그램: 지침](../modeling/uml-class-diagrams-guidelines.md) [uml 클래스 다이어그램:](../modeling/uml-class-diagrams-guidelines.md) 지침
