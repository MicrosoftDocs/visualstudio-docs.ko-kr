---
title: 아이디버그프로세스2 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723804"
---
# <a name="idebugprocess2"></a>IDebugProcess2
이 인터페이스는 포트에서 실행 중인 프로세스를 나타냅니다. 포트가 로컬 포트인 경우 `IDebugProcess2` 일반적으로 로컬 컴퓨터에서 물리적 프로세스를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugProcess2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 이 인터페이스는 사용자 지정 포트 공급자가 프로그램을 그룹으로 관리하기 위해 구현합니다. 이 인터페이스는 포트 공급자가 구현해야 합니다.

 디버그 엔진은 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)를 통해 프로그램 시작을 지원하는 경우 이 인터페이스도 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스는 주로 이 프로세스에서 식별된 프로그램 그룹과 상호 작용하기 위해 세션 디버그 관리자(SDM)에 의해 호출됩니다.

 이 인터페이스를 얻으려면 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) 또는 [GetProcess를](../../../extensibility/debugger/reference/idebugport2-getprocess.md) 호출합니다. 이 인터페이스는 호출하여 `IDebugEngineLaunch2::LaunchSuspended`반환됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugProcess2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|프로세스에 대한 설명을 가져옵니다.|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|이 프로세스에 포함된 프로그램을 모두 보검합니다.|
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|프로세스의 제목, 친숙한 이름 또는 파일 이름을 가져옵니다.|
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|이 프로세스가 실행 중인 컴퓨터 서버의 인스턴스를 가져옵니다.|
|[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|프로세스를 종료합니다.|
|[연결](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|프로세스에 연결합니다.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|SDM이 프로세스를 분리할 수 있는지 여부를 결정합니다.|
|[Detach](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|디버거를 프로세스에서 분리합니다.|
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|시스템 프로세스 식별자를 가져옵니다.|
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|이 프로세스에 대한 전역고유 식별자를 가져옵니다.|
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [더 이상 사용되지 않습니다]|프로세스를 디버깅하는 세션의 이름을 가져옵니다.<br /><br /> [더 이상 사용되지 않습니다. 항상 반환해야합니다 `E_NOTIMPL`.]|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|프로세스에서 실행 중인 스레드를 개수합니다.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|이 프로세스에서 코드를 실행하는 다음 프로그램이 중지되도록 요청합니다.|
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|이 프로세스가 실행 중인 포트를 가져옵니다.|

## <a name="remarks"></a>설명
 An에는 `IDebugProcess2` 하나 이상의 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스가 포함되어 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: Msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)
- [다음](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)
- [이벤트](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
