---
title: 예외가 발생 하 여 catch 하지 않음 | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a0e3eb6d1275e5598ad44ea553e22f0b53eeb45
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862757"
---
# <a name="exception-thrown-and-not-caught"></a>예외가 throw되고 catch되지 않았습니다.
`throw`코드에 문을 포함 했지만 **try** 블록 내에 포함 되지 않았거나 오류를 트랩할 연결 된 **catch** 블록이 없습니다. 예외는 **throw** 문을 사용 하 여 **try** 블록 내에서 throw 되 고 **catch** 문을 사용 하 여 **try** 블록 외부에서 catch 됩니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- **Try** 블록에서 예외를 throw 할 수 있는 코드를 묶고 해당 하는 **catch** 블록이 있는지 확인 합니다.  
  
- Catch 문이 올바른 형식의 예외를 예상 하는지 확인 합니다.  
  
- 예외가 다시 throw 되는 경우 다른 해당 catch 문이 있는지 확인 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Error 개체](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)   
 [throw 문](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/throw)   
 [try ... catch ... finally 문](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)