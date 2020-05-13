---
title: 아이디버그바운드브레이크포인트2 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735417"
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
이 인터페이스는 코드 위치에 바인딩된 중단점을 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugBoundBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진(DE)은 중단점에 대한 지원의 일부로 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [Bind를](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) 호출하면 이 인터페이스가 만들어집니다. [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) 및 [Next에](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) 대한 호출도 이 인터페이스를 가져올 수 있습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugBoundBreakpoint2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|지정된 바운드 중단점이 만들어진 보류 중인 중단점을 가져옵니다.|
|[겟스테이트](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|이 바인딩된 중단점의 상태를 가져옵니다.|
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|이 바인딩된 중단점에 대한 현재 적중 횟수를 가져옵니다.|
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|이 중단점을 설명하는 중단점 확인을 가져옵니다.|
|[사용](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|중단점을 활성화하거나 사용하지 않도록 설정합니다.|
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|이 바인딩된 중단점에 대한 적중 횟수를 설정합니다.|
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|이 바인딩된 중단점과 연관된 조건을 설정하거나 변경합니다.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|이 바인딩 된 중단점과 연관 된 패스 수를 설정 하거나 변경 합니다.|
|[삭제](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|중단점을 삭제합니다.|

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)
- [다음](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)
- [바인딩](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
