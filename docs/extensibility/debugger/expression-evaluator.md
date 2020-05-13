---
title: 표현식 평가기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a477aaceb57e6ccd2eb5125fcf9d8af9be59472b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738682"
---
# <a name="expression-evaluator"></a>식 계산기
식 평가기(EE)는 언어 구문을 검사하여 런타임에 변수와 식을 구문 분석하고 평가하여 IDE가 중단 모드에 있을 때 사용자가 볼 수 있도록 합니다.

## <a name="use-expression-evaluators"></a>식 계산기 사용
 식은 다음과 같이 [ParseText 메서드를](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 사용하여 만들어집니다.

1. 디버그 엔진(DE)은 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스를 구현합니다.

2. 디버그 패키지는 `IDebugExpressionContext2` [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) 인터페이스에서 개체를 가져옵니다. `IDebugStackFrame2::ParseText` [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)

3. 디버그 패키지는 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 메서드 또는 [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 메서드를 호출하여 식값을 가져옵니다. `IDebugExpression2::EvaluateAsync`명령/즉시 창에서 호출됩니다. 다른 모든 UI `IDebugExpression2::EvaluateSync`구성 요소는 을 호출합니다.

4. 식 평가 의 결과는 식 평가 결과의 이름, 형식 및 값을 포함하는 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 개체입니다.

   식 평가 중에 EE는 기호 공급자 구성 요소의 정보가 필요합니다. 기호 공급자는 구문 분석식을 식별하고 이해하는 데 사용되는 기호 정보를 제공합니다.

   비동기 식 평가가 완료되면 DE가 세션 디버그 관리자(SDM)를 통해 비동기 이벤트를 전송하여 IDE에 식 평가가 완료되었음을 알립니다. 그리고 평가 결과는 `IDebugExpression2::EvaluateSync` 메서드에 대한 호출에서 반환됩니다.

## <a name="implementation-notes"></a>구현 참고 사항
 디버그 엔진은 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 공통 언어 런타임(CLR) 인터페이스를 사용하여 식 계산기와 대화할 것으로 예상합니다. 결과적으로 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 디버그 엔진과 함께 작동하는 식 계산기는 CLR을 지원해야 합니다(모든 CLR 디버깅 인터페이스의 전체 목록은 debugref.doc의 일부인 [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]debugref.doc에서 찾을 수 있습니다).

## <a name="see-also"></a>참조
- [디버거 구성 요소](../../extensibility/debugger/debugger-components.md)
