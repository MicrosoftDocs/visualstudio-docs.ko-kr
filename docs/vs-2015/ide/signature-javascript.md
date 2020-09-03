---
title: '&lt;서명 &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <signature> JavaScript XML tag
- signature JavaScript XML tag
ms.assetid: 319138e7-cfbe-4b37-9643-2ddb7f9c63d4
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b4c640c28ada16a8a03943fcd1362d4fd521772c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671122"
---
# <a name="ltsignaturegt-javascript"></a>&lt;서명 &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

함수 또는 메서드에 대 한 관련 요소 집합을 그룹화 하 여 오버 로드 된 함수에 대 한 설명서를 제공 합니다.

## <a name="syntax"></a>구문

```
<signature externalid="id" externalFile="filename"
    helpKeyword="keyword" locid="descriptionID">
</signature>
```

#### <a name="parameters"></a>매개 변수
 `externalid` 선택 사항입니다. `format` [\<loc>](../ide/loc-javascript.md) 요소의 특성이 인 경우 `vsdoc` 이 특성은 시그니처와 연결 된 XML 코드를 찾는 데 사용 되는 멤버 ID를 지정 합니다. 특성과 달리 `locid` 이 특성은 멤버에서이 ID를 가진 모든 요소를 로드 하도록 지정 합니다. XML 코드에 있는 관련 된 설명 정보도 서명에 지정 된 요소와 병합 됩니다. 이를 통해 사이드카 파일에서와 같은 추가 요소를 `<capability>` 소스 파일에 지정 하지 않고 지정할 수 있습니다. `externalid` 는 선택적 특성입니다.

 `externalFile` 선택 사항입니다. 를 찾을 파일의 이름을 지정 합니다 `externalid` . 가 없는 경우이 특성은 무시 됩니다 `externalid` . 이는 선택적 특성입니다. 기본값은 현재 파일의 이름이 며 .js 대신 .xml의 파일 확장명을 사용 합니다. 기본적으로 지역화에 대 한 관리 되는 리소스 조회 규칙은 파일을 찾는 데 사용 됩니다.

 `helpKeyword` 선택 사항입니다. F1 도움말의 키워드입니다.

 `locid` 선택 사항입니다. 필드에 대 한 지역화 정보에 대 한 식별자입니다. 식별자는 멤버 ID이거나 OpenAjax 메타데이터에 의해 정의된 메시지 번들의 `name` 속성 값에 해당합니다. 식별자 형식은 태그에 지정 된 형식에 따라 달라 집니다 [\<loc>](../ide/loc-javascript.md) .

## <a name="remarks"></a>설명
 `<signature>`.Js 파일의 각 오버 로드 된 함수 설명에 대해 하나의 요소를 사용 하거나 `<signature>` 지정 된 각 외부 멤버 ID에 대해 하나의 요소를 사용 합니다.

 `<signature>`요소는 모든 문 앞에 함수 본문에 배치 해야 합니다. 요소를 사용 하 여 [\<summary>](../ide/summary-javascript.md) , 또는 요소를 사용 하는 경우 [\<param>](../ide/param-javascript.md) [\<returns>](../ide/returns-javascript.md) `<signature>` 블록 내에 다른 요소를 추가 합니다 `<signature>` .

## <a name="example"></a>예
 다음 코드 예제에서는 `<signature>` 요소를 사용하는 방법을 보여줍니다.

```javascript
// Use of <signature> with externalid.
// Requires use of the <loc> tag to identify the external functions.
function illuminate(light) {
    /// <signature externalid='M:Windows.Devices.Light.Illuminate()' />
    /// <signature externalid='M:Windows.Devices.Light.Illuminate(System.Int32)'>
    ///   <param name='light' type='Number' />
    /// </signature>
}

// Use of <signature> for overloads implemented in JavaScript.
function add(a, b) {
    /// <signature>
    /// <summary>function summary 1</summary>
    /// <param name="a" type="Number">The first number</param>
    /// <param name="b" type="Number">The second number</param>
    /// <returns type="Number" />
    /// </signature>
    /// <signature>
    /// <summary>function summary 2 – differ by number of params</summary>
    /// <param name="a" type="Number">Only 1 parameter</param>
    /// <returns type="Number" />
    /// </signature>
    /// <signature>
    /// <summary>function summary 3 – differ by parameter type</summary>
    /// <param name="a" type="Number">Number parameter</param>
    /// <param name="b" type="String">String parameter</param>
    /// <returns type="Number" />
    /// </signature>
    /// <signature>
    /// <summary>function summary 4 – differ by return type</summary>
    /// <param name="a" type="Number">The first number</param>
    /// <param name="b" type="Number">The second number</param>
    /// <returns type="String" />
    /// </signature>

    return a + b;
}
```

## <a name="see-also"></a>관련 항목
 [XML 문서 주석](../ide/xml-documentation-comments-javascript.md)
