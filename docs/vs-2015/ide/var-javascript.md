---
title: '&lt;var&gt;(JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <var> JavaScript XML tag
- var JavaScript XML tag
ms.assetid: 34ff9023-c81c-46d1-85b6-0022f0962e66
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f72b403d4c6c9cc71bc2a3fdbff8f778a44b3b55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663070"
---
# <a name="ltvargt-javascript"></a>&lt;var&gt;(JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

변수에 대한 문서 정보를 지정합니다.

## <a name="syntax"></a>구문

```
<var type="ValueType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    helpKeyword="keyword" locid="descriptionID">description
</var>
```

#### <a name="parameters"></a>매개 변수
 `type` 선택 사항입니다. 변수의 데이터 형식입니다. 형식은 다음 중 하나일 수 있습니다.

- ECMAScript 5 사양(예: `Number` 및 `Object`)에 있는 ECMAScript 언어 형식입니다.

- `HTMLElement`, `Window` 및 `Document`와 같은 DOM 개체입니다.

- JavaScript 생성자 함수입니다.

  `integer` 선택 사항입니다. `type`이 `Number`인 경우 변수가 정수인지 여부를 지정합니다. 변수가 정수임을 나타내려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.

  `domElement` 선택 사항입니다. 이 특성은 더 이상 사용되지 않으며, `type` 특성이 이 특성보다 우선합니다. 이 특성은 문서화된 변수가 DOM 요소인지 여부를 지정합니다. 변수가 DOM 요소임을 지정하려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. `type` 특성이 설정되지 않고 `domElement`가 `true`로 설정된 경우 IntelliSense는 명령문 완성을 수행할 때 문서화된 변수를 `HTMLElement`로 처리합니다.

  `mayBeNull` 선택 사항입니다. 문서화된 변수를 null로 설정할 수 있는지 여부를 지정합니다. 변수를 null로 설정할 수 있음을 나타내려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. 기본값은 `false`입니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.

  `elementType` 선택 사항입니다. `type`이 `Array`인 경우 이 특성은 배열의 요소 유형을 지정합니다.

  `elementInteger` 선택 사항입니다. `type`이 `Array`이고 `elementType`이 `Number`인 경우 이 특성은 배열의 요소가 정수인지 여부를 지정합니다. 배열의 요소가 정수임을 나타내려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.

  `elementDomElement` 선택 사항입니다. 이 특성은 더 이상 사용되지 않으며, `elementType` 특성이 이 특성보다 우선합니다. `type`이 `Array`인 경우 이 특성은 배열의 요소가 DOM 요소인지 여부를 지정합니다. 요소가 DOM 요소임을 지정하려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. `elementType` 특성이 설정되지 않고 `elementDomElement`가 `true`로 설정된 경우 IntelliSense는 명령문 완성을 수행할 때 배열의 각 요소를 `HTMLElement`로 처리합니다.

  `elementMayBeNull` 선택 사항입니다. `type`이 `Array`인 경우 배열의 요소를 null로 설정할 수 있는지 여부를 지정합니다. 배열의 요소를 null로 설정할 수 있음을 나타내려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. 기본값은 `false`입니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.

  `helpKeyword` 선택 사항입니다. F1 도움말의 키워드입니다.

  `locid` 선택 사항입니다. 변수에 대한 지역화 정보의 식별자입니다. 식별자는 멤버 ID이거나 OpenAjax 메타데이터에 의해 정의된 메시지 번들의 `name` 속성 값에 해당합니다. 식별자 형식은 태그에 지정 된 형식에 따라 달라 집니다 [\<loc>](../ide/loc-javascript.md) .

  `description` 선택 사항입니다. 변수에 대한 설명입니다.

## <a name="example"></a>예
 다음 코드 예제에서는 `<var>` 요소를 사용하는 방법을 보여줍니다.

```javascript
/// <var>A rectangle that has a width of 5.</var>
var Rectangle = {
    /// <field type = 'Number'>The width of the rectangle.</field>
    wid: 5,
    /// <field type = 'Number'>The length of the rectangle.</field>
    len: 0,
    /// <field type='Number'>Returns the area of the rectangle.</field>
    getArea: function (wid, len) {
        return len * wid;
    }
}
```

## <a name="see-also"></a>관련 항목
 [XML 문서 주석](../ide/xml-documentation-comments-javascript.md)
