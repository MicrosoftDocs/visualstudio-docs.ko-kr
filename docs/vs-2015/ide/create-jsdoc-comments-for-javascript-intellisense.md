---
title: JavaScript IntelliSense에 대 한 JSDoc 주석 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b974f3450b88ab22e58e284881f270c1b3d72298
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72619270"
---
# <a name="create-jsdoc-comments-for-javascript-intellisense"></a>JavaScript IntelliSense에 대한 JSDoc 주석 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio의 IntelliSense는 표준 JSDoc 주석을 사용하여 스크립트에 추가하는 정보를 표시합니다. JSDoc 주석을 사용하여 함수, 필드 및 변수와 같은 코드 요소에 대한 정보를 제공할 수 있습니다.

## <a name="jsdoc-comment-tags"></a>JSDoc 주석 태그
 다음과 같은 표준 JSDoc 주석 태그는 IntelliSense에서 코드에 대한 정보를 표시하는 데 사용됩니다.

|  JSDoc 태그   |                       Syntax                        |                                                     참고                                                      |
|--------------|-----------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| @deprecated  |              @deprecated*설명*              |                                   사용되지 않는 함수 또는 메서드를 지정합니다.                                   |
| @description |             @description*설명*              |                              함수 또는 메서드에 대한 설명을 지정합니다.                               |
|    @param    | @param {*type*} *parameterName*<em>description</em> | 함수 또는 메서드의 매개 변수에 대한 정보를 지정합니다.<br /><br /> TypeScript는도 지원 @paramTag 합니다. |
|  @property   |          @property {*type*} *propertyName*          |   설명을 포함하여 개체에 정의된 필드 또는 멤버에 대한 정보를 지정합니다.    |
|   @returns   |                  @returns {*type*}                  |           반환 값을 지정합니다.<br /><br /> TypeScript의 경우 @returnType 대신를 사용 @returns 합니다.           |
|   @summary   |               @summary*설명*                |                   함수 또는 메서드에 대 한 설명을 지정 합니다 (와 같음 @description ).                   |
|    @type     |                   @type {*type*}                    |                                상수 또는 변수의 형식을 지정합니다.                                |
|   @typedef   |         @typedef {*type*} *customTypeName*          |                                            사용자 지정 형식을 지정합니다.                                            |

### <a name="examples"></a>예제
 다음 예제에서는 @description @param @return 라는 함수에 대해, 및 JSDoc 태그를 사용 하는 방법을 보여 줍니다 `getArea` .

```javascript
/** @description Determines the area of a circle that has the specified radius parameter.
 * @param {number} radius The radius of the circle.
 * @return {number}
 */
function getArea(radius) {
    var areaVal;
    areaVal = Math.PI * radius * radius;
    return areaVal;
}
```

 앞의 예제에서 IntelliSense는 `getArea`에 대한 여는 괄호를 입력할 때 설명, 매개 변수 및 반환 정보를 표시합니다.

 ![함수에 대한 IntelliSense 정보](../ide/media/js-intellisense-jsdoc-comments.png "JS_IntelliSense_JSDoc_Comments")

 다음 예제에서는 태그를 태그와 함께 사용 하는 방법을 보여 줍니다 @typedef @property .

```javascript
/**
  * @typedef {object} Weather
  * @property {string} current The current weather.
  */
function getForecast(Weather) {
}

var w = new Weather();
```

 다음 예제에서는 JSDoc 태그를 사용 하는 방법을 보여 줍니다 @type . 이 예제와 같이 초기 별표 쌍(\*\*) 뒤에 오는 단일 별표(*)는 필요하지 않습니다.

```javascript
/**
    @type {string}
*/
const RED = 'FF0000';

```

 다음 예제에서는 JSDoc 태그를 사용 하는 방법을 보여 줍니다 @deprecated .

```javascript
/**
 * @deprecated since version 2.0
 */
function old() {
}
```
