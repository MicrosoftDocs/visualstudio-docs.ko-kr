---
title: XML 조각
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2f2bcdd0c28d7b4b99c92d3346b32ed34aa92a0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592323"
---
# <a name="xml-snippets"></a>XML 조각

XML 편집기에서는 보다 신속하게 XML 파일을 만들 수 있는 ‘XML 코드 조각’이라는 기능을 제공합니다. XML 조각을 파일에 삽입하면 이 XML 조각을 다시 사용할 수 있습니다. XSD(XML 스키마 정의 언어) 스키마를 기반으로 XML 데이터를 생성할 수도 있습니다.

## <a name="reusable-xml-snippets"></a>다시 사용할 수 있는 XML 코드 조각

XML 편집기에는 몇 가지 일반 작업을 포괄하는 많은 코드 조각이 포함되어 있습니다. 이 조각을 사용하여 XML 파일을 더욱 쉽게 만들 수 있습니다. 예를 들어, XML 스키마를 만드는 경우 “복합 형식 시퀀스 요소” 및 “단순 형식 요소” 코드 조각을 사용하면 다음 XML 텍스트가 파일에 삽입됩니다. 그러면 필요에 맞게 `name` 값을 변경할 수 있습니다.

```xml
<xs:element name="name">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="name">
        <xs:simpleType>
          <xs:restriction base="xs:string"></xs:restriction>
        </xs:simpleType>
      </xs:element>
    </xs:sequence>
  </xs:complexType>
</xs:element>
```

두 가지 방법으로 조각을 삽입할 수 있습니다. **코드 조각 삽입** 명령을 사용하면 커서 위치에 XML 코드 조각을 삽입합니다. **포함** 명령을 사용하면 선택한 텍스트 주위의 XML 코드 조각을 래핑합니다. **편집** 메뉴의 **IntelliSense** 하위 메뉴나 편집기의 오른쪽 클릭 메뉴에서 두 명령을 사용할 수 있습니다.

자세한 내용은 [방법: XML 코드 조각 사용](../xml-tools/how-to-use-xml-snippets.md)을 참조하세요.

## <a name="schema-generated-xml-snippets"></a>스키마에 의해 생성된 XML 코드 조각

XML 편집기에서는 XML 스키마에서 XML 코드 조각을 생성할 수 있는 기능을 제공합니다. 이 기능을 사용하면 요소의 스키마 정보에서 생성된 XML 요소로 해당 요소를 채울 수 있습니다. 자세한 내용은 [방법: XML 스키마에서 XML 코드 조각 생성](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)을 참조하세요.

## <a name="create-new-xml-snippets"></a>새 XML 코드 조각 만들기

기본적으로 Visual Studio에 포함된 코드 조각 외에도 사용자가 직접 XML 코드 조각을 만들어 사용할 수 있습니다. 자세한 내용은 [방법: XML 코드 조각 만들기](../xml-tools/how-to-create-xml-snippets.md)를 참조하세요.

## <a name="see-also"></a>참조

- [Visual Studio의 코드 조각](../ide/code-snippets.md)
- [XML 편집기](../xml-tools/xml-editor.md)
