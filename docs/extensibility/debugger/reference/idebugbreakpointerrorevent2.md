---
title: IDebugBreakpoint오류2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointErrorEvent2
helpviewer_keywords:
- IDebugBreakpointErrorEvent2
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09cb93f0f16420e56104f371d9caab262873390f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735049"
---
# <a name="idebugbreakpointerrorevent2"></a>IDebugBreakpointErrorEvent2
이 인터페이스는 세션 디버그 관리자(SDM)에게 경고 또는 오류로 인해 보류 중인 중단점을 로드된 프로그램에 바인딩할 수 없다는 것을 알려줍니다.

## <a name="syntax"></a>구문

```
IDebugBreakpointErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DE는 중단점에 대한 지원의 일부로 이 인터페이스를 구현합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는 이 인터페이스와 동일한 개체에서 구현되어야 합니다(SDM은 `IDebugEvent2` [QueryInterface를](/cpp/atl/queryinterface) 사용하여 인터페이스에 액세스합니다).

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 DE는 보류 중인 중단점을 디버깅 중인 프로그램에 바인딩할 수 없을 때 이 이벤트 개체를 만들고 보냅니다. 이 이벤트는 디버깅되는 프로그램에 연결될 때 SDM에서 제공하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용하여 전송됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugBreakpointErrorEvent2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|경고 또는 오류를 설명하는 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) 인터페이스를 가져옵니다.|

## <a name="remarks"></a>설명
 중단점이 바인딩될 때마다 이벤트가 SDM으로 전송됩니다. 중단점을 바인딩할 수 없는 `IDebugBreakpointErrorEvent2` 경우 a가 전송됩니다. 그렇지 않으면 [IDebugBreakpoint바운드이벤트2가](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) 전송됩니다.

 예를 들어 보류 중인 중단점과 연결된 조건이 구문 분석 또는 평가에 실패하면 현재 보류 중인 중단점을 바인딩할 수 없다는 경고가 전송됩니다. 중단점에 대한 코드가 아직 로드되지 않은 경우 이 가 발생할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
