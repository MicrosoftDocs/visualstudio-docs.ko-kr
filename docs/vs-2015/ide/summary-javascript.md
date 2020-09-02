---
title: '&lt;요약&gt;(JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- summary JavaScript XML tag
- <summary> JavaScript XML tag
ms.assetid: 6540582d-bdb3-42ec-ad2f-c176783e6f9c
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f283c2c1825c4b8b02fb5b044ce113231a919317
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646843"
---
# <a name="ltsummarygt-javascript"></a>&lt;요약&gt;(JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

함수 또는 메서드에 대한 설명을 지정합니다.

## <a name="syntax"></a>구문

```
<summary locid="descriptionID">description
</summary>
```

#### <a name="parameters"></a>매개 변수
 `locid` 선택 사항입니다. 함수 또는 메서드에 대한 지역화 정보의 식별자입니다. 식별자는 멤버 ID이거나 OpenAjax 메타데이터에 의해 정의된 메시지 번들의 `name` 속성 값에 해당합니다. 식별자 형식은 요소에 지정 된 형식에 따라 달라 집니다 [\<loc>](../ide/loc-javascript.md) .

 `description` 선택 사항입니다. 함수 또는 메서드에 대한 설명.

## <a name="remarks"></a>설명
 , 및를 포함 하는 함수에 주석을 추가 하는 데 사용 되는 요소는 [\<summary>](../ide/summary-javascript.md) [\<param>](../ide/param-javascript.md) [\<returns>](../ide/returns-javascript.md) 모든 문 앞에 함수 본문에 배치 되어야 합니다.

## <a name="example"></a>예
 다음 코드는 `<summary>` 요소를 사용하는 방법을 보여줍니다.

```javascript
function areaFunction(radiusParam)
{
    /// <summary>Determines the area of a circle when supplied a radius parameter.</summary>
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>
    /// <returns type="Number">The area.</returns>
    var areaVal;
    areaVal = Math.PI * radiusParam * radiusParam;
    return areaVal;
}

```

## <a name="see-also"></a>관련 항목
 [XML 문서 주석](../ide/xml-documentation-comments-javascript.md)
