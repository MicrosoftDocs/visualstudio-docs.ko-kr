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
ms.openlocfilehash: ca6f13620bb486cf1663bd5bef9a9a93b2c8a480
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817361"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>함수에 올바른 프로토타입 개체가 없습니다.
**Instanceof** 를 사용 하 여 개체가 특정 함수 클래스에서 파생 되었는지 여부를 확인 하려고 했지만 개체의 `prototype` 속성 `null` 을 또는 외부 개체 형식 (유효 하지 않은 개체 모두)으로 다시 정의 했습니다 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] . 외부 개체는 호스트 개체 모델의 개체 (예: Internet Explorer의 문서 또는 창 개체) 나 외부 COM 개체 일 수 있습니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 함수의 `prototype` 속성이 유효한 개체를 참조 하는지 확인 합니다 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## <a name="see-also"></a>참고 항목  
 [Function 개체](../../javascript/reference/function-object-javascript.md)   
 [prototype 속성(Object)](../../javascript/reference/prototype-property-object-javascript.md)