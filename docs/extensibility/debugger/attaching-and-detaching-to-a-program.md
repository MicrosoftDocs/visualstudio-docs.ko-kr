---
title: 프로그램에 연결 및 분리 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8bd6ea4b51c56a3cc42036b7bd26d34ff3a3eff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739274"
---
# <a name="attaching-and-detaching-to-a-program"></a>프로그램에 연결 및 분리
디버거를 연결하려면 적절한 특성을 가진 올바른 메서드 및 이벤트 시퀀스를 보내야 합니다.

## <a name="sequence-of-methods-and-events"></a>메서드 및 이벤트 시퀀스

1. 세션 디버그 관리자(SDM)는 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 메서드를 호출합니다.

    DEBug 엔진(DE) 프로세스 모델에 따라 `IDebugProgramNodeAttach2::OnAttach` 메서드는 다음에 발생할 일을 결정하는 다음 방법 중 하나를 반환합니다.

    `S_FALSE` 반환되면 디버그 엔진이 프로그램에 성공적으로 연결되었습니다. 그렇지 않으면 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드가 호출되어 연결 프로세스를 완료합니다.

    반환되는 경우 `S_OK` DE는 SDM과 동일한 프로세스에서 로드되어야 합니다. SDM은 다음 작업을 수행합니다.

   1. DE의 엔진 정보를 얻기 위해 [GetEngineInfo를](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) 호출합니다.

   2. DE를 공동 으로 만듭니다.

   3. 호출 [연결](../../extensibility/debugger/reference/idebugengine2-attach.md)합니다.

2. DE는 특성이 있는 SDM에 [IDebugEngineCreateEventEvent2를](../../extensibility/debugger/reference/idebugenginecreateevent2.md) `EVENT_SYNC` 보냅니다.

3. DE는 특성이 있는 SDM에 [IDebugProgramCreateEventEvent2를](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) `EVENT_SYNC` 보냅니다.

4. DE는 특성이 있는 SDM에 [IDebugLoadCompleteEvent2를](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) `EVENT_SYNC_STOP` 보냅니다.

   프로그램에서 분리하는 것은 다음과 같이 간단한 2단계 프로세스입니다.

5. SDM은 [분리를](../../extensibility/debugger/reference/idebugprogram2-detach.md)호출합니다.

6. DE는 [IDebugProgramDestroyEvent2를](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)보냅니다.

## <a name="see-also"></a>참조
- [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)
