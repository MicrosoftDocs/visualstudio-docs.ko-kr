---
title: 치환 인수가 잘못 되었습니다. | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4727186f-facd-4aa6-9447-bbefbae83f07
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 452af60c37e4a56996438cc2957e9b69ccee98ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816828"
---
# <a name="invalid-replacer-argument"></a>치환 인수가 잘못되었습니다.
`JSON.stringify`잘못 된 인수를 사용 하 여를 호출 하려고 한 경우 `replacer`인수는 함수 또는 배열 이어야 합니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 인수를 `replacer` 함수 또는 배열로 변경 합니다.  
  
## <a name="example"></a>예  
 이 예제의 코드에서는 `memberfilter` 가 함수 또는 배열이 아닌 개체 이기 때문에 런타임 오류가 발생 합니다.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Object();  
  
// This line will cause a runtime error.  
var jsontext = JSON.stringify(contact, memberfilter, "\t");  
```  
  
## <a name="see-also"></a>추가 정보  
 [JSON 개체](../../javascript/reference/json-object-javascript.md)   
 [JSON 함수](../../javascript/reference/json-parse-function-javascript.md)   
 [JavaScript 런타임 오류](../../javascript/reference/javascript-run-time-errors.md)