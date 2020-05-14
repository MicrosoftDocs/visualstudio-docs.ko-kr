---
title: 디버거 출시 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ceb2f484449d1b3f8474a6586d298b057875b342
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738450"
---
# <a name="launch-the-debugger"></a>디버거 실행
디버거를 실행하려면 적절한 특성을 가진 올바른 메서드 및 이벤트 시퀀스를 보내야 합니다.

## <a name="sequences-of-methods-and-events"></a>메서드 및 이벤트 시퀀스

1. 세션 디버그 관리자(SDM)는 **디버그** 메뉴를 선택한 다음 **시작을**선택하여 호출됩니다. 자세한 내용은 [프로그램 실행](../../extensibility/debugger/launching-a-program.md)을 참조하십시오.

2. SDM은 [OnAttach 메서드를](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 호출합니다.

3. DEBug 엔진(DE) 프로세스 모델에 따라 `IDebugProgramNodeAttach2::OnAttach` 메서드는 다음에 발생할 일을 결정하는 다음 방법 중 하나를 반환합니다.

     반환하는 경우 `S_FALSE` DE(디버그 엔진)는 가상 시스템의 프로세스에서 로드됩니다.

     또는

     반환하는 경우 `S_OK` DE는 SDM의 프로세스 에서 로드됩니다. 그런 다음 SDM은 다음 작업을 수행합니다.

    1. DE의 엔진 정보를 얻기 위해 [GetEngineInfo를](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) 호출합니다.

    2. DE를 공동 으로 만듭니다.

    3. 호출 [연결](../../extensibility/debugger/reference/idebugengine2-attach.md)합니다.

4. DE는 특성이 있는 SDM에 [IDebugEngineCreateEventEvent2를](../../extensibility/debugger/reference/idebugenginecreateevent2.md) `EVENT_SYNC` 보냅니다.

5. DE는 특성이 있는 SDM에 [IDebugProgramCreateEventEvent2를](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) `EVENT_SYNC` 보냅니다.

6. DE는 특성이 있는 SDM에 [IDebugThreadCreateEvent2를](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) `EVENT_SYNC` 보냅니다.

7. DE는 특성이 있는 SDM에 [IDebugLoadCompleteEvent2를](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) `EVENT_SYNC` 보냅니다.

8. DE는 특성이 있는 SDM에 [IDebugEntryPointEventEvent2를](../../extensibility/debugger/reference/idebugentrypointevent2.md) `EVENT_SYNC` 보냅니다.

## <a name="see-also"></a>참조
- [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)
- [프로그램 실행](../../extensibility/debugger/launching-a-program.md)
