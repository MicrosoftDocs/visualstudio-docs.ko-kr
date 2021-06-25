---
title: 식 계산(Visual Studio 디버깅 SDK) | Microsoft Docs
description: 중단 모드 중에 IDE는 프로그램 변수와 관련된 식을 평가합니다. 디버그 엔진이 식을 구문 분석하고 평가하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cf213c30ef26490b44579d83c68b2640360584a7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904515"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>식 계산(Visual Studio 디버깅 SDK)
중단 모드 중에 IDE는 여러 프로그램 변수가 포함된 단순 식을 평가해야 합니다. 평가를 수행하려면 디버그 엔진(DE)이 IDE 창 중 하나에 입력된 식을 구문 분석하고 평가해야 합니다.

 식은 [IDebugExpressionContext2::P arseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 메서드를 사용하여 만들어지고 결과 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 인터페이스로 표시됩니다.

 **IDebugExpression2** 인터페이스는 DE에 의해 구현되고 **해당 EvalAsync** 메서드를 호출하여 IDE에 식 계산 결과를 표시하기 위해 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스를 IDE에 반환합니다. [IDebugProperty2::GetPropertyInfo는](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 식 값을 **조사식** 창이나 지역 창에 넣는 데 사용되는 **구조체를 반환합니다.**

 디버그 패키지 또는 SDM(세션 디버그 관리자)은 [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 또는 [EvaluateSync를](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 호출하여 평가 결과를 나타내는 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스를 얻습니다. `IDebugProperty2` 에는 식의 이름, 형식 및 값을 반환하는 메서드가 있습니다. 이 정보는 다양한 디버거 창에 표시됩니다.

## <a name="using-expression-evaluation"></a>식 계산 사용
 식 계산을 사용하려면 다음 표와 같이 [IDebugExpressionContext2::P arseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 메서드와 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 인터페이스의 모든 메서드를 구현해야 합니다.

|메서드|설명|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|식을 비동기적으로 계산합니다.|
|[중단](../../extensibility/debugger/reference/idebugexpression2-abort.md)|비동기 식 계산을 종료합니다.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|식을 동기적으로 계산합니다.|

 동기 및 비동기 평가에서는 [IDebugProperty2::GetPropertyInfo 메서드를](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 구현해야 합니다. 비동기 식 평가에는 [IDebugExpressionEvaluationCompleteEvent2를](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)구현해야 합니다.

## <a name="see-also"></a>참조
- [실행 제어 및 상태 평가](../../extensibility/debugger/execution-control-and-state-evaluation.md)
