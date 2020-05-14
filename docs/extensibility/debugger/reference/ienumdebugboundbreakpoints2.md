---
title: 이넘디버그바운드브레이크포인트2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 421d46efbef189fd6ffc86812d2bfdd28f5da5ff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717448"
---
# <a name="ienumdebugboundbreakpoints2"></a>IEnumDebugBoundBreakpoints2
이 인터페이스는 보류 중인 중단점 또는 중단점 바인딩 이벤트와 관련된 바인딩된 중단점을 개명합니다.

## <a name="syntax"></a>구문

```
IEnumDebugBoundBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진(DE)은 중단점에 대한 지원의 일부로 이 인터페이스를 구현합니다. 중단점이 지원되는 경우 이 인터페이스를 구현해야 합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 비주얼 스튜디오 호출:

- [EnumBreakpoints가](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) 트리거된 모든 중단점 목록을 나타내는 이 인터페이스를 가져옵니다.

- [EnumBoundBreak포인트는](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) 바인딩된 모든 중단점 목록을 나타내는 이 인터페이스를 가져옵니다.

- [EnumBoundBreakpoint는](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) 보류 중인 중단점에 바인딩된 모든 중단점 목록을 나타내는 이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IEnumDebugBoundBreakpoints2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|열거 시퀀스에서 지정된 경계 중단점 수를 검색합니다.|
|[건너뛸](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|열거 시퀀스에서 지정된 바인딩된 중단점 수를 건너뜁니다.|
|[다시 설정](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|열거 순서를 시작 부분으로 재설정합니다.|
|[복제](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|현재 열거체와 동일한 열거 상태를 포함하는 열거형 을 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|열거형에서 바인딩된 중단점 수를 가져옵니다.|

## <a name="remarks"></a>설명
 Visual Studio는 이 인터페이스로 표시되는 경계 중단점을 사용하여 IDE의 중단점 표시를 업데이트합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
