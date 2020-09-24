---
title: 'IDiaSymbol:: get_typeIds | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 410f8afdac24139791c19c3936049c855a51d4f9
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "91146906"
---
# <a name="idiasymbolget_typeids"></a>IDiaSymbol::get_typeIds
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 기호에 대 한 컴파일러 관련 형식 식별자 값의 배열을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT get_typeIds (   
   DWORD  cTypeIds,  
   DWORD* pcTypeIds,  
   DWORD  typeIds[]  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `cTypeIds`  
 진행 데이터를 보관할 버퍼의 크기입니다.  
  
 `pcTypeIds`  
 제한이 는 작성 된의 수를 반환 하 고, `typeIds` `typeIds` 가 이면 `NULL` 사용 가능한 총 형식 식별자 수를 반환 합니다.  
  
 `typeIds[]`  
 제한이 형식 식별자로 채워질 배열입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 `S_FALSE` 또는 오류 코드가 반환 됩니다.  
  
> [!NOTE]
> 반환 값은 `S_FALSE` 기호에 대해 속성을 사용할 수 없음을 의미 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
