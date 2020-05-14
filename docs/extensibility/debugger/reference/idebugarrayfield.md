---
title: 이데버그어레이필드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField
helpviewer_keywords:
- IDebugArrayField interface
ms.assetid: 9667b0a5-4295-46cc-9388-b75c1350be15
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dab01c1e956ced7e6894b951ab16f4ce68eb778b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736298"
---
# <a name="idebugarrayfield"></a>IDebugArrayField
이 인터페이스는 배열 기호 또는 형식을 설명합니다.

## <a name="syntax"></a>구문

```
IDebugArrayField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 기호 공급자는 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스를 구현 하는 동일한 개체에이 인터페이스를 구현 합니다. 이 인터페이스는 배열 개체를 나타내는 특수화입니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [GetKind가](../../../extensibility/debugger/reference/idebugfield-getkind.md) 플래그를 `FIELD_TYPE_ARRAY`반환하는 경우 [쿼리 인터페이스를](/cpp/atl/queryinterface) 사용하여 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스에서 이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 및 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스의 메서드 외에도 다음을 구현합니다.

|방법|설명|
|------------|-----------------|
|[GetNumberOfElements](../../../extensibility/debugger/reference/idebugarrayfield-getnumberofelements.md)|배열의 요소 수를 가져옵니다.|
|[GetElementType](../../../extensibility/debugger/reference/idebugarrayfield-getelementtype.md)|배열에서 요소의 형식을 가져옵니다.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayfield-getrank.md)|배열의 순위를 가져옵니다.|

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
