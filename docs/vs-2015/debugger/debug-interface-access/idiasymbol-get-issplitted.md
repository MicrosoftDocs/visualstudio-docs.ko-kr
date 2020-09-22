---
title: 'IDiaSymbol:: get_isSplitted | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isSplitted method
ms.assetid: ff160cf6-003b-4ef5-a406-20a7b287b2bf
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4b1aa0eafe321f41d5f9dcf9622e44f9079fc946
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841707"
---
# <a name="idiasymbolget_issplitted"></a>IDiaSymbol::get_isSplitted
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

데이터 기호가 다른 기호의 집계 또는 컬렉션으로 분할 되었는지 여부를 지정 하는 플래그를 검색 합니다. 컴파일러는 기호가 큰 기호의 일부인 경우에도 기호를 별도의 엔터티로 처리 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT get_isSplitted(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pFlag`  
 제한이 기호가 `TRUE` 기호의 집합체로 분할 되었으면를 반환 하 고, 그렇지 않으면를 반환 `FALSE` 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 `S_FALSE` 또는 오류 코드가 반환 됩니다.  
  
> [!NOTE]
> 반환 값은 `S_FALSE` 기호에 대해 속성을 사용할 수 없음을 의미 합니다.  
  
## <a name="remarks"></a>설명  
 [IDiaSymbol:: get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md) 메서드는 `TRUE` 분할 기호의 일부인 모든 기호에 대해를 반환 합니다.  
  
## <a name="requirements"></a>요구 사항  
  
|요구 사항|Description|  
|-----------------|-----------------|  
|헤더:|dia2.h|  
|버전:|DIA SDK v8.0|  
  
## <a name="see-also"></a>참고 항목  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)
