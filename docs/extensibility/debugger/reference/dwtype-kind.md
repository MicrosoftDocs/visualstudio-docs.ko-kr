---
title: dwTYPE_KIND | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9d790f12d3fc21bbae7373470746af2ebfe6dc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737187"
---
# <a name="dwtype_kind"></a>dwTYPE_KIND
[IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 개체의 형식을 해석 하는 방법을 지정 합니다.

## <a name="syntax"></a>구문

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
[TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) 노조는 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) 구조로 해석되어야 한다.

`TYPE_KIND_PDB`\
`TYPE_INFO` 노조는 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) 구조로 해석되어야 한다.

`TYPE_KIND_BUILT`\
`TYPE_INFO` 노조는 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) 구조로 해석되어야 한다.

## <a name="remarks"></a>설명
이 열거형의 값은 `dwKind` [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) 구조의 필드에 나타나며 `type` 조합원을 해석하는 방법을 결정하는 데 사용됩니다. `TYPE_INFO` [구조는 GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) 메서드에 대 한 호출에 의해 반환 됩니다.

## <a name="requirements"></a>요구 사항
헤더: sh.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [겟타입정보](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
