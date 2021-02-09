---
title: '방법: 요소에 CLR 특성 설정'
description: System.object 클래스에서 상속 하는 특성을 추가 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8e566eafce9b5763830c00659a860e6329671bcd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922654"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>방법: 요소에 CLR 특성 설정
사용자 지정 특성은 도메인 요소, 도형, 연결선 및 다이어그램에 추가할 수 있는 특수 한 특성입니다. 클래스에서 상속 되는 특성을 추가할 수 있습니다 `System.Attribute` .

### <a name="to-add-a-custom-attribute"></a>사용자 지정 특성을 추가 하려면

1. **DSL 탐색기** 에서 사용자 지정 특성을 추가 하려는 요소를 선택 합니다.

2. **속성** 창에서 **사용자 지정 특성** 속성 옆에 있는 찾아보기 (**...**) 아이콘을 클릭 합니다.

     **특성 편집** 대화 상자가 열립니다.

3. **이름** 열에서을 클릭 **\<add attribute>** 하 고 특성의 이름을 입력 합니다. Enter 키를 누릅니다.

4. 특성 이름 아래의 줄에 괄호가 표시 됩니다. 이 줄에서 특성에 대 한 매개 변수 형식 (예:)을 입력 한 `string` 다음 enter 키를 누릅니다.

5. **이름 속성** 열에 적절 한 이름 (예:)을 입력 `MyString` 합니다.

6. **확인** 을 클릭합니다.

     이제 **사용자 지정 특성** 속성이 다음 형식으로 특성을 표시 합니다.

     `[`*AttributeName* `(` *ParameterName* `=` *유형*`)]`

## <a name="see-also"></a>참고 항목

- [도메인 특정 언어 도구 용어집](/previous-versions/bb126564(v=vs.100))