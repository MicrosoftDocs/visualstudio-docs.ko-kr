---
title: 아이디버그프로그램2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 150746197be4945b012717bef08e18ea57168177
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722725"
---
# <a name="idebugprogram2"></a>IDebugProgram2
이 인터페이스는 프로세스에서 실행 중인 프로그램을 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진(DE)과 사용자 지정 포트 공급자는 프로세스의 프로그램을 나타내기 위해 이 인터페이스를 구현합니다. 세션 디버그 관리자(SDM)는 이 인터페이스를 구현하여 [연결](../../../extensibility/debugger/reference/idebugprogram2-attach.md)에 대한 정보를 제공합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 이벤트는 새 프로그램에 대해 이 인터페이스를 반환합니다. 이 인터페이스는 여러 인터페이스에서 여러 메서드의 매개 변수로도 사용됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugProgram2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|이 프로그램에서 실행 중인 스레드를 연수합니다.|
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|프로그램의 이름을 가져옵니다.|
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|이 프로그램이 실행 중인 프로세스를 가져옵니다.|
|[Terminate](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|이 프로그램을 종료합니다.|
|[연결](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|이 프로그램에 연결합니다.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|DEBug 엔진(DE)이 프로그램에서 분리될 수 있는지 확인합니다.|
|[Detach](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|이 프로그램에서 디버거를 분리합니다.|
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|이 프로그램에 대한 전역고유 식별자를 가져옵니다.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|프로그램 속성을 가져옵니다.|
|[실행](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|중지된 상태에서 이 프로그램을 계속 실행합니다. 이전 실행 상태가 지워집니다.|
|[계속](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|중지된 상태에서 이 프로그램을 계속 실행합니다. 이전 실행 상태가 유지됩니다.|
|[단계](../../../extensibility/debugger/reference/idebugprogram2-step.md)|단계를 수행합니다.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|다음에 스레드 중 하나가 코드를 실행할 때 이 프로그램이 실행을 중지해 달라는 요청입니다.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|이 프로그램을 실행하는 DE(디버그 엔진)의 이름과 식별자를 가져옵니다.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|소스 파일에서 지정된 위치에 대한 코드 컨텍스트를 개수합니다.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|이 프로그램의 메모리 바이트를 가져옵니다.|
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|이 프로그램 또는 이 프로그램의 일부에 대한 분해 스트림을 가져옵니다.|
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|이 프로그램이 로드하고 실행 중이면 모듈을 연큐시합니다.|
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|이 프로그램에 대한 편집 및 계속(ENC) 업데이트를 가져옵니다.<br /><br /> 사용자 지정 디버그 엔진은 이 메서드를 `E_NOTIMPL`구현하지 않습니다(항상 반환해야 합니다).|
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|이 프로그램의 코드 경로를 연수합니다.|
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|파일에 덤프를 씁니다.|

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="remarks"></a>설명
 프로그램은 특정 런타임 아키텍처에서 실행되는 스레드 컨테이너이며 프로세스는 하나 이상의 프로그램으로 구성됩니다.

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [다음](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [이벤트](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
