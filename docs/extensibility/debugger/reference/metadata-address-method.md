---
title: METADATA_ADDRESS_METHOD | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_METHOD
helpviewer_keywords:
- METADATA_ADDRESS_METHOD structure
ms.assetid: fc0e5370-1b4f-4867-837f-0d63c4b9dd09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bc3dd7a34e4f9a3e1b933781aeaf4e18cad7ec17
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714450"
---
# <a name="metadata_address_method"></a>METADATA_ADDRESS_METHOD
이 구조는 클래스 메서드의 주소를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _tagMETADATA_ADDRESS_METHOD {
   _mdToken tokMethod;
   DWORD    dwOffset;
   DWORD    dwVersion;
} METADATA_ADDRESS_METHOD;
```

```csharp
public struct METADATA_ADDRESS_METHOD {
   public int  tokMethod;
   public uint dwOffset;
   public uint dwVersion;
}
```

## <a name="members"></a>멤버
 `tokMethod`\
 메서드의 ID입니다.

 [C++] `_mdToken` 32 `typedef` 비트에 `int`대 한입니다.

 `dwOffset`\
 클래스 시작에서 이 메서드까지의 오프셋입니다(vtable에 오프셋을 나타낼 수 있음).

 `dwVersion`\
 메서드의 버전입니다(이 값은 기호 공급자에 고유합니다).

## <a name="remarks"></a>설명
 이 구조는 `dwKind` `DEBUG_ADDRESS_UNION` 구조의 필드가 설정될 때 `ADDRESS_KIND_METHOD` [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) 구조체의 결합의 일부입니다(ADDRESS_KIND 열거된 값). [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
