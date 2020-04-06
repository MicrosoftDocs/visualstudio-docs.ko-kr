---
title: FIELD_INFO_FIELDS | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9a3d2e796d37606c51918d8e49db920161d63f55
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736900"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
[IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 개체에 대해 검색할 정보를 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_FIELD_INFO_FIELDS { 
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
typedef DWORD FIELD_INFO_FIELDS;
```

```csharp
public enum enum_FIELD_INFO_FIELDS {
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
```

## <a name="fields"></a>필드
`FIF_FULLNAME`\
`bstrFullName` [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) 구조에서 필드를 초기화/사용합니다.

`FIF_NAME`\
`FIELD_INFO` 구조에서 `bstrName` 필드를 초기화/사용합니다.

`FIF_TYPE`\
`FIELD_INFO` 구조에서 `bstrType` 필드를 초기화/사용합니다.

`FIF_MODIFIERS`\
`FIELD_INFO` 구조에서 `bstrModifiers` 필드를 초기화/사용합니다.

## <a name="remarks"></a>설명
또한 이러한 값은 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) 메서드에 인수로 전달되어 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) 구조의 필드를 초기화할 필드를 지정합니다.

이러한 값은 `dwFields` `FIELD_INFO` 구조의 멤버에서 사용되는 필드와 유효한 필드를 나타내는 데도 사용됩니다.

이러한 플래그는 약간 으로 `OR`결합될 수 있습니다.

## <a name="requirements"></a>요구 사항
헤더: sh.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
