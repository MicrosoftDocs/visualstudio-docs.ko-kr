---
title: CV_access_e | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1ce5997555b37cf5ab30f091e7124b5025284c0e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164380"
---
# <a name="cv_access_e"></a>CV_access_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

멤버 함수 및 변수의 표시 여부 (액세스 수준) 범위를 지정 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## <a name="elements"></a>요소  
 CV_private  
 멤버에 전용 액세스 권한이 있습니다.  
  
 CV_protected  
 멤버에 보호 된 액세스 권한이 있습니다.  
  
 CV_public  
 멤버에 공용 액세스 권한이 있습니다.  
  
## <a name="remarks"></a>설명  
 `friend`액세스 지정자는 클래스의 private 및 protected 요소 모두에 액세스할 수 있는 비 멤버 함수에서 일반적으로 사용 되기 때문에 여기에 포함 되지 않습니다. [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) 메서드를 사용 하 여 액세스 권한이 있는 기호를 찾습니다 `SymTagFriend` .  
  
## <a name="requirements"></a>요구 사항  
 헤더: cvconst  
  
## <a name="see-also"></a>관련 항목  
 [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol:: get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
