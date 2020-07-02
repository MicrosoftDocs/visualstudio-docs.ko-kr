---
title: 날짜 개체가 필요 합니다. | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 969f2bcb578d74ac02a7bdaa6984de5948e49e27
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817608"
---
# <a name="date-object-expected"></a>Date 개체가 필요합니다.
이 아닌 형식의 개체에 대해 **valueOf** **메서드를 호출** 하려고 했습니다 .이 예제에서는 `Date` 이 호출 형식의 개체는 형식 이어야 합니다 `Date` . 예를 들면 다음과 같습니다.  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 형식의 개체에 대해 **valueOf** 메서드를 호출 **하기만 하면 됩니다.** `Date`  
  
## <a name="see-also"></a>참고 항목  
 [날짜 개체](../../javascript/reference/date-object-javascript.md)   
 [getDate 메서드 (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [내장 개체](../../javascript/intrinsic-objects-javascript.md)