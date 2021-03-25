---
description: 이 인터페이스는 프로그램에서 실행 중인 스레드를 나타냅니다.
title: IDebugThread2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 24a9cef2e62dc2597871f270c9ee48ad58c0a0e1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086978"
---
# <a name="idebugthread2"></a>IDebugThread2
이 인터페이스는 프로그램에서 실행 중인 스레드를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugThread2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE (디버그 엔진)는 단일 프로그램의 실행 스레드를 나타내기 위해이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 [Getthread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) 를 호출 하 여 현재 활성 스레드를 나타내는이 인터페이스를 가져옵니다.

 이 인터페이스는 중단점 요청을 만드는 데도 사용 됩니다 ( [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)참조).

 이 인터페이스는 바인딩된 중단점 또는 오류 중단점을 확인할 때에도 반환 됩니다 ( [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) 및 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)참조).

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugThread2` .

|메서드|Description|
|------------|-----------------|
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|이 스레드에 대 한 스택 프레임 목록을 검색 합니다.|
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|스레드의 이름을 가져옵니다.|
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|스레드 이름을 설정 합니다.|
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|스레드가 실행 되 고 있는 프로그램을 가져옵니다.|
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|다음 문을 지정 된 스택 프레임 및 코드 컨텍스트로 설정할 수 있는지 여부를 확인 합니다.|
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|다음 문을 지정 된 스택 프레임 및 코드 컨텍스트로 설정 합니다.|
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|시스템 스레드 식별자를 가져옵니다.|
|[일시 중지됨](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|스레드를 일시 중단 합니다.|
|[다시 시작](../../../extensibility/debugger/reference/idebugthread2-resume.md)|스레드를 다시 시작 합니다.|
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|스레드를 설명 하는 속성을 가져옵니다.|
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|이 물리적 스레드와 연결 된 논리 스레드를 가져옵니다.|

## <a name="remarks"></a>설명
 단일 물리적 스레드를 여러 프로그램에서 실행할 수 있으므로 둘 이상의 `IDebugThread2` 프로그램에서 둘 이상의 프로그램이 동일한 실제 스레드를 나타낼 수 있습니다.

 중단점이 나 예외가 발생 [하면 이벤트를 호출 하](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)여 이벤트를 보냅니다. 이 메서드에 대 한 인수 중 하나는 `IDebugThread2` 현재 스레드를 나타내는 인터페이스입니다. [Enum프레임 정보](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 는 현재 스택 프레임에 대 한 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 인터페이스를 가져오는 데 사용 됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
