---
title: 아이데버그이벤트콜백2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a74825a955afdde03e63673c4b1b6afda5904953
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729881"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
이 인터페이스는 DE(디버그 엔진)에서 세션 디버그 관리자(SDM)에 디버그 이벤트를 보내는 데 사용됩니다.

## <a name="syntax"></a>구문

```
IDebugEventCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]디버그 엔진에서 이벤트를 수신하기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 디버그 엔진은 일반적으로 SDM에서 [연결,](../../../extensibility/debugger/reference/idebugprogram2-attach.md) [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md)또는 LaunchSuspended 를 호출할 때 이 [인터페이스를](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)수신합니다. 디버그 엔진은 이벤트를 호출하여 SDM에 [이벤트를](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)보냅니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugEventCallback2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|SDM에 디버깅 이벤트 알림을 보냅니다.|

## <a name="remarks"></a>설명
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 및 [EvaluateAsync는](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) `IDebugEventCallback2` 인터페이스를 수행한다는 것을 지정하지만, 이것은 사실이 아니며 인터페이스 포인터는 항상 null 값이 됩니다. 대신 디버그 엔진은 `IDebugEventCallback2` [연결,](../../../extensibility/debugger/reference/idebugprogram2-attach.md) [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md)또는 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)에 대한 호출에서 수신된 인터페이스를 사용해야 합니다.

 패키지가 관리 코드에서 [IDebugEventCallback을](../../../extensibility/debugger/reference/idebugeventcallback2.md) 구현하는 경우 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)에 전달되는 다양한 인터페이스에서 호출하는 것이 좋습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [연결](../../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md)
