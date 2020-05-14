---
title: FIELD_KIND_EX | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- FIELD_KIND_EX enumeration
ms.assetid: 922c3208-1e94-485f-b70a-3bc96affeff8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0c13d83f80b311838eca32945462c1f17ca23f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736883"
---
# <a name="field_kind_ex"></a>FIELD_KIND_EX
[IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 개체에 포함할 수 있는 추가 필드 종류를 열거합니다. 이 열거형은 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) 열거를 확장합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_FIELD_KIND_EX
{
    FIELD_KIND_EX_NONE = 0,
    FIELD_TYPE_EX_METHODVAR = 0x1,
    FIELD_TYPE_EX_CLASSVAR = 0x2
};
typedef DWORD FIELD_KIND_EX;
```

```csharp
public enum enum_FIELD_KIND_EX
{
    FIELD_KIND_EX_NONE = 0,
    FIELD_TYPE_EX_METHODVAR = 0x1,
    FIELD_TYPE_EX_CLASSVAR = 0x2
};
```

## <a name="fields"></a>필드
`FIELD_KIND_EX_NONE`\
필드에 확장 된 형식을 포함 하지 않습니다.

`FIELD_TYPE_EX_METHODVAR`\
필드에는 메서드 변수가 포함되어 있습니다.

`FIELD_TYPE_EX_CLASSVAR`\
필드에는 클래스 변수가 포함되어 있습니다.

## <a name="requirements"></a>요구 사항
헤더: Sh.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)
