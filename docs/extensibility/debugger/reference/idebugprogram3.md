---
title: IDebugProgram3 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722650"
---
# <a name="idebugprogram3"></a>IDebugProgram3
이 인터페이스는 프로세스에서 실행 중 이며 스레드 정보를 제공 하 여 [실행](../../../extensibility/debugger/reference/idebugprogram2-execute.md) 을 확장 하는 프로그램을 나타냅니다.

## <a name="syntax"></a>Syntax

```
IDebugProgram3 : IDebugProgram3
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진 (DE) 및 사용자 지정 포트 공급자는 프로세스에서 프로그램을 나타내기 위해이 인터페이스를 구현 합니다. 또한 세션 디버그 관리자 (SDM)는 [연결할](../../../extensibility/debugger/reference/idebugprogram2-attach.md)정보를 제공 하기 위해이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 이벤트는 새 프로그램에 대해이 인터페이스를 반환 합니다. 이 인터페이스는 여러 인터페이스에서 많은 메서드에 대 한 매개 변수로도 사용 됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugProgram3` .

|메서드|설명|
|------------|-----------------|
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|프로그램을 실행 합니다. 스레드는 실행 될 때 사용자가 보고 있는 스레드에 디버거 정보를 제공 하기 위해 반환 됩니다.|

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>설명
 프로그램은 특정 런타임 아키텍처에서 실행 되는 스레드 컨테이너 이며 프로세스는 하나 이상의 프로그램으로 구성 됩니다.

## <a name="see-also"></a>추가 정보
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [다음](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [이벤트](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
