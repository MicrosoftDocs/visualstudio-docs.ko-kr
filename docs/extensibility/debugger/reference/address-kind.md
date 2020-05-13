---
title: ADDRESS_KIND | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1298df79bbe34b240d6e7b186f42e20b3d1a89de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738153"
---
# <a name="address_kind"></a>ADDRESS_KIND
주소의 종류를 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
typedef DWORD ADDRESS_KIND;
```

```csharp
public enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
```

## <a name="fields"></a>필드
`ADDRESS_KIND_NATIVE`\
[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) 구조로 표시되는 네이티브 주소입니다.

`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`\
`this` (Visual`Me` Basic) 포인터를 기준으로 관리되지 않는 주소이며 [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) 구조로 표시됩니다.

`ADDRESS_KIND_UNMANAGED_PHYSICAL`\
[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) 구조로 표시되는 관리되지 않는 실제 주소입니다.

`ADDRESS_KIND_METHOD`\
[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) 구조로 표시되는 클래스의 메서드입니다.

`ADDRESS_KIND_FIELD`\
[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) 구조로 표시되는 클래스의 필드입니다.

`ADDRESS_KIND_LOCAL`\
주소는 로컬 변수에 대한 것이며 [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) 구조로 표시됩니다.

`ADDRESS_KIND_PARAM`\
[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) 구조로 표시되는 메서드 또는 함수 매개 변수입니다.

`ADDRESS_KIND_ARRAYELEM`\
[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) 구조로 표시되는 배열 요소입니다.

`ADDRESS_KIND_RETVAL`\
[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) 구조로 표시되는 반환 값입니다.

## <a name="remarks"></a>설명
[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) 메서드는 가능한 구조의 결합, [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) 구조의 결합을 포함 하는 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 구조를 반환 합니다. 구조의 `dwKind` 필드는 `ADDRESS_KIND` 값을 보유하며 공용 구조자 필드를 해석하는 방법을 설명합니다. `DEBUG_ADDRESS_UNION`

## <a name="requirements"></a>요구 사항
헤더: sh.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
