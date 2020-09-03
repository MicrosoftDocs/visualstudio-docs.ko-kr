---
title: 함수가 필요 합니다. | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5002
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f177bf81a43c45dcff4cef3040c64425ed544057
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816971"
---
# <a name="function-expected"></a>함수가 필요합니다.
개체가 아닌 개체에서 **함수 프로토타입** 메서드 중 하나를 호출 하려고 `Function` 했거나 함수 호출 컨텍스트에서 개체를 사용 했습니다. 예를 들어 다음 코드는 함수가 함수가 **아니기 때문에** 이 오류를 생성 합니다.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 개체에 대 한 **함수 프로토타입** 메서드만 호출 `Function` 합니다.  
  
- 함수 호출 연산자를 사용 하 여 `()` 함수만 호출 하는지 확인 합니다.  
  
## <a name="see-also"></a>추가 정보  
 [Function 개체](../../javascript/reference/function-object-javascript.md)   
 [prototype 속성(Object)](../../javascript/reference/prototype-property-object-javascript.md)