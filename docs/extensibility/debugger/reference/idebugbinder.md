---
title: 이더버그바인더 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fcdec19c4667356edaf9e057c86ddc24baf747b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735965"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 평가기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 평가기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 이 인터페이스는 일반적으로 기호 공급자가 반환하는 기호 필드를 기호의 현재 값을 포함하는 메모리 컨텍스트 또는 개체에 바인딩합니다.

## <a name="syntax"></a>구문

```
IDebugBinder : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 이 인터페이스는 식 평가를 지원하며 DEBug 엔진(DE)에서 구현해야 합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스는 식 평가 프로세스에 사용되며 일반적으로 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 및 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)의 구현에 사용됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugBinder`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[바인딩](../../../extensibility/debugger/reference/idebugbinder-bind.md)|기호의 현재 값을 포함하는 메모리 컨텍스트 또는 개체를 가져옵니다.|
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|개체의 런타임 유형을 결정합니다.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|개체 위치 또는 메모리 주소를 메모리 컨텍스트로 변환합니다.|
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|함수 매개 변수를 만드는 데 사용되는 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 개체를 가져옵니다.|
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|변수에 대한 정확한 형식을 가져옵니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 구문 분석 트리에서 식 계산기에서 사용되는 개체를 반환합니다. 식 계산기는 기호 공급자를 사용하여 식의 기호를 소스 코드의 형식 및 위치 측면에서 각 기호를 설명하는 [IDebugField의](../../../extensibility/debugger/reference/idebugfield.md)인스턴스로 변환하여 식을 구문 분석합니다. [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md) 메서드는 `IDebugField` 기호 형식을 연결 하거나 메모리의 실제 값에 바인딩하는 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 개체에 개체를 변환 합니다. 그런 `IDebugObject` 다음 이러한 개체는 나중에 평가를 위해 구문 분석 트리에 저장됩니다.

## <a name="requirements"></a>요구 사항
 헤더: ee.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
