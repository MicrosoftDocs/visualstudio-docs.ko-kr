---
title: 표현식 평가(비주얼 스튜디오 디버깅 SDK) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e41179fd530818f5ac59aa54420ede1b4eafa1ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738707"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>표현식 평가(비주얼 스튜디오 디버깅 SDK)
중단 모드에서 IDE는 여러 프로그램 변수와 관련된 간단한 식을 평가해야 합니다. 평가를 수행하려면 DE(디버그 엔진)가 IDE의 창 중 하나에 입력된 식을 구문 분석하고 평가해야 합니다.

 표현식은 [IDebugExpressionContext2::P arseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 메서드를 사용하여 만들어지며 결과 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 인터페이스로 표시됩니다.

 **IDebugExpression2** 인터페이스는 DE에 의해 구현되고 IDE에서 식 평가 결과를 표시하기 위해 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스를 IDE에 반환하기 위해 **EvalAsync** 메서드를 호출합니다. [IDebugProperty2:GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) **는 식의** 값을 Watch 창이나 **지역 지역 창에** 넣는 데 사용되는 구조를 반환합니다.

 디버그 패키지 또는 세션 디버그 관리자(SDM)는 [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 또는 [EvaluateSync를](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 호출하여 평가 결과를 나타내는 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스를 가져옵니다. `IDebugProperty2`에는 식의 이름, 형식 및 값을 반환하는 메서드가 있습니다. 이 정보는 다양한 디버거 창에 나타납니다.

## <a name="using-expression-evaluation"></a>식 평가 사용
 식 평가를 사용하려면 다음 표와 같이 [IDebugExpressionContext2::P arseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 메서드와 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 인터페이스의 모든 메서드를 구현해야 합니다.

|방법|설명|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|식을 비동기적으로 평가합니다.|
|[중단](../../extensibility/debugger/reference/idebugexpression2-abort.md)|비동기 식 평가를 종료합니다.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|식을 동기적으로 평가합니다.|

 동기 및 비동기 [평가는 IDebugProperty2:GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 메서드를 구현해야 합니다. 비동기 식 평가에는 [IDebugExpression평가CompleteEvent2의](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)구현이 필요합니다.

## <a name="see-also"></a>참조
- [실행 제어 및 상태 평가](../../extensibility/debugger/execution-control-and-state-evaluation.md)
