---
title: BasicType | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 38de89b9774ac20f67b91e4ba864534122f4cdb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62580839"
---
# <a name="basictype"></a>BasicType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

기호의 기본 유형을 지정 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum BasicType {   
   btNoType   = 0,  
   btVoid     = 1,  
   btChar     = 2,  
   btWChar    = 3,  
   btInt      = 6,  
   btUInt     = 7,  
   btFloat    = 8,  
   btBCD      = 9,  
   btBool     = 10,  
   btLong     = 13,  
   btULong    = 14,  
   btCurrency = 25,  
   btDate     = 26,  
   btVariant  = 27,  
   btComplex  = 28,  
   btBit      = 29,  
   btBSTR     = 30,  
   btHresult  = 31  
};  
```  
  
## <a name="elements"></a>요소  
 btNoType  
 기본 형식을 지정 하지 않았습니다.  
  
 btVoid  
 기본 형식은 `void` 입니다.  
  
 btChar  
 기본 형식은 `char` (c/c + + 형식)입니다.  
  
 btWChar  
 기본 형식은 와이드 (유니코드) 문자 ( `WCHAR` )입니다.  
  
 btInt  
 기본 형식은 `signed int` (C/c + + 형식)입니다.  
  
 btUInt  
 기본 형식은 `unsigned int` (C/c + + 형식)입니다.  
  
 btFloat  
 기본 형식은 부동 소수점 숫자 ( `FLOAT` )입니다.  
  
 btBCD  
 기본 형식은 이진으로 코딩 된 10 진수 ( `BCD` )입니다.  
  
 btBool  
 기본 형식은 부울 ( `BOOL` )입니다.  
  
 btLong  
 기본 형식은 `long int` (c/c + + 형식)입니다.  
  
 btULong  
 기본 형식은 `unsigned long int` (C/c + + 형식)입니다.  
  
 btCurrency  
 기본 형식은 currency입니다.  
  
 btDate  
 기본 형식은 날짜/시간 ( `DATE` )입니다.  
  
 btVariant  
 기본 유형은 변수 유형 구조 ()입니다 `VARIANT` .  
  
 btComplex  
 기본 형식은 복소수입니다.  
  
 btBit  
 기본 형식은 bit입니다.  
  
 btBSTR  
 기본 형식은 기본 또는 이진 문자열 ()입니다 `BSTR` .  
  
 btHresult  
 기본 형식은 `HRESULT` 입니다.  
  
## <a name="remarks"></a>설명  
 이 열거형의 값은 [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) 메서드에서 반환 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: cvconst  
  
## <a name="see-also"></a>관련 항목  
 [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
