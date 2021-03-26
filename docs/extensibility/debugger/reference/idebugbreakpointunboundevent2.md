---
description: 이 인터페이스는 런타임에 바인딩된 중단점이 로드 된 프로그램에서 바인딩 해제 되었음을 SDM (세션 디버그 관리자)에 지시 합니다.
title: IDebugBreakpointUnboundEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointUnboundEvent2
helpviewer_keywords:
- IDebugBreakpointUnboundEvent2
ms.assetid: 6b1e1863-0c64-4d85-8ab9-aface522fdea
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 27c032c1563bf208c378044b4e093529a2dba10c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088642"
---
# <a name="idebugbreakpointunboundevent2"></a>IDebugBreakpointUnboundEvent2
이 인터페이스는 런타임에 바인딩된 중단점이 로드 된 프로그램에서 바인딩 해제 되었음을 SDM (세션 디버그 관리자)에 지시 합니다.

## <a name="syntax"></a>구문

```
IDebugBreakpointUnboundEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE (디버그 엔진)는 중단점에 대 한 지원의 일부로이 인터페이스를 구현 합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는이 인터페이스와 동일한 개체에서 구현 되어야 합니다. 즉, SDM에서 인터페이스에 액세스 하는 데 [QueryInterface](/cpp/atl/queryinterface) 를 사용 합니다 `IDebugEvent2` .

## <a name="notes-for-callers"></a>호출자 참고 사항
 바인딩된 중단점이 바인딩 해제 된 경우 DE는이 이벤트 개체를 만들어 보냅니다. 이벤트는 디버깅 중인 프로그램에 연결 될 때 SDM에서 제공 하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback 함수를 사용 하 여 보냅니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugBreakpointUnboundEvent2` .

|메서드|Description|
|------------|-----------------|
|[GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)|바인딩 해제 된 중단점을 가져옵니다.|
|[GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)|중단점이 바인딩 해제 된 이유를 가져옵니다.|

## <a name="remarks"></a>설명
 디버그 엔진 DLL 또는 클래스가 언로드될 때 해당 모듈의 코드에 바인딩된 모든 중단점은 디버깅 중인 프로그램에서 바인딩되지 않아야 합니다. `IDebugBreakpointUnboundEvent2`바인딩되지 않은 각 중단점에 대해이 전송 됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
