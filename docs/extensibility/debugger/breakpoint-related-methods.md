---
title: 중단점 관련 방법 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72ec63e500ac86a4a5bd66a2956fe0fb06c8834
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739202"
---
# <a name="breakpoint-related-methods"></a>중단점 관련 방법
디버그 엔진(DE)은 중단점 설정을 지원해야 합니다. Visual Studio 디버깅은 다음과 같은 유형의 중단점을 지원합니다.

- Bound

     UI를 통해 요청되고 지정된 코드 위치에 성공적으로 바인딩됨

- Pending

     UI를 통해 요청되었지만 아직 실제 지침에 바인딩되지 않음

## <a name="discussion"></a>토론
 예를 들어 명령이 아직 로드되지 않은 경우 보류 중인 중단점이 발생합니다. 코드가 로드되면 보류 중인 중단점은 지정된 위치, 즉 코드에 중단 명령을 삽입하기 위해 코드에 바인딩하려고 시도합니다. 이벤트는 성공적인 바인딩을 나타내거나 바인딩 오류가 있음을 알리기 위해 세션 디버그 관리자(SDM)로 전송됩니다.

 보류 중인 중단점은 해당 바인딩 중단점의 자체 내부 목록도 관리합니다. 보류 중인 중단점이 하나되면 코드에 여러 중단점이 삽입될 수 있습니다. Visual Studio 디버깅 UI는 보류 중인 중단점과 해당 바인딩 중단점에 대한 트리 보기를 표시합니다.

 보류 중인 중단점을 만들고 사용하려면 [IDebugEngine2:CreatePending중단점](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) 메서드와 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 인터페이스의 다음 메서드를 구현해야 합니다.

|방법|설명|
|------------|-----------------|
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|지정된 보류 중인 중단점이 코드 위치에 바인딩할 수 있는지 여부를 결정합니다.|
|[바인딩](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|지정된 보류 중인 중단점을 하나 이상의 코드 위치에 바인딩합니다.|
|[겟스테이트](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|보류 중인 중단점의 상태를 가져옵니다.|
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|보류 중인 중단점을 만드는 데 사용되는 중단점 요청을 가져옵니다.|
|[사용](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|보류 중인 중단점의 사용 상태를 전환합니다.|
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|보류 중인 중단점에서 바인딩된 모든 중단점을 모두 확대합니다.|
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|보류 중인 중단점으로 인해 발생하는 모든 오류 중단점을 에대한 값으로 보그는 것입니다.|
|[삭제](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|보류 중인 중단점과 바인딩된 모든 중단점을 삭제합니다.|

 바인딩된 중단점 및 오류 중단점을 열거하려면 [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) 및 [IEnumDebugErrorBreakpoints2의](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)모든 메서드를 구현해야 합니다.

 코드 위치에 바인딩되는 보류 중인 중단점은 다음 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) 메서드를 구현해야 합니다.

|방법|설명|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|중단점을 포함하는 보류 중인 중단점을 가져옵니다.|
|[겟스테이트](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|바인딩된 중단점의 상태를 가져옵니다.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|중단점을 설명하는 중단점 확인을 가져옵니다.|
|[사용](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|중단점을 활성화하거나 사용하지 않도록 설정합니다.|
|[삭제](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|바인딩된 중단점을 삭제합니다.|

 확인 및 요청 정보는 다음 [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) 메서드의 구현이 필요합니다.

|방법|설명|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|해상도로 표시되는 중단점의 유형을 가져옵니다.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|중단점을 설명하는 중단점 확인 정보를 가져옵니다.|

 바인딩 중에 발생할 수 있는 오류를 해결하려면 다음 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) 메서드를 구현해야 합니다.

|방법|설명|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|오류 중단점을 포함하는 보류 중인 중단점을 가져옵니다.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|오류 중단점을 설명하는 중단점 오류 확인을 가져옵니다.|

 바인딩 중에 발생할 수 있는 오류 해결에는 다음 메서드인 [IDebugErrorBreakpointResolution2가](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)필요합니다.

|방법|설명|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|중단점의 형식을 가져옵니다.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|중단점의 해결 정보를 가져옵니다.|

 중단점에서 소스 코드를 확인하려면 [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) 및/또는 [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)의 메서드 메서드를 구현해야 합니다.

## <a name="see-also"></a>참조
- [실행 제어 및 상태 평가](../../extensibility/debugger/execution-control-and-state-evaluation.md)
