---
title: 아이디버그프로그램3 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9da63d54f64a4ef7592fdbc4d36e2b31220f82df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722650"
---
# <a name="idebugprogram3"></a>IDebugProgram3
이 인터페이스는 프로세스에서 실행 중인 프로그램을 나타내며 스레드 정보를 제공하여 [Execute를](../../../extensibility/debugger/reference/idebugprogram2-execute.md) 확장합니다.

## <a name="syntax"></a>구문

```
IDebugProgram3 : IDebugProgram3
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진(DE)과 사용자 지정 포트 공급자는 프로세스의 프로그램을 나타내기 위해 이 인터페이스를 구현합니다. 세션 디버그 관리자(SDM)는 이 인터페이스를 구현하여 [연결](../../../extensibility/debugger/reference/idebugprogram2-attach.md)에 대한 정보를 제공합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 이벤트는 새 프로그램에 대해 이 인터페이스를 반환합니다. 이 인터페이스는 여러 인터페이스에서 여러 메서드의 매개 변수로도 사용됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugProgram3`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|프로그램을 실행합니다. 스레드가 반환되어 디버거가 실행 시 사용자가 보고 있는 스레드에 대한 정보를 제공합니다.|

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="remarks"></a>설명
 프로그램은 특정 런타임 아키텍처에서 실행되는 스레드 컨테이너이며 프로세스는 하나 이상의 프로그램으로 구성됩니다.

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [다음](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [이벤트](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
