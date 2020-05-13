---
title: METADATA_ADDRESS_LOCAL | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3adf9ca5f679c7a526f10b1ee6c91d50dac52d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714480"
---
# <a name="metadata_address_local"></a>METADATA_ADDRESS_LOCAL

이 구조는 범위 내의 로컬 변수(일반적으로 함수 또는 메서드)의 주소를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _tagMETADATA_ADDRESS_LOCAL {
    _mdToken  tokMethod;
    IUnknown* pLocal;
    DWORD     dwIndex;
} METADATA_ADDRESS_LOCAL;
```

```csharp
public struct METADATA_ADDRESS_LOCAL {
    public int    tokMethod;
    public object pLocal;
    public uint   dwIndex;
}
```

## <a name="members"></a>멤버

`tokMethod`\
로컬 변수의 메서드 또는 함수의 ID입니다.

[C++] `_mdToken` 32 `typedef` 비트에 `int`대 한입니다.

`pLocal`\
이 구조가 나타내는 주소가 있는 토큰입니다.

`dwIndex`\
메서드 또는 함수에서 이 로컬 변수의 인덱스 또는 다른 값(언어별)일 수 있습니다.

## <a name="remarks"></a>설명

이 구조는 `dwKind` `DEBUG_ADDRESS_UNION` 구조의 필드가 설정될 때 `ADDRESS_KIND_LOCAL` [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) 구조체의 결합의 일부입니다(ADDRESS_KIND 열거된 값). [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)

> [!WARNING]
> [C++ 전용] null이 아닌 `pLocal` 경우 token `Release` 포인터`addr` [(DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 구조의 필드)를 호출해야합니다.
>
> ```cpp
> if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
> {
>     addr.addr.addrLocal.pLocal->Release();
> }
> ```

## <a name="requirements"></a>요구 사항

헤더: sh.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조

- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
