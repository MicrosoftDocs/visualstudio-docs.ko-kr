---
title: 지원 되는 이벤트 유형 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712809"
---
# <a name="supported-event-types"></a>지원 되는 이벤트 유형
Visual Studio 디버깅은 현재 다음 이벤트 유형을 지원 합니다.

- 비동기 이벤트

   디버깅 중인 응용 프로그램의 상태가 변경 되 고 있음을 세션 디버그 관리자 (SDM) 및 IDE에 알립니다. 이러한 이벤트는 SDM 및 IDE의 레저에서 처리 됩니다. 이벤트가 처리 되 면 디버그 엔진 (DE)로 회신이 전송 되지 않습니다. [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) 및 [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) 인터페이스는 비동기 이벤트의 예입니다.

- 동기 이벤트

   디버깅 중인 응용 프로그램의 상태가 변경 되 고 있음을 SDM 및 IDE에 알립니다. 이러한 이벤트와 비동기 이벤트의 유일한 차이점은 [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) 메서드를 통해 회신이 전송 된다는 것입니다.

   IDE가 이벤트를 수신 하 고 처리 한 후에 처리를 계속 해야 하는 경우에는 동기 이벤트를 전송 하는 것이 유용 합니다.

- 동기 중지 이벤트 또는 이벤트 중지

   디버깅 중인 응용 프로그램에서 코드 실행이 중지 되었음을 SDM 및 IDE에 알립니다. 메서드 [이벤트](../../extensibility/debugger/reference/idebugeventcallback2-event.md)를 사용 하 여 중지 이벤트를 보내는 경우 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) 매개 변수가 필요 합니다. 다음 메서드 중 하나를 호출 하 여 이벤트 중지를 계속 합니다.

  - [실행](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [Step](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [계속](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) 및 [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) 인터페이스는 이벤트 중지의 예입니다.

  > [!NOTE]
  > 비동기 중지 이벤트는 지원 되지 않습니다. 비동기 중지 이벤트를 전송 하는 것은 오류입니다.

## <a name="discussion"></a>토론(Discussion)
 실제 이벤트 구현은 DE의 디자인에 따라 달라 집니다. 전송 된 각 이벤트의 유형은 특성에 따라 결정 되며,이는 DE를 설계할 때 설정 됩니다. 예를 들어 한 DE는 비동기 이벤트로 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 를 보낼 수 있는 반면 다른 DE는 중지 이벤트로 보낼 수 있습니다.

 다음 표에서는 이벤트 유형 뿐만 아니라 이벤트에 필요한 프로그램 및 스레드 매개 변수를 지정 합니다. 모든 이벤트는 동기적 일 수 있습니다. 이벤트를 동기화 할 필요가 없습니다.

> [!NOTE]
> [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) 인터페이스는 모든 이벤트에 필요 합니다.

|이벤트|IDebugProgram2|IDebugThread2|이벤트 중지|
|-----------|--------------------|-------------------|---------------------|
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|허용 되지만 필요 하지 않음|허용 되지만 필요 하지 않음|예|
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|필수|필수|예|
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|허용 되지만 필요 하지 않음|허용 되지만 필요 하지 않음|예|
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|허용 되지만 필요 하지 않음|허용 되지만 필요 하지 않음|예|
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|허용 되지만 필요 하지 않음|허용 되지만 필요 하지 않음|예|
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|필수|필수|예|
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|필수|필수|예|
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|허용되지 않음|허용되지 않음|예|
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|허용되지 않음|허용되지 않음|예|
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|필수|필수|예|
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|허용 되지만 필요 하지 않음|허용 되지만 필요 하지 않음|가능 여부|
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|필수|필수|예|
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|허용 되지만 필요 하지 않음|허용 되지만 필요 하지 않음|가능 여부|
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|필수|필수|예|
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|필수|필수|예|
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|허용 되지만 필요 하지 않음|허용 되지만 필요 하지 않음|가능 여부|
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|필수|허용 되지만 필요 하지 않음|예|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|허용 되지만 필요 하지 않음|허용 되지만 필요 하지 않음|예|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|필수|허용 되지만 필요 하지 않음|예|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|필수|허용 되지만 필요 하지 않음|예|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|필수|허용 되지만 필요 하지 않음|예|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|필수|허용 되지만 필요 하지 않음|예|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|허용 되지만 필요 하지 않음|허용 되지만 필요 하지 않음|예|
|IDebugStopCompleteEvent2|필수|필수|예|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|필수|필수|예|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|허용 되지만 필요 하지 않음|허용 되지만 필요 하지 않음|예|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|필수|필수|예|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|필수|필수|예|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|허용 되지만 필요 하지 않음|허용 되지만 필요 하지 않음|예|

## <a name="see-also"></a>참고 항목
- [이벤트 전송](../../extensibility/debugger/sending-events.md)
