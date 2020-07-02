---
title: 종결 되지 않은 주석 | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d4286315-814b-4966-b4c4-1ee19d796eff
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16f675cb62c0c3fd5f3aba7ba6190427fe101353
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85814805"
---
# <a name="unterminated-comment"></a>종결되지 않은 주석입니다.
여러 줄 주석 블록을 시작 했지만 제대로 종료 되지 않았습니다. 여러 줄 주석은 "/*" 조합으로 시작 하 고 역방향 " \* /" 조합으로 끝납니다. 다음은 예입니다.  
  
```JavaScript  
/* This is a comment  
This is another part of the same comment.*/  
```  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- "*/"를 사용 하 여 여러 줄로 된 주석을 종료 해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Comment 문](../../javascript/reference/comment-statements-javascript.md)