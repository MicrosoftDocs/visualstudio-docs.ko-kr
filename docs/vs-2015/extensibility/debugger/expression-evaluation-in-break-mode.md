---
title: 중단 모드에서 식 계산 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 362e50e20519c358564d13ba169f706fe384ca5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152753"
---
# <a name="expression-evaluation-in-break-mode"></a>중단 모드에서 식 계산
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

다음에서는 디버거가 중단 모드에 있을 때 발생 하는 프로세스를 설명 하 고 식 계산을 수행 해야 합니다.  
  
## <a name="expression-evaluation-process"></a>식 계산 프로세스  
 다음은 식 계산과 관련 된 기본 단계입니다.  
  
1. SDM (세션 디버그 관리자)은 [IDebugStackFrame2:: GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 를 호출 하 여 식 컨텍스트 인터페이스인 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)를 가져옵니다.  
  
2. 그러면 SDM에서 구문 분석할 문자열을 사용 하 여 [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 를 호출 합니다.  
  
3. ParseText가 S_OK 반환 하지 않으면 오류의 원인이 반환 됩니다.  
  
     그렇지  
  
     ParseText가 S_OK 반환 하는 경우 SDM은 [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 또는 [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 중 하나를 호출 하 여 구문 분석 된 식에서 최종 값을 가져올 수 있습니다.  
  
    - 를 사용 하는 경우 `IDebugExpression2::EvaluateSync` 지정 된 콜백 인터페이스를 사용 하 여 진행 중인 평가 프로세스를 전달 합니다. 최종 값은 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스에서 반환 됩니다.  
  
    - 를 사용 하는 경우 `IDebugExpression2::EvaluateAsync` 지정 된 콜백 인터페이스를 사용 하 여 진행 중인 평가 프로세스를 전달 합니다. 평가가 완료 되 면 EvaluateAsync은 콜백을 통해 [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) 인터페이스를 보냅니다. 이 이벤트 인터페이스를 사용 하면 [Getresult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)를 사용 하 여 최종 값을 가져올 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)
