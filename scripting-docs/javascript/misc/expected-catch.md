---
title: "' Catch '가 필요 합니다. | Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47411a6376cd843b3a12cf74ed1800775b98cd83
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861955"
---
# <a name="expected-catch"></a>'catch'가 필요합니다.
**Try** 블록을 처리 하는 예외를 사용 했지만 관련 **catch** 문을 작성 하지 않았습니다. 예외 처리 메커니즘을 사용 하려면 예외가 발생 하는 경우 실행 하지 않아야 하는 코드와 함께 실패할 수 있는 코드를 **try** 블록 내에 래핑해야 합니다. 예외는 **throw** 문을 사용 하 여 **try** 블록 내에서 throw 되 고 하나 이상의 **catch** 문을 사용 하 여 **try** 블록 외부에서 catch 됩니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 연결 된 **catch** 블록을 추가 합니다.  
  
- **Catch** 블록 대신 **finally** 블록을 사용해 보세요.  
  
## <a name="see-also"></a>참고 항목  
 [try ... catch ... finally 문](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)   
 [Error 개체](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)