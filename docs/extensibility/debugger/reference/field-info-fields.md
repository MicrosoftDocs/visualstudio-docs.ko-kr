---
description: IDebugField 개체에 대해 검색할 정보를 지정 합니다.
title: FIELD_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 024c12d5112398e055141a8db4995f2801ca5401
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170291"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
[Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 개체에 대해 검색할 정보를 지정 합니다.

## <a name="syntax"></a>Syntax

```cpp
enum enum_FIELD_INFO_FIELDS { 
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
`bstrFullName` [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) 구조체에서 필드를 초기화/사용 합니다.

`FIF_NAME`\
`bstrName`구조에서 필드를 초기화/사용 `FIELD_INFO` 합니다.

`FIF_TYPE`\
`bstrType`구조에서 필드를 초기화/사용 `FIELD_INFO` 합니다.

`FIF_MODIFIERS`\
`bstrModifiers`구조에서 필드를 초기화/사용 `FIELD_INFO` 합니다.

## <a name="remarks"></a>설명
이러한 값은 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) 메서드에 인수로 전달 되어 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) 구조체에서 초기화할 필드를 지정 합니다.

이러한 값은 구조체의 멤버에도 사용 되어 사용 되는 `dwFields` `FIELD_INFO` 필드와 유효한 필드를 표시 합니다.

이러한 플래그는 비트와 함께 사용할 수 있습니다 `OR` .

## <a name="requirements"></a>요구 사항
헤더: sh

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
