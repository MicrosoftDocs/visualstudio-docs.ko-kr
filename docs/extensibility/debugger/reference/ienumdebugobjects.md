---
title: 이넘디버그오브젝트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c04409fb695613fea5d54b285946c04719fbe5b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716259"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 평가기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 평가기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 이 인터페이스는 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 인터페이스를 구현하는 개체의 컬렉션을 나타냅니다.

## <a name="syntax"></a>구문

```
IEnumDebugObjects : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 식 평가기는 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 인터페이스를 구현하는 개체 집합을 제공하기 위해 이 인터페이스를 구현합니다. [GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) 메서드가 있기 때문에 표준 COM 열거형이 아닙니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
- [GetElements는](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) 이 인터페이스를 반환합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는 다음 메서드를 구현합니다.

|방법|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|열거형에서 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 개체의 다음 집합을 검색합니다.|
|[건너뛸](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|지정된 수의 항목을 건너뜁니다.|
|[다시 설정](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|열거형항목을 첫 번째 항목으로 재설정합니다.|
|[복제](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|현재 열거형의 복사본을 검색합니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|열거형의 항목 수를 검색합니다.|

## <a name="remarks"></a>설명
 이 인터페이스를 사용하면 디버그 엔진이 배열의 개체 집합을 열거할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: ee.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)
