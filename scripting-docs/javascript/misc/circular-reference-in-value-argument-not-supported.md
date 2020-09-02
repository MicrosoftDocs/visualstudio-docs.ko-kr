---
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
ms.openlocfilehash: 633ed9c37e8ccde0844205910a8fa2dc12d91414
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817621"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>값 인수에 순환 참조를 사용하는 것은 지원되지 않습니다.
잘못 된 값을 사용 하 여를 호출 하려고 한 경우 `JSON.stringify` `value`인수, 배열 또는 개체는 순환 참조를 포함 합니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 인수에서 순환 참조를 제거 합니다.  
  
## <a name="example"></a>예  
 이 예제의 코드는에 대 한 참조를 포함 하 고가에 대 한 참조를 포함 하기 때문에 런타임 오류가 발생 합니다 `john` `mary` `mary` `john` . 순환 참조를 제거 하려면 개체의 속성 또는 개체의 속성을 제거 하거나 설정 해제 `brother` `mary` `sister` `john` 합니다.  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>추가 정보  
 [JSON 개체](../../javascript/reference/json-object-javascript.md)   
 [JSON 함수](../../javascript/reference/json-parse-function-javascript.md)   
 [JavaScript 런타임 오류](../../javascript/reference/javascript-run-time-errors.md)