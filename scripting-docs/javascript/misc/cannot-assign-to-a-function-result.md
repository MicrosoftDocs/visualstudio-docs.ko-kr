---
title: 함수 결과에 할당할 수 없습니다. | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5003
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 84ec3426c80da0578dda7cb99e9160b81e31ab87
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817634"
---
# <a name="cannot-assign-to-a-function-result"></a>함수 결과에 할당할 수 없습니다.
함수 결과에 값을 할당 하려고 했습니다. 함수의 결과는 변수에 할당할 수 있지만 변수로 사용할 수는 없습니다. 함수 자체에 새 값을 할당 하려는 경우 괄호 (함수 호출 연산자)를 생략 합니다. 다음 예에서는이 오류가 발생 하는 상황을 보여 줍니다.  
  
```js
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 함수 호출 결과의 값을 *에 할당할*수 있는 값으로 사용 하지 마세요. 그러나 함수 호출 결과를 *변수에* 할당할 수 있습니다.  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
- 또는 함수 자체 (반환 값 아님)를 변수에 할당할 수 있습니다.  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>참고 항목  
 [Function 개체](../../javascript/reference/function-object-javascript.md)   
 [JavaScript 코드 작성](../../javascript/writing-javascript-code.md)   
 [함수](../../javascript/functions-javascript.md)