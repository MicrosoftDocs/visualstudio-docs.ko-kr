---
title: "getUTCHours 메서드 (Date) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getUTCHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- hours
- UTC times, returning
- getUTCHours method
ms.assetid: 7c9825dd-4b3a-4614-8e09-f40df123b630
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 34a07f9f63fe22d3101cc748e9dde978385a71ab
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/17/2018
---
# <a name="getutchours-method-date-javascript"></a>getUTCHours 메서드(Date)(JavaScript)
시간 값을 가져옵니다는 `Date` utc (협정 세계시)를 사용 하 여 개체입니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
dateObj.getUTCHours()   
```  
  
#### <a name="parameters"></a>매개 변수  
 필요한 `dateObj` 참조는 `Date` 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 0과 자정 이후의 시간 수를 나타내는 23 사이의 정수를 반환 합니다. 시간은 오전 1시: 00 이전 하는 경우 0이 반환 됩니다. 경우는 `Date` 시간을 지정 하지 않고 개체를 만든 시간 UTC 시간으로 0은 기본적으로, 합니다. 이 이번에는 0 일 수 있습니다 다른 표준 시간대에 있습니다.  
  
## <a name="remarks"></a>설명  
 자정 이후 경과 된 시간의 번호를 가져오려면 현지 시간을 사용 하 여는 `getHours` 메서드.  
  
## <a name="example"></a>예제  
 다음 예제에서는 `getUTCHours` 메서드를 사용하는 방법을 보여 줍니다.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCHours());  
document.write("<br/>");  
  
var date2 = new Date("1/1/2001 11:22:33");  
document.write(date2.getUTCHours());  
  
// Output (in the PST time zone):  
// 15
// 2 
```  
  
## <a name="requirements"></a>요구 사항  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **적용 대상**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>참고 항목  
 [getHours 메서드 (Date)](../../javascript/reference/gethours-method-date-javascript.md)   
 [setHours 메서드 (Date)](../../javascript/reference/sethours-method-date-javascript.md)   
 [setUTCHours 메서드(Date)](../../javascript/reference/setutchours-method-date-javascript.md)