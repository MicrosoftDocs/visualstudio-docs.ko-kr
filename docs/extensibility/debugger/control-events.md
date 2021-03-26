---
title: 컨트롤 이벤트 | Microsoft Docs
description: IDebugEvent2 인터페이스를 사용 하 여 프로그램을 제어 하는 실행 중에 이벤트를 보내는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: aeee5ed91eca7666d08dfd08ec02b850a7739db9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085535"
---
# <a name="control-events"></a>컨트롤 이벤트
프로그램의 제어 된 실행 중에 이벤트를 전송 해야 합니다. 모든 이벤트는 [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) 인터페이스를 사용 하 여 전송 되며 [IDebugEvent2:: getattributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) 메서드를 구현 해야 하는 특성이 있습니다.

## <a name="additional-methods"></a>추가 방법
 일부 이벤트의 경우 다음과 같이 추가 메서드를 구현 해야 합니다.

- DE (디버그 엔진)를 초기화할 때 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 인터페이스를 전송 하려면 [IDebugEngineCreateEvent2:: getengine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) 메서드를 구현 해야 합니다.

- 실행 제어를 사용 하려면 [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) 및[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) 인터페이스와 같은 컨트롤 이벤트를 구현 해야 합니다. **IDebugBreakEvent2** 는 비동기 중단에만 필요 합니다.

- 함수를 한 단계씩 실행 하려면 [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) 인터페이스 및 해당 메서드를 구현 해야 합니다.

  중단점에서 파생 되는 이벤트에는 [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)및 [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) 인터페이스 뿐만 아니라 [IDebugBreakpointBoundEvent2:: getpendingbreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) 메서드를 구현 해야 합니다.

  비동기 식 계산을 사용 하려면 [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) 인터페이스와 해당 [IDebugExpressionEvaluationCompleteEvent2:: Getexpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[및 getexpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) 메서드를 구현 해야 합니다.

  동기 이벤트를 구현 하려면 [IDebugEngine2:: ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) 메서드를 구현 해야 합니다.

  엔진에서 문자열 스타일의 출력을 쓰려면 [IDebugOutputStringEvent2:: GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) 메서드를 구현 해야 합니다.

## <a name="see-also"></a>참조
- [실행 제어 및 상태 평가](../../extensibility/debugger/execution-control-and-state-evaluation.md)
