---
title: 중단점 관련 메서드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 47ba1529521fdce042512a38d32ad2ca2eb3cb82
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146435"
---
# <a name="breakpoint-related-methods"></a>중단점 관련 메서드
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

디버그 엔진 (DE)은 중단점의 설정을 지원 해야 합니다. Visual Studio 디버깅은 다음과 같은 중단점 형식을 지원 합니다.  
  
- Bound  
  
     UI를 통해 요청 되 고 지정 된 코드 위치에 바인딩 되었습니다.  
  
- 보류 중  
  
     UI를 통해 요청 되었지만 실제 명령에 아직 바인딩되어 있지 않습니다.  
  
## <a name="discussion"></a>토론(Discussion)  
 예를 들어 명령이 아직 로드 되지 않은 경우 보류 중인 중단점이 발생 합니다. 코드를 로드할 때 보류 중인 중단점은 지정 된 위치 (즉, 코드에 중단 명령 삽입)에서 코드에 바인딩하려를 시도 합니다. 이벤트는 성공적인 바인딩을 나타내기 위해 세션 디버그 관리자 (SDM)에 전송 되거나, 바인딩 오류가 있음을 알리기 위해 전송 됩니다.  
  
 보류 중인 중단점은 해당 하는 바인딩된 중단점의 내부 목록도 관리 합니다. 보류 중인 중단점 하나를 통해 코드에 많은 중단점이 삽입 될 수 있습니다. Visual Studio 디버깅 UI는 보류 중인 중단점과 해당 바인딩된 중단점의 트리 뷰를 보여 줍니다.  
  
 보류 중인 중단점을 만들고 사용 하려면 [IDebugEngine2:: CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) 메서드를 구현 하 고 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 인터페이스의 다음 메서드를 구현 해야 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|지정 된 보류 중인 중단점이 코드 위치에 바인딩할 수 있는지 여부를 확인 합니다.|  
|[바인딩하며](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|지정 된 보류 중인 중단점을 하나 이상의 코드 위치에 바인딩합니다.|  
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|보류 중인 중단점의 상태를 가져옵니다.|  
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|보류 중인 중단점을 만드는 데 사용 되는 중단점 요청을 가져옵니다.|  
|[사용](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|보류 중인 중단점의 활성화 상태를 전환 합니다.|  
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|보류 중인 중단점에서 바인딩된 모든 중단점을 열거 합니다.|  
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|보류 중인 중단점에서 발생 하는 모든 오류 중단점을 열거 합니다.|  
|[Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|보류 중인 중단점과이 중단점에서 바인딩된 모든 중단점을 삭제 합니다.|  
  
 바인딩된 중단점과 오류 중단점을 열거 하려면 [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) 및 of [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)의 모든 메서드를 구현 해야 합니다.  
  
 코드 위치에 바인딩하는 보류 중단점은 다음 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) 메서드를 구현 해야 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|중단점을 포함 하는 보류 중인 중단점을 가져옵니다.|  
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|바인딩된 중단점의 상태를 가져옵니다.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|중단점을 설명 하는 중단점 확인을 가져옵니다.|  
|[사용](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|중단점을 사용 하거나 사용 하지 않도록 설정 합니다.|  
|[Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|바인딩된 중단점을 삭제 합니다.|  
  
 해결 및 요청 정보는 다음 [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) 메서드를 구현 해야 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|해상도로 표시 되는 중단점의 형식을 가져옵니다.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|중단점을 설명 하는 중단점 확인 정보를 가져옵니다.|  
  
 바인딩 중 발생할 수 있는 오류를 해결 하려면 다음 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) 메서드를 구현 해야 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|오류 중단점을 포함 하는 보류 중인 중단점을 가져옵니다.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|오류 중단점을 설명 하는 중단점 오류 확인을 가져옵니다.|  
  
 바인딩 중에 발생할 수 있는 오류를 해결 하려면 다음 [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)메서드를 사용 해야 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|중단점의 형식을 가져옵니다.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|중단점에 대 한 확인 정보를 가져옵니다.|  
  
 중단점에서 소스 코드를 보려면 [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) 및/또는 [IDebugStackFrame2:: GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)메서드의 메서드를 구현 해야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [실행 제어 및 상태 평가](../../extensibility/debugger/execution-control-and-state-evaluation.md)
