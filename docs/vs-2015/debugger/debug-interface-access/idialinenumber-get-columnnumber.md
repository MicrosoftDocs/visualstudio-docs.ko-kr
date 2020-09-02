---
title: 'IDiaLineNumber:: get_columnNumber | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumber method
ms.assetid: e317f29a-6525-46a7-8421-33985392f8fd
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 51763dea01039ce084804bfa007fd8f0577cb9e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192371"
---
# <a name="idialinenumberget_columnnumber"></a>IDiaLineNumber::get_columnNumber
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

식 또는 문이 시작 되는 열 번호를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
[C++]  
HRESULT get_columnNumber (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pRetVal`  
 제한이 식 또는 문이 시작 되는 열 번호를 반환 합니다. 값이 0 이면 열 정보가 없습니다.  
  
## <a name="return-value"></a>반환 값  
 성공하면 `S_OK`를 반환합니다. `S_FALSE`이 속성이 지원 되지 않으면를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.  
  
## <a name="remarks"></a>설명  
 이 메서드에서 반환 하는 열 값은 줄의 줄에 있는 문의 첫 번째 문자에 대 한 바이트 오프셋입니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
