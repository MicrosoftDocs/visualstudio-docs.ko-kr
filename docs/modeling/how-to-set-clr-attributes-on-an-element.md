---
title: '방법: 요소에 CLR 특성 설정'
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ebda963bf1afa55fa8d7f98774c72a75d242ceef
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85532459"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>방법: 요소에 CLR 특성 설정
사용자 지정 특성은 도메인 요소, 도형, 연결선 및 다이어그램에 추가할 수 있는 특수 한 특성입니다. 클래스에서 상속 되는 특성을 추가할 수 있습니다 `System.Attribute` .

### <a name="to-add-a-custom-attribute"></a>사용자 지정 특성을 추가 하려면

1. **DSL 탐색기**에서 사용자 지정 특성을 추가 하려는 요소를 선택 합니다.

2. **속성** 창에서 **사용자 지정 특성** 속성 옆에 있는 찾아보기 (**...**) 아이콘을 클릭 합니다.

     **특성 편집** 대화 상자가 열립니다.

3. **이름** 열에서을 클릭 **\<add attribute>** 하 고 특성의 이름을 입력 합니다. Enter 키를 누릅니다.

4. 특성 이름 아래의 줄에 괄호가 표시 됩니다. 이 줄에서 특성에 대 한 매개 변수 형식 (예:)을 입력 한 `string` 다음 enter 키를 누릅니다.

5. **이름 속성** 열에 적절 한 이름 (예:)을 입력 `MyString` 합니다.

6. **확인**을 클릭합니다.

     이제 **사용자 지정 특성** 속성이 다음 형식으로 특성을 표시 합니다.

     `[`*AttributeName* `(` *ParameterName* `=` *유형*`)]`

## <a name="see-also"></a>참고 항목

- [도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)