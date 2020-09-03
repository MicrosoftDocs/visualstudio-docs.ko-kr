---
title: 식 계산 (Visual Studio 디버깅 SDK) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738707"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>식 계산 (Visual Studio 디버깅 SDK)
중단 모드에서 IDE는 여러 프로그램 변수를 포함 하는 간단한 식을 계산 해야 합니다. 디버그 엔진 (DE)은 해당 평가를 수행 하기 위해 IDE 창 중 하나에 입력 된 식을 구문 분석 하 고 평가 해야 합니다.

 식은 [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 메서드를 사용 하 여 생성 되 고 결과 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 인터페이스로 표시 됩니다.

 **IDebugExpression2** 인터페이스는 DE에 의해 구현 되 고 ide에 식 계산 결과를 표시 하기 위해 **EvalAsync** 메서드를 호출 하 여 ide에 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스를 반환 합니다. [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 은 식의 값을 **조사식** 창 또는 **지역** 창에 넣는 데 사용 되는 구조체를 반환 합니다.

 디버그 패키지 또는 세션 디버그 관리자 (SDM)는 [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 또는 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 를 호출 하 여 평가 결과를 나타내는 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스를 가져옵니다. `IDebugProperty2` 에는 식의 이름, 유형 및 값을 반환 하는 메서드가 있습니다. 이 정보는 다양 한 디버거 창에 표시 됩니다.

## <a name="using-expression-evaluation"></a>식 계산 사용
 식 계산을 사용 하려면 다음 표에 나와 있는 것 처럼 [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 메서드와 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 인터페이스의 모든 메서드를 구현 해야 합니다.

|메서드|설명|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|식을 비동기식으로 계산 합니다.|
|[중단이](../../extensibility/debugger/reference/idebugexpression2-abort.md)|비동기 식 계산을 종료 합니다.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|식을 동기적으로 계산 합니다.|

 동기 및 비동기 평가를 수행 하려면 [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 메서드를 구현 해야 합니다. 비동기 식 계산에는 [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)의 구현이 필요 합니다.

## <a name="see-also"></a>추가 정보
- [실행 제어 및 상태 평가](../../extensibility/debugger/execution-control-and-state-evaluation.md)
