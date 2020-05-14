---
title: 출시 기반 첨부 파일 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4910a97350366500b56593ec0076fdf0990b6d8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738465"
---
# <a name="launch-based-attachment"></a>시작 기반 첨부 파일
프로그램에 대한 시작 기반 첨부 파일은 자동으로 수행됩니다. 프로그램을 호스팅하는 프로세스가 SDM에서 시작되면 시작 기반 첨부 파일은 수동 부착 방법과 유사한 경로를 따릅니다. 자세한 내용은 [프로그램에 연결 을](../../extensibility/debugger/attaching-to-the-program.md)참조하십시오.

## <a name="the-attaching-process"></a>부착 프로세스
 주요 차이점은 다음과 같이 **Attach** 호출 다음의 이벤트 시퀀스입니다.

1. **IDebugEngineCreateEvent2** 이벤트 개체를 SDM에 보냅니다. 자세한 내용은 [이벤트 보내기](../../extensibility/debugger/sending-events.md)를 참조하십시오.

2. **Attach** `IDebugProgram2::GetProgramId` 메서드에 전달 된 **IDebugProgram2** 인터페이스에서 메서드를 호출 합니다.

3. **IDebugProgramCreateEvent2** 이벤트 개체를 보내 프로그램을 DE에 나타내기 위해 로컬 **IDebugProgram2** 개체가 만들어졌다는 것을 SDM에 알립니다.

4. [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) 이벤트 개체를 보내 시작 된 프로세스에 대 한 새 스레드가 만들어집니다 SDM에 알립니다.

## <a name="see-also"></a>참조
- [필요한 이벤트 보내기](../../extensibility/debugger/sending-the-required-events.md)
- [프로그램을 디버깅할 수 있도록 설정](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
