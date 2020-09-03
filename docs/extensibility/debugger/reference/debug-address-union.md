---
title: DEBUG_ADDRESS_UNION | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737531"
---
# <a name="debug_address_union"></a>DEBUG_ADDRESS_UNION
여러 종류의 주소를 설명 합니다.

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
합집합을 해석 하는 방법을 지정 하는 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) 열거형의 값입니다.

`addr.addrNative`\
[C + + 전용] = ADDRESS_KIND_NATIVE 인 경우 [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) 구조를 포함 합니다 `dwKind` .

`addr.addrThisRel`\
[C + + 전용] = ADDRESS_KIND_UNMANAGED_THIS_RELATIVE 인 경우[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) 구조를 포함 합니다 `dwKind` .

`addr.addUPhysical`\
[C + + 전용] = ADDRESS_KIND_UNMANAGED_PHYSICAL 인 경우[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) 구조를 포함 합니다 `dwKind` .

`addr.addrMethod`\
[C + + 전용] = ADDRESS_KIND_METHOD 인 경우[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) 구조를 포함 합니다 `dwKind` .

`addr.addrField`\
[C + + 전용] = ADDRESS_KIND_FIELD 인 경우[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) 구조를 포함 합니다 `dwKind` .

`addr.addrLocal`\
[C + + 전용] = ADDRESS_KIND_LOCAL 인 경우[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) 구조를 포함 합니다 `dwKind` .

`addr.addrParam`\
[C + + 전용] = ADDRESS_KIND_PARAM 인 경우[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) 구조를 포함 합니다 `dwKind` .

`addr.addrArrayElem`\
[C + + 전용] = ADDRESS_KIND_ARRAYELEM 인 경우[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) 구조를 포함 합니다 `dwKind` .

`addr.addrRetVal`\
[C + + 전용] = ADDRESS_KIND_RETVAL 인 경우[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) 구조를 포함 합니다 `dwKind` .

`addr.unused`\
[C + + 전용] 패딩.

`addr`\
[C + + 전용] 공용 구조체의 이름입니다.

`unionmember`\
[C #만 해당] 이 값은에 따라 적절 한 구조체 형식으로 마샬링되어야 `dwKind` 합니다. 합집합의 연결 및 해석에 대 한 설명을 참조 하세요 `dwKind` .

## <a name="remarks"></a>설명
이 구조체는 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 구조체의 일부 이며 다양 한 종류의 주소 중 하나를 나타냅니다 .이 구조는 `DEBUG_ADDRESS` [getaddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) 메서드를 호출 하 여 채워집니다.

 [C #만 해당] 다음 표에서는 `unionmember` 각 주소 유형에 대 한 멤버를 해석 하는 방법을 보여 줍니다. 이 예에서는 한 종류의 주소에 대해이 작업을 수행 하는 방법을 보여 줍니다.

|`dwKind`|`unionmember` 로 해석 됨|
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
이 예제에서는 `METADATA_ADDRESS_ARRAYELEM` `DEBUG_ADDRESS_UNION` c #에서 구조체의 한 종류의 주소 ()를 해석 하는 방법을 보여 줍니다. 나머지 요소는 정확히 동일한 방법으로 해석할 수 있습니다.

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
헤더: sh

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
