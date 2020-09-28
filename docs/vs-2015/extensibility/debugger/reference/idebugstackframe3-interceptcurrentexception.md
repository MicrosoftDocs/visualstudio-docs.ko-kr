---
title: 'IDebugStackFrame3:: InterceptCurrentException | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42472690431d48a9baafbb0abee27c1a07d24fcd
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "91403857"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

현재 예외를 가로채 려는 경우 현재 스택 프레임에서 디버거에 의해 호출 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT InterceptCurrentException(  
   INTERCEPT_EXCEPTION_ACTION dwFlags,  
   UINT64*                    pqwCookie  
);  
```  
  
```csharp  
int InterceptCurrentException(  
   uint dwFlags,   
   out  ulong pqwCookie  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwFlags`  
 진행 다른 동작을 지정 합니다. 현재 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) 값만 `IEA_INTERCEPT` 지원 되며 반드시 지정 해야 합니다.  
  
 `pqwCookie`  
 제한이 특정 예외를 식별 하는 고유 값입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.  
  
 가장 일반적으로 발생 하는 오류는 다음과 같습니다.  
  
|오류|Description|  
|-----------|-----------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|현재 예외를 가로챌 수 없습니다.|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|현재 실행 프레임은 처리기에 대해 아직 검색 되지 않았습니다.|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|이 메서드는이 프레임에 대해 지원 되지 않습니다.|  
  
## <a name="remarks"></a>설명  
 예외가 throw 되 면 디버거는 예외 처리 프로세스 중 키 지점에서 런타임에 대 한 제어권을 얻습니다. 이러한 키를 잠시 동안 디버거는 프레임에서 예외를 가로채 려는 경우 현재 스택 프레임을 요청할 수 있습니다. 이러한 방식으로 가로채기 예외는 스택 프레임에 예외 처리기가 없는 경우에도 기본적으로 스택 프레임에 대 한 즉석 예외 처리기입니다 (예: 프로그램 코드의 try/catch 블록).  
  
 디버거가 예외를 가로채 야 하는지 확인 하려는 경우 현재 스택 프레임 개체에 대해이 메서드를 호출 합니다. 이 메서드는 예외의 모든 세부 정보를 처리 합니다. [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) 인터페이스가 구현 되지 않았거나 `InterceptStackException` 메서드에서 오류를 반환 하는 경우 디버거는 일반적으로 예외 처리를 계속 합니다.  
  
> [!NOTE]
> 예외는 관리 코드, 즉 디버깅 중인 프로그램이 .NET 런타임에서 실행 되는 경우에만 가로챌 수 있습니다. 물론 타사 언어 구현자는 `InterceptStackException` 사용자가 선택 하는 경우 자체 디버그 엔진에서를 구현할 수 있습니다.  
  
 가로채기가 완료 되 면 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) 가 신호를 받을 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
