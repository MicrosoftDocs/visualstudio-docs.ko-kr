---
title: 아이데버그엔진프로그램2::워치포표현평가 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e988e1d64af38a55f5d946f704e1edb4df29b1d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730368"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
프로그램이 중지된 경우에도 지정된 스레드에서 식 평가를 수행하도록 허용(또는 허용하지 않는) 식 계산을 허용합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT WatchForExpressionEvaluationOnThread( 
   IDebugProgram2*       pOriginatingProgram,
   DWORD                 dwTid,
   DWORD                 dwEvalFlags,
   IDebugEventCallback2* pExprCallback,
   BOOL                  fWatch
);
```

```csharp
int WatchForExpressionEvaluationOnThread( 
   IDebugProgram2       pOriginatingProgram,
   uint                  dwTid,
   uint                  dwEvalFlags,
   IDebugEventCallback2 pExprCallback,
   int                   fWatch
);
```

## <a name="parameters"></a>매개 변수
`pOriginatingProgram`\
【인】 식을 평가하는 프로그램을 나타내는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 개체입니다.

`dwTid`\
【인】 스레드의 식별자를 지정합니다.

`dwEvalFlags`\
【인】 평가를 수행할 방법을 지정하는 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 열거형의 플래그 조합입니다.

`pExprCallback`\
【인】 식 평가 중에 발생하는 디버그 이벤트를 보내는 데 사용할 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 개체입니다.

`fWatch`\
【인】 0이 아닌`TRUE`경우 ( ) 에 의해 `dwTid`식별된 스레드에 대한 식 평가를 허용합니다. 그렇지 않으면`FALSE`0 () 해당 스레드에 대한 식 평가를 허용하지 않습니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 세션 디버그 관리자(SDM)가 `pOriginatingProgram` 매개 변수로 식별된 프로그램을 요청하여 식을 평가하도록 요청하면 이 메서드를 호출하여 연결된 다른 모든 프로그램에 알부신니다.

 한 프로그램의 식 평가는 `IDispatch` 속성의 함수 평가 또는 평가로 인해 다른 프로그램에서 코드가 실행될 수 있습니다. 따라서 이 메서드를 사용하면 이 프로그램에서 스레드가 중지될 수 있더라도 식 평가가 실행되고 완료될 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
