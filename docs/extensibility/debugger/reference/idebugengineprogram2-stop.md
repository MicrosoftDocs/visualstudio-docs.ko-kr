---
title: 'IDebugEngineProgram2:: Stop | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6013770e3a334e7924cafe4563d437d4f7730bfc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892686"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
이 프로그램에서 실행 중인 모든 스레드를 중지 합니다.

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
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드는이 프로그램이 다중 프로그램 환경에서 디버깅 될 때 호출 됩니다. 다른 프로그램의 중지 이벤트를 수신 하면이 메서드가이 프로그램에서 호출 됩니다. 이 메서드의 구현은 비동기 여야 합니다. 즉,이 메서드가 반환 되기 전에 모든 스레드를 중지 해야 하는 것은 아닙니다. 이 메서드의 구현은이 프로그램에서 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) 메서드를 호출 하는 것 처럼 간단할 수 있습니다.

 프로그램이 중지 되 면 구현자는 [IDebugStopCompleteEvent2](../../../extensibility/debugger/reference/idebugstopcompleteevent2.md) 를 전송 해야 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
