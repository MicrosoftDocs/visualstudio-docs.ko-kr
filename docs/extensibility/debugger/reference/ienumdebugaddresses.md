---
title: 이넘디버그 주소 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14b42ec37babe72b47b0e832397d33029c4fc3d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717589"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
이 인터페이스는 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 인터페이스를 구현하는 개체의 컬렉션을 나타냅니다.

## <a name="syntax"></a>구문

```
IEnumDebugAdresses : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 이 인터페이스는 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 인터페이스를 구현하는 개체 집합을 제공하기 위해 기호 공급자에 의해 구현됩니다. [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) 메서드가 있기 때문에 표준 COM 열거형이 아닙니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스는 [Get주소FromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) 및 [Get주소FromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는 다음 메서드를 구현합니다.

|방법|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|열거형에서 [다음 IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 개체 집합을 검색합니다.|
|[건너뛸](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|지정된 수의 항목을 건너뜁니다.|
|[다시 설정](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|열거형항목을 첫 번째 항목으로 재설정합니다.|
|[복제](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|현재 열거형의 복사본을 검색합니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|열거형의 항목 수를 검색합니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 일반적으로 디버그 엔진에서 식 계산자에게 줄 적절한 주소를 결정하는 데 사용됩니다.

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
