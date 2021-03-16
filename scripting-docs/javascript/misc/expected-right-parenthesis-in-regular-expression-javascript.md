---
description: 정규식 캡처, 어설션 또는 그룹을 만들려고 했지만 닫는 괄호는 포함 되지 않았습니다.
title: 정규식에 ') '가 필요 합니다. (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4504a637625a1f15de12a721eb6fcba5dbc7fa6a
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571703"
---
# <a name="expected--in-regular-expression-javascript"></a>정규식에 ')'가 필요합니다.(JavaScript)
정규식 캡처, 어설션 또는 그룹을 만들려고 했지만 닫는 괄호는 포함 되지 않았습니다. 괄호는 정규식에서 여러 가지 용도로 사용 됩니다. 주로 이러한 항목은 하위 식을 캡처하고, 어설션을 지정 하거나, *, +,? 등을 기준으로 항목을 단일 단위로 처리할 수 있도록 패턴을 그룹화 하는 데 사용 됩니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 오른쪽에 닫는 괄호를 추가 합니다.  
  
    > [!NOTE]
    > 단일 괄호를 일치 시키려는 경우에는를 사용 하 \\ 여 특수 문자로 해석 되지 않도록 백슬래시를 사용 하 여 이스케이프 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 합니다.  
  
## <a name="see-also"></a>참조  
 [Regular Expression 개체](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [정규식 구문 (JavaScript)](/previous-versions/1400241x(v=vs.100))
