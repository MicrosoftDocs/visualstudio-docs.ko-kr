---
title: 함수에 유효한 프로토타입 개체가 없습니다. | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15b00087cd66b873044b7bafb1bfecf4fc91f8d9
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862394"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>함수에 올바른 프로토타입 개체가 없습니다.
**Instanceof** 를 사용 하 여 개체가 특정 함수 클래스에서 파생 되었는지 여부를 확인 하려고 했지만 개체의 `prototype` 속성 `null` 을 또는 외부 개체 형식 (유효 하지 않은 개체 모두)으로 다시 정의 했습니다 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] . 외부 개체는 호스트 개체 모델의 개체 (예: Internet Explorer의 문서 또는 창 개체) 나 외부 COM 개체 일 수 있습니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 함수의 `prototype` 속성이 유효한 개체를 참조 하는지 확인 합니다 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## <a name="see-also"></a>참고 항목  
 [Function 개체](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [prototype 속성(Object)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)