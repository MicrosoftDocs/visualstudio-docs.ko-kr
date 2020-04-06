---
title: DEBUGREF_INFO_FLAGS | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cb10ae5d3b4ce9f8aa777f643d412e075bd5293f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737380"
---
# <a name="debugref_info_flags"></a>DEBUGREF_INFO_FLAGS
디버그 참조 개체에 대해 검색할 정보를 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
typedef DWORD DEBUGREF_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
```

## <a name="fields"></a>필드
`DEBUGREF_INFO_NAME`\
구조에서 `bstrName` 필드를 초기화/사용합니다.

`DEBUGREF_INFO_TYPE`\
구조에서 `bstrType` 필드를 초기화/사용합니다.

`DEBUGREF_INFO_VALUE`\
구조에서 `bstrValue` 필드를 초기화/사용합니다.

`DEBUGREF_INFO_ATTRIB`\
구조에서 `dwAttrib` 필드를 초기화/사용합니다.

`DEBUGREF_INFO_REFTYPE`\
구조에서 `dwRefType` 필드를 초기화/사용합니다.

`DEBUGREF_INFO_REF`\
구조에서 `pReference` 필드를 초기화/사용합니다.

`DEBUGREF_INFO_VALUE_AUTOEXPAND`\
값 필드에는 이 유형의 개체에 대해 사용 가능한 경우 자동 확장 값이 포함되어야 합니다.

`DEBUGREF_INFO_NONE`\
플래그가 설정되지 않은 것을 나타냅니다.

`DEBUGREF_INFO_ALL`\
플래그의 마스크를 나타냅니다.

## <a name="remarks"></a>설명
이러한 플래그는 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) 및 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) 메서드에 전달되어 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 구조의 필드를 초기화할 필드를 나타냅니다.

`DEBUG_REFERENCE_INFO` 구조의 멤버에 `dwFields` 사용 되는 필드 와 구조가 반환 될 때 유효한 나타내는 데 사용 됩니다.

이러한 값은 약간 과 `OR`결합될 수 있습니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
