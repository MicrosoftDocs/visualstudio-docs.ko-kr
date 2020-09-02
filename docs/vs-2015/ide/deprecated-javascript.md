---
title: '&lt;사용 되지 않음 &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 343f3ebe4bea7ee999f60741c189f35defb0ac7b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665811"
---
# <a name="ltdeprecatedgt-javascript"></a>&lt;사용 되지 않음 &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용되지 않는 함수 또는 메서드를 지정합니다.

## <a name="syntax"></a>구문

```
<deprecated
    type="deprecate|remove"
    locid="descriptionID">description
</deprecated>
```

#### <a name="parameters"></a>매개 변수
 `type` 선택 사항입니다. 이후 릴리스에서 함수 또는 메서드를 제거할지 또는 함수나 메서드가 이미 제거 되었고 사용 중에 오류가 발생할 수 있는지 여부를 지정 합니다. `deprecate`이후 릴리스에서 함수 또는 메서드가 제거 되도록 지정 하려면로 설정 합니다. `remove`함수 또는 메서드가 이미 제거 되었음을 지정 하려면로 설정 합니다.

 `locid` 선택 사항입니다. 함수 또는 메서드에 대한 지역화 정보의 식별자입니다. 식별자는 멤버 ID이거나 OpenAjax 메타데이터에 의해 정의된 메시지 번들의 `name` 속성 값에 해당합니다. 식별자 형식은 요소에 지정 된 형식에 따라 달라 집니다 [\<loc>](../ide/loc-javascript.md) .

 `description` 선택 사항입니다. 사용 되지 않는 함수 또는 메서드에 대 한 설명입니다.

## <a name="remarks"></a>설명
 를 포함 하는 함수에 주석을 추가 하는 데 사용 되는 요소는 `<deprecated>` 모든 문 앞에 함수 본문에 배치 해야 합니다. 함수를 사용 되지 않는 것으로 표시 하는 경우 해당 요소를 요소로 대체 하는 것이 좋습니다 [\<summary>](../ide/summary-javascript.md) `<deprecated>` .

## <a name="example"></a>예
 다음 코드는 `<deprecated>` 요소를 사용하는 방법을 보여줍니다.

```javascript
function areaFunction(radiusParam) {
    /// <deprecated type="deprecate" >Determines the area of a circle when supplied a radius parameter.</deprecated>
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>
    /// <returns type="Number">The area.</returns>
    var areaVal;
    areaVal = Math.PI * radiusParam * radiusParam;
    return areaVal;
}

```

## <a name="see-also"></a>관련 항목
 [XML 문서 주석](../ide/xml-documentation-comments-javascript.md)
