---
title: IDiaSymbol::get_registerId | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 580637cf1058c8bfbd10ac7812e59c802830d95e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841975"
---
# <a name="idiasymbolget_registerid"></a>IDiaSymbol::get_registerId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[LocationType 열거가](../../debugger/debug-interface-access/locationtype.md) 로 설정 된 경우 위치의 등록 지정자를 검색 `LocIsEnregistered` 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT get_registerId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pRetVal`  
 제한이 위치의 등록 지정자를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 `S_FALSE` 또는 오류 코드가 반환 됩니다.  
  
> [!NOTE]
> 반환 값은 `S_FALSE` 기호에 대해 속성을 사용할 수 없음을 의미 합니다.  
  
## <a name="remarks"></a>설명  
 기호가 레지스터를 기준으로 하는 경우, 즉 기호의 [LocationType 열거형](../../debugger/debug-interface-access/locationtype.md) 이로 설정 된 경우 메서드를 사용 하 고 `LocIsRegRel` `get_registerId` [IDiaSymbol:: get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) 메서드를 호출 하 여 기호가 있는 레지스터에서 오프셋을 가져옵니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType 열거형](../../debugger/debug-interface-access/locationtype.md)
