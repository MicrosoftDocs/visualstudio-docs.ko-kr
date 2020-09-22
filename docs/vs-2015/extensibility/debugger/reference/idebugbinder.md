---
title: IDebugBinder | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dc00c50e3c340ab0685ab1010c6e924e77a18a09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841403"
---
# <a name="idebugbinder"></a>IDebugBinder
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [Clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.  
  
 이 인터페이스는 기호 공급자에 의해 일반적으로 반환 되는 기호 필드를 메모리 컨텍스트 또는 기호의 현재 값을 포함 하는 개체에 바인딩합니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugBinder : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 이 인터페이스는 식 계산을 지원 하며 디버그 엔진 (DE)에서 구현 해야 합니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 이 인터페이스는 식 계산 프로세스에서 사용 되며 일반적으로 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 및 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)구현에 사용 됩니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDebugBinder` .  
  
|메서드|Description|  
|------------|-----------------|  
|[바인딩하며](../../../extensibility/debugger/reference/idebugbinder-bind.md)|기호의 현재 값을 포함 하는 메모리 컨텍스트 또는 개체를 가져옵니다.|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|개체의 런타임 형식을 결정 합니다.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|개체 위치 또는 메모리 주소를 메모리 컨텍스트로 변환 합니다.|  
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|함수 매개 변수를 만드는 데 사용 되는 [Idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 개체를 가져옵니다.|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|변수의 정확한 유형을 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 이 인터페이스는 구문 분석 트리에서 식 계산기에 사용 되는 개체를 반환 합니다. 식 계산기는 기호 공급자를 사용 하 여 식의 기호를 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md)의 인스턴스로 변환 하는 식의 구문을 분석 하 여 소스 코드의 해당 형식 및 위치를 기준으로 각 기호를 설명 합니다. [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md) 메서드는 `IDebugField` 기호 형식을 메모리의 실제 값에 연결 하거나 바인딩하는 [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 개체로 개체를 변환 합니다. 이러한 `IDebugObject` 개체는 나중에 계산할 수 있도록 구문 분석 트리에 저장 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: ee. h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [식 계산 인터페이스](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
