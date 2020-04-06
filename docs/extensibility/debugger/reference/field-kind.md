---
title: FIELD_KIND | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_KIND
helpviewer_keywords:
- FIELD_KIND enumeration
ms.assetid: fd522b9c-52e2-42fa-939d-343347d5c3b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cafe4a34745f3b34070f7d8fed1a246c806375a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736867"
---
# <a name="field_kind"></a>FIELD_KIND
[IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 개체에 포함 된 필드의 종류를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_FIELD_KIND {
    FIELD_KIND_NONE       = 0x00000000,

    // Type of field
    FIELD_KIND_TYPE       = 0x00000001,
    FIELD_KIND_SYMBOL     = 0x00000002,

    // Storage type of the field
    FIELD_TYPE_PRIMITIVE  = 0x00000010,
    FIELD_TYPE_STRUCT     = 0x00000020,
    FIELD_TYPE_CLASS      = 0x00000040,
    FIELD_TYPE_INTERFACE  = 0x00000080,
    FIELD_TYPE_UNION      = 0x00000100,
    FIELD_TYPE_ARRAY      = 0x00000200,
    FIELD_TYPE_METHOD     = 0x00000400,
    FIELD_TYPE_BLOCK      = 0x00000800,
    FIELD_TYPE_POINTER    = 0x00001000,
    FIELD_TYPE_ENUM       = 0x00002000,
    FIELD_TYPE_LABEL      = 0x00004000,
    FIELD_TYPE_TYPEDEF    = 0x00008000,
    FIELD_TYPE_BITFIELD   = 0x00010000,
    FIELD_TYPE_NAMESPACE  = 0x00020000,
    FIELD_TYPE_MODULE     = 0x00040000,
    FIELD_TYPE_DYNAMIC    = 0x00080000,
    FIELD_TYPE_PROP       = 0x00100000,
    FIELD_TYPE_INNERCLASS = 0x00200000,
    FIELD_TYPE_REFERENCE  = 0x00400000,
    FIELD_TYPE_EXTENDED   = 0x00800000,

    // Specific information about symbols
    FIELD_SYM_MEMBER      = 0x01000000,
    FIELD_SYM_LOCAL       = 0x02000000,
    FIELD_SYM_PARAM       = 0x04000000,
    FIELD_SYM_THIS        = 0x08000000,
    FIELD_SYM_GLOBAL      = 0x10000000,
    FIELD_SYM_PROP_GETTER = 0x20000000,
    FIELD_SYM_PROP_SETTER = 0x40000000,
    FIELD_SYM_EXTENDED    = 0x80000000,

    FIELD_KIND_MASK       = 0x0000000f,
    FIELD_TYPE_MASK       = 0x00fffff0,
    FIELD_SYM_MASK        = 0xff000000,

    FIELD_KIND_ALL        = 0xffffffff
};
typedef DWORD FIELD_KIND;
```

```csharp
public enum enum_FIELD_KIND {
    FIELD_KIND_NONE       = 0x00000000,

    // Type of field
    FIELD_KIND_TYPE       = 0x00000001,
    FIELD_KIND_SYMBOL     = 0x00000002,

    // Storage type of the field
    FIELD_TYPE_PRIMITIVE  = 0x00000010,
    FIELD_TYPE_STRUCT     = 0x00000020,
    FIELD_TYPE_CLASS      = 0x00000040,
    FIELD_TYPE_INTERFACE  = 0x00000080,
    FIELD_TYPE_UNION      = 0x00000100,
    FIELD_TYPE_ARRAY      = 0x00000200,
    FIELD_TYPE_METHOD     = 0x00000400,
    FIELD_TYPE_BLOCK      = 0x00000800,
    FIELD_TYPE_POINTER    = 0x00001000,
    FIELD_TYPE_ENUM       = 0x00002000,
    FIELD_TYPE_LABEL      = 0x00004000,
    FIELD_TYPE_TYPEDEF    = 0x00008000,
    FIELD_TYPE_BITFIELD   = 0x00010000,
    FIELD_TYPE_NAMESPACE  = 0x00020000,
    FIELD_TYPE_MODULE     = 0x00040000,
    FIELD_TYPE_DYNAMIC    = 0x00080000,
    FIELD_TYPE_PROP       = 0x00100000,
    FIELD_TYPE_INNERCLASS = 0x00200000,
    FIELD_TYPE_REFERENCE  = 0x00400000,
    FIELD_TYPE_EXTENDED   = 0x00800000,

    // Specific information about symbols
    FIELD_SYM_MEMBER      = 0x01000000,
    FIELD_SYM_LOCAL       = 0x02000000,
    FIELD_SYM_PARAM       = 0x04000000,
    FIELD_SYM_THIS        = 0x08000000,
    FIELD_SYM_GLOBAL      = 0x10000000,
    FIELD_SYM_PROP_GETTER = 0x20000000,
    FIELD_SYM_PROP_SETTER = 0x40000000,
    FIELD_SYM_EXTENDED    = 0x80000000,

    FIELD_KIND_MASK       = 0x0000000f,
    FIELD_TYPE_MASK       = 0x00fffff0,
    FIELD_SYM_MASK        = 0xff000000,

    FIELD_KIND_ALL        = 0xffffffff
};
```

## <a name="fields"></a>필드
`FIELD_KIND_TYPE`\
필드가 형식일 뿐임을 나타냅니다.

`FIELD_KIND_SYMBOL`\
필드가 유형, 이름 및 기타 정보가 있는 기호임을 나타냅니다.

`FIELD_TYPE_PRIMITIVE`\
필드가 기본 데이터 형식임을 나타냅니다.

`FIELD_TYPE_STRUCT`\
필드가 구조임을 나타냅니다.

`FIELD_TYPE_CLASS`\
필드가 클래스임을 나타냅니다.

`FIELD_TYPE_INTERFACE`\
필드가 인터페이스임을 나타냅니다.

`FIELD_TYPE_UNION`\
필드가 공용 구조관임을 나타냅니다.

`FIELD_TYPE_ARRAY`\
필드가 배열임을 나타냅니다.

`FIELD_TYPE_METHOD`\
필드가 메서드임을 나타냅니다.

`FIELD_TYPE_BLOCK`\
필드가 블록임을 나타냅니다.

`FIELD_TYPE_POINTER`\
필드가 포인터임을 나타냅니다.

`FIELD_TYPE_ENUM`\
필드가 들어간 데이터 형식임을 나타냅니다.

`FIELD_TYPE_LABEL`\
필드가 레이블임을 나타냅니다.

`FIELD_TYPE_TYPEDEF`\
필드가 typedef임을 나타냅니다.

`FIELD_TYPE_BITFIELD`\
필드가 비트필드임을 나타냅니다.

`FIELD_TYPE_NAMESPACE`\
필드가 네임스페이스임을 나타냅니다.

`FIELD_TYPE_MODULE`\
필드가 모듈임을 나타냅니다.

`FIELD_TYPE_DYNAMIC`\
필드가 동적임을 나타냅니다.

`FIELD_TYPE_PROP`\
필드가 속성임을 나타냅니다.

`FIELD_TYPE_INNERCLASS`\
필드가 내부 클래스임을 나타냅니다.

`FIELD_TYPE_REFERENCE`\
필드가 참조임을 나타냅니다.

`FIELD_TYPE_EXTENDED`\
다음에 사용하도록 예약됩니다.

`FIELD_SYM_MEMBER`\
필드가 멤버임을 나타냅니다.

`FIELD_SYM_LOCAL`\
필드가 로컬임을 나타냅니다.

`FIELD_SYM_PARAMETER`\
필드가 매개 변수임을 나타냅니다.

`FIELD_SYM_THIS`\
필드가 "this" 포인터임을 나타냅니다.

`FIELD_SYM_GLOBAL`\
필드가 전역임을 나타냅니다.

`FIELD_SYM_PROP_GETTER`\
필드는 속성을 검색합니다.

`FIELD_SYM_PROP_SETTER`\
필드가 속성을 설정했음을 나타냅니다.

`FIELD_SYM_EXTENDED`\
다음에 사용하도록 예약됩니다.

`FIELD_KIND_MASK`\
필드 종류에 대한 마스크를 나타냅니다.

`FIELD_TYPE_MASK`\
필드 유형에 대한 마스크를 나타냅니다.

`FIELD_SYM_MASK`\
기호 정보에 대한 마스크를 나타냅니다.

## <a name="remarks"></a>설명
[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 메서드에 대한 호출에서 반환되었습니다.

필드 종류에 따라 보다 구체적인 인터페이스 형식에 대 한 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스에서 [QueryInterface호출할](/cpp/atl/queryinterface) 수 있습니다. 예를 들어 [GetKind가](../../../extensibility/debugger/reference/idebugfield-getkind.md) `FIELD_TYPE_METHOD`반환되면 I를 `QueryInterface` `DebugField` 호출하여 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) 인터페이스를 가져올 수 있습니다.

## <a name="requirements"></a>요구 사항
헤더: sh.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
