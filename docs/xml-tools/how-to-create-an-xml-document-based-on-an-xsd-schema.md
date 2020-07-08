---
title: '방법: XSD 스키마를 기반으로 XML 문서 만들기'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 424b325b244499a18077cc1df0ff9164c41763d2
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815463"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>방법: XSD 스키마를 기반으로 XML 문서 만들기

**샘플 XML 생성** 기능은 XSD(XML 스키마) 파일을 기반으로 샘플 XML 파일을 생성합니다.

다음과 같은 경우 이 옵션을 사용할 수 있습니다.

- 스키마의 다양한 구문 용도를 파악하려는 경우

- 스키마에서 의도된 작업을 수행하는지 확인하려는 경우

**샘플 XML 생성** 기능은 전역 요소에서만 사용할 수 있으며 이 기능을 사용하려면 유효한 XML 스키마 집합이 필요합니다.

일반적으로 이 기능은 유효한 XML 문서를 생성합니다. 그러나 스키마에 다음 중 하나 이상이 포함되어 있으면 예제 XML이 유효하지 않을 수 있습니다.

- `xs:key`, `xs:keyref` 및 `xs:unique` ID 제약 조건

- `xs:pattern` 패싯

- `xs:QName` 형식의 열거형

- `xs:ENTITY`, `xs:ENTITIES` 및 `xs:NOTATION` 형식

또한 `xs:base64Binary` 콘텐츠는 해당 형식의 스키마에 열거형이 나타나는 경우에만 생성됩니다.

## <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>XSD 파일을 기반으로 XML 인스턴스 문서를 생성하려면

1. [:방법 XSD 스키마 파일 만들기 및 편집](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)의 단계를 수행합니다.

2. [XML 스키마 탐색기](../xml-tools/xml-schema-explorer.md)에서 `PurchaseOrder` 전역 요소를 마우스 오른쪽 단추로 클릭합니다. **샘플 XML 생성**을 선택합니다.

     이 옵션을 선택하면 다음 샘플 XML 콘텐츠를 포함하는 PurchaseOrder.*xml* 파일이 XML 편집기에서 생성되고 열립니다.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <PurchaseOrder OrderDate="1900-01-01" xmlns="http://tempuri.org/PurchaseOrderSchema.xsd">
      <ShipTo country="US">
        <name>name1</name>
        <street>street1</street>
        <city>city1</city>
        <state>state1</state>
        <zip>1</zip>
      </ShipTo>
      <ShipTo country="US">
        <name>name2</name>
        <street>street2</street>
        <city>city2</city>
        <state>state2</state>
        <zip>-79228162514264337593543950335</zip>
      </ShipTo>
      <BillTo country="US">
        <name>name1</name>
        <street>street1</street>
        <city>city1</city>
        <state>state1</state>
        <zip>1</zip>
      </BillTo>
    </PurchaseOrder>
    ```
