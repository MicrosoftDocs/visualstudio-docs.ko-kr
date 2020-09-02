---
title: 'IDebugStackFrame2:: GetExpressionContext | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetExpressionContext
helpviewer_keywords:
- IDebugStackFrame2::GetExpressionContext
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7aea3543401faa1e7a6fd3ab2d3de073b5e6b3bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164741"
---
# <a name="idebugstackframe2getexpressioncontext"></a>IDebugStackFrame2::GetExpressionContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

스택 프레임 및 스레드의 현재 컨텍스트 내에서 식 계산에 대 한 평가 컨텍스트를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetExpressionContext (   
   IDebugExpressionContext2** ppExprCxt  
);  
```  
  
```csharp  
int GetExpressionContext (   
   out IDebugExpressionContext2 ppExprCxt  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppExprCxt`  
 제한이 식 계산에 대 한 컨텍스트를 나타내는 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) 개체를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 일반적으로 식 계산 컨텍스트는 식 계산을 수행 하기 위한 범위로 간주할 수 있습니다. [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 메서드를 호출 하 여 식을 구문 분석 한 다음 결과 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 또는 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 메서드를 호출 하 여 구문 분석 된 식을 평가 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
