---
title: UNMANAGED_ADDRESS_THIS_RELATIVE | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE
helpviewer_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE structure
ms.assetid: e6a91ace-2d47-4ff9-aefb-8d8b68eab0b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea493170c7b422129485fcea4248981a2b506001
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713264"
---
# <a name="unmanaged_address_this_relative"></a>UNMANAGED_ADDRESS_THIS_RELATIVE
이 구조는 포인터(Visual `this` `Me` Basic)를 기준으로 하는 주소를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _tagUNMANAGED_THIS_RELATIVE {
   DWORD dwOffset;
   DWORD dwBitOffset;
   DWORD dwBitLength;
} UNMANAGED_ADDRESS_THIS_RELATIVE;
```

```csharp
public struct UNMANAGED_THIS_RELATIVE {
   public uint dwOffset;
   public uint dwBitOffset;
   public uint dwBitLength;
}
```

## <a name="members"></a>멤버
 `dwOffset`\
 기본 위치에서 바이트 오프셋(예: 클래스 vtable 시작).

 `dwBitOffset`\
 기본 위치에서 비트로 오프셋(비트 필드를 참조하지 않는 한 항상 0).

 `dwBitLength`\
 주소를 나타내는 비트 수(비트 필드를 참조하지 않는 한 항상 0).

## <a name="remarks"></a>설명
 이 구조는 `dwKind` `DEBUG_ADDRESS_UNION` 구조의 필드가 설정될 때 `ADDRESS_KIND_UNMANAGED_THIS_RELATIVE` [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) 구조체의 결합의 일부입니다(ADDRESS_KIND 열거된 값). [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
