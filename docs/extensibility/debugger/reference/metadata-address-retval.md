---
title: METADATA_ADDRESS_RETVAL | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_RETVAL
helpviewer_keywords:
- METADATA_ADDRESS_RETVAL structure
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f2437d10078eb623e063b3292d96ef9bb4a9cf64
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714268"
---
# <a name="metadata_address_retval"></a>METADATA_ADDRESS_RETVAL
이 구조는 메서드 또는 함수의 반환 값을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _tagMETADATA_ADDRESS_RETVAL {
   _mdToken tokMethod;
   DWORD    dwCorType;
   DWORD    dwSigSize;
   BYTE     rgSig[10];
} METADATA_ADDRESS_RETVAL;
```

```csharp
public struct METADATA_ADDRESS_RETVAL {
   public int    tokMethod;
   public uint   dwCorType;
   public uint   dwSigSize;
   public byte[] rgSig;
}
```

## <a name="members"></a>멤버
 `tokMethod`\
 메서드의 ID이 반환 값입니다.

 `dwCorType`\
 반환 값의 기본 형식입니다. 이 값은 .NET 프레임워크 SDK corhdr.h 파일에 정의된 `CorElementType` 열거형의 값입니다.

 `dwSigSize`\
 반환 값 서명의 `rgSig`크기(저장됨)입니다.

 `rgSig`\
 반환 값의 서명을 형성하는 바이트 배열입니다.

## <a name="remarks"></a>설명
 이 구조는 `dwKind` `DEBUG_ADDRESS_UNION` 구조의 필드가 설정될 때 `ADDRESS_KIND_RETVAL` [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) 구조체의 결합의 일부입니다(ADDRESS_KIND 열거된 값). [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
