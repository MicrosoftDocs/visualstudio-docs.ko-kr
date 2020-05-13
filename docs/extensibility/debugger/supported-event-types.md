---
title: 지원되는 이벤트 유형 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94e26897c50fd7e10a8b831655610848cb93043f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712809"
---
# <a name="supported-event-types"></a>지원되는 이벤트 유형
Visual Studio 디버깅은 현재 다음과 같은 이벤트 유형을 지원합니다.

- 비동기 이벤트

   세션 디버그 관리자(SDM) 및 IDE에 디버깅 중인 응용 프로그램의 상태가 변경되고 있음을 알립니다. 이러한 이벤트는 SDM 및 IDE의 여가 시간에 처리됩니다. 이벤트가 처리되면 DE(디버그 엔진)로 회신이 전송되지 않습니다. [IDebugOutputStringEventEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) 및 [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) 인터페이스는 비동기 이벤트의 예입니다.

- 동기 이벤트

   SDM 및 IDE에 디버깅 중인 응용 프로그램의 상태가 변경되고 있음을 알립니다. 이러한 이벤트와 비동기 이벤트 간의 유일한 차이점은 [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) 메서드를 통해 회신을 전송한다는 것입니다.

   동기 이벤트를 보내는 것은 IDE가 이벤트를 수신하고 처리한 후에도 처리를 계속하기 위해 DE가 필요한 경우에 유용합니다.

- 동기 식 중지 이벤트 또는 중지 이벤트

   SDM 및 IDE에 디버깅 중인 응용 프로그램이 코드 실행을 중지했다는 사실을 알립니다. 메서드 [이벤트를](../../extensibility/debugger/reference/idebugeventcallback2-event.md)통해 중지 이벤트를 보낼 때 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) 매개 변수가 필요합니다. 중지 이벤트는 다음 방법 중 하나를 호출하여 계속됩니다.

  - [실행](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [단계](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [계속](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    인터페이스 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) 및 [IDebug예외Event2는](../../extensibility/debugger/reference/idebugexceptionevent2.md) 이벤트를 중지하는 예입니다.

  > [!NOTE]
  > 비동기 중지 이벤트는 지원되지 않습니다. 비동기 중지 이벤트를 보내는 것은 오류입니다.

## <a name="discussion"></a>토론
 이벤트의 실제 구현은 DE의 디자인에 따라 다릅니다. 전송된 각 이벤트의 형식은 DE를 디자인할 때 설정되는 속성에 의해 결정됩니다. 예를 들어 한 DE는 [IDebugProgramCreateEvent2를](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 비동기 이벤트로 보내고 다른 DE는 중지 이벤트로 보낼 수 있습니다.

 다음 표에서는 이벤트 유형뿐만 아니라 이벤트에 필요한 프로그램 및 스레드 매개 변수를 지정합니다. 모든 이벤트는 동기가 될 수 있습니다. 이벤트가 동기일 필요가 없습니다.

> [!NOTE]
> 모든 이벤트에는 [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) 인터페이스가 필요합니다.

|이벤트|IDebugProgram2|IDebugThread2|이벤트 중지|
|-----------|--------------------|-------------------|---------------------|
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|허용되지만 필수는 아닙니다.|허용되지만 필수는 아닙니다.|예|
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|필수|필수|예|
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|허용되지만 필수는 아닙니다.|허용되지만 필수는 아닙니다.|예|
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|허용되지만 필수는 아닙니다.|허용되지만 필수는 아닙니다.|예|
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|허용되지만 필수는 아닙니다.|허용되지만 필수는 아닙니다.|예|
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|필수|필수|예|
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|필수|필수|예|
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|허용되지 않음|허용되지 않음|예|
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|허용되지 않음|허용되지 않음|예|
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|필수|필수|예|
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|허용되지만 필수는 아닙니다.|허용되지만 필수는 아닙니다.|가능 여부|
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|필수|필수|예|
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|허용되지만 필수는 아닙니다.|허용되지만 필수는 아닙니다.|가능 여부|
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|필수|필수|예|
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|필수|필수|예|
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|허용되지만 필수는 아닙니다.|허용되지만 필수는 아닙니다.|가능 여부|
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|필수|허용되지만 필수는 아닙니다.|예|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|허용되지만 필수는 아닙니다.|허용되지만 필수는 아닙니다.|예|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|필수|허용되지만 필수는 아닙니다.|예|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|필수|허용되지만 필수는 아닙니다.|예|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|필수|허용되지만 필수는 아닙니다.|예|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|필수|허용되지만 필수는 아닙니다.|예|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|허용되지만 필수는 아닙니다.|허용되지만 필수는 아닙니다.|예|
|IDebugStopCompleteEvent2|필수|필수|예|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|필수|필수|예|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|허용되지만 필수는 아닙니다.|허용되지만 필수는 아닙니다.|예|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|필수|필수|예|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|필수|필수|예|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|허용되지만 필수는 아닙니다.|허용되지만 필수는 아닙니다.|예|

## <a name="see-also"></a>참조
- [이벤트 전송](../../extensibility/debugger/sending-events.md)
