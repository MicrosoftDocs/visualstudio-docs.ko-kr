---
title: "데이터 속성 및 접근자 속성 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 7e132831-375d-4728-9a57-5c6f91075b1c
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b800131ba76aa432492c0caefdbb9e8d5291924
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2017
---
# <a name="data-properties-and-accessor-properties"></a>데이터 속성 및 접근자 속성
이 섹션에는 데이터 속성 및 접근자 속성에 대해 필요할 가능성이 큰 모든 정보가 포함되어 있습니다.  
  
### <a name="data-properties"></a>데이터 속성  
 *데이터 속성*은 값을 가져오고 설정할 수 있는 속성입니다. 데이터 속성의 설명자에 `value` 및 `writable` 속성이 포함되어 있습니다.  
  
 다음 표에는 데이터 속성 설명자의 특성이 나열되어 있습니다.  
  
|데이터 설명자 특성|설명|기본|  
|-------------------------------|-----------------|-------------|  
|`value`|속성의 현재 값입니다.|`undefined`|  
|`writable`|`true` 또는 `false` `writable`이 `true`로 설정된 경우 속성 값을 수정할 수 있습니다.|`false`|  
|`enumerable`|`true` 또는 `false` `enumerable`이 `true`로 설정된 경우 `for...in` 문을 사용하여 속성을 열거할 수 있습니다.|`false`|  
|`configurable`|`true` 또는 `false` `configurable`이 `true`로 설정된 경우 특성 설정을 변경할 수 있고 속성을 삭제할 수 있습니다.|`false`|  
  
 설명자에 `value`, `writable`, `get` 또는 `set` 특성이 없고 지정된 속성 이름이 없으면 데이터 속성이 추가됩니다.  
  
 `configurable` 특성이 `false`이고 `writable`이 `true`이면 `value`와 `writable` 특성을 변경할 수 있습니다.  
  
#### <a name="data-properties-added-without-using-defineproperty"></a>defineProperty를 사용하지 않고 추가된 데이터 속성  
 `Object.defineProperty`, `Object.defineProperties` 또는 `Object.create` 함수를 사용하지 않고 데이터 속성을 추가하는 경우 `writable`, `enumerable` 및 `configurable` 특성이 모두 `true`로 설정됩니다. 속성이 추가되고 나면 `Object.defineProperty` 함수를 사용하여 수정할 수 있습니다.  
  
 다음 방법을 사용하여 데이터 속성을 추가할 수 있습니다.  
  
-   `obj.color = "white";`에서와 같이 할당 연산자(=)  
  
-   `obj = { color: "white", height: 5 };`에서와 같이 개체 리터럴  
  
-   [생성자를 사용하여 형식 정의](../../javascript/advanced/using-constructors-to-define-types.md)에 설명된 대로 생성자 함수  
  
### <a name="accessor-properties"></a>접근자 속성  
 *접근자 속성*은 속성 값을 설정하거나 검색할 때마다 사용자 제공 함수를 호출하는 데 사용합니다. 접근자 속성의 설명자에는 `get` 특성, `set` 특성 또는 둘 다가 포함됩니다.  
  
 다음 표에는 접근자 속성 설명자의 특성이 나열되어 있습니다.  
  
|접근자 설명자 특성|설명|기본|  
|-----------------------------------|-----------------|-------------|  
|`get`|속성 값을 반환하는 함수입니다. 함수에 매개 변수가 없습니다.|`undefined`|  
|`set`|속성 값을 설정하는 함수입니다. 할당할 값을 포함하는 매개 변수가 하나 있습니다.|`undefined`|  
|`enumerable`|`true` 또는 `false` `enumerable`이 `true`로 설정된 경우 `for...in` 문을 사용하여 속성을 열거할 수 있습니다.|`false`|  
|`configurable`|`true` 또는 `false` `configurable`이 `true`로 설정된 경우 특성 설정을 변경할 수 있고 속성을 삭제할 수 있습니다.|`false`|  
  
 `get` 접근자가 정의되어 있지 않고 속성 값에 액세스하려고 하면 `undefined` 값이 반환됩니다. `set` 접근자가 정의되어 있지 않고 접근자 속성에 값을 할당하려고 하면 아무 동작도 발생하지 않습니다.  
  
### <a name="property-modifications"></a>속성 수정  
 개체에 이미 이름이 지정된 속성이 있으면 그 속성의 특성이 수정됩니다. 속성을 수정하는 경우 설명자에 지정되지 않은 기존의 특성이 그대로 유지됩니다.  
  
 기존 속성의 `configurable` 특성이 `false`이면 `writable` 특성을 `true`에서 `false`로 변경하는 수정 작업만 허용됩니다.  
  
 접근자 속성을 데이터 속성 또는 그 반대로 변경할 수 있습니다. 이 작업을 수행하면 설명자에 지정되지 않은 `configurable` 및 `enumerable` 특성이 속성에 유지됩니다. 설명자에 지정되지 않은 기타 특성은 기본값으로 설정됩니다.  
  
 `Object.defineProperty` 함수를 여러 번 호출하여 구성 가능한 접근자 속성을 점진적으로 정의할 수 있습니다. 예를 들어 하나의 `Object.defineProperty` 호출을 통해 하나의 `get` 접근자만 정의했다면, 이후 동일한 속성 이름을 호출해 `set` 접근자를 정의할 수 있습니다. 그러면 속성에 `get` 접근자와 `set` 접근자가 모두 포함됩니다.  
  
 기존 속성에 적용되는 설명자 개체를 가져오려면 [Object.getOwnPropertyDescriptor 함수](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)를 사용할 수 있습니다.  
  
 [Object.seal 함수](../../javascript/reference/object-seal-function-javascript.md) 및 [Object.freeze 함수](../../javascript/reference/object-freeze-function-javascript.md)를 사용하여 속성 특성의 수정을 방지할 수 있습니다.
