---
title: 식 계산 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caff42c2e203151c6bab7d50b41744c2469ab3c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151625"
---
# <a name="evaluating-expressions"></a>식 계산
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

식은 자동, 조사식, 간략 한 조사식 또는 직접 실행 창에서 전달 된 문자열에서 생성 됩니다. 식이 계산 될 때 변수 또는 인수의 이름 및 형식과 해당 값이 포함 된 인쇄 가능한 문자열을 생성 합니다. 이 문자열은 해당 IDE 창에 표시 됩니다.  
  
## <a name="implementation"></a>구현  
 식은 프로그램이 중단점에서 중지 될 때 평가 됩니다. 식 자체는 지정 된 식 계산 컨텍스트 내에서 바인딩과 계산에 사용할 수 있는 구문 분석 된 식을 나타내는 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 인터페이스로 표시 됩니다. 스택 프레임은 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스를 구현 하 여 디버그 엔진 (DE)에서 제공 하는 식 계산 컨텍스트를 결정 합니다.  
  
 사용자 문자열과 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스가 지정 된 경우 디버그 엔진 (DE)은 사용자 문자열을 [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 메서드에 전달 하 여 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 인터페이스를 가져올 수 있습니다. 반환 된 IDebugExpression2 인터페이스에는 평가할 준비가 된 구문 분석 된 식이 포함 됩니다.  
  
 인터페이스를 사용 하 여 `IDebugExpression2` DE는 [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 또는 [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)를 사용 하 여 동기 또는 비동기 식 계산을 통해 식의 값을 가져올 수 있습니다. 이 값은 변수 또는 인수의 이름 및 형식과 함께 표시를 위해 IDE에 전송 됩니다. 값, 이름 및 형식은 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스로 표시 됩니다.  
  
 식 계산을 사용 하도록 설정 하려면 DE가 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 및 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스를 구현 해야 합니다. 동기 및 비동기를 모두 계산 하려면 [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 메서드를 구현 해야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [스택 프레임](../../extensibility/debugger/stack-frames.md)   
 [식 계산 컨텍스트](../../extensibility/debugger/expression-evaluation-context.md)   
 [디버깅 작업](../../extensibility/debugger/debugging-tasks.md)
