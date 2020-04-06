---
title: 프로그램에 첨부 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f39b489a57ab93ba5f2d116738c591bd53ff95f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739247"
---
# <a name="attach-to-the-program"></a>프로그램에 연결
프로그램을 적절한 포트로 등록한 후에는 디버거를 디버깅하려는 프로그램에 연결해야 합니다.

## <a name="choose-how-to-attach"></a>부착 방법 선택
 세션 디버그 관리자(SDM)가 디버깅 중인 프로그램에 연결하려고 시도하는 방법에는 세 가지가 있습니다.

1. [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) 메서드를 통해 디버그 엔진에 의해 시작 되는 프로그램의 경우 (해석 된 언어의 일반적인), SDM 연결 되는 프로그램과 연결 된 [IDebugProgramNode2 개체에서 IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) 인터페이스를 가져옵니다. [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) SDM이 인터페이스를 `IDebugProgramNodeAttach2` 가져올 수 있는 경우 SDM은 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 메서드를 호출합니다. 메서드가 `IDebugProgramNodeAttach2::OnAttach` `S_OK` 반환되어 프로그램에 연결되지 않았으며 프로그램에 연결하려는 다른 시도를 할 수 있음을 나타냅니다.

2. SDM이 연결된 프로그램에서 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) 인터페이스를 가져올 수 있는 경우 SDM은 [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md) 메서드를 호출합니다. 이 방법은 포트 공급자가 원격으로 시작한 프로그램에 일반적으로 적합합니다.

3. `IDebugProgramNodeAttach2::OnAttach` 또는 `IDebugProgramEx2::Attach` 메서드를 통해 프로그램을 연결할 수 없는 경우 SDM은 `CoCreateInstance` 함수를 호출하여 디버그 엔진(아직 로드되지 않은 경우)을 로드한 다음 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드를 호출합니다. 이 방법은 포트 공급자가 로컬로 시작한 프로그램에 일반적으로 적합합니다.

    사용자 지정 포트 공급자가 `IDebugEngine2::Attach` 메서드를 사용자 지정 포트 공급자의 구현에서 `IDebugProgramEx2::Attach` 메서드를 호출할 수도 있습니다. 일반적으로 이 경우 사용자 지정 포트 공급자는 원격 컴퓨터에서 디버그 엔진을 시작합니다.

   세션 디버그 관리자(SDM)가 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드를 호출할 때 첨부 파일이 수행됩니다.

   디버깅할 응용 프로그램과 동일한 프로세스에서 DE를 실행하는 경우 [다음 IDebugProgramNode2의](../../extensibility/debugger/reference/idebugprogramnode2.md)다음 메서드를 구현해야 합니다.

- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)

- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)

  메서드가 `IDebugEngine2::Attach` 호출된 후 `IDebugEngine2::Attach` 메서드 구현에서 다음 단계를 따릅니다.

1. [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 이벤트 개체를 SDM에 보냅니다. 자세한 내용은 [이벤트 보내기](../../extensibility/debugger/sending-events.md)를 참조하십시오.

2. 메서드에 전달 된 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 개체에 `IDebugEngine2::Attach` [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) 메서드를 호출 합니다.

     이렇게 하면 `GUID` 프로그램을 식별하는 데 사용되는 a가 반환됩니다. 는 `GUID` DE에 로컬 프로그램을 나타내는 개체에 저장 해야 하 고 `IDebugProgram2::GetProgramId` `IDebugProgram2` 메서드가 인터페이스에서 호출 될 때 반환 해야 합니다.

    > [!NOTE]
    > 인터페이스를 `IDebugProgramNodeAttach2` 구현하면 프로그램의 메서드가 `GUID` `IDebugProgramNodeAttach2::OnAttach` 전달됩니다. 메서드에서 `GUID` `GUID` 반환 `IDebugProgram2::GetProgramId` 되는 프로그램에 사용 됩니다.

3. [IDebugCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 이벤트 개체를 보내 프로그램을 DE에 나타내기 위해 로컬 `IDebugProgram2` 개체가 만들어졌다는 것을 SDM에 알립니다. 자세한 내용은 [이벤트 보내기](../../extensibility/debugger/sending-events.md)를 참조하십시오.

    > [!NOTE]
    > 메서드에 전달된 `IDebugProgram2` 개체와 `IDebugEngine2::Attach` 는 다 다. 이전에 전달된 `IDebugProgram2` 개체는 포트에서만 인식되며 별도의 개체입니다.

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
