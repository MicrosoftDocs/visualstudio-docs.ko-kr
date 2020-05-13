---
title: 아이디버그프로퍼티2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b04abdac135143ccbbd1b8e5632bf85c974f29d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721230"
---
# <a name="idebugproperty2"></a>IDebugProperty2
이 인터페이스는 스택 프레임 속성, 프로그램 문서 속성 또는 기타 속성을 나타냅니다. 속성은 일반적으로 식 평가의 결과입니다.

> [!NOTE]
> "속성"의 이러한 사용은 클래스의 멤버 변수를 의미하는 것과 혼동해서는 안되지만 이러한 엔터티를 `IDebugProperty2` 나타낼 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugProperty2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DE는 특정 종류의 값을 나타내기 위해 이 인터페이스를 구현합니다. 예를 들어, 값은 식 평가의 결과로 숫자 값, 메모리를 표시하는 데 사용되는 메모리 컨텍스트 또는 레지스터 및 해당 값의 목록일 수 있습니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [평가 동기화](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 또는 [EvaluateAsync를](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 호출하여 평가 결과를 나타내는 이 인터페이스를 가져옵니다. `IDebugExpression2::EvaluateAsync`[IDebugExpressionExpressionCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) 인터페이스를 SDM에 전송하여 이 인터페이스를 반환하고, 이 인터페이스는 [GetResult를](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) 호출하여 속성을 검색합니다.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) 는 연결된 스크립트 문서를 제공하기 위해 이 인터페이스를 반환합니다.

- [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) 함수의 반환 값을 나타내는이 인터페이스를 반환 합니다.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) 이름 또는 메모리 컨텍스트 와 같은 프로그램의 다양 한 속성을 나타내는이 인터페이스를 반환 합니다.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) 는 로컬 변수와 같은 스택 프레임의 다양한 속성을 나타내기 위해 이 인터페이스를 반환합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugProperty2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[겟프로퍼정보](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|속성을 설명하는 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 구조를 채웁니다.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|문자열에서 속성의 값을 설정합니다.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|지정된 참조 값에서 속성 값을 설정합니다.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|속성의 자식을 새는다.|
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|속성의 부모를 반환합니다.|
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|속성의 가장 파생된 속성을 설명하는 속성을 반환합니다.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|속성 값을 구성하는 메모리 바이트를 반환합니다.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|속성 값에 대한 메모리 컨텍스트를 반환합니다.|
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|속성 값의 크기를 바이트로 반환합니다.|
|[Get참조](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|이 속성의 값에 대 한 참조를 반환 합니다.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|속성의 확장 된 정보를 반환 합니다.|

## <a name="remarks"></a>설명
 `IDebugProperty2` 인터페이스로 표시되는 속성은 이름, 형식 및 주소가 있는 값으로 생각할 수 있습니다. 보다 일반적인 용어로, a는 `IDebugProperty2` 부모 노드와 하위 노드를 포함하는 계층 구조가 있는 모든 것을 나타낼 수 있습니다.

 속성은 일반적으로 일시적이며 현재 스택 프레임만큼만 지속됩니다. 반면에 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 인터페이스로 표시되는 참조는 값이 메모리에 남아 있는 한 지속됩니다.

 IDE는 인터페이스를 `IDebugProperty2` 사용하여 사용자가 런타임에 속성을 찾아보고 수정할 수 있도록 할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
