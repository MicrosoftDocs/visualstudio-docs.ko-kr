---
title: '&lt;반환 &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- returns JavaScript XML tag
- <returns> JavaScript XML tag
ms.assetid: 10d97829-c0ae-40a5-b04c-d8b538cdefbc
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f8fd8cdc8acdbf42b97e00f3c85647dd863721d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669963"
---
# <a name="ltreturnsgt-javascript"></a>&lt;반환 &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

함수 또는 메서드 호출의 결과에 대 한 문서 정보를 지정 합니다.

## <a name="syntax"></a>구문

```
<returns type="ValueType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    locid="descriptionID" value="code">description
</returns>
```

#### <a name="parameters"></a>매개 변수
 `type` 선택 사항입니다. 반환 값의 데이터 형식입니다. 형식은 다음 중 하나일 수 있습니다.

- ECMAScript 5 사양의 ECMAScript 언어 형식 (예: `Number` 및) `Object`

- `HTMLElement`, `Window` 및 `Document`와 같은 DOM 개체입니다.

- JavaScript 생성자 함수입니다.

  `integer` 선택 사항입니다. `type`가 이면 `Number` 반환 값이 정수 인지 여부를 지정 합니다. `true`반환 값이 정수 임을 나타내려면로 설정 하 고, 그렇지 않으면로 설정 `false` 합니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.

  `domElement` 선택 사항입니다. 이 특성은 더 이상 사용되지 않으며, `type` 특성이 이 특성보다 우선합니다. 이 특성은 문서화 된 반환 값이 DOM 요소 인지 여부를 지정 합니다. `true`반환 값이 DOM 요소 임을 지정 하려면로 설정 하 고, 그렇지 않으면로 설정 `false` 합니다. `type`특성이 설정 되지 않고 `domElement` 로 설정 된 경우 IntelliSense는 `true` 문 완성을 수행할 때 문서화 된 반환 값을로 처리 합니다 `HTMLElement` .

  `mayBeNull` 선택 사항입니다. 문서화 된 반환 값을 null로 설정할 수 있는지 여부를 지정 합니다. `true`반환 값을 null로 설정할 수 있음을 나타내려면로 설정 하 고, 그렇지 않으면로 설정 `false` 합니다. 기본값은 `false`입니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.

  `elementType` 선택 사항입니다. `type`이 `Array`인 경우 이 특성은 배열의 요소 유형을 지정합니다.

  `elementInteger` 선택 사항입니다. `type`이 `Array`이고 `elementType`이 `Number`인 경우 이 특성은 배열의 요소가 정수인지 여부를 지정합니다. 배열의 요소가 정수임을 나타내려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.

  `elementDomElement` 선택 사항입니다. 이 특성은 더 이상 사용되지 않으며, `elementType` 특성이 이 특성보다 우선합니다. `type`이 `Array`인 경우 이 특성은 배열의 요소가 DOM 요소인지 여부를 지정합니다. 요소가 DOM 요소임을 지정하려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. `elementType` 특성이 설정되지 않고 `elementDomElement`가 `true`로 설정된 경우 IntelliSense는 명령문 완성을 수행할 때 배열의 각 요소를 `HTMLElement`로 처리합니다.

  `elementMayBeNull` 선택 사항입니다. `type`이 `Array`인 경우 배열의 요소를 null로 설정할 수 있는지 여부를 지정합니다. 배열의 요소를 null로 설정할 수 있음을 나타내려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. 기본값은 `false`입니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.

  `locid` 선택 사항입니다. 반환 값에 대 한 지역화 정보에 대 한 식별자입니다. 식별자는 멤버 ID이거나 OpenAjax 메타데이터에 의해 정의된 메시지 번들의 `name` 속성 값에 해당합니다. 식별자 형식은 태그에 지정 된 형식에 따라 달라 집니다 [\<loc>](../ide/loc-javascript.md) .

  `value` 선택 사항입니다. 함수 코드 자체 대신 IntelliSense에서 사용 하기 위해 평가 해야 하는 코드를 지정 합니다. 예를 들어이 특성을 사용 하 여와 같은 비동기 콜백에 대 한 IntelliSense를 제공할 수 있습니다 `Promise` . 특성을 `value` 요소와 함께 사용 `<returns>` 하면 긴 코드 실행을 우회 하 여 IntelliSense 성능을 향상 시킬 수 있습니다.

  `description` 선택 사항입니다. 반환 값에 대한 설명입니다.

## <a name="remarks"></a>설명
 `<returns>`요소는 모든 문 앞에 함수 본문에 배치 해야 합니다.

## <a name="example"></a>예제
 다음 코드 예제에서는 `<returns>` 요소를 사용하는 방법을 보여줍니다.

```javascript
function areaFunction(radiusParam)
{
    /// <summary>Determines the area of a circle when provided a radius parameter.</summary>
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>
    /// <returns type="Number">The area.</returns>
    var areaVal;
    areaVal = Math.PI * radiusParam * radiusParam;
    return areaVal;
}

// The following examples use the <remarks> element with a value attribute.

function getJson(complete) {
    /// <returns value='complete("")' ></returns>
    var r = new XMLHttpRequest();
    // . . .
}

getJson(function (json) {
    json.  // IntelliSense for a String object is
           // available here.
});

function calculate(x) {
    /// <returns value='1'/>
}
calculate().  // Completion list for a Number.

```

## <a name="see-also"></a>관련 항목
 [XML 문서 주석](../ide/xml-documentation-comments-javascript.md)
