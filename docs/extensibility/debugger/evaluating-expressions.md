---
title: 표현식 평가 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18e342704cbb4abd7de9667576ce331ef8fbf60a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738825"
---
# <a name="evaluate-expressions"></a>표현식 평가
표현식은 **자동,** **보기,** **QuickWatch**또는 **즉시** 창에서 전달된 문자열에서 만들어집니다. 식을 평가할 때 변수 또는 인수의 이름과 형식과 해당 값을 포함하는 인쇄 가능한 문자열을 생성합니다. 이 문자열은 해당 IDE 창에 표시됩니다.

## <a name="implementation"></a>구현
 식은 프로그램이 중단점에서 중지된 경우 평가됩니다. 식 자체는 지정된 식 평가 컨텍스트 내에서 바인딩 및 평가할 준비가 된 구문 분석식을 나타내는 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 인터페이스로 표시됩니다. 스택 프레임은 Debug Engine(DE)이 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스를 구현하여 제공하는 식 평가 컨텍스트를 결정합니다.

 사용자 문자열과 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스가 있는 경우 DE(디버그 엔진)는 사용자 문자열을 [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 메서드에 전달하여 IDebugExpression2 인터페이스를 가져올 수 있습니다. [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 반환되는 IDebugExpression2 인터페이스에는 평가할 준비가 된 구문 분석식이 포함되어 있습니다.

 인터페이스를 `IDebugExpression2` 사용하면 DE는 [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 또는 [IDebugExpression2::EvaluateAsync를](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)사용하여 동기 식 또는 비동기 식 평가를 통해 식값을 얻을 수 있습니다. 이 값은 변수 또는 인수의 이름 및 유형과 함께 표시를 위해 IDE로 전송됩니다. 값, 이름 및 형식은 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스로 표시됩니다.

 식 평가를 사용하려면 DE는 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 및 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스를 구현해야 합니다. 동기 평가와 비동기 평가 모두 [IDebugProperty2:GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 메서드의 구현이 필요합니다.

## <a name="see-also"></a>참조
- [스택 프레임](../../extensibility/debugger/stack-frames.md)
- [식 평가 컨텍스트](../../extensibility/debugger/expression-evaluation-context.md)
- [디버그 작업](../../extensibility/debugger/debugging-tasks.md)
