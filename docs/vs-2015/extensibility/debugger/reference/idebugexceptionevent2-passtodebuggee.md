---
title: IDebugExceptionEvent2::P assToDebuggee | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ecc7eb3830522cdee0022f4193482daab3780230
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150403"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

실행을 다시 시작할 때 디버깅 중인 프로그램에 예외를 전달할지 여부를 지정 합니다. 그렇지 않으면 예외를 삭제 해야 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```csharp  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `fPass`  
 진행 `TRUE`실행을 다시 시작할 때 디버깅 중인 프로그램에 예외를 전달 해야 하는 경우 0이 아닌 값이 반환 되 고, 예외를 삭제 해야 하는 경우에는 0 ( `FALSE` )입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 이 메서드를 호출 하면 디버깅 중인 프로그램에서 코드가 실행 되지 않습니다. 호출은 다음 코드 실행에 대 한 상태를 설정 하기만 하면 됩니다. 예를 들어 [Canpasstodebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) 메서드에 대 한 호출은 `S_OK` [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)와 함께 반환 될 수 있습니다.`dwState` 필드를로 설정 `EXCEPTION_STOP_SECOND_CHANCE` 합니다.  
  
 IDE는 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) 이벤트를 수신 하 고 [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md) 메서드를 호출할 수 있습니다. 메서드가 호출 되지 않는 경우 디버그 엔진 (DE)에는 대/소문자를 처리 하는 기본 동작이 있어야 합니다 `PassToDebuggee` .  
  
## <a name="see-also"></a>관련 항목  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [계속](../../../extensibility/debugger/reference/idebugprogram2-continue.md)
