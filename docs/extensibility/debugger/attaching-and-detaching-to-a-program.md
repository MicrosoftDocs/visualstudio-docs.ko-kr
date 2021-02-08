---
title: 프로그램에 연결 및 분리 | Microsoft Docs
description: 디버거를 연결 하기 위한 적절 한 특성으로 올바른 메서드 및 이벤트 시퀀스를 보내는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d41f9e3f88f28dbbb83e9c7e00fe8b8afd434c26
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837751"
---
# <a name="attaching-and-detaching-to-a-program"></a>프로그램에 연결 및 분리
디버거를 연결 하려면 적절 한 특성으로 올바른 메서드 및 이벤트 시퀀스를 전송 해야 합니다.

## <a name="sequence-of-methods-and-events"></a>메서드 및 이벤트 시퀀스

1. 세션 디버그 관리자 (SDM)는 [Onattach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 메서드를 호출 합니다.

    디버그 엔진 (DE) 프로세스 모델을 기반으로 메서드는 다음 메서드 중 하나를 반환 하 여 다음에 발생 하는 `IDebugProgramNodeAttach2::OnAttach` 작업을 결정 합니다.

    `S_FALSE`가 반환 되 면 디버그 엔진이 프로그램에 성공적으로 연결 된 것입니다. 그렇지 않으면 attach [메서드를 호출 하 여 연결](../../extensibility/debugger/reference/idebugengine2-attach.md) 프로세스를 완료 합니다.

    가 반환 되는 경우에는 `S_OK` .sdm와 동일한 프로세스에서 DE를 로드 해야 합니다. SDM은 다음 작업을 수행 합니다.

   1. [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) 를 호출 하 여 DE의 엔진 정보를 가져옵니다.

   2. DE를 공동 만듭니다.

   3. [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)를 호출 합니다.

2. DE는 특성을 사용 하 여 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 을 SDM으로 보냅니다 `EVENT_SYNC` .

3. DE는 특성을 사용 하 여 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 을 SDM으로 보냅니다 `EVENT_SYNC` .

4. DE는 특성을 사용 하 여 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 을 SDM으로 보냅니다 `EVENT_SYNC_STOP` .

   프로그램에서 분리는 다음과 같은 간단한 2 단계 프로세스입니다.

5. SDM은 [Detach](../../extensibility/debugger/reference/idebugprogram2-detach.md)를 호출 합니다.

6. DE는 [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)을 보냅니다.

## <a name="see-also"></a>참고 항목
- [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)
