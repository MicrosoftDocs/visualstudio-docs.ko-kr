---
title: IDebugBoundBreakpoint2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4d22b10085baefeb3a0286c1b4edcb5876c0dac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735417"
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
이 인터페이스는 코드 위치에 바인딩되는 중단점을 나타냅니다.

## <a name="syntax"></a>Syntax

```
IDebugBoundBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE (디버그 엔진)는 중단점에 대 한 지원의 일부로이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) 를 호출 하면이 인터페이스가 생성 됩니다. [Getbreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) [Next](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) 에 대 한 호출은이 인터페이스를 가져올 수도 있습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugBoundBreakpoint2` .

|메서드|설명|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|지정 된 바인딩된 중단점이 만들어진 보류 중인 중단점을 가져옵니다.|
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|이 바인딩된 중단점의 상태를 가져옵니다.|
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|이 바인딩된 중단점의 현재 적중 횟수를 가져옵니다.|
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|이 중단점을 설명 하는 중단점 확인을 가져옵니다.|
|[사용](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|중단점을 사용 하거나 사용 하지 않도록 설정 합니다.|
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|이 바인딩된 중단점의 적중 횟수를 설정 합니다.|
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|이 바인딩된 중단점과 연결 된 조건을 설정 하거나 변경 합니다.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|이 바인딩된 중단점과 연결 된 패스 수를 설정 하거나 변경 합니다.|
|[Delete](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|중단점을 삭제합니다.|

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)
- [다음](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)
- [바인딩하며](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
