---
title: 아이데버그이벤트2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6341f8003b962a7f45420b076b23623ebdaf861
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729916"
---
# <a name="idebugevent2"></a>IDebugEvent2
이 인터페이스는 중단점에서 중지하는 것과 같은 중요한 디버그 정보와 디버깅 메시지와 같은 중요하지 않은 정보를 모두 통신하는 데 사용됩니다.

## <a name="syntax"></a>구문

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진(DE) 및 사용자 지정 포트 공급자는 다른 모든 이벤트 인터페이스와 동일한 개체에서 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 또는 [이벤트에](../../../extensibility/debugger/reference/idebugportevents2-event.md)지정된 인터페이스 ID(IID) 인수를 사용하여 세션 디버그 관리자(SDM)는 `IDebugEvent2` 인터페이스에서 [QueryInterface를](/cpp/atl/queryinterface) 호출하여 적절한 이벤트 인터페이스를 얻습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugEvent2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[겟특성](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|이 디버그 이벤트에 대한 특성을 가져옵니다.|

## <a name="remarks"></a>설명
 [IDebugBreakpointEvent2와](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)같은 보다 구체적인 이벤트 인터페이스는 IDebugEvent2 인터페이스에서 파생되지 않고 대신 `IDebugEvent2`와 동일한 개체에서 별도의 인터페이스로 구현됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [이벤트](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
