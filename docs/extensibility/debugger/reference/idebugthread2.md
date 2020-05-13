---
title: 아이데버그스레드2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1965ff1b4cfa89e4584c194942dec7ae486473ff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718588"
---
# <a name="idebugthread2"></a>IDebugThread2
이 인터페이스는 프로그램에서 실행 중인 스레드를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugThread2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진(DE)은 단일 프로그램에서 실행 스레드를 나타내기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [GetThread를](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) 호출하여 현재 활성 스레드를 나타내는 이 인터페이스를 가져옵니다.

 이 인터페이스는 중단점 요청을 만드는 데도 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)사용됩니다(BP_REQUEST_INFO 참조).

 이 인터페이스는 바인딩 또는 오류 중단점을 확인할 때도 반환됩니다(BP_RESOLUTION_INFO 및 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)참조). [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugThread2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|이 스레드의 스택 프레임 목록을 검색합니다.|
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|스레드의 이름을 가져옵니다.|
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|스레드의 이름을 설정합니다.|
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|스레드가 실행 중인 프로그램을 가져옵니다.|
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|다음 문을 지정된 스택 프레임 및 코드 컨텍스트로 설정할 수 있는지 여부를 결정합니다.|
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|다음 문을 지정된 스택 프레임 및 코드 컨텍스트로 설정합니다.|
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|시스템 스레드 식별자를 가져옵니다.|
|[일시 중단](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|스레드를 일시 중단합니다.|
|[다시 시작](../../../extensibility/debugger/reference/idebugthread2-resume.md)|스레드를 다시 시작합니다.|
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|스레드를 설명하는 속성을 가져옵니다.|
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|이 물리적 스레드와 연결된 논리 스레드를 가져옵니다.|

## <a name="remarks"></a>설명
 단일 물리적 스레드는 여러 프로그램에서 실행할 수 `IDebugThread2` 있으므로 두 개 이상의 프로그램에서 두 개 이상의 실제 스레드가 동일한 물리적 스레드를 나타낼 수 있습니다.

 중단점 또는 예외가 발생하면 Event [를](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)호출하여 이벤트가 전송됩니다. 이 메서드에 대한 인수 중 `IDebugThread2` 하나는 현재 스레드를 나타내는 인터페이스입니다. [EnumFrameInfo는](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 현재 스택 프레임에 대한 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 인터페이스를 가져오는 데 사용됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
