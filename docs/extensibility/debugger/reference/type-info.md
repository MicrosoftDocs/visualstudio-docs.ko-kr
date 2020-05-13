---
title: TYPE_INFO | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 82796c1d82dc3ca77151abcec3e1dd6ce13ac59d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713324"
---
# <a name="type_info"></a>TYPE_INFO
이 구조는 필드 유형에 대한 다양한 종류의 정보를 지정합니다.

## <a name="syntax"></a>구문

```cpp
struct _tagTYPE_INFO_UNION {
   dwTYPE_KIND dwKind;
   union {
      METADATA_TYPE typeMeta;
      PDB_TYPE      typePdb;
      BUILT_TYPE    typeBuilt;
      DWORD         unused;
   } type;
} TYPE_INFO;
```

```csharp
public struct TYPE_INFO {
   public uint   dwKind;
   public IntPtr unionmember;
};
```

## <a name="members"></a>멤버
 `dwKind`\
 공용 구조체를 해석하는 방법을 결정하는 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) 열거형의 값입니다.

 `type.typeMeta`\
 [C++ 전용] [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) 구조가 `dwKind` 포함되어 `TYPE_KIND_METADATA`있는 경우.

 `type.typePdb`\
 [C++ 전용] [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) 구조가 `dwKind` 포함되어 `TYPE_KIND_PDB`있는 경우.

 `type.typeBuilt`\
 [C++ 전용] [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) 구조를 `dwKind` `TYPE_KIND_BUILT`포함합니다.

 `type.unused`\
 사용하지 않은 패딩.

 `type`\
 공용 구조의 이름입니다.

 `unionmember`\
 [C# 만] `dwKind`을 기반으로 적절한 구조 유형으로 마샬링합니다.

## <a name="remarks"></a>설명
 이 구조는 채워진 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) 메서드에 전달됩니다. 구조의 내용을 해석하는 방법은 `dwKind` 필드에 따라 다다.

> [!NOTE]
> [C++ 전용] `dwKind` 같으면 `TYPE_KIND_BUILT`구조를 파괴할 때 기본 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 개체를 `TYPE_INFO` 해제해야 합니다. 이를 위해 `typeInfo.type.typeBuilt.pUnderlyingField->Release()`를 호출합니다.

 [C# 만] 다음 표에서는 각 유형의 멤버를 `unionmember` 해석하는 방법을 보여 주며, 예제에서는 한 종류의 형식에 대해 이 작업을 수행하는 방법을 보여 주며 있습니다.

|`dwKind`|`unionmember`로 해석|
|--------------|----------------------------------|
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|

## <a name="example"></a>예제
 이 예제에서는 C#에서 구조체의 `unionmember` 멤버를 `TYPE_INFO` 해석하는 방법을 보여 주습니다. 이 예제에서는 한 형식()만`TYPE_KIND_METADATA`해석하지만 다른 형식은 정확히 동일한 방식으로 해석됩니다.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(TYPE_INFO ti)
        {
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)
            {
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,
                                               typeof(METADATA_TYPE));
            }
        }
    }
}
```

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [겟타입정보](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
