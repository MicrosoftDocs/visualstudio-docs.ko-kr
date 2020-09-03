---
title: 예기치 않은 수량자 (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da4ff08ae667b868670364c7ad6b9a6b69ae6ad3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815333"
---
# <a name="unexpected-quantifier-javascript"></a>예기치 않은 수량자입니다.(JavaScript)
정규식 검색 패턴을 작성할 때 잘못 된 반복 요인이 있는 pattern 요소를 만들었습니다. 예를 들어 패턴  
  
```js
/^+/  
```  
  
 ^ (입력의 시작) 요소에 반복 요인이 있을 수 없기 때문에이 잘못 되었습니다. 다음 표에서는 반복 요소가 없을 수 있는 요소를 나열 합니다.  
  
|요소|설명|  
|-------------|-----------------|  
|^|입력 시작|  
|$|입력 끝|  
|\b|단어 경계|  
|\B|비단어 경계|  
|*|0 개 이상의 반복|  
|+|하나 이상의 반복|  
|?|0 회 또는 1 회 반복|  
|개의|n 회 반복|  
|{n,}|n 개 이상의 반복|  
|{n, m}|N 개에서 m 회 반복 (포함)|  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 검색 패턴 요소에 올바른 반복 요소만 포함 되어 있는지 확인 합니다.  
  
## <a name="see-also"></a>추가 정보  
 [Regular Expression 개체](../../javascript/reference/regular-expression-object-javascript.md)   
 [정규식 구문 (JavaScript)](https://msdn.microsoft.com/library/1400241x)