---
title: IDebugBreakpointRequest2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 263b947fff45eafd2d2e5afc029572b69ea24b82
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158775"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 모든 중단점 형식을 만들고 바인딩하는 데 필요한 정보를 나타냅니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugBreakpointRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 세션 디버그 관리자 (SDM)는 일반적으로이 인터페이스를 구현 합니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 DE (디버그 엔진)는 보류 중인 중단점을 만들기 위해 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) 호출을 통해이 인터페이스를 수신 합니다. [Get간 Pointrequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) 에 대 한 호출은 DE에서이 인터페이스를 검색할 수 있습니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDebugBreakpointRequest2` .  
  
|메서드|설명|  
|------------|-----------------|  
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|이 중단점 요청의 중단점 위치 유형을 가져옵니다.|  
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|이 중단점 요청을 설명 하는 중단점 요청 정보를 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 디버그 중인 프로그램이 로드 되 면 [바인드](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) 를 호출 하 여 보류 중인 중단점을 프로그램의 요청 된 위치에 바인딩합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [Get간의 Pointrequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)   
 [바인딩하며](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
