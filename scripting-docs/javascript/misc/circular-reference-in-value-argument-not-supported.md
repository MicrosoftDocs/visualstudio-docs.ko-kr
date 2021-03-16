---
description: 유효 하지 않은 값을 사용 하 여 json.stringify를 호출 하려고 한 경우
title: 값 인수의 순환 참조가 지원 되지 않습니다. | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5034
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d06f0fa-86f5-49d1-8d50-af1759990f43
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 88e4ead99f8c59a1300d018bff9d3e81b0874b51
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571144"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>값 인수에 순환 참조를 사용하는 것은 지원되지 않습니다.
잘못 된 값을 사용 하 여를 호출 하려고 한 경우 `JSON.stringify` `value`인수, 배열 또는 개체는 순환 참조를 포함 합니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 인수에서 순환 참조를 제거 합니다.  
  
## <a name="example"></a>예제  
 이 예제의 코드는에 대 한 참조를 포함 하 고가에 대 한 참조를 포함 하기 때문에 런타임 오류가 발생 합니다 `john` `mary` `mary` `john` . 순환 참조를 제거 하려면 개체의 속성 또는 개체의 속성을 제거 하거나 설정 해제 `brother` `mary` `sister` `john` 합니다.  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>참조  
 [JSON 개체](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON)   
 [JSON 함수](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)   
 [JavaScript 런타임 오류](/microsoft-edge/devtools-guide/console/error-and-status-codes#javascript-run-time-errors)
