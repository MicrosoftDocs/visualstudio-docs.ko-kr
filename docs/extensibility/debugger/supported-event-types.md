---
title: 지원되는 이벤트 유형 | Microsoft Docs
description: 비동기 이벤트, 동기 이벤트 및 중지 이벤트를 포함하여 디버깅을 Visual Studio 지원하는 이벤트 유형에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fff86a142f541c1b17012b6190dd68e8d5628a3c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902906"
---
# <a name="supported-event-types"></a>지원되는 이벤트 유형
Visual Studio 디버깅은 현재 다음과 같은 이벤트 유형을 지원합니다.

- 비동기 이벤트

   디버그 중인 애플리케이션의 상태가 변경되고 있음을 SDM(세션 디버그 관리자) 및 IDE에 알립니다. 이러한 이벤트는 SDM 및 IDE에서 처리됩니다. 이벤트가 처리되면 DE(디버그 엔진)에 회신이 전송되지 않습니다. [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) 및 [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) 인터페이스는 비동기 이벤트의 예입니다.

- 동기 이벤트

   디버그 중인 애플리케이션의 상태가 변경되고 있음을 SDM 및 IDE에 알립니다. 이러한 이벤트와 비동기 이벤트의 유일한 차이점은 [회신이 ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) 메서드를 통해 전송된다는 것입니다.

   동기 이벤트를 보내는 것은 IDE가 이벤트를 수신하고 처리한 후 DE가 처리를 계속해야 하는 경우에 유용합니다.

- 동기 이벤트 중지 또는 이벤트 중지

   디버그 중인 애플리케이션의 코드 실행이 중지되었음을 SDM 및 IDE에 알립니다. [이벤트](../../extensibility/debugger/reference/idebugeventcallback2-event.md)메서드를 통해 중지 이벤트를 보내는 경우 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) 매개 변수가 필요합니다. 중지 이벤트는 다음 메서드 중 하나를 호출하여 계속됩니다.

  - [실행](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [Step](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [계속](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) 및 [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) 인터페이스는 이벤트를 중지하는 예입니다.

  > [!NOTE]
  > 비동기 중지 이벤트는 지원되지 않습니다. 비동기 중지 이벤트를 보내는 것은 오류입니다.

## <a name="discussion"></a>토론
 이벤트의 실제 구현은 DE의 디자인에 따라 달라집니다. 전송된 각 이벤트의 형식은 DE를 디자인할 때 설정되는 특성에 따라 결정됩니다. 예를 들어 한 DE는 [IDebugProgramCreateEvent2를](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 비동기 이벤트로 보내고 다른 DE는 이를 중지 이벤트로 보낼 수 있습니다.

 다음 표에서는 이벤트 유형뿐만 아니라 이벤트에 필요한 프로그램 및 스레드 매개 변수를 지정합니다. 모든 이벤트는 동기식일 수 있습니다. 어떤 이벤트도 동기적일 필요가 없습니다.

> [!NOTE]
> [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) 인터페이스는 모든 이벤트에 필요합니다.

|이벤트|IDebugProgram2|IDebugThread2|이벤트 중지|
|-----------|--------------------|-------------------|---------------------|
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|허용되지만 필수는 아닙니다.|허용되지만 필수는 아닙니다.|No|
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|필수|필수|yes|
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|허용되지만 필수는 아닙니다.|허용되지만 필수는 아닙니다.|No|
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|허용되지만 필수는 아닙니다.|허용되지만 필수는 아닙니다.|No|
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|허용되지만 필수는 아닙니다.|허용되지만 필수는 아닙니다.|No|
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|필수|필수|yes|
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|필수|필수|예|
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|허용되지 않음|허용되지 않음|No|
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|허용되지 않음|허용되지 않음|No|
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|필수|필수|yes|
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|허용되지만 필수는 아닙니다.|허용되지만 필수는 아닙니다.|가능 여부|
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|필수|필수|yes|
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|허용되지만 필수는 아닙니다.|허용되지만 필수는 아닙니다.|가능 여부|
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|필수|필수|yes|
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|필수|필수|yes|
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|허용되지만 필수는 아닙니다.|허용되지만 필수는 아닙니다.|가능 여부|
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|필수|허용되지만 필수는 아닙니다.|No|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|허용되지만 필수는 아닙니다.|허용되지만 필수는 아닙니다.|No|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|필수|허용되지만 필수는 아닙니다.|No|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|필수|허용되지만 필수는 아닙니다.|No|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|필수|허용되지만 필수는 아닙니다.|No|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|필수|허용되지만 필수는 아닙니다.|No|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|허용되지만 필수는 아닙니다.|허용되지만 필수는 아닙니다.|No|
|IDebugStopCompleteEvent2|필수|필수|yes|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|필수|필수|yes|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|허용되지만 필수는 아닙니다.|허용되지만 필수는 아닙니다.|No|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|필수|필수|예|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|필수|필수|예|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|허용되지만 필수는 아닙니다.|허용되지만 필수는 아닙니다.|예|

## <a name="see-also"></a>참고 항목
- [이벤트 보내기](../../extensibility/debugger/sending-events.md)
