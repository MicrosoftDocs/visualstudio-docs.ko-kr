---
title: 'IDebugExpression2:: EvaluateAsync | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729757"
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
이 메서드는 식을 비동기식으로 계산 합니다.

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
진행 식 계산을 제어 하는 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 열거형의 플래그 조합입니다.

`pExprCallback`\
진행 이 매개 변수는 항상 null 값입니다.

## <a name="return-value"></a>반환 값
성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. 일반적인 오류 코드는 다음과 같습니다.

|오류|설명|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|현재 다른 식이 계산 중 이며 동시 식 계산이 지원 되지 않습니다.|

## <a name="remarks"></a>설명
이 메서드는 식 계산을 시작한 직후에 반환 해야 합니다. 식이 성공적으로 계산 되 면 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) 는 [attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) 또는 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)를 통해 제공 된 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 이벤트 콜백으로 전송 되어야 합니다.

## <a name="example"></a>예
다음 예제에서는 IDebugExpression2 인터페이스를 구현 하는 간단한 개체에 대해이 메서드를 구현 하는 방법을 보여 줍니다 `CExpression` . [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)

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

## <a name="see-also"></a>추가 정보
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
