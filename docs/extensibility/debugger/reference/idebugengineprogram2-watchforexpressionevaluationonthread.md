---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
titleSuffix: ''
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 4f36431ef7a190e98d35e795ffd8213781553dfc
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036121"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
프로그램이 중지 된 경우에도 지정 된 스레드에서 식 계산을 수행 하도록 허용 하거나 허용 하지 않습니다.

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
진행 식을 계산 하는 프로그램을 나타내는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 개체입니다.

`dwTid`\
진행 스레드의 식별자를 지정 합니다.

`dwEvalFlags`\
진행 계산을 수행 하는 방법을 지정 하는 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 열거형의 플래그 조합입니다.

`pExprCallback`\
진행 식 평가 중에 발생 하는 디버그 이벤트를 보내는 데 사용 되는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 개체입니다.

`fWatch`\
진행 0이 아닌 경우 ( `TRUE` )로 식별 되는 스레드에서 식 계산을 허용 하 `dwTid` 고, 그렇지 않으면 0 ( `FALSE` )은 해당 스레드에서 식 계산을 허용 하지 않습니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 세션 디버그 관리자 (SDM)가 매개 변수로 식별 된 프로그램에 `pOriginatingProgram` 식을 계산 하도록 요청 하면이 메서드를 호출 하 여 연결 된 다른 모든 프로그램에 알립니다.

 한 프로그램에서 식 계산을 실행 하면 모든 속성의 함수 실행 또는 계산으로 인해 코드가 다른에서 실행 될 수 있습니다 `IDispatch` . 이로 인해이 메서드는이 프로그램에서 스레드가 중지 된 경우에도 식 계산을 실행 하 고 완료할 수 있도록 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
