---
title: 식 계산기 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738682"
---
# <a name="expression-evaluator"></a>식 계산기
식 계산기 (EE)는 런타임에 변수와 식을 구문 분석 하 고 평가 하 여 IDE가 중단 모드에 있을 때 사용자가 볼 수 있도록 하는 언어의 구문을 검사 합니다.

## <a name="use-expression-evaluators"></a>식 계산기 사용
 식은 다음과 같이 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 메서드를 사용 하 여 생성 됩니다.

1. 디버그 엔진 (DE)은 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스를 구현 합니다.

2. 디버그 패키지는 `IDebugExpressionContext2` [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) 인터페이스에서 개체를 가져온 다음 메서드를 호출 `IDebugStackFrame2::ParseText` 하 여 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 개체를 가져옵니다.

3. 디버그 패키지는 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 메서드 또는 [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 메서드를 호출 하 여 식의 값을 가져옵니다. `IDebugExpression2::EvaluateAsync` 는 명령/직접 실행 창에서 호출 됩니다. 다른 모든 UI 구성 요소는 `IDebugExpression2::EvaluateSync` 를 호출 합니다.

4. 식 계산의 결과는 이름, 형식 및 식 계산 결과의 값을 포함 하는 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 개체입니다.

   식을 평가 하는 동안 EE에 기호 공급자 구성 요소의 정보가 필요 합니다. 기호 공급자는 구문 분석 된 식을 식별 하 고 이해 하는 데 사용 되는 기호화 된 정보를 제공 합니다.

   비동기 식 계산이 완료 되 면 세션 디버그 관리자 (SDM)를 통해 해제 하 여 비동기 이벤트를 보내 식 평가가 완료 되었음을 IDE에 알립니다. 그런 다음, 계산 결과가 메서드 호출에서 반환 됩니다 `IDebugExpression2::EvaluateSync` .

## <a name="implementation-notes"></a>구현 참고 사항
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]디버그 엔진은 CLR (공용 언어 런타임) 인터페이스를 사용 하 여 식 계산기와 통신할 것으로 간주 합니다. 따라서 디버그 엔진에서 작동 하는 식 계산기는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] clr을 지원 해야 합니다. 모든 clr 디버깅 인터페이스의 전체 목록은의 일부인 debugref.doc에서 찾을 수 있습니다 [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] .

## <a name="see-also"></a>추가 정보
- [디버거 구성 요소](../../extensibility/debugger/debugger-components.md)
