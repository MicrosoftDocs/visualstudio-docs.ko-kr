---
title: NATIVE_ADDRESS | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- NATIVE_ADDRESS
helpviewer_keywords:
- NATIVE_ADDRESS structure
ms.assetid: 7a0cd085-bfc8-45cc-a3d4-4459070e207a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7c62bbea846f3d486ead8add4dfab2182df1e1bb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714337"
---
# <a name="native_address"></a>NATIVE_ADDRESS

이 구조는 네이티브 주소를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _tagNATIVE_ADDRESS {
    DWORD unknown;
} NATIVE_ADDRESS;
```

```csharp
public struct NATIVE_ADDRESS {
    public uint unknown;
}
```

## <a name="members"></a>멤버

`unknown`\
네이티브 주소(이 의 의미는 런타임 및 운영 체제에 따라 다름).

## <a name="remarks"></a>설명

이 구조는 `dwKind` `DEBUG_ADDRESS_UNION` 구조의 필드가 설정될 때 `ADDRESS_KIND_NATIVE` [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) 구조체의 결합의 일부입니다(ADDRESS_KIND 열거된 값). [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)

## <a name="requirements"></a>요구 사항

헤더: sh.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조

- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
