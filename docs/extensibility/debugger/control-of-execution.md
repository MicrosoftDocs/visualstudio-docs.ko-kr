---
title: 실행 제어 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e2d338c5470611a5eea0c6279404c4eaddebb2d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739080"
---
# <a name="control-of-execution"></a>실행 제어
디버그 엔진(DE)은 일반적으로 다음 이벤트 중 하나를 마지막 시작 이벤트로 보냅니다.

- 새로 시작된 프로그램에 연결하는 경우 진입점 이벤트

- 이미 실행 중인 프로그램에 연결하는 경우 로드 완료 이벤트

  이 두 이벤트는 모두 이벤트를 중지하는 것으로, 이는 DE가 IDE를 통해 사용자의 응답을 기다리는 것을 의미합니다. 자세한 내용은 [작동 모드를](../../extensibility/debugger/operational-modes.md)참조하십시오.

## <a name="stopping-event"></a>이벤트 중지
 중지 이벤트가 디버그 세션으로 전송되는 경우:

1. 현재 명령 포인터를 포함하는 프로그램 및 스레드는 이벤트 인터페이스에서 가져올 수 있습니다.

2. IDE는 현재 소스 코드 파일과 위치를 결정하며, 이 파일은 편집기에서 강조 표시된대로 표시됩니다.

3. 디버그 세션은 일반적으로 프로그램의 **Continue** 메서드를 호출하여 이 첫 번째 중지 이벤트에 응답합니다.

4. 그런 다음 중단점을 치는 것과 같은 중지 조건이 발생할 때까지 프로그램이 실행됩니다. 이 경우 DE는 디버그 세션에 중단점 이벤트를 보냅니다. 중단점 이벤트는 중지 이벤트이며 DE는 사용자 응답을 다시 기다립니다.

5. 사용자가 함수에 들어서거나, 위계하거나, 밖으로 나가도록 선택하면 IDE는 디버그 세션을 호출하여 프로그램의 `Step` 메서드를 호출하라는 메시지를 표시합니다. 그런 다음 IDE는 단계 단위(명령, 명령 또는 줄)와 단계 유형(함수의 단계, 단계 또는 함수 밖으로 단계)을 전달합니다. 단계가 완료되면 DE는 디버그 세션에 단계 완료 이벤트를 보냅니다.

    또는

    사용자가 현재 명령 포인터에서 계속 실행하도록 선택하면 IDE는 디버그 세션을 호출하여 프로그램의 **Execute** 메서드를 호출하라는 메시지를 표시합니다. 프로그램은 다음 중지 조건이 발생할 때까지 실행을 다시 시작합니다.

    또는

    디버그 세션이 특정 중지 이벤트를 무시하는 경우 디버그 세션은 프로그램의 **Continue** 메서드를 호출합니다. 프로그램이 중지 조건이 발생했을 때 함수에 들어오거나, 이상 또는 꺼진 경우 단계를 계속합니다.

   프로그래밍 방식으로 DE가 중지 조건이 발생하면 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 또는 [IDebugEntryPointEvent2와](../../extensibility/debugger/reference/idebugentrypointevent2.md) 같은 중지 이벤트를 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) 인터페이스를 통해 세션 디버그 관리자(SDM)로 보냅니다. DE는 프로그램 및 현재 명령 포인터를 포함하는 스레드를 나타내는 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 및 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) 인터페이스를 전달합니다. SDM은 [IDebugThread2::EnumFrameInfo를](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 호출하여 최상위 스택 프레임을 얻고 [IDebugStackFrame2::GetDocumentContext를](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) 호출하여 현재 명령 포인터와 연결된 문서 컨텍스트를 가져옵니다. 이 문서 컨텍스트는 일반적으로 소스 코드 파일 이름, 줄 및 열 번호입니다. IDE는 이러한 코드를 사용하여 현재 명령 포인터가 포함된 소스 코드를 강조 표시합니다.

   SDM은 일반적으로 [IDebugProgram2::Continue를](../../extensibility/debugger/reference/idebugprogram2-continue.md)호출하여 이 첫 번째 중지 이벤트에 응답합니다. 그런 다음 이 프로그램은 중단점을 치는 것과 같은 중지 조건이 발생할 때까지 실행되며, 이 경우 DE는 [IDebugBreakpointEvent2 인터페이스를](../../extensibility/debugger/reference/idebugbreakpointevent2.md) SDM에 보냅니다. 중단점 이벤트는 중지 이벤트이며 DE는 사용자 응답을 다시 기다립니다.

   사용자가 함수에 들어서거나, 위계하거나, 함수에서 나가기로 선택하면 IDE는 SDM에 [IDebugProgram2:Step](../../extensibility/debugger/reference/idebugprogram2-step.md)을 호출하라는 메시지를 표시합니다. 그런 다음 IDE는 [STEPUNIT(명령,](../../extensibility/debugger/reference/stepunit.md) 명령 또는 줄)과 [STEPKIND를](../../extensibility/debugger/reference/stepkind.md)전달합니다. 단계가 완료되면 DE는 중지 이벤트인 SDM에 [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) 인터페이스를 보냅니다.

   사용자가 현재 명령 포인터에서 계속 실행하도록 선택하면 IDE는 SDM에 [IDebugProgram2:Execute를](../../extensibility/debugger/reference/idebugprogram2-execute.md)호출하도록 요청합니다. 프로그램은 다음 중지 조건이 발생할 때까지 실행을 다시 시작합니다.

   디버그 패키지가 특정 중지 이벤트를 무시하는 경우 디버그 패키지는 [IDebugProgram2::Continue를](../../extensibility/debugger/reference/idebugprogram2-continue.md)호출하는 SDM을 호출합니다. 프로그램이 중지 조건이 발생했을 때 함수에 들어오거나, 초과하거나, 나가는 경우 단계를 계속합니다. 이는 프로그램이 스테핑 상태를 유지하므로 계속하는 방법을 알 수 있음을 의미합니다.

   SDM에서 **수행**한 `Step`호출은 실행 및 계속비동기이며, 이는 SDM이 호출이 빠르게 반환될 것으로 예상한다는 것을 의미합니다. **Continue** DE가 SDM에 **'Execute'** 또는 **Continue** `Step`반환 전에 동일한 스레드에서 중지 이벤트를 보내면 SDM이 중단됩니다.

## <a name="see-also"></a>참조
- [디버그 작업](../../extensibility/debugger/debugging-tasks.md)
