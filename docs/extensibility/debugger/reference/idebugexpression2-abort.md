---
title: 'IDebugExpression2:: Abort | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 18e0e4b810e76bd5c5de7b0f8d77e7cd72ceb565
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901691"
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
이 메서드는 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 메서드를 호출 하 여 시작 된 비동기 식 계산을 취소 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Abort(
   void
);
```

```csharp
int Abort();
```

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 비동기 식 계산을 취소 하면 [attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) 또는 [attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드에 전달 된 이벤트 콜백에 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) 이벤트를 보내지 않습니다.

## <a name="see-also"></a>참고 항목
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
