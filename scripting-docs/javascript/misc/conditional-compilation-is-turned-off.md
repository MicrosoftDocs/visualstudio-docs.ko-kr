---
description: 먼저 조건부 컴파일을 설정 하지 않고 조건부 컴파일 변수를 사용 하려고 했습니다.
title: 조건부 컴파일이 꺼져 있습니다. | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ccda9769597d6a981a9277d2b1e1f54b73d6ae18
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571430"
---
# <a name="conditional-compilation-is-turned-off"></a>조건부 컴파일이 해제되었습니다.
먼저 조건부 컴파일을 설정 하지 않고 조건부 컴파일 변수를 사용 하려고 했습니다. 조건부 컴파일을 켜면 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 컴파일러가 @로 시작 하는 식별자를 조건부 컴파일 변수로 해석 합니다. 이렇게 하려면 다음과 같이 문을 사용 하 여 조건부 코드를 시작 합니다.  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 조건부 코드의 시작 부분에 다음 문을 추가 합니다.  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>참조  
 [조건부 컴파일](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/121hztk3(v=vs.84))   
 [조건부 컴파일 변수](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/s59bkzce(v=vs.84))   
 [@cc_on 선언문](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-cc-on)   
 [@if 선언문](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-if)   
 [@set 선언문](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-set)
