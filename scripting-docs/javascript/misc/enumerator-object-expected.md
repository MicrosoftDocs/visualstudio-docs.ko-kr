---
title: 열거자 개체가 필요 합니다. | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5015
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5e63ee2970c90ffcfff5c02a384d3346b3ea6229
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862635"
---
# <a name="enumerator-object-expected"></a>Enumerator 개체가 필요합니다.
이 아닌 형식의 개체에 대해 Enumerator. prototype. **atEnd, enumerator** . Prototype. MoveFirst 또는 **enumerator** 메서드를 호출 하려고 `Enumerator` 했습니다. 이 호출 형식의 개체는 형식 이어야 합니다 `Enumerator` . 다음은이 규칙을 위반 하는 코드의 예입니다.  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 형식이 인 개체의 경우에만 **열거자. prototype. atEnd**, **enumerator**. Prototype. **moveFirst**또는 **enumerator** 메서드를 호출 `Enumerator` 합니다. 개체가 개체 인지 확인 하려면 `Enumerator` 다음을 사용 합니다.  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>참고 항목  
 [Enumerator 개체](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/Enumerator)