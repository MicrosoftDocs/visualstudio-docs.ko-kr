---
title: FIELD_MODIFIERS | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f7a24345174854462a2118df626223a8a299cd7f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736847"
---
# <a name="field_modifiers"></a>FIELD_MODIFIERS
필드 유형에 대한 수정자를 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_FIELD_MODIFIERS {
    FIELD_MOD_NONE             = 0x00000000,

    // Modifier of the field
    FIELD_MOD_ACCESS_NONE      = 0x00000001,
    FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,
    FIELD_MOD_ACCESS_PROTECTED = 0x00000004,
    FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,

    // Storage modifier of the field
    FIELD_MOD_NOMODIFIERS      = 0x00000010,
    FIELD_MOD_STATIC           = 0x00000020,
    FIELD_MOD_CONSTANT         = 0x00000040,
    FIELD_MOD_TRANSIENT        = 0x00000080,
    FIELD_MOD_VOLATILE         = 0x00000100,
    FIELD_MOD_ABSTRACT         = 0x00000200,
    FIELD_MOD_NATIVE           = 0x00000400,
    FIELD_MOD_SYNCHRONIZED     = 0x00000800,
    FIELD_MOD_VIRTUAL          = 0x00001000,
    FIELD_MOD_INTERFACE        = 0x00002000,
    FIELD_MOD_FINAL            = 0x00004000,
    FIELD_MOD_SENTINEL         = 0x00008000,
    FIELD_MOD_INNERCLASS       = 0x00010000,
    FIELD_TYPE_OPTIONAL        = 0x00020000,
    FIELD_MOD_BYREF            = 0x00040000,
    FIELD_MOD_HIDDEN           = 0x00080000,
    FIELD_MOD_MARSHALASOBJECT  = 0x00100000,
    FIELD_MOD_SPECIAL_NAME     = 0x00200000,
    FIELD_MOD_HIDEBYSIG        = 0x00400000,

    FIELD_MOD_WRITEONLY        = 0x80000000,
    FIELD_MOD_ACCESS_MASK      = 0x000000ff,
    FIELD_MOD_MASK             = 0xffffff00,
    FIELD_MOD_ALL              = 0x7fffffff
};
typedef DWORD FIELD_MODIFIERS;
```

```csharp
public enum enum_FIELD_MODIFIERS {
    FIELD_MOD_NONE             = 0x00000000,

    // Modifier of the field
    FIELD_MOD_ACCESS_NONE      = 0x00000001,
    FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,
    FIELD_MOD_ACCESS_PROTECTED = 0x00000004,
    FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,

    // Storage modifier of the field
    FIELD_MOD_NOMODIFIERS      = 0x00000010,
    FIELD_MOD_STATIC           = 0x00000020,
    FIELD_MOD_CONSTANT         = 0x00000040,
    FIELD_MOD_TRANSIENT        = 0x00000080,
    FIELD_MOD_VOLATILE         = 0x00000100,
    FIELD_MOD_ABSTRACT         = 0x00000200,
    FIELD_MOD_NATIVE           = 0x00000400,
    FIELD_MOD_SYNCHRONIZED     = 0x00000800,
    FIELD_MOD_VIRTUAL          = 0x00001000,
    FIELD_MOD_INTERFACE        = 0x00002000,
    FIELD_MOD_FINAL            = 0x00004000,
    FIELD_MOD_SENTINEL         = 0x00008000,
    FIELD_MOD_INNERCLASS       = 0x00010000,
    FIELD_TYPE_OPTIONAL        = 0x00020000,
    FIELD_MOD_BYREF            = 0x00040000,
    FIELD_MOD_HIDDEN           = 0x00080000,
    FIELD_MOD_MARSHALASOBJECT  = 0x00100000,
    FIELD_MOD_SPECIAL_NAME     = 0x00200000,
    FIELD_MOD_HIDEBYSIG        = 0x00400000,

    FIELD_MOD_WRITEONLY        = 0x80000000,
    FIELD_MOD_ACCESS_MASK      = 0x000000ff,
    FIELD_MOD_MASK             = 0xffffff00,
    FIELD_MOD_ALL              = 0x7fffffff
};
```

## <a name="fields"></a>필드
`FIELD_MOD_ACCESS_TYPE`\
필드에 액세스할 수 없음을 나타냅니다.

`FIELD_MOD_ACCESS_PUBLIC`\
필드에 공용 액세스 권한이 있음을 나타냅니다.

`FIELD_MOD_ACCESS_PROTECTED`\
필드에 보호된 액세스 권한이 있음을 나타냅니다.

`FIELD_MOD_ACCESS_PRIVATE`\
필드에 개인 액세스 권한이 있음을 나타냅니다.

`FIELD_MOD_NOMODIFIERS`\
필드에 수정자가 없음을 나타냅니다.

`FIELD_MOD_STATIC`\
필드가 정적임을 나타냅니다.

`FIELD_MOD_CONSTANT`\
필드가 상수임을 나타냅니다.

`FIELD_MOD_TRANSIENT`\
필드가 일시적임을 나타냅니다.

`FIELD_MOD_VOLATILE`\
필드가 휘발성임을 나타냅니다.

`FIELD_MOD_ABSTRACT`\
필드가 추상적임을 나타냅니다.

`FIELD_MOD_NATIVE`\
필드가 네이티브임을 나타냅니다.

`FIELD_MOD_SYNCHRONIZED`\
필드가 동기화되어 있음을 나타냅니다.

`FIELD_MOD_VIRTUAL`\
필드가 가상임을 나타냅니다.

`FIELD_MOD_INTERFACE`\
필드가 인터페이스임을 나타냅니다.

`FIELD_MOD_FINAL`\
필드가 최종임을 나타냅니다.

`FIELD_MOD_SENTINEL`\
필드가 파수꾼임을 나타냅니다.

`FIELD_MOD_INNERCLASS`\
필드가 내부 클래스임을 나타냅니다.

`FIELD_TYPE_OPTIONAL`\
필드는 선택 사항임을 나타냅니다.

`FIELD_MOD_BYREF`\
필드가 참조 인수임을 나타냅니다. 이것은 특히 메서드 인수를 위한 것입니다.

`FIELD_MOD_HIDDEN`\
필드를 숨겨야 하거나 다른 컨텍스트에서 표시해야 함을 나타냅니다. 예를 들어, [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] 정적 지역 주민.

`FIELD_MOD_MARSHALASOBJECT`\
필드는 인터페이스가 있는 개체를 `IUnknown` 나타냅니다.

`FIELD_MOD_SPECIAL_NAME`\
필드에 생성자(만 `.ctor` [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] 해당)에 대한 특수 이름이 있음을 나타냅니다.

`FIELD_MOD_HIDEBYSIG`\
필드에 키워드가 `Overloads` 적용되었음을 나타냅니다(전용).[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]

`FIELD_MOD_WRITEONLY`\
필드가 쓰기 전용임을 나타냅니다. 이 값은 `FIELD_MOD_ALL`에 포함되지 않습니다. 사용자는 `FIELD_MOD_WRITEONLY` 필드를 명시적으로 요청해야 합니다.

`FIELD_MOD_ACCESS_MASK`\
필드 액세스를 위한 마스크를 나타냅니다.

`FIELD_MOD_MASK`\
필드 수정자에 대한 마스크를 나타냅니다.

## <a name="remarks"></a>설명
`dwModifiers` [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) 구조의 부재에 사용됩니다.

이러한 값은 특정 필드를 필터링하기 위해 [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) 메서드에도 전달됩니다.

## <a name="requirements"></a>요구 사항
헤더: sh.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)
