---
description: 잘못 된 문자 집합 범위가 포함 된 정규식을 만들려고 했습니다.
title: 문자 집합의 범위가 잘못 되었습니다. (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5021
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9441f9cfd3adf94ddd38841d522c83922c9154f1
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571677"
---
# <a name="invalid-range-in-character-set-javascript"></a>문자 집합의 범위가 잘못되었습니다.(JavaScript)
잘못 된 문자 집합 범위가 포함 된 정규식을 만들려고 했습니다. 문자 집합은 단일 문자 (예: a-z 또는 0-9)의 범위 여야 합니다. \w와 같은 문자 클래스는 문자 집합에 포함할 수 없습니다. 범위의 첫 번째 문자는 범위의 두 번째 문자 앞에와 야 합니다. 예를 들어:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 단일 문자만 사용 하 여 정규식 문자 집합을 작성 하 고 올바른 순서로 되어 있는지 확인 합니다.  
  
## <a name="see-also"></a>참조  
 [Regular Expression 개체](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [정규식 구문 (JavaScript)](/previous-versions/1400241x(v=vs.100))
