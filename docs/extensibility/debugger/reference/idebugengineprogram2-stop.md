---
title: 아이데버그엔진프로그램2::정지 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 286a448ee33f57d2e3a3282dc8d72b11a843a9c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730488"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
이 프로그램에서 실행 중인 모든 스레드를 중지합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Stop( 
   void 
);
```

```csharp
int Stop();
```

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드는 이 프로그램이 다중 프로그램 환경에서 디버깅될 때 호출됩니다. 다른 프로그램에서 중지 이벤트가 수신되면 이 메서드가 이 프로그램에서 호출됩니다. 이 메서드의 구현은 비동기적이어야 합니다. 즉, 이 메서드가 반환되기 전에 모든 스레드를 중지해야 하는 것은 아닙니다. 이 메서드의 구현은 이 프로그램에서 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) 메서드를 호출하는 것만큼 간단할 수 있습니다.

 구현자는 프로그램이 중지될 때 [IDebugStopCompleteEvent2를](../../../extensibility/debugger/reference/idebugstopcompleteevent2.md) 보내야 합니다.

## <a name="see-also"></a>참조
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
