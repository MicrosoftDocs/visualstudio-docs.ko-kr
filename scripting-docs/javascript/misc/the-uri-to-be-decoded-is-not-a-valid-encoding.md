---
title: 디코딩할 URI가 올바른 인코딩이 아닙니다. | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38ea642cece501804b6ee2efaac778c3b8d520fc
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861861"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>디코딩할 URI가 올바른 인코딩이 아닙니다.
잘못 된 형식의 URI (Uniform Resource Identifier)를 디코드 하려고 했습니다. Uri에는 특수 구문이 있습니다. 영숫자가 아닌 대부분의 문자는 URI에서 사용할 수 있으려면 인코딩해야 합니다. 및 메서드를 사용 `encodeURI` `encodeURIComponent` 하 여 일반 문자열에서 URI를 만들 수 있습니다 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
 전체 URI는 구성 요소 및 구분 기호의 시퀀스로 구성 됩니다. 일반적인 형식은 다음과 같습니다.  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 꺾쇠 괄호 안의 이름은 구성 요소를 나타내고, ":", "/", ";" 및 "?"는 구분 기호로 사용 되는 예약 된 문자입니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 유효한 Uri만 디코딩하 려 고 하는지 확인 합니다. 일반 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 문자열에는 잘못 된 문자가 포함 될 수 있으므로 디코딩할 수 없습니다.  
  
## <a name="see-also"></a>참고 항목  
 [decodeURI 함수](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/decodeuri)   
 [decodeURIComponent 함수](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/decodeuricomponent)