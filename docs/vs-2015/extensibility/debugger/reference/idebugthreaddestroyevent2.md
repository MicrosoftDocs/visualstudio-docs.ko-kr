---
title: IDebugThreadDestroyEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThreadDestroyEvent2
helpviewer_keywords:
- IDebugThreadDestroyEvent2
ms.assetid: fca3f603-9432-457b-9ddd-8b0ec17da046
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 837fba4afa64c0627fcac7ab9d904ef41c00e27a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704793"
---
# <a name="idebugthreaddestroyevent2"></a>IDebugThreadDestroyEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 스레드 실행이 완료 될 때 디버그 엔진 (DE)에서 세션 디버그 관리자 (SDM)로 전송 됩니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugThreadDestroyEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 DE는이 인터페이스를 구현 하 여 스레드가 종료 되었음을 보고 합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는이 인터페이스와 동일한 개체에서 구현 되어야 합니다. SDM은 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 를 사용 하 여 `IDebugEvent2` 인터페이스에 액세스 합니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 DE는 스레드가 종료 되었음을 보고 하기 위해이 이벤트 개체를 만들어 보냅니다. 이벤트는 디버깅 중인 프로그램에 연결 될 때 SDM에서 제공 하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용 하 여 보냅니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDebugThreadDestroyEvent2` .  
  
|메서드|설명|  
|------------|-----------------|  
|[GetExitCode](../../../extensibility/debugger/reference/idebugthreaddestroyevent2-getexitcode.md)|스레드의 종료 코드를 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 Visual Studio는이 이벤트를 사용 하 여 **스레드** 창을 업데이트 합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
