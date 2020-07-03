---
title: 프로그램에 연결 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 00b9780d0d302b9e067feed057d1a8d49c5f9fc0
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903215"
---
# <a name="attach-to-the-program"></a>프로그램에 연결
적절 한 포트를 사용 하 여 프로그램을 등록 한 후에는 디버그 하려는 프로그램에 디버거를 연결 해야 합니다.

## <a name="choose-how-to-attach"></a>연결 방법 선택
 디버깅 중인 프로그램에 SDM (세션 디버그 관리자)을 연결 하는 방법에는 세 가지가 있습니다.

1. [Launchsuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) 메서드 (예: 해석 된 언어)를 통해 디버그 엔진에서 시작 되는 프로그램의 경우 SDM은 연결 되는 프로그램과 연결 된 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 개체에서 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) 인터페이스를 가져옵니다. SDM에서 인터페이스를 가져올 수 있는 경우에 `IDebugProgramNodeAttach2` 는 sdm에서 [onattach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 메서드를 호출 합니다. `IDebugProgramNodeAttach2::OnAttach`메서드는 `S_OK` 를 반환 하 여 프로그램에 연결 되지 않았고 다른 시도를 프로그램에 연결할 수 있음을 표시 합니다.

2. SDM이 연결 된 프로그램에서 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) 인터페이스를 가져올 수 있는 경우 Sdm은 [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md) 메서드를 호출 합니다. 이 방법은 포트 공급자가 원격으로 시작한 프로그램에 일반적입니다.

3. 또는 메서드를 통해 프로그램을 연결할 수 없는 경우 `IDebugProgramNodeAttach2::OnAttach` `IDebugProgramEx2::Attach` SDM은 함수를 호출 하 여 디버그 엔진 (아직 로드 되지 않은 경우)을 로드 한 `CoCreateInstance` 다음 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드를 호출 합니다. 이 방법은 포트 공급자에서 로컬로 실행 되는 프로그램에 일반적입니다.

    사용자 지정 포트 공급자가 `IDebugEngine2::Attach` 메서드의 사용자 지정 포트 공급자 구현에서 메서드를 호출할 수도 있습니다 `IDebugProgramEx2::Attach` . 일반적으로이 경우 사용자 지정 포트 공급자는 원격 컴퓨터에서 디버그 엔진을 시작 합니다.

   첨부 파일은 세션 디버그 관리자 (SDM)가 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드를 호출할 때 이루어집니다.

   디버그할 응용 프로그램과 동일한 프로세스에서 DE를 실행 하는 경우 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)의 다음 메서드를 구현 해야 합니다.

- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)

- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)

  메서드를 `IDebugEngine2::Attach` 호출한 후 메서드 구현에서 다음 단계를 수행 합니다 `IDebugEngine2::Attach` .

1. [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 이벤트 개체를 SDM으로 보냅니다. 자세한 내용은 [이벤트 전송](../../extensibility/debugger/sending-events.md)을 참조 하세요.

2. 메서드에 전달 된 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 개체에서 [get프로그래밍 id](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) 메서드를 호출 합니다 `IDebugEngine2::Attach` .

     프로그램을 식별 하는 데 사용 되는을 반환 `GUID` 합니다. 는 `GUID` 로컬 프로그램을 나타내는 개체에 저장 되어야 하며, `IDebugProgram2::GetProgramId` 인터페이스에서 메서드가 호출 될 때 반환 되어야 합니다 `IDebugProgram2` .

    > [!NOTE]
    > 인터페이스를 구현 하는 경우 `IDebugProgramNodeAttach2` 프로그램의 `GUID` 이 메서드에 전달 됩니다 `IDebugProgramNodeAttach2::OnAttach` . 이는 `GUID` `GUID` 메서드에 의해 반환 되는 프로그램에 사용 됩니다 `IDebugProgram2::GetProgramId` .

3. [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 이벤트 개체를 보내 `IDebugProgram2` 프로그램을 나타내기 위해 로컬 개체가 생성 되었음을 SDM에 알립니다. 자세한 내용은 [이벤트 전송](../../extensibility/debugger/sending-events.md)을 참조 하세요.

    > [!NOTE]
    > 이 `IDebugProgram2` 개체가 메서드로 전달 된 것과 동일한 개체가 아닌 경우 `IDebugEngine2::Attach` 이전에 전달 된 `IDebugProgram2` 개체는 포트 에서만 인식 되며 별도의 개체입니다.

## <a name="see-also"></a>참조
- [시작 기반 첨부 파일](../../extensibility/debugger/launch-based-attachment.md)
- [이벤트 전송](../../extensibility/debugger/sending-events.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)
- [연결](../../extensibility/debugger/reference/idebugprogramex2-attach.md)
- [연결](../../extensibility/debugger/reference/idebugengine2-attach.md)
