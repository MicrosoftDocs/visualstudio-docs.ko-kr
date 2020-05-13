---
title: IDebug표현2:평가동기화 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2cd1eba56f8e3c5a1a779acc3330790e9ba2bc96
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729757"
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
이 메서드는 식을 비동기적으로 평가합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EvaluateAsync (
    EVALFLAGS             dwFlags,
    IDebugEventCallback2* pExprCallback
);
```

```csharp
int EvaluateAsync(
    enum_EVALFLAGS       dwFlags,
    IDebugEventCallback2 pExprCallback
);
```

## <a name="parameters"></a>매개 변수
`dwFlags`\
【인】 식 평가를 제어하는 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 열거형의 플래그 조합입니다.

`pExprCallback`\
【인】 이 매개 변수는 항상 null 값입니다.

## <a name="return-value"></a>Return Value
성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다. 일반적인 오류 코드는 다음과 같은 것입니다.

|Error|설명|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|다른 식은 현재 평가 중이며 동시 식 평가는 지원되지 않습니다.|

## <a name="remarks"></a>설명
이 메서드는 식 평가를 시작한 후 즉시 반환해야 합니다. 식이 성공적으로 평가되면 [IDebugExpressionExpressionCompleteEvent2는](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) [연결](../../../extensibility/debugger/reference/idebugprogram2-attach.md) 또는 [첨부를](../../../extensibility/debugger/reference/idebugengine2-attach.md)통해 제공된 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 이벤트 콜백으로 전송되어야 합니다.

## <a name="example"></a>예제
다음 예제에서는 `CExpression` [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) 인터페이스를 구현 하는 간단한 개체에 대 한이 메서드를 구현 하는 방법을 보여 줍니다.

```cpp
HRESULT CExpression::EvaluateAsync(EVALFLAGS dwFlags,
                                   IDebugEventCallback2* pExprCallback)
{
    // Set the aborted state to FALSE
    // in case the user tries to redo the evaluation after aborting.
    m_bAborted = FALSE;
    // Post the WM_EVAL_EXPR message in the message queue of the current thread.
    // This starts the expression evaluation on a background thread.
    PostThreadMessage(GetCurrentThreadId(), WM_EVAL_EXPR, 0, (LPARAM) this);
    return S_OK;
}
```

## <a name="see-also"></a>참조
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
