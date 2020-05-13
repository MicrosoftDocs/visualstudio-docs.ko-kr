---
title: 아이디버그포인터오브젝트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b28189b3f0a07a27f5e4478f64963a63d634db5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725496"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 평가기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 평가기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 이 인터페이스는 포인터 개체를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugPointerObject : IDebugObject
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 식 계산기는 포인터 개체를 나타내기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 인터페이스는 포인터를 `IDebugObject` 나타내는 경우 [QueryInterface를](/cpp/atl/queryinterface) 사용하여 이 인터페이스를 가져올 수 있습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 [IDebugObject에서](../../../extensibility/debugger/reference/idebugobject.md)상속된 메서드 외에도 인터페이스는 `IDebugPointerObject` 다음 메서드를 노출합니다.

|방법|설명|
|------------|-----------------|
|[Dereference](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|인터페이스가 가리키는 개체를 가져옵니다.|
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|인터페이스가 연속 바이트의 시리즈로 가리키는 값을 가져옵니다.|
|[설정수](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|일련의 연속 바이트에서 인터페이스가 가리키는 값을 설정합니다.|

## <a name="remarks"></a>설명
 식 계산기는 이 인터페이스를 사용하여 구문 분석 트리의 포인터를 나타냅니다.

## <a name="requirements"></a>요구 사항
 헤더: ee.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
