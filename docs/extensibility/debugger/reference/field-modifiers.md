---
title: FIELD_MODIFIERS | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736847"
---
# <a name="field_modifiers"></a>FIELD_MODIFIERS
필드 형식의 한정자를 지정 합니다.

## <a name="syntax"></a>Syntax

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
필드에 보호 된 액세스 권한이 있음을 나타냅니다.

`FIELD_MOD_ACCESS_PRIVATE`\
필드에 개인 액세스 권한이 있음을 나타냅니다.

`FIELD_MOD_NOMODIFIERS`\
필드에 한정자가 없음을 나타냅니다.

`FIELD_MOD_STATIC`\
필드가 정적 임을 나타냅니다.

`FIELD_MOD_CONSTANT`\
필드가 상수 임을 나타냅니다.

`FIELD_MOD_TRANSIENT`\
임시 필드 임을 나타냅니다.

`FIELD_MOD_VOLATILE`\
는 필드가 휘발성 임을 나타냅니다.

`FIELD_MOD_ABSTRACT`\
는 필드가 추상 필드 임을 나타냅니다.

`FIELD_MOD_NATIVE`\
필드가 네이티브 임을 나타냅니다.

`FIELD_MOD_SYNCHRONIZED`\
필드가 동기화 됨을 나타냅니다.

`FIELD_MOD_VIRTUAL`\
는 필드가 가상 필드 임을 나타냅니다.

`FIELD_MOD_INTERFACE`\
는 필드가 인터페이스 임을 나타냅니다.

`FIELD_MOD_FINAL`\
필드가 final 임을 나타냅니다.

`FIELD_MOD_SENTINEL`\
필드가 센티널 임을 나타냅니다.

`FIELD_MOD_INNERCLASS`\
필드가 내부 클래스 임을 나타냅니다.

`FIELD_TYPE_OPTIONAL`\
필드가 선택적 임을 나타냅니다.

`FIELD_MOD_BYREF`\
필드가 참조 인수 임을 나타냅니다. 이는 메서드 인수 전용입니다.

`FIELD_MOD_HIDDEN`\
다른 컨텍스트에서 필드를 숨기 거 나 표시 해야 함을 나타냅니다. 예를 들어 [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] 정적 지역입니다.

`FIELD_MOD_MARSHALASOBJECT`\
필드가 인터페이스를 사용 하 여 개체를 나타내는지 여부를 나타냅니다 `IUnknown` .

`FIELD_MOD_SPECIAL_NAME`\
필드에 `.ctor` 생성자 (전용)와 같은 특수 한 이름이 있음을 나타냅니다 [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] .

`FIELD_MOD_HIDEBYSIG`\
필드에 키워드가 적용 됨을 나타냅니다 `Overloads` ( [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] 전용).

`FIELD_MOD_WRITEONLY`\
필드가 쓰기 전용 임을 나타냅니다. 이러한 `FIELD_MOD_ALL` 쓰기 전용 필드는 함수 evaluation 으로만 사용 되므로이 값은에 포함 되지 않습니다. 사용자가 필드를 명시적으로 요청 해야 합니다 `FIELD_MOD_WRITEONLY` .

`FIELD_MOD_ACCESS_MASK`\
필드 액세스에 대 한 마스크를 나타냅니다.

`FIELD_MOD_MASK`\
필드 한정자에 대 한 마스크를 나타냅니다.

## <a name="remarks"></a>설명
`dwModifiers` [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) 구조체의 멤버에 사용 됩니다.

이러한 값은 또한 특정 필드에 대해 필터링 하기 위해 [enumfields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) 메서드에 전달 됩니다.

## <a name="requirements"></a>요구 사항
헤더: sh

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)
