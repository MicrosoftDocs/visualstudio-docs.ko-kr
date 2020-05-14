---
title: 시계 창 표현식 평가 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9cef2f27eec095ee7b136153ecb764feba9effbb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738843"
---
# <a name="evaluate-a-watch-window-expression"></a>시계 창 표현식 평가
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 계산기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 실행이 일시 중지되면 Visual Studio는 DE(디버그 엔진)를 호출하여 감시 목록에 있는 각 식의 현재 값을 결정합니다. DE는 식 계산기(EE)를 사용하여 각 식을 평가하고 Visual Studio는 해당 값을 **보기** 창에 표시합니다.

 다음은 감시 목록 식을 평가하는 방법에 대한 개요입니다.

1. Visual Studio는 DE의 [GetExpressionContext를](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 호출하여 식을 평가하는 데 사용할 수 있는 식 컨텍스트를 가져옵니다.

2. 보기 목록의 각 표현식에 대해 Visual [Studio는 ParseText를](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 호출하여 식 텍스트를 구문 분석식으로 변환합니다.

3. `IDebugExpressionContext2::ParseText`구문 [분석하여](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 텍스트를 구문 분석하는 실제 작업을 수행하 고 [IDebugParsedExpression 개체를](../../extensibility/debugger/reference/idebugparsedexpression.md) 생성 합니다.

4. `IDebugExpressionContext2::ParseText`는 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 개체를 `IDebugParsedExpression` 만들고 개체를 넣습니다. 이`DebugExpression2` I 개체는 Visual Studio로 반환됩니다.

5. Visual Studio는 [평가Sync를](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 호출하여 구문 분석된 식을 평가합니다.

6. `IDebugExpression2::EvaluateSync`실제 평가를 수행 하 고 Visual Studio에 반환 되는 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 개체를 생성 하기 위해 [EvaluateSync에](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 대 한 호출을 전달 합니다.

7. Visual Studio호출 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 다음 감시 목록에 표시 되는 식의 값을 가져옵니다.

## <a name="parse-then-evaluate"></a>그런 다음 구문 분석
 복잡한 식을 구문 분석하는 데 는 평가하는 데 시간이 훨씬 오래 걸릴 수 있으므로 식을 평가하는 프로세스는 1) 식을 구문 분석하고 2) 구문 분석식을 평가합니다. 이렇게 하면 평가가 여러 번 발생할 수 있지만 식은 한 번만 구문 분석해야 합니다. 중간 구문 분석식은 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 개체의 EE에서 반환되며, 이 개체는 차례로 캡슐화되고 [DE에서 IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 개체로 반환됩니다. 개체는 `IDebugExpression` 개체에 대한 `IDebugParsedExpression` 모든 평가를 연기합니다.

> [!NOTE]
> Visual Studio에서 이 프로세스를 가정하더라도 EE가 이 2단계 프로세스를 준수할 필요는 없습니다. EE는 [EvaluateSync가](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 호출될 때 동일한 단계에서 구문 분석및 평가할 수 있습니다(예를 들어 MyCEE 샘플의 작동 방식). 언어가 복잡한 식을 형성할 수 있는 경우 평가 단계에서 구문 분석 단계를 분리할 수 있습니다. 이렇게 하면 많은 시계 표현식이 표시될 때 Visual Studio 디버거의 성능이 향상될 수 있습니다.

## <a name="in-this-section"></a>섹션 내용
 [식 평가의 샘플 구현](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md) MyCEE 샘플을 사용하여 식 평가 프로세스를 단계별로 수행합니다.

 [시계 표현식 평가](../../extensibility/debugger/evaluating-a-watch-expression.md) 성공적인 식 구문 분석 후에 발생하는 일을 설명합니다.

## <a name="related-sections"></a>관련 단원
 [평가 컨텍스트](../../extensibility/debugger/evaluation-context.md) DE(디버그 엔진)가 식 계산기(EE)를 호출할 때 전달되는 인수를 제공합니다.

## <a name="see-also"></a>참조
 [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
