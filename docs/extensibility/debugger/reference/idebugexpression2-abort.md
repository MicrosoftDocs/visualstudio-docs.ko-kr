---
title: IDebug표현2::중단 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5de2e34a8ae1e038c2109627099dacc5bd03a1ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729766"
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
이 메서드는 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 메서드에 대 한 호출에 의해 시작 된 비동기 식 평가를 취소 합니다.

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
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 비동기 식 평가가 취소되면 [연결](../../../extensibility/debugger/reference/idebugprogram2-attach.md) 또는 [첨부](../../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드에 전달된 이벤트 콜백에 [IDebugExpressionExpression예원EventEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) 이벤트를 보내지 마십시오.

## <a name="see-also"></a>참조
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
