---
title: 조사식 창 식 계산 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f13573cfecbd81f36e3b77e9b23beeaa558c08dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842042"
---
# <a name="evaluating-a-watch-window-expression"></a>조사식 창 식 계산
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [Clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.  
  
 실행이 일시 중지 되 면 Visual Studio는 디버그 엔진 (DE)을 호출 하 여 조사식 목록에서 각 식의 현재 값을 확인 합니다. DE는 식 계산기 (EE)를 사용 하 여 각 식을 평가 하 고, Visual Studio는 **조사식** 창에 해당 값을 표시 합니다.  
  
 조사식 목록 식이 평가 되는 방법에 대 한 개요는 다음과 같습니다.  
  
1. Visual Studio는 DE의 [Getexpressioncontext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 를 호출 하 여 식을 계산 하는 데 사용할 수 있는 식 컨텍스트를 가져옵니다.  
  
2. 조사식 목록의 각 식에 대해 Visual Studio는 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 를 호출 하 여 식 텍스트를 구문 분석 된 식으로 변환 합니다.  
  
3. `IDebugExpressionContext2::ParseText` 는 [구문 분석](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 을 호출 하 여 텍스트를 구문 분석 하 고 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 개체를 생성 하는 실제 작업을 수행 합니다.  
  
4. `IDebugExpressionContext2::ParseText`[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 개체를 만들고이 개체에 `IDebugParsedExpression` 개체를 넣습니다. `DebugExpression2`그런 다음이 개체는 Visual Studio로 반환 됩니다.  
  
5. Visual Studio는 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 을 호출 하 여 구문 분석 된 식을 평가 합니다.  
  
6. `IDebugExpression2::EvaluateSync`[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 에 대 한 호출을 전달 하 여 실제 평가를 수행 하 고 Visual Studio로 반환 되는 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 개체를 생성 합니다.  
  
7. Visual Studio는 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 를 호출 하 여 조사식 목록에 표시 되는 식의 값을 가져옵니다.  
  
## <a name="parse-then-evaluate"></a>구문 분석 후 평가  
 복잡 한 식의 구문 분석을 계산 하는 것 보다 훨씬 더 오래 걸릴 수 있으므로 식을 계산 하는 프로세스는 두 단계로 구분 됩니다. 1) 식 구문 분석 및 2) 구문 분석 된 식을 평가 합니다. 이러한 방식으로 평가는 여러 번 발생할 수 있지만 식은 한 번만 구문 분석 해야 합니다. 구문 분석 된 중간 식은 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 개체의 EE에서 반환 됩니다 .이 개체는 DE로 캡슐화 되 고 DE에서 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 개체로 반환 됩니다. 개체는 `IDebugExpression` 개체에 대 한 모든 계산을 지연 시킵니다 `IDebugParsedExpression` .  
  
> [!NOTE]
> Visual Studio에서 가정 하는 경우에도 EE에서이 2 단계 프로세스를 따를 필요는 없습니다. [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 가 호출 될 때 EE는 동일한 단계에서 구문을 분석 하 고 평가할 수 있습니다. 예를 들어 MyCEE 샘플이 작동 합니다. 언어가 복잡 한 식을 구성할 수 있는 경우 평가 단계에서 구문 분석 단계를 분리 하는 것이 좋습니다. 이렇게 하면 많은 조사식 식이 표시 되는 경우 Visual Studio 디버거의 성능을 향상 시킬 수 있습니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [식 계산의 샘플 구현](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 MyCEE 샘플을 사용 하 여 식 계산 과정을 단계별로 실행 합니다.  
  
 [조사식 창 계산](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 식 구문 분석이 완료 된 후 발생 하는 상황을 설명 합니다.  
  
## <a name="related-sections"></a>관련 단원  
 [평가 컨텍스트](../../extensibility/debugger/evaluation-context.md)  
 디버그 엔진 (DE)에서 식 계산기 (EE)를 호출할 때 전달 되는 인수를 제공 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
