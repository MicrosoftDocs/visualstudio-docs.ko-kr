---
title: 아이데버그예외2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbd53d56b21886e972b33c219367edd603cbf0d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729785"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
DE(디버그 엔진)는 현재 실행 중인 프로그램에서 예외가 throw될 때 이 인터페이스를 세션 디버그 관리자(SDM)로 보냅니다.

## <a name="syntax"></a>구문

```
IDebugExceptionEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DE는 디버깅 중인 프로그램에서 예외가 발생했음을 보고하기 위해 이 인터페이스를 구현합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는 이 인터페이스와 동일한 개체에서 구현되어야 합니다. SDM은 [쿼리인터페이스를](/cpp/atl/queryinterface) 사용하여 `IDebugEvent2` 인터페이스에 액세스합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 DE는 예외를 보고하기 위해 이 이벤트 개체를 만들고 보냅니다. 이 이벤트는 디버깅되는 프로그램에 연결될 때 SDM에서 제공하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용하여 전송됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugExceptionEvent2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|이 이벤트를 발생시킨 예외에 대한 자세한 정보를 가져옵니다.|
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|이 이벤트를 발생시킨 예외에 대해 사람이 읽을 수 있는 설명을 가져옵니다.|
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|DE(디버그 엔진)가 실행이 다시 시작될 때 디버깅되는 프로그램에 이 예외를 전달하는 옵션을 지원하는지 여부를 결정합니다.|
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|실행을 다시 시작할 때 디버깅 되는 프로그램에 예외를 전달 해야 하는지 또는 예외를 삭제 해야 하는지 여부를 지정 합니다.|

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="remarks"></a>설명
 이벤트를 보내기 전에 DE는 이 예외 이벤트가 [SetException에](../../../extensibility/debugger/reference/idebugengine2-setexception.md)대한 이전 호출에 의해 첫 번째 또는 두 번째 기회 예외로 지정되었는지 확인합니다. 첫 번째 예외로 지정된 경우 `IDebugExceptionEvent2` 이벤트는 SDM으로 전송됩니다. 그렇지 않은 경우 DE는 응용 프로그램에 예외를 처리할 수 있는 기회를 제공합니다. 예외 처리기가 제공되지 않고 예외가 두 번째 예외로 지정된 경우 `IDebugExceptionEvent2` 이벤트가 SDM으로 전송됩니다. 그렇지 않으면 DE는 프로그램 실행을 다시 시작하고 운영 체제 또는 런타임은 예외를 처리합니다.

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
