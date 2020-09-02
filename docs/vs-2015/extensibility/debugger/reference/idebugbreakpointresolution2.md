---
title: IDebugBreakpointResolution2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBreakpointResolution2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 451d5bce-b9c1-48ff-beaa-2b4c3e1ceea0
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 031d8ffab94239c6169a61f3748172787267043c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160079"
---
# <a name="idebugbreakpointresolution2"></a>IDebugBreakpointResolution2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 바인딩된 중단점을 설명 하는 정보를 나타냅니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugBreakpointResolution2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 DE (디버그 엔진)는 중단점에 대 한 지원의 일부로이 인터페이스를 구현 합니다. 이 인터페이스는 사용자가 중단점의 속성을 볼 때 세션 디버그 관리자에서 사용 하는 바인딩된 중단점에 대 한 설명을 제공 합니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 [Get간 Pointresolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) 을 호출 하면이 인터페이스가 반환 됩니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDebugBreakpointResolution2` .  
  
|메서드|설명|  
|------------|-----------------|  
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|이 해상도로 표시 되는 중단점의 형식을 가져옵니다.|  
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|이 중단점을 설명 하는 중단점 확인 정보를 가져옵니다.|  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)
