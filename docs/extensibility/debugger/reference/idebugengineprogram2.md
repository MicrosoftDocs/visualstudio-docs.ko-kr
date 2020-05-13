---
title: 아이데버그엔진프로그램2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e5ccf2327e660a983bcb3032363a92ac8a6f71d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730305"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
이 인터페이스는 다중 스레드 디버깅 지원을 제공합니다.

## <a name="syntax"></a>구문

```
IDebugEngineProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진은 여러 스레드의 동시 디버깅을 지원하기 위해 이 인터페이스를 구현합니다. 이 인터페이스는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스를 구현하는 동일한 개체에서 구현됩니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [QueryInterface를](/cpp/atl/queryinterface) 사용하여 인터페이스에서 `IDebugProgram2` 이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugEngineProgram2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[중지](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|이 프로그램에서 실행 중인 모든 스레드를 중지합니다.|
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|지정된 스레드에서 실행(또는 실행 감시 중지)을 감시합니다.|
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|프로그램이 중지된 경우에도 지정된 스레드에서 식 평가를 수행하도록 허용(또는 허용하지 않는) 식 계산을 허용합니다.|

## <a name="remarks"></a>설명
 Visual Studio는 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 이벤트에 대한 응답으로 이 인터페이스를 호출하고 프로그램의 "스레드 단계 감시" 및 "스레드에서 식 평가 감시" 상태를 설정합니다. [프로그램이 중지될](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) 때마다 중지가 호출됩니다. 이 메서드는 프로그램에 모든 스레드를 종료할 수 있는 기회를 제공합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
