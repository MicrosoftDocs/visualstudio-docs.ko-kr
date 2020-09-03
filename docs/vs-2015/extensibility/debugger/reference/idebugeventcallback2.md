---
title: IDebugEventCallback2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6114a31701e5abc4714f315b4e4f1ecf022c401c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163819"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 디버그 엔진 (DE)에서 세션 디버그 관리자 (SDM)로 디버그 이벤트를 보내는 데 사용 됩니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 디버그 엔진에서 이벤트를 수신 하기 위해이 인터페이스를 구현 합니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 디버그 엔진은 일반적으로 SDM이 [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)또는 [launchsuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)를 호출할 때이 인터페이스를 수신 합니다. 디버그 엔진은 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)를 호출 하 여 이벤트를 SDM으로 보냅니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDebugEventCallback2` .  
  
|메서드|설명|  
|------------|-----------------|  
|[이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|디버깅 이벤트에 대 한 알림을 SDM에 보냅니다.|  
  
## <a name="remarks"></a>설명  
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 및 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 는 인터페이스를 사용 하도록 지정 하지만 `IDebugEventCallback2` 이는 그렇지 않으며 인터페이스 포인터는 항상 null 값이 됩니다. 대신, 디버그 엔진은 `IDebugEventCallback2` 연결에서 수신 된 인터페이스를 사용 하 여 [연결](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md)또는 [launchsuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)를 호출 해야 합니다.  
  
 패키지가 관리 코드에서 [Idebugeventcallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) 을 구현 하는 경우 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)에 전달 되는 다양 한 인터페이스에서 호출 하는 것이 좋습니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended 중단 됨](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [첨부](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md)
