---
title: TYPE_INFO | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713324"
---
# <a name="type_info"></a>TYPE_INFO
이 구조는 필드 형식에 대 한 다양 한 종류의 정보를 지정 합니다.

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
 합집합을 해석 하는 방법을 결정 하는 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) 열거형의 값입니다.

 `type.typeMeta`\
 [C + + 전용] 가 인 경우 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) 구조를 포함 `dwKind` `TYPE_KIND_METADATA` 합니다.

 `type.typePdb`\
 [C + + 전용] 가 인 경우 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) 구조를 포함 `dwKind` `TYPE_KIND_PDB` 합니다.

 `type.typeBuilt`\
 [C + + 전용] 가 인 경우 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) 구조를 포함 `dwKind` `TYPE_KIND_BUILT` 합니다.

 `type.unused`\
 사용 되지 않는 패딩입니다.

 `type`\
 공용 구조체의 이름입니다.

 `unionmember`\
 [C #만 해당] 을 기반으로 하는 적절 한 구조체 형식으로이를 마샬링합니다 `dwKind` .

## <a name="remarks"></a>설명
 이 구조체는 채워진 [Gettypeinfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) 메서드에 전달 됩니다. 구조체의 내용을 해석 하는 방법은 필드를 기준으로 `dwKind` 합니다.

> [!NOTE]
> [C + + 전용] 가 `dwKind` 와 같으면 `TYPE_KIND_BUILT` 구조를 소멸 시킬 때 기본 [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 개체를 해제 해야 합니다 `TYPE_INFO` . 이를 위해 `typeInfo.type.typeBuilt.pUnderlyingField->Release()`를 호출합니다.

 [C #만 해당] 다음 표에서는 `unionmember` 각 종류의 형식에 대해 멤버를 해석 하는 방법을 보여 줍니다. 이 예제에서는 한 종류의 형식에 대해이 작업을 수행 하는 방법을 보여 줍니다.

|`dwKind`|`unionmember` 로 해석 됨|
|--------------|----------------------------------|
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|

## <a name="example"></a>예
 이 예제에서는 `unionmember` `TYPE_INFO` c #에서 구조체의 멤버를 해석 하는 방법을 보여 줍니다. 이 예제에서는 하나의 형식 ()만 해석 하지만 다른 형식 ()은 해석 하는 방법을 보여 줍니다 `TYPE_KIND_METADATA` .

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
 헤더: sh

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
