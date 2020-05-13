---
title: IDebug인터셉트예외2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2
ms.assetid: 8ebc256b-5428-4ed6-a505-6aedc8242b8e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a07f2808c1aaeca3c1631fce658fdf6e8da32d60
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727771"
---
# <a name="idebuginterceptexceptioncompleteevent2"></a>IDebugInterceptExceptionCompleteEvent2
이 인터페이스는 DE가 가로채진 이벤트 처리를 완료하면 DE(디버그 엔진)가 세션 디버그 관리자(SDM)로 전송됩니다.

## <a name="syntax"></a>구문

```
IDebugInterceptExceptionCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DE는 이 인터페이스를 구현하여 가로채는 예외의 처리가 완료되었음을 보고합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는 이 인터페이스와 동일한 개체에서 구현되어야 합니다. SDM은 [쿼리인터페이스를](/cpp/atl/queryinterface) 사용하여 `IDebugEvent2` 인터페이스에 액세스합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 DE는 이 이벤트 개체를 만들고 전송하여 가로채진 예외의 완료를 보고합니다. 이 이벤트는 디버깅되는 프로그램에 연결될 때 SDM에서 제공하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용하여 전송됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 인터페이스는 `IDebugInterceptExceptionCompleteEvent2` 다음 메서드를 구현합니다.

|방법|설명|
|------------|-----------------|
|[GetInterceptCookie](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2-getinterceptcookie.md)|처리된 예외와 연결된 고유 값을 반환합니다.|

## <a name="remarks"></a>설명
 이 이벤트는 해당 메서드가 가로채진 예외 처리를 성공적으로 완료하면 [InterceptCurrentException에서](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) 전송됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
