---
title: EVALFLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9e6ee00402c13b2a79e4e6757a127211eda9c3c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149380"
---
# <a name="evalflags"></a>EVALFLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

식 계산을 제어 하는 플래그를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
};  
typedef DWORD EVALFLAGS;  
```  
  
```csharp  
public enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
}  
```  
  
## <a name="members"></a>멤버  
 EVAL_RETURNVALUE  
 반환 값 (있는 경우)을 계산 하도록 지정 합니다.  
  
 EVAL_NOSIDEEFFECTS  
 의도 하지 않은 결과를 허용 하지 않도록 지정 합니다.  
  
 EVAL_ALLOWBPS  
 중단점에 대 한 중지를 지정 합니다.  
  
 EVAL_ALLOWERRORREPORT  
 허용 되는 호스트에 대 한 오류 보고를 지정 합니다. 주로 Internet Explorer의 스크립트에서 식 계산에 사용 됩니다.  
  
 EVAL_FUNCTION_AS_ADDRESS  
 함수를 호출 하는 대신 함수를 주소로 계산 합니다.  
  
 EVAL_NOFUNCEVAL  
 함수가 계산 되지 않도록 합니다. 예를 들어 `int` 식의 토큰을 고려 `myExpression(int) + 10` 합니다. 이 함수는 값이 아니라 주소로 올바르게 계산 될 수 있습니다.  
  
 EVAL_NOEVENTS  
 식 평가 중에 발생 하는 이벤트를 세션 디버그 관리자 (SDM) 또는 IDE로 보내지 않아야 함을 나타내는 플래그입니다.  
  
## <a name="remarks"></a>설명  
 이러한 플래그는 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 및 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 메서드에 인수로 전달 됩니다.  
  
 이러한 플래그는 비트 or와 함께 사용할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
