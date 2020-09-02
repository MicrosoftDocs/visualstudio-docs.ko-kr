---
title: IDebugProcess2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72659491ec6718397a4fbb494175eea0896c7f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723804"
---
# <a name="idebugprocess2"></a>IDebugProcess2
이 인터페이스는 포트에서 실행 되는 프로세스를 나타냅니다. 포트가 로컬 포트인 경우는 `IDebugProcess2` 일반적으로 로컬 컴퓨터의 실제 프로세스를 나타냅니다.

## <a name="syntax"></a>Syntax

```
IDebugProcess2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 이 인터페이스는 프로그램을 그룹으로 관리 하기 위해 사용자 지정 포트 공급자에 의해 구현 됩니다. 이 인터페이스는 포트 공급자에 의해 구현 되어야 합니다.

 디버그 엔진은 [Launchsuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)를 통해 프로그램 시작을 지 원하는 경우에도이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 이 인터페이스는이 프로세스에서 식별 된 프로그램 그룹과 상호 작용 하기 위해 주로 세션 디버그 관리자 (SDM)에서 호출 됩니다.

 [Getprocess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) 또는 [getprocess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) 를 호출 하 여이 인터페이스를 가져옵니다. 또한이 인터페이스는를 호출 하 여 반환 됩니다 `IDebugEngineLaunch2::LaunchSuspended` .

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugProcess2` .

|메서드|설명|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|프로세스에 대 한 설명을 가져옵니다.|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|이 프로세스에 포함 된 프로그램을 열거 합니다.|
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|프로세스의 제목, 이름 또는 파일 이름을 가져옵니다.|
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|이 프로세스가 실행 되 고 있는 컴퓨터 서버의 인스턴스를 가져옵니다.|
|[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|프로세스를 종료 합니다.|
|[연결](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|프로세스에 연결 합니다.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|SDM에서 프로세스를 분리할 수 있는지 여부를 확인 합니다.|
|[분리](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|프로세스에서 디버거를 분리 합니다.|
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|시스템 프로세스 식별자를 가져옵니다.|
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|이 프로세스에 대 한 guid (globally unique identifier)를 가져옵니다.|
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> MAPI|프로세스를 디버깅 하는 세션의 이름을 가져옵니다.<br /><br /> Mapi. 항상를 반환 해야 `E_NOTIMPL` 합니다.]|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|프로세스에서 실행 되는 스레드를 열거 합니다.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|이 프로세스에서 코드를 실행 하는 다음 프로그램이 중지 되도록 요청 합니다.|
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|이 프로세스가 실행 되 고 있는 포트를 가져옵니다.|

## <a name="remarks"></a>설명
 는 `IDebugProcess2` 하나 이상의 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스를 포함 합니다.

## <a name="requirements"></a>요구 사항
 헤더: Msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)
- [다음](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)
- [이벤트](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
