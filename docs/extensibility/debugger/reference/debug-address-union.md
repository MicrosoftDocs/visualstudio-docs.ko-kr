---
title: DEBUG_ADDRESS_UNION | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad531ee10914e404459632c98aae4a9bbda8e437
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737531"
---
# <a name="debug_address_union"></a>DEBUG_ADDRESS_UNION
다양한 종류의 주소를 설명합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _tagDEBUG_ADDRESS_UNION {
   ADDRESS_KIND dwKind;
   union {
      NATIVE_ADDRESS                  addrNative;
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;
      METADATA_ADDRESS_METHOD         addrMethod;
      METADATA_ADDRESS_FIELD          addrField;
      METADATA_ADDRESS_LOCAL          addrLocal;
      METADATA_ADDRESS_PARAM          addrParam;
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;
      METADATA_ADDRESS_RETVAL         addrRetVal;
      DWORD                           unused;
   } addr;
} DEBUG_ADDRESS_UNION;
```

```csharp
public struct DEBUG_ADDRESS_UNION {
   public ADDRESS_KIND dwKind;
   public IntPtr       unionmember;
}
```

## <a name="members"></a>멤버
`dwKind`\
공용 구조체를 해석하는 방법을 지정하는 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) 열거형의 값입니다.

`addr.addrNative`\
[C++ 전용] = [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) ADDRESS_KIND_NATIVE 경우 `dwKind` NATIVE_ADDRESS 구조를 포함합니다.

`addr.addrThisRel`\
[C++ 전용] =[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) ADDRESS_KIND_UNMANAGED_THIS_RELATIVE 경우 `dwKind` UNMANAGED_ADDRESS_THIS_RELATIVE 구조를 포함합니다.

`addr.addUPhysical`\
[C++ 전용] =[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) ADDRESS_KIND_UNMANAGED_PHYSICAL 경우 `dwKind` UNMANAGED_ADDRESS_PHYSICAL 구조를 포함합니다.

`addr.addrMethod`\
[C++ 전용] =[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) ADDRESS_KIND_METHOD 경우 `dwKind` METADATA_ADDRESS_METHOD 구조를 포함합니다.

`addr.addrField`\
[C++ 전용] =[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) ADDRESS_KIND_FIELD 경우 `dwKind` METADATA_ADDRESS_FIELD 구조를 포함합니다.

`addr.addrLocal`\
[C++ 전용] =[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) ADDRESS_KIND_LOCAL 경우 `dwKind` METADATA_ADDRESS_LOCAL 구조를 포함합니다.

`addr.addrParam`\
[C++ 전용] =[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) ADDRESS_KIND_PARAM 경우 `dwKind` METADATA_ADDRESS_PARAM 구조를 포함합니다.

`addr.addrArrayElem`\
[C++ 전용] =[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) ADDRESS_KIND_ARRAYELEM 경우 `dwKind` METADATA_ADDRESS_ARRAYELEM 구조를 포함합니다.

`addr.addrRetVal`\
[C++ 전용] =[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) ADDRESS_KIND_RETVAL 경우 `dwKind` METADATA_ADDRESS_RETVAL 구조를 포함합니다.

`addr.unused`\
[C++ 전용] 패딩.

`addr`\
[C++ 전용] 공용 구조의 이름입니다.

`unionmember`\
[C# 만] 이 값은 `dwKind`을 기반으로 적절한 구조 체로 마샬링해야 합니다. 노조의 `dwKind` 연관성 및 해석에 대한 발언을 참조하십시오.

## <a name="remarks"></a>설명
이 구조는 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 구조의 일부이며 여러 종류의 주소 중 하나를 `DEBUG_ADDRESS` 나타냅니다(구조는 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) 메서드에 대한 호출로 채워져 있음).

 [C# 만] 다음 표에서는 각 주소 `unionmember` 종류에 대한 멤버를 해석하는 방법을 보여 주어 있습니다. 예제에서는 한 종류의 주소에 대해 이 작업을 수행하는 방법을 보여 주며 있습니다.

|`dwKind`|`unionmember`로 해석|
|--------------|----------------------------------|
|`ADDRESS_KIND_NATIVE`|[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|
|`ADDRESS_KIND_METHOD`|[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|
|`ADDRESS_KIND_FIELD`|[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|
|`ADDRESS_KIND_LOCAL`|[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|
|`ADDRESS_KIND_PARAM`|[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|
|`ADDRESS_KIND_ARRAYELEM`|[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|
|`ADDRESS_KIND_RETVAL`|[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|

## <a name="example"></a>예제
이 예제에서는 C#의 구조체의 한 종류의 주소()`METADATA_ADDRESS_ARRAYELEM`를 해석하는 `DEBUG_ADDRESS_UNION` 방법을 보여 주며 있습니다. 나머지 요소는 정확히 같은 방식으로 해석될 수 있습니다.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(DEBUG_ADDRESS_UNION dau)
        {
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)
            {
                 METADATA_ADDRESS_ARRAYELEM arrayElem =
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,
                                 typeof(METADATA_ADDRESS_ARRAYELEM));
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
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
