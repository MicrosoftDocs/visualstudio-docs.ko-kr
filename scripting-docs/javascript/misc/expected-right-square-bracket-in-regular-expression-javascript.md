---
title: 정규식에 '] '가 필요 합니다. (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a2a2b83b818e37c0b62e103fe284c5c4d110c6c
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815634"
---
# <a name="expected--in-regular-expression-javascript"></a>정규식에 ']'가 필요합니다.(JavaScript)
정규식 일치 항목에 대 한 문자 클래스를 만들려고 했지만 오른쪽 대괄호가 포함 되지 않았습니다. 개별 리터럴 문자 조합을 문자 클래스로 조합 하 여 대괄호 안에 배치할 수 있습니다. 문자 클래스는 포함 하는 문자 하나를 찾습니다. 예를 들어/[abc]/는 문자 "a", "b" 또는 "c" 중 하나를 찾습니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 정규식에 오른쪽 괄호를 추가 합니다.  
  
    > [!NOTE]
    > 대괄호 하나를 일치 시키려면 백슬래시를 사용 하 여 이스케이프 \\ 합니다. 그러면에서 특수 문자로 해석 되지 않습니다 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## <a name="see-also"></a>참고 항목  
 [Regular Expression 개체](../../javascript/reference/regular-expression-object-javascript.md)   
 [정규식 구문 (JavaScript)](https://msdn.microsoft.com/library/1400241x)