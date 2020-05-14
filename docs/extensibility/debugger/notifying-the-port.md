---
title: 항구 알림 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff94c20969e77bcc70af2f5a16137e09366a0d7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738322"
---
# <a name="notify-the-port"></a>포트에 알림
프로그램을 실행한 후 포트에 다음과 같이 알림을 받아야 합니다.

1. 포트가 새 프로그램 노드를 받으면 프로그램 만들기 이벤트를 디버그 세션으로 다시 보냅니다. 이벤트는 프로그램을 나타내는 인터페이스를 함께 전달합니다.

2. 디버그 세션은 연결할 수 있는 DE(디버그 엔진)의 식별자에 대해 프로그램을 쿼리합니다.

3. 디버그 세션은 DE가 해당 프로그램에 대해 허용되는 DEs 목록에 있는지 확인합니다. 디버그 세션은 원래 디버그 패키지에 의해 전달된 솔루션의 활성 프로그램 설정에서 이 목록을 가져옵니다.

    DE는 허용 가능한 목록에 있어야 하며 그렇지 않으면 DE가 프로그램에 연결되지 않습니다.

   프로그래밍 방식으로 포트가 새 프로그램 노드를 처음 수신하면 프로그램을 나타내는 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스가 만들어집니다.

> [!NOTE]
> 나중에 DE버그 엔진(DE)에서 `IDebugProgram2` 만든 인터페이스와 혼동해서는 안 됩니다.

 포트는 COM `IConnectionPoint` 인터페이스를 통해 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 프로그램 생성 이벤트를 세션 디버그 관리자(SDM)로 다시 보냅니다.

> [!NOTE]
> 나중에 DE에서 `IDebugProgramCreateEvent2` 전송되는 인터페이스와 혼동해서는 안 됩니다.

 이벤트 인터페이스 자체와 함께 포트는 각각 포트, 프로세스 및 프로그램을 나타내는 [IDebugPort2,](../../extensibility/debugger/reference/idebugport2.md) [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)및 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스를 보냅니다. SDM은 [IDebugProgram2::GetEngineInfo를](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) 호출하여 프로그램을 디버깅할 수 있는 DE의 GUID를 가져옵니다. GUID는 원래 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 인터페이스에서 가져온 것입니다.

 SDM은 DE가 허용 가능한 DEs 목록에 있는지 확인합니다. SDM은 원래 디버그 패키지에 의해 전달된 솔루션의 활성 프로그램 설정에서 이 목록을 가져옵니다. DE는 허용 가능한 목록에 있어야 하며 그렇지 않으면 프로그램에 연결되지 않습니다.

 DE의 ID가 알려지면 SDM은 프로그램에 연결할 준비가 됩니다.

## <a name="see-also"></a>참조
- [프로그램 실행](../../extensibility/debugger/launching-a-program.md)
- [출시 후 연결](../../extensibility/debugger/attaching-after-a-launch.md)
- [작업 디버깅](../../extensibility/debugger/debugging-tasks.md)
