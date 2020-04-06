---
title: 아이디버그보류중단점2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e6f2c1df37e953a5d8c66bad9d0a3574a463fad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725643"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
이 인터페이스는 코드 위치에 바인딩할 준비가 된 중단점을 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugPendingBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진(DE)은 중단점에 대한 지원의 일부로 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [CreatePending중단점을](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) 호출하면 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) 인터페이스에서 보류 중인 중단점이 만들어집니다. [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) 에 대한 `IDebugBreakpoint2` 호출은 프로그램의 경계 중단점을 나타내는 인터페이스를 만듭니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugPendingBreakpoint2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|이 보류 중인 중단점이 코드 위치에 바인딩할 수 있는지 여부를 결정합니다.|
|[바인딩](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|이 보류 중인 중단점을 하나 이상의 코드 위치에 바인딩합니다.|
|[겟스테이트](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|보류 중인 중단점의 상태를 가져옵니다.|
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|이 보류 중인 중단점을 만드는 데 사용된 중단점 요청을 가져옵니다.|
|[Virtualize](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|이 보류 중인 중단점의 가상화 상태를 전환합니다.|
|[사용](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|보류 중인 중단점의 활성화된 상태를 전환합니다.|
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|이 보류 중인 중단점과 연관된 조건을 설정하거나 변경합니다.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|보류 중인 중단점과 연결된 패스 수를 설정하거나 변경합니다.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|이 보류 중인 중단점에서 바인딩된 모든 중단점을 모두 확대합니다.|
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|이 보류 중인 중단점으로 인해 발생한 모든 오류 중단점을 에 대한 모든 중단점을 등록합니다.|
|[삭제](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|이 보류 중인 중단점과 바인딩된 모든 중단점을 삭제합니다.|

## <a name="remarks"></a>설명
 `IDebugPendingBreakpoint2`하나 또는 여러 프로그램에 적용할 수 있는 코드에 중단점을 바인딩하는 데 필요한 모든 정보를 공급자로 생각할 수 있습니다.

 보류 중인 중단점은 잠재적으로 두 개 이상의 바인딩된 중단점을 생성할 수 있습니다. 예를 들어 C++스타일 템플릿의 중단점은 해당 템플릿의 각 고유 인스턴스에 대한 경계 중단점을 생성할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)
