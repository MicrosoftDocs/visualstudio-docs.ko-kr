---
title: 출시 후 시작 이벤트 보내기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c71db002420a2b822bffd34f2ae05e712f6a4bb9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713008"
---
# <a name="send-startup-events-after-a-launch"></a>시작 후 시작 이벤트 보내기
DE(디버그 엔진)가 프로그램에 연결되면 일련의 시작 이벤트를 디버그 세션으로 다시 보냅니다.

 디버그 세션으로 다시 전송되는 시작 이벤트는 다음과 같습니다.

- 엔진 생성 이벤트입니다.

- 프로그램 만들기 이벤트입니다.

- 스레드 생성 및 모듈 로드 이벤트.

- 코드가 로드되고 실행준비가 되었지만 코드가 실행되기 전에 전송되는 로드 완료 이벤트입니다.

  > [!NOTE]
  > 이 이벤트가 계속되면 전역 변수가 초기화되고 시작 루틴이 실행됩니다.

- 가능한 다른 스레드 생성 및 모듈 로드 이벤트.

- 프로그램이 **Main** 또는 와 `WinMain`같은 주요 진입점에 도달했음을 알리는 진입점 이벤트입니다. DE가 이미 실행 중인 프로그램에 연결하는 경우 이 이벤트는 일반적으로 전송되지 않습니다.

  프로그래밍 방식으로 DE는 먼저 세션 디버그 관리자(SDM)를 엔진 생성 이벤트를 나타내는 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 인터페이스를 보낸 다음 프로그램 생성 이벤트를 나타내는 [IDebugProgramCreateEvent2를](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)보냅니다.

  이러한 이벤트는 일반적으로 하나 이상의 [IDebugThreadCreateEventEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) 스레드 생성 이벤트 및 [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) 모듈 로드 이벤트 다음에 발생합니다.

  코드가 로드되고 실행될 준비가 되었지만 코드가 실행되기 전에 DE는 SDM에 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 로드 완료 이벤트를 보냅니다. 마지막으로 프로그램이 아직 실행되지 않은 경우 DE는 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 진입점 이벤트를 전송하여 프로그램이 기본 진입점에 도달했으며 디버깅준비가 되었음을 나타냅니다.

## <a name="see-also"></a>참조
- [실행 제어](../../extensibility/debugger/control-of-execution.md)
- [작업 디버깅](../../extensibility/debugger/debugging-tasks.md)
