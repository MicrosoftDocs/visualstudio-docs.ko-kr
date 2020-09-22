---
title: CV_call_e | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cd1ee4c024894e5752277a5000d37745c88c4ac6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841862"
---
# <a name="cv_call_e"></a>CV_call_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

함수에 대 한 호출 규칙을 지정 합니다.  
  
> [!NOTE]
> 가장 일반적인 열거형 값만 여기에 설명 되어 있습니다. 전체 열거형은 cvconst 헤더 파일에서 사용할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
typedef enum CV_call_e {   
   CV_CALL_NEAR_C    = 0x00,  
   CV_CALL_NEAR_FAST = 0x04,  
   CV_CALL_NEAR_STD  = 0x07,  
   CV_CALL_NEAR_SYS  = 0x09,  
   CV_CALL_THISCALL  = 0x0b,  
   CV_CALL_CLRCALL   = 0x16  
} CV_call_e;  
```  
  
## <a name="elements"></a>요소  
 CV_CALL_NEAR_C  
 오른쪽에서 왼쪽으로 가까운 푸시를 사용 하 여 함수 호출 규칙을 지정 합니다. 호출 함수는 스택을 지웁니다.  
  
 CV_CALL_NEAR_FAST  
 레지스터를 사용 하 여 왼쪽에서 오른쪽으로 가까운 푸시를 사용 하 여 함수 호출 규칙을 지정 합니다. 호출 된 함수는 매개 변수 바이트의 합계를 사용 하 여 스택을 지웁니다.  
  
 CV_CALL_NEAR_STD  
 근거리 표준 호출 (오른쪽에서 왼쪽 푸시)을 사용 하 여 함수 호출 규칙을 지정 합니다.  
  
 CV_CALL_NEAR_SYS  
 Near 시스템 호출을 사용 하 여 함수 호출 규칙을 지정 합니다.  
  
 CV_CALL_THISCALL  
 `this`호출 ( `this` register에서 포인터가 전달)을 사용 하 여 함수 호출 규칙을 지정 합니다.  
  
 CV_CALL_CLRCALL  
 관리 코드 호출 규칙이 라고도 하는 CLR (공용 언어 런타임)에서 사용 하는 함수 호출 규칙을 지정 합니다.  
  
## <a name="remarks"></a>설명  
 이 열거형의 값은 [IDiaSymbol:: get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) 메서드를 호출 하 여 반환 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: cvconst  
  
## <a name="see-also"></a>참고 항목  
 [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
