---
title: 아이데버그오브젝트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6801176964a47646f03091131e1be89cf63c97f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726306"
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 평가기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 평가기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 이 인터페이스는 바인더가 기호 및 식의 값을 캡슐화하기 위해 만드는 개체를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugObject : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 식 계산기는 개체를 나타내기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스는 식 계산기에서 구문 분석식에서 사용하는 모든 개체에 대한 기본 클래스입니다. [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md) 메서드에 대 한 호출에 의해 반환 됩니다. [쿼리인터페이스는](/cpp/atl/queryinterface) 이 인터페이스에서 보다 특수화된 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugObject`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|개체의 크기를 가져옵니다.|
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|개체값을 연속적인 바이트 로 가져옵니다.|
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|연속된 바이트 시리즈에서 개체값을 설정합니다.|
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|이 개체의 참조 값을 설정합니다.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|개체 값의 주소를 나타내는 메모리 컨텍스트를 가져옵니다.|
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|디버그 엔진의 주소 공간에 관리되는 개체의 복사본을 만듭니다.|
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|이 개체가 null 참조인지 여부를 테스트합니다.|
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|개체를 이 개체와 비교합니다.|
|[Isreadonly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|이 개체가 읽기 전용인지 확인합니다.|
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|개체가 투명 프록시인지 여부를 결정합니다.|

## <a name="remarks"></a>설명
 식 계산기는 이 인터페이스를 기본 클래스로 사용하여 구문 분석 트리의 개체를 나타냅니다.

## <a name="requirements"></a>요구 사항
 헤더: ee.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)
- [바인딩](../../../extensibility/debugger/reference/idebugbinder-bind.md)
