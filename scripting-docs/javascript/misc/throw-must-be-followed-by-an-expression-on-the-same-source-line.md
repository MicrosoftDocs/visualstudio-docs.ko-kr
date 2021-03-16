---
description: Throw 키워드를 사용 했지만 동일한 소스 줄에서 식과 함께 사용 하지 않았습니다.
title: 같은 소스 줄에서 Throw 뒤에는 식이와 야 합니다. Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cfa2bace6f82ae972204cc0a405cc7e8682e98af
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570715"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>같은 소스 줄에서 throw 뒤에는 식이 와야 합니다.
`throw`키워드를 사용 했지만 동일한 소스 줄에서 식과 함께 사용 하지 않았습니다. `throw`문은 `throw` 키워드와 throw 될 식이 차례로 오는 두 부분으로 구성 됩니다. 예를 들어:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 이러한 두 구성 요소는 분할할 수 없습니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- `throw`키워드와 throw 되는 식이 같은 줄에 표시 되는지 확인 합니다.  
  
## <a name="see-also"></a>참조  
 [Error 개체](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)   
 [throw 문](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/throw)   
 [try ... catch ... finally 문](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)
