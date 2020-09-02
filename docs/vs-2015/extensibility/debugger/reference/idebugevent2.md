---
title: IDebugEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f663be5910b342a6adba5da0b84d7e0d80cacc10
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695407"
---
# <a name="idebugevent2"></a>IDebugEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 중단점에서 중지와 같은 중요 한 디버그 정보와 디버깅 메시지와 같은 중요 하지 않은 정보를 모두 전달 하는 데 사용 됩니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 DE (디버그 엔진) 및 사용자 지정 포트 공급자는 다른 모든 이벤트 인터페이스와 동일한 개체에서이 인터페이스를 구현 합니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 또는 [이벤트](../../../extensibility/debugger/reference/idebugportevents2-event.md)에 지정 된 IID (인터페이스 ID) 인수를 사용 하 여, 세션 디버그 관리자 (SDM)는 인터페이스에서 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 를 호출 `IDebugEvent2` 하 여 적절 한 이벤트 인터페이스를 가져옵니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDebugEvent2` .  
  
|메서드|설명|  
|------------|-----------------|  
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|이 디버그 이벤트의 특성을 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)와 같은 보다 구체적인 이벤트 인터페이스는 IDebugEvent2 인터페이스에서 파생 되지 않지만 대신와 동일한 개체에서 별도의 인터페이스로 구현 됩니다 `IDebugEvent2` .  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [이벤트](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
