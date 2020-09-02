---
title: 'IDiaStackFrame:: get_systemExceptionHandling | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_systemExceptionHandling
ms.assetid: c76cf265-dea0-4159-883f-32b50bbef044
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a9c78aa32e0d1fab892738e6c2a9fc73cb14d8f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144755"
---
# <a name="idiastackframeget_systemexceptionhandling"></a>IDiaStackFrame::get_systemExceptionHandling
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

시스템 예외 처리가 적용 되는지 여부를 나타내는 플래그를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT get_systemExceptionHandling (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pRetVal`  
 제한이 `TRUE` 이 프레임에 대해 시스템 예외 처리가 적용 되 면이 고, 그렇지 않으면를 반환 `FALSE` 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공하면 `S_OK`를 반환합니다. `S_FALSE`속성이 지원 되지 않으면를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.  
  
## <a name="remarks"></a>설명  
 시스템 예외 처리는 구조화 된 예외 처리 라고도 합니다. 이는 c + + 예외 처리와 동일 하지 않습니다.  
  
 C + + 예외 처리가 적용 되는지 확인 하려면 [IDiaStackFrame:: get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-cplusplusexceptionhandling.md) 메서드를 호출 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackFrame::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-cplusplusexceptionhandling.md)
