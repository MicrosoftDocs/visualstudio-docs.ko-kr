---
title: '방법: XML 스키마에서 XML 조각 생성'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 2c128d2a-aaa6-4814-aa95-e07056afe338
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c7dff8e1bb211343ccc44e0d1fd33d96c102283
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817179"
---
# <a name="how-to-generate-an-xml-snippet-from-an-xml-schema"></a>방법: XML 스키마에서 XML 코드 조각 생성

XML 편집기에는 XSD(XML 스키마 정의 언어) 스키마에서 XML 코드 조각을 생성할 수 있는 기능이 있습니다. 예를 들어, XML 파일을 만들 때 요소 이름 옆에서 **Tab** 키를 눌러 해당 요소의 스키마 정보에서 생성된 XML 데이터로 요소를 채울 수 있습니다.

이 기능은 요소에서만 사용할 수 있으며 다음 규칙이 적용됩니다.

- 요소에 연결된 스키마 형식이 있어야 합니다. 즉, 연결된 스키마에 따라 요소가 유효해야 합니다. 스키마 형식은 추상적일 수 없으며 형식에 필수 특성 및/또는 필수 자식 요소가 포함되어야 합니다.

- 편집기에서 현재 요소는 특성 없이 비어 있어야 합니다. 예를 들어, 다음은 모두 유효합니다.

  - `<Account`

  - `<Account>`

  - `<Account></Account>`

- 요소 이름의 바로 오른쪽에 커서가 있어야 합니다.

생성된 조각에는 모든 필수 특성 및 요소가 포함됩니다. `minOccurs`가 1보다 큰 경우 해당 요소의 최소 필수 인스턴스 수(최대 100개)가 조각에 포함됩니다. 스키마에 고정 값이 있으면 조각에도 고정 값이 포함됩니다. `xsd:any` 및 `xsd:anyAttribute` 요소는 무시되며 그 결과로 추가 조각 구문은 없습니다.

기본값이 생성되고 편집 가능한 값으로 표시됩니다. 스키마에서 기본값을 지정하면 이 기본값이 사용됩니다. 그러나 스키마 기본값이 빈 문자열인 경우 편집기에서 다음 방법으로 기본값이 생성됩니다.

- union 형식의 멤버를 통해 직접 또는 간접적으로 스키마 형식에 열거형 패싯이 포함된 경우 스키마 개체 모델에서 첫 번째 열거형 값이 기본값으로 사용됩니다.

- 스키마 형식이 atomic 형식인 경우 편집기에서 atomic 형식을 가져오고 atomic 형식 이름을 삽입합니다. 파생된 단순 형식의 경우 기본 단순 형식이 사용됩니다. list 형식의 경우 atomic 형식은 `itemType`입니다. union의 경우 atomic 형식은 첫 번째 `memberType`의 atomic 형식입니다.

## <a name="example"></a>예제

이 섹션의 단계에서는 XML 편집기의 스키마에 의해 생성된 XML 코드 조각 기능을 사용하는 방법을 보여 줍니다.

> [!NOTE]
> 이 프로시저를 시작하기 전에 스키마 파일을 로컬 컴퓨터에 저장합니다.

### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>새 XML 파일을 만들어 XML 스키마와 연결하는 방법

1. **파일** 메뉴에서 **새로 만들기**를 가리키고 **파일**을 클릭합니다.

2. **템플릿** 창에서 **XML 파일**을 선택하고 **열기**를 클릭합니다.

     편집기에서 새 파일이 열립니다. 파일에는 기본 XML 선언, `<?xml version="1.0" encoding="utf-8">`이 포함됩니다.

3. 문서 속성 창의 **스키마** 필드에서 찾아보기 단추( **...** )를 클릭합니다.

     **XSD 스키마** 대화 상자가 표시됩니다.

4. **추가**를 클릭합니다.

     **XSD 스키마 열기** 대화 상자가 표시됩니다.

5. 스키마 파일을 선택하고 **열기**를 클릭합니다.

6. **확인**을 클릭합니다.

     이제 XML 스키마가 XML 문서와 연결되었습니다.

### <a name="to-generate-an-xml-snippet"></a>XML 조각을 생성하려면

1. 편집기 창에 `<`를 입력합니다.

2. 멤버 목록에 가능한 항목이 표시됩니다.

     **!--** 주석을 추가합니다.

     **!DOCTYPE** 문서 형식을 추가합니다.

     **?** 처리 명령을 추가합니다.

     **Contact** 루트 요소를 추가합니다.

3. 멤버 목록에서 **Contact**를 선택하고 **Enter** 키를 누릅니다.

     시작 태그 `<Contact`가 추가되고 요소 이름 뒤에 커서가 놓입니다.

4. **Tab** 키를 눌러 스키마 정보를 기반으로 `Contact` 요소에 대한 XML 데이터를 생성합니다.

## <a name="input"></a>입력

다음 스키마 파일은 연습에 사용됩니다.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<xs:schema elementFormDefault="qualified"
           xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:simpleType name="phoneType">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Voice"/>
      <xs:enumeration value="Fax"/>
      <xs:enumeration value="Pager"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:element name="Contact">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="Name">
          <xs:simpleType>
            <xs:restriction base="xs:string"></xs:restriction>
          </xs:simpleType>
        </xs:element>
        <xs:element name="Title"
                    type="xs:string" />
        <xs:element name="Phone"
                    minOccurs="1"
                    maxOccurs="unbounded">
          <xs:complexType>
            <xs:sequence>
              <xs:element name="Number"
                          minOccurs="1">
                <xs:simpleType>
                  <xs:restriction base="xs:string"></xs:restriction>
                </xs:simpleType>
              </xs:element>
              <xs:element name="Type"
                          default="Voice"
                          minOccurs="1"
                          type="phoneType"/>
            </xs:sequence>
          </xs:complexType>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

### <a name="output"></a>출력

다음은 `Contact` 요소와 연결된 스키마 정보를 기반으로 생성되는 XML 데이터입니다. `bold`로 표시된 항목은 XML 코드 조각에서 편집 가능한 필드임을 나타냅니다.

```xml
<Contact>
  <Name>name</Name>
  <Title>title</Title>
  <Phone>
    <Number>number</Number>
    <Type>Voice</Type>
  </Phone>
</Contact>
```

## <a name="see-also"></a>참조

- [XML 코드 조각](../xml-tools/xml-snippets.md)
- [방법: XML 코드 조각 사용](../xml-tools/how-to-use-xml-snippets.md)
