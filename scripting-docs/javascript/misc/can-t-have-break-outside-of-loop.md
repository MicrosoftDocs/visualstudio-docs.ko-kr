---
title: 루프 외부에 ' break '를 사용할 수 없습니다. | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee177c8070fc5af8123d7fd78e69b1f767a5b700
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862798"
---
# <a name="cant-have-break-outside-of-loop"></a>루프 외부에서 'break'를 사용할 수 없습니다.
루프 외부에서 **break** 키워드를 사용 하려고 했습니다. **Break** 키워드는 루프 또는 문을 종료 하는 데 사용 됩니다 `switch` . 루프 또는 문의 본문에 포함 되어야 합니다 `switch` . 그러나 **레이블은** break 키워드 뒤에 올 수 있습니다.  
  
```js
break labelname;  
```  
  
 중첩 된 루프 또는 문을 사용 하 고 가장 안쪽에 있지 않은 루프를 중단 해야 하는 경우에만 **break** 키워드의 레이블이 지정 된 형식이 필요 `switch` 합니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- **Break** 키워드가 바깥쪽 루프 또는 switch 문 내에 표시 되는지 확인 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [break 문](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/break)   
 [프로그램 흐름 제어](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)   
 [스크립트 문제 해결](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/What_went_wrong)