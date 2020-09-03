---
title: DEBUGPROP_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa7e4a498188dc91f2a47b3ccf27f367f15ec77b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737399"
---
# <a name="debugprop_info_flags"></a>DEBUGPROP_INFO_FLAGS
디버그 속성 개체에 대해 검색할 정보를 지정 합니다.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
typedef DWORD DEBUGPROP_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
```

## <a name="fields"></a>필드
`DEBUGPROP_INFO_FULLNAME`\
필드를 초기화/사용 `bstrFullName` 합니다.

`DEBUGPROP_INFO_NAME`\
필드를 초기화/사용 `bstrName` 합니다.

`DEBUGPROP_INFO_TYPE`\
필드를 초기화/사용 `bstrType` 합니다.

`DEBUGPROP_INFO_VALUE`\
필드를 초기화/사용 `bstrValue` 합니다.

`DEBUGPROP_INFO_ATTRIB`\
필드를 초기화/사용 `dwAttrib` 합니다.

`DEBUGPROP_INFO_PROP`\
`pProperty` [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스를 포함 하는 필드를 초기화/사용 합니다.

`DEBUGPROP_INFO_VALUE_AUTOEXPAND`\
값 필드에이 형식의 개체에 대 한 자동 확장 값 (사용 가능한 경우)을 포함 하도록 지정 합니다.

`DEBUGPROP_INFO_VALUE_NOFUNCEVAL`\
더 이상 사용되지 않습니다.

`DEBUGPROP_INFO_VALUE_RAW`\
Beautified 값 또는 멤버를 반환 하지 않습니다. 즉, 값의 형식을 지정 하지 마십시오.

`DEBUGPROP_INFO_VALUE_NO_TOSTRING`\
특수 한 합성 값을 반환 하지 않습니다. 예를 들어 `ToString()` 개체에 대해를 호출 하 여 값을 생성 하지 마십시오.

`DEBUGPROP_INFO_NONE`\
플래그가 설정 되지 않도록 지정 합니다.

`DEBUGPROP_INFO_STANDARD`\
,, 및 필드를 초기화/사용 `dwAttrib` `bstrName` `bstrType` `bstrValue` 합니다.

`DEBUGPROP_INFO_All`\
모든 플래그의 마스크를 나타냅니다.

## <a name="remarks"></a>설명
이러한 값은 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [Enumchildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)및 [enumchildren](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) 메서드에 전달 되어 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 구조를 초기화할 필드를 표시 합니다.

이러한 값은 구조체의 멤버를 사용 하 여 구조체의 `dwFields` `DEBUG_PROPERTY_INFO` 필드를 사용 하 고 구조가 반환 될 때 유효한 지를 나타내는 데도 사용 됩니다.

이러한 값은 비트와 함께 사용할 수 있습니다 `OR` .

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
