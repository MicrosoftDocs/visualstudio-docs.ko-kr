---
title: 식 계산기 아키텍처 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738704"
---
# <a name="expression-evaluator-architecture"></a>식 계산기 아키텍처
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.

 소유 언어를 Visual Studio 디버그 패키지에 통합 하는 것은 필요한 EE (식 계산기) 인터페이스를 설정 하 고 공용 언어 SP (런타임 기호 공급자) 및 바인더 인터페이스를 호출 해야 함을 의미 합니다. SP 및 binder 개체는 현재 실행 주소와 함께 식이 계산 되는 컨텍스트입니다. 이러한 인터페이스에서 생성 하 고 사용 하는 정보는 EE 아키텍처의 핵심 개념을 나타냅니다.

## <a name="overview"></a>개요

### <a name="parse-the-expression"></a>식 구문 분석
 프로그램을 디버그할 때 식은 여러 가지 이유로 평가 되지만 디버깅 중인 프로그램이 중단점에서 중지 된 경우 (사용자가 배치 하는 중단점 또는 예외에 의해 발생 한 경우) 항상 사용 됩니다. 이 순간에는 Visual Studio가 디버그 엔진 (DE)에서 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) 인터페이스로 표시 되는 스택 프레임을 가져올 때입니다. 그런 다음 Visual Studio는 [Getexpressioncontext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 를 호출 하 여 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스를 가져옵니다. 이 인터페이스는 식을 평가할 수 있는 컨텍스트를 나타냅니다. [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 는 평가 프로세스에 대 한 진입점입니다. 이 시점까지 모든 인터페이스가 DE에 의해 구현 됩니다.

 `IDebugExpressionContext2::ParseText`가 호출 되 면 de는 중단점이 발생 한 소스 파일의 언어와 연결 된 EE를 인스턴스화합니다. (de는이 시점 에서도 SH를 인스턴스화합니다.) EE는 [Idebugexpressionevaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) 인터페이스로 표시 됩니다. 그런 다음 [구문 분석](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 을 호출 하 여 식 (텍스트 형식)을 구문 분석 된 식으로 변환 하 고, 평가할 준비를 합니다. 이 구문 분석 된 식은 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 인터페이스로 표시 됩니다. 식은 일반적으로 구문 분석 되 고이 시점에서 계산 되지 않습니다.

 DE는 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 인터페이스를 구현 하는 개체를 만들고 개체를 `IDebugParsedExpression` 개체에 배치 `IDebugExpression2` 하 고 `IDebugExpression2` 에서 개체를 반환 합니다 `IDebugExpressionContext2::ParseText` .

### <a name="evaluate-the-expression"></a>식 계산
 Visual Studio는 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 또는 [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 를 호출 하 여 구문 분석 된 식을 평가 합니다. 이러한 두 메서드는 모두 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (메서드를 즉시 호출 하 고 `IDebugExpression2::EvaluateSync` ,는 메서드를 즉시 호출 하 여 `IDebugExpression2::EvaluateAsync` )를 호출 하 고 구문 분석 된 식을 평가 하 고 구문 분석 된 식의 값과 형식을 나타내는 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스를 반환 합니다. `IDebugParsedExpression::EvaluateSync` 제공 된 SH, address 및 binder를 사용 하 여 구문 분석 된 식을 인터페이스에서 나타내는 실제 값으로 변환 합니다 `IDebugProperty2` .

### <a name="for-example"></a>예를 들면 다음과 같습니다.
 실행 중인 프로그램에서 중단점이 적중 되 면 사용자는 **간략 한 조사식** 대화 상자에서 변수를 보도록 선택 합니다. 이 대화 상자에는 변수의 이름, 값 및 해당 형식이 표시 됩니다. 일반적으로 사용자는 값을 변경할 수 있습니다.

 간략 한 **조사식** 대화 상자가 표시 되 면 검사 되는 변수의 이름이 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)에 텍스트로 전송 됩니다. 이렇게 하면 구문 분석 된 식 (이 경우 변수)을 나타내는 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 개체가 반환 됩니다. 그런 다음 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 를 호출 하 여 `IDebugProperty2` 변수의 값과 형식 뿐만 아니라 해당 이름을 나타내는 개체를 생성 합니다. 표시 되는 정보입니다.

 사용자가 변수 값을 변경 하는 경우 [Setvalueasstring](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) 이 새 값을 사용 하 여 호출 됩니다. 그러면 메모리의 변수 값이 변경 되어 프로그램 실행이 다시 시작 될 때 사용 됩니다.

 변수의 값을 표시 하는이 프로세스에 대 한 자세한 내용은 [지역 표시](../../extensibility/debugger/displaying-locals.md) 를 참조 하세요. 변수의 값을 변경 하는 방법에 대 한 자세한 내용은 [로컬 값 변경](../../extensibility/debugger/changing-the-value-of-a-local.md) 을 참조 하세요.

## <a name="in-this-section"></a>섹션 내용
 [평가 컨텍스트](../../extensibility/debugger/evaluation-context.md) DE가 EE를 호출할 때 전달 되는 인수를 제공 합니다.

 [키 식 계산기 인터페이스](../../extensibility/debugger/key-expression-evaluator-interfaces.md) 실행 컨텍스트와 함께 EE를 작성할 때 필요한 중요 한 인터페이스에 대해 설명 합니다.

## <a name="see-also"></a>추가 정보
- [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [지역 표시](../../extensibility/debugger/displaying-locals.md)
- [로컬의 값 변경](../../extensibility/debugger/changing-the-value-of-a-local.md)
