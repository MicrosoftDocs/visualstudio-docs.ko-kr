---
title: IDebugProperty2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1f72a66e6dbfe2749910019760c16f6363498785
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841735"
---
# <a name="idebugproperty2"></a>IDebugProperty2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 스택 프레임 속성, 프로그램 문서 속성 또는 일부 다른 속성을 나타냅니다. 속성은 일반적으로 식 계산의 결과입니다.  
  
> [!NOTE]
> 이러한 엔터티를 나타낼 수 있지만 "속성"을 사용 하면 클래스의 멤버 변수를 의미 하는 것과 혼동 해서는 안 됩니다 `IDebugProperty2` .  
  
## <a name="syntax"></a>구문  
  
```  
IDebugProperty2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 DE는 특정 종류의 값을 나타내기 위해이 인터페이스를 구현 합니다. 예를 들어 값은 식 계산의 결과로 숫자 값, 메모리를 표시 하는 데 사용 되는 메모리 컨텍스트, 레지스터 및 해당 값 목록 일 수 있습니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 또는 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 를 호출 하 여 평가 결과를 나타내는이 인터페이스를 가져옵니다. `IDebugExpression2::EvaluateAsync`[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) 인터페이스를 SDM에 전송 하 여이 인터페이스를 반환 합니다. 그러면이 인터페이스는 [getresult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) 를 호출 하 여 속성을 검색 합니다.  
  
 [Getdebugproperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) 는 연결 된 스크립트 문서를 제공 하기 위해이 인터페이스를 반환 합니다.  
  
 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) 는 함수의 반환 값을 나타내기 위해이 인터페이스를 반환 합니다.  
  
 [Getdebugproperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) 는 이름 또는 메모리 컨텍스트와 같은 프로그램의 다양 한 속성을 나타내기 위해이 인터페이스를 반환 합니다.  
  
 [Getdebugproperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) 는 지역 변수와 같은 스택 프레임의 다양 한 속성을 나타내기 위해이 인터페이스를 반환 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDebugProperty2` .  
  
|메서드|Description|  
|------------|-----------------|  
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|속성을 설명 하는 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 구조체를 채웁니다.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|문자열에서 속성 값을 설정 합니다.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|지정 된 참조 값에서 속성의 값을 설정 합니다.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|속성의 자식을 열거 합니다.|  
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|속성의 부모를 반환 합니다.|  
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|속성의 가장 많이 파생 된 속성을 설명 하는 속성을 반환 합니다.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|속성의 값을 구성 하는 메모리 바이트를 반환 합니다.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|속성 값에 대 한 메모리 컨텍스트를 반환 합니다.|  
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|속성 값의 크기 (바이트)를 반환 합니다.|  
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|이 속성 값에 대 한 참조를 반환 합니다.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|속성의 확장 정보를 반환 합니다.|  
  
## <a name="remarks"></a>설명  
 인터페이스로 표시 되는 속성은 `IDebugProperty2` 이름, 형식 및 주소를 사용 하는 값으로 간주할 수 있습니다. 보다 일반적인 용어로는 `IDebugProperty2` 부모 및 자식 노드를 사용 하 여 계층 구조가 있는 모든 항목을 나타낼 수 있습니다.  
  
 속성은 일반적으로 일시적 이며, 예를 들어 현재 스택 프레임이 지속 되는 동안에만 지속 됩니다. 반면에 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 인터페이스로 표시 되는 참조는 값이 메모리에 유지 되는 동안 지속 됩니다.  
  
 IDE는 인터페이스를 사용 `IDebugProperty2` 하 여 사용자가 런타임에 속성을 검색 하 고 수정할 수 있도록 합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
