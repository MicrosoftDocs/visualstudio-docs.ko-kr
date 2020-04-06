---
title: IDebugStackFrame2::GetExpressionContext | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetExpressionContext
helpviewer_keywords:
- IDebugStackFrame2::GetExpressionContext
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fb1a075d04ed53fdbe2181975a56eddfcbc3b683
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719745"
---
# <a name="idebugstackframe2getexpressioncontext"></a>IDebugStackFrame2::GetExpressionContext
스택 프레임 및 스레드의 현재 컨텍스트 내에서 식 평가에 대 한 평가 컨텍스트를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetExpressionContext ( 
   IDebugExpressionContext2** ppExprCxt
);
```

```csharp
int GetExpressionContext ( 
   out IDebugExpressionContext2 ppExprCxt
);
```

## <a name="parameters"></a>매개 변수
`ppExprCxt`\
【아웃】 식 평가를 위한 컨텍스트를 나타내는 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 일반적으로 식 평가 컨텍스트는 식 평가를 수행하기 위한 범위로 생각할 수 있습니다. [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 메서드를 호출하여 식을 구문 분석한 다음 결과 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 또는 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 메서드를 호출하여 구문 분석된 식을 평가합니다.

## <a name="see-also"></a>참조
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
