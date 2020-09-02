---
title: THUNK_ORDINAL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b98098c0b6e1de9c3c2ceda5c644bc2957ab22bd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62576410"
---
# <a name="thunk_ordinal"></a>THUNK_ORDINAL
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

썽크 유형을 지정 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef enum THUNK_ORDINAL {   
   THUNK_ORDINAL_NOTYPE,  
   THUNK_ORDINAL_ADJUSTOR,  
   THUNK_ORDINAL_VCALL,  
   THUNK_ORDINAL_PCODE,  
   THUNK_ORDINAL_LOAD   
  
   // trampoline thunk ordinals - only for use in Trampoline thunk symbols  
   THUNK_ORDINAL_TRAMP_INCREMENTAL,  
   THUNK_ORDINAL_TRAMP_BRANCHISLAND,  
} THUNK_ORDINAL;  
```  
  
## <a name="elements"></a>요소  
 THUNK_ORDINAL_NOTYPE  
 표준 썽크.  
  
 THUNK_ORDINAL_ADJUSTOR  
 `this`Adjustor 썽크입니다.  
  
 THUNK_ORDINAL_VCALL  
 가상 호출 썽크입니다.  
  
 THUNK_ORDINAL_PCODE  
 P-코드 썽크  
  
 THUNK_ORDINAL_LOAD  
 로드 썽크를 지연 합니다.  
  
 THUNK_ORDINAL_TRAMP_INCREMENTAL  
 증분 trampoline 썽크 (한 메모리 공간에서 다른 메모리 공간으로 호출을 바운스 하는 데 사용 됨)  
  
 THUNK_ORDINAL_TRAMP_BRANCHISLAND  
 분기 지점 trampoline 썽크입니다.  
  
## <a name="remarks"></a>설명  
 이 열거형의 값은 [IDiaSymbol:: get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) 메서드에 대 한 호출에서 반환 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: cvconst  
  
## <a name="see-also"></a>관련 항목  
 [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
