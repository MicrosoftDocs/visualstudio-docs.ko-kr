---
description: 문을 사용 하 여 조건부 컴파일 문에서 사용할 변수를 만들려고 @set 했지만 변수 이름 앞에 @ 기호를 넣지 않았습니다.
title: "' @ '가 필요 합니다. | Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1032
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7aa02ed1e436c92014d44e57f2c71ff7db5f99b
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570624"
---
# <a name="expected-"></a>‘\@’가 필요합니다.
문을 사용 하 여 조건부 컴파일 문에서 사용할 변수를 만들려고 `@set` 했지만 **@** 변수 이름 앞에 "" 기호를 넣지 않았습니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- **@** 변수 이름 바로 앞에 "" 기호를 추가 합니다. 예를 들어:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>참조  
 [@set 선언문](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-set)   
 [조건부 컴파일](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/121hztk3(v=vs.84))   
 [조건부 컴파일 변수](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/s59bkzce(v=vs.84))
