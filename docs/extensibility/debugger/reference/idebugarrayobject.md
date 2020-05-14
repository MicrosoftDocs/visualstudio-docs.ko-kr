---
title: 아이데버그어레이오브젝트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 709273b89d89759163acb725220d1092d33ad72f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736220"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 평가기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 평가기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 이 인터페이스는 배열 개체를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugArrayObject : IDebugObject
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 식 평가기는 배열을 나타내기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 개체가 배열을 나타내는 경우 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 인터페이스는 [QueryInterface를](/cpp/atl/queryinterface) 사용하여 이 인터페이스를 가져올 수 있습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 `IDebugObject` 인터페이스의 메서드 외에도 다음 메서드가 인터페이스에서 `IDebugArrayObject` 구현됩니다.

|방법|설명|
|------------|-----------------|
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|배열의 요소 수를 가져옵니다.|
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|배열의 요소를 가져옵니다.|
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|배열의 모든 요소를 가져옵니다.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|배열의 순위를 가져옵니다.|
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|배열의 차원을 가져옵니다.|

## <a name="remarks"></a>설명
 식 계산기는 이 인터페이스를 사용하여 구문 분석 트리의 배열을 나타냅니다.

## <a name="requirements"></a>요구 사항
 헤더: ee.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
