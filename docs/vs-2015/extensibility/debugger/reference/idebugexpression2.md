---
title: IDebugExpression2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ec8b26f422ca39b771a47f8eb60ee862d7d388f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62568371"
---
# <a name="idebugexpression2"></a>IDebugExpression2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 바인딩 및 평가를 위해 준비 된 구문 분석 식을 나타냅니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 DE (디버그 엔진)는이 인터페이스를 구현 하 여 평가할 준비 된 식을 나타냅니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 에 대 한 호출은이 인터페이스를 반환 합니다. [Getexpressioncontext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 는 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스를 반환 합니다. 이러한 인터페이스는 디버그 중인 프로그램이 일시 중지 되 고 스택 프레임을 사용할 수 있는 경우에만 액세스할 수 있습니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDebugExpression2` .  
  
|메서드|설명|  
|------------|-----------------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|이 식을 비동기식으로 계산 합니다.|  
|[중단이](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|비동기 식 계산을 종료 합니다.|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|이 식을 동기적으로 계산 합니다.|  
  
## <a name="remarks"></a>설명  
 프로그램이 중지 되 면 세션 디버그 관리자 (SDM)는 [Enum프레임 정보](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)에 대 한 호출을 사용 하 여 DE에서 스택 프레임을 가져옵니다. 그런 다음, SDM은 [Getexpressioncontext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 를 호출 하 여 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스를 가져옵니다. 그런 다음 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 를 호출 하 여 `IDebugExpression2` 평가할 준비가 된 구문 분석 된 식을 나타내는 인터페이스를 만듭니다.  
  
 SDM은 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 또는 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 를 호출 하 여 실제로 식을 계산 하 고 값을 생성 합니다.  
  
 구현에서 `IDebugExpressionContext2::ParseText` DE는 COM의 함수를 사용 하 여 `CoCreateInstance` 식 계산기를 인스턴스화하고 [Idebugexpressionevaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) 인터페이스를 가져옵니다 (인터페이스의 예제 참조 `IDebugExpressionEvaluator` ). 그런 다음 [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 를 호출 하 여 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) 인터페이스를 가져옵니다. 이 인터페이스는 및의 구현에서 `IDebugExpression2::EvaluateSync` `IDebugExpression2::EvaluateAsync` 평가를 수행 하는 데 사용 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)
