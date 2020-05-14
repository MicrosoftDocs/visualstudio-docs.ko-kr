---
title: 아이디버그브레이크포인트바운드이벤트2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointBoundEvent2
helpviewer_keywords:
- IDebugBreakpointBoundEvent2
ms.assetid: 24ba362e-5be1-481a-b071-e1ebd3cae6e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7943addb4334710da3252a4d822330e45b6e0f80
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735304"
---
# <a name="idebugbreakpointboundevent2"></a>IDebugBreakpointBoundEvent2
이 인터페이스는 세션 디버그 관리자(SDM)에게 보류 중인 중단점이 로드된 프로그램에 성공적으로 바인딩되었음을 알려줍니다.

## <a name="syntax"></a>구문

```
IDebugBreakpointBoundEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DE는 중단점에 대한 지원의 일부로 이 인터페이스를 구현합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는 이 인터페이스와 동일한 개체에서 구현되어야 합니다(SDM은 `IDebugEvent2` [QueryInterface를](/cpp/atl/queryinterface) 사용하여 인터페이스에 액세스합니다).

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 DE는 보류 중인 중단점이 디버깅 중인 프로그램에 성공적으로 바인딩될 때 이 이벤트 개체를 만들고 보냅니다. 이 이벤트는 디버깅되는 프로그램에 연결될 때 SDM에서 제공하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용하여 전송됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugBreakpointBoundEvent2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)|바인딩중인 보류 중인 중단점을 가져옵니다.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)|이 이벤트에 바인딩된 중단점의 열거수를 만듭니다.|

## <a name="remarks"></a>설명
 중단점이 바인딩될 때마다 이벤트가 SDM으로 전송됩니다. 중단점을 바인딩할 수 없는 경우 [IDebugBreakpointErrorEvent2가](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) 전송됩니다. 그렇지 않으면 `IDebugBreakpointBoundEvent2` a가 전송됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
