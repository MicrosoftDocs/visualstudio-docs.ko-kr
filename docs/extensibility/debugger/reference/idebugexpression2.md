---
title: 아이디버그표현2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2e23ad4f673e4e150ea677d993c5b36a4e386c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729684"
---
# <a name="idebugexpression2"></a>IDebugExpression2
이 인터페이스는 바인딩 및 평가준비가 된 구문 분석식을 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugExpression2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DEBug 엔진(DE)은 평가할 준비가 된 구문 분석식을 나타내기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [ParseText에](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 대한 호출은 이 인터페이스를 반환합니다. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스를 반환합니다. 이러한 인터페이스는 디버깅 중인 프로그램이 일시 중지되고 스택 프레임을 사용할 수 있는 경우에만 액세스할 수 있습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugExpression2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|이 식을 비동기적으로 평가합니다.|
|[중단](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|비동기 식 평가를 종료합니다.|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|이 식을 동기적으로 평가합니다.|

## <a name="remarks"></a>설명
 프로그램이 중지되면 세션 디버그 관리자(SDM)는 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)를 호출하여 DE에서 스택 프레임을 가져옵니다. 그런 다음 SDM은 [GetExpressionContext를](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 호출하여 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스를 가져옵니다. 그 다음에 는 평가할 준비가 된 구문 분석식을 나타내는 `IDebugExpression2` 인터페이스를 만들기 위해 [ParseText를](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 호출합니다.

 SDM은 실제로 식을 평가하고 값을 생성하기 위해 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 또는 [EvaluateAsync를](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 호출합니다.

 `IDebugExpressionContext2::ParseText`구현에서 DE는 COM의 `CoCreateInstance` 함수를 사용하여 식 계산기를 인스턴스화하고 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) 인터페이스를 `IDebugExpressionEvaluator` 가져옵니다(인터페이스의 예제 참조). 그런 다음 [DE는 파즈를](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 호출하여 [IDebugParsedExpression 인터페이스를](../../../extensibility/debugger/reference/idebugparsedexpression.md) 가져옵니다. 이 인터페이스는 평가를 `IDebugExpression2::EvaluateSync` 구현하고 `IDebugExpression2::EvaluateAsync` 수행하는 데 사용된다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)
