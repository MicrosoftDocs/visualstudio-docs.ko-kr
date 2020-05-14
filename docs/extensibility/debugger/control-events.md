---
title: 이벤트 제어 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc2c3ad9c9b63923bdf2f107e7bc582f3c76cd62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739093"
---
# <a name="control-events"></a>이벤트 제어
프로그램을 제어하는 실행 중에 이벤트를 보내야 합니다. 모든 이벤트는 [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) 인터페이스를 사용하여 전송되며 [IDebugEvent2:GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) 메서드를 구현해야 하는 특성이 있습니다.

## <a name="additional-methods"></a>추가 방법
 일부 이벤트는 다음과 같이 추가 메서드를 구현해야 합니다.

- 디버그 엔진(DE)이 초기화될 때 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 인터페이스를 보내려면 [IDebugEngineCreateEvent2:GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) 메서드를 구현해야 합니다.

- 실행 제어에는 [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) 및[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) 인터페이스와 같은 제어 이벤트를 구현해야 합니다. **IDebugBreakEvent2는** 비동기 중단에만 필요합니다.

- 함수를 단계별로 실행하려면 [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) 인터페이스와 해당 메서드를 구현해야 합니다.

  중단점에서 파생된 이벤트에는 [IDebugBreakpointErrorEventEvent2,](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) [IDebugBreakpointEventEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)및 [IDebugBreakpointBoundEvent2 인터페이스와 IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) 인터페이스의 구현이 필요하며, [IDebugBreakpointBoundEvent2:GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) 및 [EnumBoundBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) 메서드가 필요합니다.

  비동기 식 평가를 사용하려면 [IDebugExpressionExpressionCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) 인터페이스와 [IDebugExpressionEvaluationCompleteEvent2:GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[및 GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) 메서드를 구현해야 합니다.

  동기 이벤트는 [IDebugEngine2::ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) 메서드를 구현해야 합니다.

  엔진이 문자열 스타일 출력을 작성하려면 [IDebugOutputStringEventEvent2:GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) 메서드를 구현해야 합니다.

## <a name="see-also"></a>참조
- [실행 제어 및 상태 평가](../../extensibility/debugger/execution-control-and-state-evaluation.md)
