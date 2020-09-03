---
title: DEBUGREF_INFO_FLAGS | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737380"
---
# <a name="debugref_info_flags"></a>DEBUGREF_INFO_FLAGS
디버그 참조 개체에 대해 검색할 정보를 지정 합니다.

## <a name="syntax"></a>Syntax

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
구조에서 필드를 초기화/사용 `bstrName` 합니다.

`DEBUGREF_INFO_TYPE`\
구조에서 필드를 초기화/사용 `bstrType` 합니다.

`DEBUGREF_INFO_VALUE`\
구조에서 필드를 초기화/사용 `bstrValue` 합니다.

`DEBUGREF_INFO_ATTRIB`\
구조에서 필드를 초기화/사용 `dwAttrib` 합니다.

`DEBUGREF_INFO_REFTYPE`\
구조에서 필드를 초기화/사용 `dwRefType` 합니다.

`DEBUGREF_INFO_REF`\
구조에서 필드를 초기화/사용 `pReference` 합니다.

`DEBUGREF_INFO_VALUE_AUTOEXPAND`\
값 필드에는이 형식의 개체에 대 한 자동 확장 값 (사용 가능한 경우)이 포함 되어야 합니다.

`DEBUGREF_INFO_NONE`\
플래그가 설정 되지 않았음을 나타냅니다.

`DEBUGREF_INFO_ALL`\
플래그의 마스크를 나타냅니다.

## <a name="remarks"></a>설명
이러한 플래그는 [Enumchildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) 및 [getreferenceinfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) 메서드에 전달 되어 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 구조체에서 초기화할 필드를 표시 합니다.

구조체 `dwFields` 의 멤버에서 사용 되는 `DEBUG_REFERENCE_INFO` 필드 및 구조가 반환 될 때 유효한 필드를 표시 하는 데 사용 됩니다.

이러한 값은 비트와 함께 사용할 수 있습니다 `OR` .

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
