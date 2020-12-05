---
title: 시작 기반 첨부 파일 | Microsoft Docs
description: 프로그램에 대 한 시작 기반 첨부 파일에 대해 알아봅니다 .이는 자동 이며 수동 첨부 파일의 경로와 같은 경로를 따릅니다.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 7e041c692a833b7d0a1891c078388a3f5b2d11e4
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606673"
---
# <a name="launch-based-attachment"></a>시작 기반 첨부 파일
프로그램에 대 한 시작 기반 첨부 파일은 자동입니다. 프로그램을 호스트 하는 프로세스가 SDM에 의해 시작 되 면 시작 기반 첨부 파일은 수동 첨부 파일 방법과 비슷한 경로를 따릅니다. 자세한 내용은 [프로그램에 연결](../../extensibility/debugger/attaching-to-the-program.md)을 참조 하세요.

## <a name="the-attaching-process"></a>연결 프로세스
 주요 차이점은 다음과 같이 **Attach** 호출을 따르는 이벤트 시퀀스입니다.

1. **IDebugEngineCreateEvent2** 이벤트 개체를 SDM으로 보냅니다. 자세한 내용은 [이벤트 전송](../../extensibility/debugger/sending-events.md)을 참조 하세요.

2. `IDebugProgram2::GetProgramId` **Attach** 메서드에 전달 된 **IDebugProgram2** 인터페이스에서 메서드를 호출 합니다.

3. 프로그램을 표시 하기 위해 로컬 **IDebugProgram2** 개체가 생성 되었음을 SDM에 알리기 위해 **IDebugProgramCreateEvent2** 이벤트 개체를 보냅니다.

4. 시작 된 프로세스에 대해 새 스레드를 만들도록 SDM에 알리기 위해 [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) 이벤트 개체를 보냅니다.

## <a name="see-also"></a>참고 항목
- [필요한 이벤트 보내기](../../extensibility/debugger/sending-the-required-events.md)
- [디버깅할 프로그램 사용](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
