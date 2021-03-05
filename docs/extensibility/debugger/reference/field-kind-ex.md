---
description: IDebugField 개체에 포함 될 수 있는 추가 종류의 필드를 열거 합니다.
title: FIELD_KIND_EX | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- FIELD_KIND_EX enumeration
ms.assetid: 922c3208-1e94-485f-b70a-3bc96affeff8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 211cc83587a48b4e77afd9094f0227cacb4394c2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170278"
---
# <a name="field_kind_ex"></a>FIELD_KIND_EX
[Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 개체에 포함 될 수 있는 추가 종류의 필드를 열거 합니다. 이 열거형은 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) 열거형을 확장 합니다.

## <a name="syntax"></a>Syntax

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
필드에 확장 형식이 포함 되어 있지 않습니다.

`FIELD_TYPE_EX_METHODVAR`\
필드에 메서드 변수가 포함 되어 있습니다.

`FIELD_TYPE_EX_CLASSVAR`\
필드에 클래스 변수가 포함 되어 있습니다.

## <a name="requirements"></a>요구 사항
헤더: Sh

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)
