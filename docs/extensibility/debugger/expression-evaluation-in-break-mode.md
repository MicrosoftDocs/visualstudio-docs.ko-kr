---
title: 중단 모드에서 표현식 평가 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc09fc43bd9f0edea4f6dc32e5f37c387c045796
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738728"
---
# <a name="expression-evaluation-in-break-mode"></a>중단 모드에서 표현식 평가
다음 섹션에서는 디버거가 중단 모드에 있을 때 발생하는 프로세스에 대해 설명하고 식 평가를 수행해야 합니다.

## <a name="expression-evaluation-process"></a>표현식 평가 프로세스
 식 을 평가하는 데 관련된 기본 단계는 다음과 같습니다.

1. 세션 디버그 관리자(SDM)는 [IDebugStackFrame2:GetExpressionContext를](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 호출하여 식 컨텍스트 인터페이스인 [IDebugExpressionContext2를](../../extensibility/debugger/reference/idebugexpressioncontext2.md)가져옵니다.

2. 그런 다음 SDM은 구문 분석할 문자열을 사용하여 [IDebugExpressionContext2::ParseText를](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 호출합니다.

3. ParseText가 S_OK 반환하지 않으면 오류의 이유가 반환됩니다.

     -그렇지 않으면-

     ParseText가 S_OK 반환하는 경우 SDM은 [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 또는 [IDebugExpression2::EvaluateAsync를](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 호출하여 구문 분석된 식에서 최종 값을 얻을 수 있습니다.

    - 사용 `IDebugExpression2::EvaluateSync`하는 경우 는 주어진 콜백 인터페이스 평가의 진행 중인 프로세스를 통신 합니다. 최종 값은 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스에서 반환됩니다.

    - 사용 `IDebugExpression2::EvaluateAsync`하는 경우 는 주어진 콜백 인터페이스 평가의 진행 중인 프로세스를 통신 합니다. 평가가 완료되면 EvaluateAsync는 콜백을 통해 [IDebugExpressionEvaluateCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) 인터페이스를 보냅니다. 이 이벤트 인터페이스를 사용하면 [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).

## <a name="see-also"></a>참조
- [호출 디버거 이벤트](../../extensibility/debugger/calling-debugger-events.md)
