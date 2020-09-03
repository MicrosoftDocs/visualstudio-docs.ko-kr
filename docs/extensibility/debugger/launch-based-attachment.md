---
title: 시작 기반 첨부 파일 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738465"
---
# <a name="launch-based-attachment"></a>시작 기반 첨부 파일
프로그램에 대 한 시작 기반 첨부 파일은 자동입니다. 프로그램을 호스트 하는 프로세스가 SDM에 의해 시작 되 면 시작 기반 첨부 파일은 수동 첨부 파일 방법과 비슷한 경로를 따릅니다. 자세한 내용은 [프로그램에 연결](../../extensibility/debugger/attaching-to-the-program.md)을 참조 하세요.

## <a name="the-attaching-process"></a>연결 프로세스
 주요 차이점은 다음과 같이 **Attach** 호출을 따르는 이벤트 시퀀스입니다.

1. **IDebugEngineCreateEvent2** 이벤트 개체를 SDM으로 보냅니다. 자세한 내용은 [이벤트 전송](../../extensibility/debugger/sending-events.md)을 참조 하세요.

2. `IDebugProgram2::GetProgramId` **Attach** 메서드에 전달 된 **IDebugProgram2** 인터페이스에서 메서드를 호출 합니다.

3. 프로그램을 표시 하기 위해 로컬 **IDebugProgram2** 개체가 생성 되었음을 SDM에 알리기 위해 **IDebugProgramCreateEvent2** 이벤트 개체를 보냅니다.

4. 시작 된 프로세스에 대해 새 스레드를 만들도록 SDM에 알리기 위해 [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) 이벤트 개체를 보냅니다.

## <a name="see-also"></a>추가 정보
- [필요한 이벤트 보내기](../../extensibility/debugger/sending-the-required-events.md)
- [디버깅할 프로그램 사용](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
