---
title: '&lt;field &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <field> JavaScript XML tag
- field JavaScript XML tag
ms.assetid: c494bae0-3095-42a3-aa0a-4c415188c65c
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a3fc786e4d99d1eaff4a8b152ea9496ce8400ff1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663862"
---
# <a name="ltfieldgt-javascript"></a>&lt;field &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

개체에 정의 된 필드 또는 멤버에 대 한 설명을 포함 하 여 문서 정보를 지정 합니다.

## <a name="syntax"></a>구문

```
<field name="fieldName" static="true|false"
    type="FieldType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    helpKeyword="keyword" locid="descriptionID"
    value="code">description
</field>
```

#### <a name="parameters"></a>매개 변수
 `name` 필드 또는 멤버의 이름입니다. `<field>`생성자 함수에서 요소를 사용 하는 경우 `name` 는 필수 이며 태그가 적용 되는 멤버를 정의 합니다. `<field>`요소가 필드에 직접 주석을 추가 하는 경우이 특성은 무시 되 고 Visual Studio에서 사용 되는 이름은 소스 코드의 실제 필드 이름이 됩니다.

 `static` 선택 사항입니다. 필드가 생성자 함수의 멤버 인지, 아니면 생성자 함수에서 반환 하는 개체의 멤버 인지를 지정 합니다. 필드를 `true` 생성자 함수의 멤버로 처리 하려면로 설정 합니다. `false`생성자 함수에서 반환 하는 개체의 멤버로 필드를 처리 하려면로 설정 합니다.

 `type` 선택 사항입니다. 필드의 데이터 형식입니다. 형식은 다음 중 하나일 수 있습니다.

- ECMAScript 5 사양의 ECMAScript 언어 형식 (예: `Number` 및) `Object`

- `HTMLElement`, `Window` 및 `Document`와 같은 DOM 개체입니다.

- JavaScript 생성자 함수입니다.

  `integer` 선택 사항입니다. `type`가 이면 `Number` 필드가 정수 인지 여부를 지정 합니다. 필드가 정수 임을 나타내려면로 설정 하 `true` 고, 그렇지 않으면로 설정 `false` 합니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.

  `domElement` 선택 사항입니다. 이 특성은 더 이상 사용되지 않으며, `type` 특성이 이 특성보다 우선합니다. 이 특성은 문서화 된 필드가 DOM 요소 인지 여부를 지정 합니다. `true`필드가 DOM 요소 임을 지정 하려면로 설정 하 고, 그렇지 않으면로 설정 `false` 합니다. `type`특성이 설정 되지 않고 `domElement` 로 설정 된 경우 IntelliSense는 `true` 문 완성을 수행할 때 문서화 된 필드를로 처리 합니다 `HTMLElement` .

  `mayBeNull` 선택 사항입니다. 문서화 된 필드를 null로 설정할 수 있는지 여부를 지정 합니다. 필드를 `true` null로 설정할 수 있음을 나타내려면로 설정 하 고, 그렇지 않으면로 설정 `false` 합니다. 기본값은 `false`입니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.

  `elementType` 선택 사항입니다. `type`이 `Array`인 경우 이 특성은 배열의 요소 유형을 지정합니다.

  `elementInteger` 선택 사항입니다. `type`이 `Array`이고 `elementType`이 `Number`인 경우 이 특성은 배열의 요소가 정수인지 여부를 지정합니다. 배열의 요소가 정수임을 나타내려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.

  `elementDomElement` 선택 사항입니다. 이 특성은 더 이상 사용되지 않으며, `elementType` 특성이 이 특성보다 우선합니다. `type`이 `Array`인 경우 이 특성은 배열의 요소가 DOM 요소인지 여부를 지정합니다. 요소가 DOM 요소임을 지정하려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. `elementType` 특성이 설정되지 않고 `elementDomElement`가 `true`로 설정된 경우 IntelliSense는 명령문 완성을 수행할 때 배열의 각 요소를 `HTMLElement`로 처리합니다.

  `elementMayBeNull` 선택 사항입니다. `type`이 `Array`인 경우 배열의 요소를 null로 설정할 수 있는지 여부를 지정합니다. 배열의 요소를 null로 설정할 수 있음을 나타내려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. 기본값은 `false`입니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.

  `helpKeyword` 선택 사항입니다. F1 도움말의 키워드입니다.

  `locid` 선택 사항입니다. 필드에 대 한 지역화 정보에 대 한 식별자입니다. 식별자는 멤버 ID이거나 OpenAjax 메타데이터에 의해 정의된 메시지 번들의 `name` 속성 값에 해당합니다. 식별자 형식은 태그에 지정 된 형식에 따라 달라 집니다 [\<loc>](../ide/loc-javascript.md) .

  `value` 선택 사항입니다. 함수 코드 자체 대신 IntelliSense에서 사용 하기 위해 평가 해야 하는 코드를 지정 합니다. 의 경우 `<field>` 이 특성은 생성자 함수에 대해 지원 되지만 개체 리터럴에는 지원 되지 않습니다. 필드 형식이 정의 되어 있지 않은 경우이 특성을 사용 하 여 형식 정보를 제공할 수 있습니다. 예를 들어를 사용 `value=’1’` 하 여 필드 형식을 숫자로 취급할 수 있습니다.

  `description` 선택 사항입니다. 필드에 대 한 설명입니다.

## <a name="remarks"></a>설명
 `name`특성은 생성자 함수에서 필드를 문서화 하는 경우에 필요 합니다. 다른 모든 시나리오의 경우 요소의 모든 특성 `<field>` 은 선택 사항입니다.

 생성자 함수를 문서화 하는 경우 요소는 `<field>` 필드 선언 바로 앞에 나와야 합니다. `name`특성은 소스 코드에서 사용 되는 필드 이름과 일치 해야 합니다. 개체 멤버의 경우 `name` `<field>` 요소가 개체 멤버 선언 바로 앞에 표시 되는 경우 특성을 생략할 수 있습니다.

## <a name="example"></a>예
 다음 코드 예제에서는 `<field>` 요소를 사용하는 방법을 보여줍니다.

```javascript
// Use of <field> in an object definition.
var Rectangle = {
    /// <field type='Number'>The width of the rectangle.</field>
    wid: 5,
    /// <field type='Number'>The length of the rectangle.</field>
    len: 0,
    /// <field type='Number'>Returns the area of the rectangle.</field>
    getArea: function (wid, len) {
        return len * wid;
    }
}

// Use of <field> in a constructor function.
// The name attribute is required.
function Engine() {
    /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>
    this.HorsePower = 150;
}
```

## <a name="example"></a>예
 다음 예제에서는 `<field>` 특성이로 설정 된 요소를 사용 하는 방법을 보여 줍니다 `static` `true` .

```javascript
function Engine() {
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>
}

Engine.HorsePower = 140;
// IntelliSense on the field is available here.
Engine.

```

## <a name="example"></a>예
 다음 예제에서는 `<field>` 특성이로 설정 된 요소를 사용 하는 방법을 보여 줍니다 `static` `false` .

```javascript
function Engine() {
    /// <field name='HorsePower' static='false' type='Number'>Non-static field desc.</field>
}

Engine.HorsePower = 140;
var eng = new Engine();
// IntelliSense on the field is available here.
eng.

```

## <a name="example"></a>예
 다음 예제에서는 특성에서 요소를 사용 하는 방법을 보여 줍니다 `<field>` `value` .

```javascript
function calculator(a) {
    /// <field name='f' value='1'/>
}
new calculator().f.   // Completion list for a Number.

```

## <a name="see-also"></a>관련 항목
 [XML 문서 주석](../ide/xml-documentation-comments-javascript.md)
