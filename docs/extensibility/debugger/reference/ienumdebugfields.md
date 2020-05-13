---
title: 이넘데버그필드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d577ff2f5848f2cb348bcaccf57875507018634b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716787"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
이 인터페이스는 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스를 구현하는 개체의 컬렉션을 나타냅니다.

## <a name="syntax"></a>구문

```
IEnumDebugFields : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 이 인터페이스는 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스를 구현 하는 개체 집합을 제공 하기 위해 기호 공급자에 의해 구현 됩니다. [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) 메서드가 있기 때문에 표준 COM 열거형이 아닙니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스는 [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) 및 [GetName스페이스사용주소에서](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)반환됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는 다음 메서드를 구현합니다.

|방법|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|열거형에서 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 개체의 다음 집합을 검색합니다.|
|[건너뛸](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|지정된 수의 항목을 건너뜁니다.|
|[다시 설정](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|열거형항목을 첫 번째 항목으로 재설정합니다.|
|[복제](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|현재 열거형의 복사본을 검색합니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|열거형의 항목 수를 검색합니다.|

## <a name="remarks"></a>설명

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)
- [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)
