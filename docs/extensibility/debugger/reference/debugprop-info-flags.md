---
title: DEBUGPROP_INFO_FLAGS | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737399"
---
# <a name="debugprop_info_flags"></a>DEBUGPROP_INFO_FLAGS
디버그 속성 개체에 대해 검색할 정보를 지정합니다.

## <a name="syntax"></a>구문

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
`bstrFullName` 필드를 초기화/사용합니다.

`DEBUGPROP_INFO_NAME`\
`bstrName` 필드를 초기화/사용합니다.

`DEBUGPROP_INFO_TYPE`\
`bstrType` 필드를 초기화/사용합니다.

`DEBUGPROP_INFO_VALUE`\
`bstrValue` 필드를 초기화/사용합니다.

`DEBUGPROP_INFO_ATTRIB`\
`dwAttrib` 필드를 초기화/사용합니다.

`DEBUGPROP_INFO_PROP`\
`pProperty` [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스가 포함된 필드를 초기화/사용합니다.

`DEBUGPROP_INFO_VALUE_AUTOEXPAND`\
이 유형의 개체에 대해 값 필드에 자동 확장 값(사용 가능한 경우)이 포함되어야 한다고 지정합니다.

`DEBUGPROP_INFO_VALUE_NOFUNCEVAL`\
사용되지 않습니다.

`DEBUGPROP_INFO_VALUE_RAW`\
미화된 값이나 멤버를 반환하지 마십시오(즉, 값을 포맷하지 않음).

`DEBUGPROP_INFO_VALUE_NO_TOSTRING`\
특수 합성된 값을 반환하지 마십시오(예: 값을 `ToString()` 생성하기 위해 개체를 호출하지 않음).

`DEBUGPROP_INFO_NONE`\
플래그가 설정되지 않은 지 지정합니다.

`DEBUGPROP_INFO_STANDARD`\
의 초기화/사용 `bstrName` `bstrType`은 `dwAttrib` `bstrValue` , 및 필드.

`DEBUGPROP_INFO_All`\
모든 플래그의 마스크를 나타냅니다.

## <a name="remarks"></a>설명
이러한 값은 [GetPropertyInfo,](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) [에이numChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)및 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) 메서드에 전달되어 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 구조를 초기화할 필드를 나타냅니다.

이러한 값은 `dwFields` `DEBUG_PROPERTY_INFO` 구조의 멤버에 사용되며 구조가 반환될 때 사용되는 구조필드와 유효한 필드를 나타냅니다.

이러한 값은 약간 과 `OR`결합될 수 있습니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [겟프로퍼정보](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
