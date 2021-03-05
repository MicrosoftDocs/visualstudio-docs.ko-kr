---
description: IDebugField 개체의 형식을 해석 하는 방법을 지정 합니다.
title: dwTYPE_KIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f51a84951cdfe09e13454035c3219324e9a68368
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170330"
---
# <a name="dwtype_kind"></a>dwTYPE_KIND
[Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 개체의 형식을 해석 하는 방법을 지정 합니다.

## <a name="syntax"></a>Syntax

```cpp
enum enum_dwTYPE_KIND {
    TYPE_KIND_METADATA = 0x0001,
    TYPE_KIND_PDB      = 0x0002,
    TYPE_KIND_BUILT    = 0x0003,
};

typedef DWORD dwTYPE_KIND;
```

```csharp
public enum enum_dwTYPE_KIND {
    TYPE_KIND_METADATA = 0x0001,
    TYPE_KIND_PDB      = 0x0002,
    TYPE_KIND_BUILT    = 0x0003,
};
```

## <a name="fields"></a>필드
`TYPE_KIND_METADATA`\
[TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) union은 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) 구조체로 해석 되어야 합니다.

`TYPE_KIND_PDB`\
`TYPE_INFO`Union은 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) 구조체로 해석 되어야 합니다.

`TYPE_KIND_BUILT`\
`TYPE_INFO`Union은 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) 구조체로 해석 되어야 합니다.

## <a name="remarks"></a>설명
이 열거형의 값은 `dwKind` [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) 구조체의 필드에 표시 되며 union 멤버를 해석 하는 방법을 결정 하는 데 사용 됩니다 `type` . `TYPE_INFO`구조체는 [gettypeinfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) 메서드를 호출 하 여 반환 됩니다.

## <a name="requirements"></a>요구 사항
헤더: sh

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
