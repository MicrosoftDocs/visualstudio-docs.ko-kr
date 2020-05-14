---
title: 표현식 평가기 아키텍처 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aac782c653f230d5598a49d43eb70f548de6dc41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738704"
---
# <a name="expression-evaluator-architecture"></a>표현식 계산기 아키텍처
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 계산기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 전용 언어를 Visual Studio 디버그 패키지에 통합한다는 것은 필요한 식 계산기(EE) 인터페이스를 설정하고 공통 언어 런타임 기호 공급자(SP) 및 바인더 인터페이스를 호출해야 함을 의미합니다. SP 및 바인더 개체는 현재 실행 주소와 함께 식이 평가되는 컨텍스트입니다. 이러한 인터페이스가 생성하고 사용하는 정보는 EE 아키텍처의 주요 개념을 나타냅니다.

## <a name="overview"></a>개요

### <a name="parse-the-expression"></a>표현식 구문 분석
 프로그램을 디버깅하는 경우 표현식은 여러 가지 이유로 평가되지만 항상 디버깅 중인 프로그램이 중단점(사용자가 배치한 중단점 또는 예외로 인한 중단점)에서 중지된 경우 항상 평가됩니다. 이 시점에서 Visual Studio는 DEBug 엔진(DE)에서 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) 인터페이스로 표시되는 스택 프레임을 가져옵니다. 그런 다음 Visual Studio에서 [GetExpressionContext를](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 호출하여 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스를 가져옵니다. 이 인터페이스는 식을 평가할 수 있는 컨텍스트를 나타냅니다. [구문 분석은](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 평가 프로세스의 진입점입니다. 이 시점까지 모든 인터페이스는 DE에 의해 구현됩니다.

 호출 `IDebugExpressionContext2::ParseText` 될 때 DE는 중단점이 발생한 소스 파일의 언어와 관련된 EE를 인스턴스화합니다 (DE는 이 시점에서 SH를 인스턴스화합니다). EE는 [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) 인터페이스로 표시됩니다. 그런 다음 [DE는 구문 분석(텍스트](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 형식)을 평가할 준비가 된 구문 분석식으로 변환하도록 구문 분석(구문 분석)을 호출합니다. 이 구문 분석식은 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 인터페이스로 표시됩니다. 식은 일반적으로 구문 분석되며 이 시점에서 평가되지 않습니다.

 DE는 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 인터페이스를 `IDebugParsedExpression` 구현하고 개체를 `IDebugExpression2` 개체에 넣고 에서 `IDebugExpression2` `IDebugExpressionContext2::ParseText`개체를 반환하는 개체를 만듭니다.

### <a name="evaluate-the-expression"></a>표현식 평가
 Visual Studio는 [평가동기화](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 또는 [EvaluateAsync를](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 호출하여 구문 분석식을 평가합니다. 이러한 두 메서드 는 [EvaluateSync(백그라운드](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) `IDebugExpression2::EvaluateSync` `IDebugExpression2::EvaluateAsync` 스레드를 통해 메서드를 호출하는 동안 메서드를 호출하는 동안 메서드를 호출)를 호출하여 구문 분석식을 평가하고 구문 분석식의 값과 형식을 나타내는 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스를 반환합니다. `IDebugParsedExpression::EvaluateSync`제공된 SH, 주소 및 바인더를 사용하여 `IDebugProperty2` 구문 분석된 식을 인터페이스로 나타내는 실제 값으로 변환합니다.

### <a name="for-example"></a>예를 들면 다음과 같습니다.
 실행 중인 프로그램에서 중단점에 도달한 후 사용자는 **QuickWatch** 대화 상자에서 변수를 보도록 선택합니다. 이 대화 상자에는 변수의 이름, 해당 값 및 해당 형식이 표시됩니다. 사용자는 일반적으로 값을 변경할 수 있습니다.

 **QuickWatch** 대화 상자가 표시되면 검사중인 변수의 이름이 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)로 텍스트로 전송됩니다. 이렇게 하면 구문 분석된 식(이 경우 변수)을 나타내는 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 개체가 반환됩니다. 그런 다음 [EvaluateSync를](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) `IDebugProperty2` 호출하여 변수의 값과 형식및 이름을 나타내는 개체를 생성합니다. 표시되는 것은 이 정보입니다.

 사용자가 변수의 값을 변경 하는 경우 [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) 프로그램 실행을 다시 시작할 때 사용 되도록 메모리에 변수의 값을 변경 하는 새 값으로 호출 됩니다.

 변수 값을 표시하는 이 프로세스에 대한 자세한 내용은 [지역 변수](../../extensibility/debugger/displaying-locals.md) 표시를 참조하십시오. 변수의 값이 변경되는 방법에 대한 자세한 내용은 로컬 값 [변경을](../../extensibility/debugger/changing-the-value-of-a-local.md) 참조하십시오.

## <a name="in-this-section"></a>섹션 내용
 [평가 컨텍스트](../../extensibility/debugger/evaluation-context.md) DE가 EE를 호출할 때 전달되는 인수를 제공합니다.

 [키 표현식 평가기 인터페이스](../../extensibility/debugger/key-expression-evaluator-interfaces.md) 평가 컨텍스트와 함께 EE를 작성할 때 필요한 중요한 인터페이스에 대해 설명합니다.

## <a name="see-also"></a>참조
- [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [지역 주민 표시](../../extensibility/debugger/displaying-locals.md)
- [로컬 값 변경](../../extensibility/debugger/changing-the-value-of-a-local.md)
