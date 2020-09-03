---
title: IDebugExceptionEvent2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729785"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
디버그 엔진 (DE)은 현재 실행 중인 프로그램에서 예외가 throw 될 때이 인터페이스를 세션 디버그 관리자 (SDM)로 보냅니다.

## <a name="syntax"></a>Syntax

```
IDebugExceptionEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE는 디버깅 중인 프로그램에서 예외가 발생 했음을 보고 하기 위해이 인터페이스를 구현 합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는이 인터페이스와 동일한 개체에서 구현 되어야 합니다. SDM은 [QueryInterface](/cpp/atl/queryinterface) 를 사용 하 여 `IDebugEvent2` 인터페이스에 액세스 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 DE는 예외를 보고 하기 위해이 이벤트 개체를 만들어 보냅니다. 이벤트는 디버깅 중인 프로그램에 연결 될 때 SDM에서 제공 하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용 하 여 전송 됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugExceptionEvent2` .

|메서드|설명|
|------------|-----------------|
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|이 이벤트를 발생 시킨 예외에 대 한 자세한 정보를 가져옵니다.|
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|이 이벤트를 발생 시킨 throw 된 예외에 대 한 사람이 읽을 수 있는 설명을 가져옵니다.|
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|디버그 엔진 (DE)이 실행을 다시 시작할 때 디버깅 중인 프로그램에이 예외를 전달 하는 옵션을 지원 하는지 여부를 결정 합니다.|
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|실행을 다시 시작할 때 디버깅 중인 프로그램에 예외를 전달할지 여부를 지정 합니다. 그렇지 않으면 예외를 삭제 해야 합니다.|

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>설명
 이벤트를 보내기 전에 DE는이 예외 이벤트가 [setexception](../../../extensibility/debugger/reference/idebugengine2-setexception.md)에 대 한 이전 호출에 의해 첫 번째 또는 두 번째 예외가 지정 되었는지를 확인 합니다. 첫 번째 예외로 지정 된 경우 `IDebugExceptionEvent2` 이벤트는 SDM으로 전송 됩니다. 그렇지 않은 경우 DE는 응용 프로그램에 예외를 처리할 수 있는 기회를 제공 합니다. 예외 처리기가 제공 되지 않고 예외가 두 번째 예외로 지정 된 경우 `IDebugExceptionEvent2` 이벤트는 SDM으로 전송 됩니다. 그렇지 않은 경우 DE는 프로그램의 실행을 다시 시작 하 고 운영 체제 또는 런타임에서 예외를 처리 합니다.

## <a name="see-also"></a>추가 정보
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
