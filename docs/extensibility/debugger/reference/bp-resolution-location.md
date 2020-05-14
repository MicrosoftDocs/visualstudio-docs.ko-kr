---
title: BP_RESOLUTION_LOCATION | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b11d80e90daec19a14ca509e5a4b9bdb2d1ced4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737815"
---
# <a name="bp_resolution_location"></a>BP_RESOLUTION_LOCATION
중단점 확인 위치의 구조를 지정합니다.

## <a name="syntax"></a>구문

```cpp
struct _BP_RESOLUTION_LOCATION {
    BP_TYPE bpType;
    union {
        BP_RESOLUTION_CODE bpresCode;
        BP_RESOLUTION_DATA bpresData;
        int                unused;
    } bpResLocation;
} BP_RESOLUTION_LOCATION;
```

```csharp
public struct BP_RESOLUTION_LOCATION {
    public uint   bpType;
    public IntPtr unionmember1;
    public IntPtr unionmember2;
    public IntPtr unionmember3;
    public uint   unionmember4;
};
```

## <a name="members"></a>멤버
`bpType`\
공용 구조체 또는 `unionmemberX` 멤버를 해석하는 방법을 지정하는 `bpResLocation` [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) 열거형의 값입니다.

`bpResLocation.bpresCode`\
[C++ 전용] [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) 구조를 포함합니다. `bpType`  =  `BPT_CODE`

`bpResLocation.bpresData`\
[C++ 전용] [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) 구조를 포함 `bpType`  =  `BPT_DATA`합니다.

`bpResLocation.unused`\
[C++ 전용] 자리 표시자입니다.

`unionmember1`\
[C# 만] 해석 방법에 대한 비고를 참조하십시오.

`unionmember2`\
[C# 만] 해석 방법에 대한 비고를 참조하십시오.

`unionmember3`\
[C# 만] 해석 방법에 대한 비고를 참조하십시오.

`unionmember4`\
[C# 만] 해석 방법에 대한 비고를 참조하십시오.

## <a name="remarks"></a>설명
이 구조는 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) 및 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) 구조의 구성원입니다.

 [C# 만] 멤버는 `unionmemberX` 다음 표에 따라 해석됩니다. `bpType` 값에 대한 왼쪽 열을 아래로 찾은 `unionmemberX` 다음 가로질러 `unionmemberX` 각 멤버가 나타내는 것을 확인하고 그에 따라 마샬링합니다. C#에서 이 구조를 해석하는 방법에 대한 예제를 참조하십시오.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPT_DATA`|`string`(데이터 표현)|`string`(기능 이름)|`string`(이미지 이름)|`enum_BP_RES_DATA_FLAGS`|

## <a name="example"></a>예제
이 예제에서는 C#에서 `BP_RESOLUTION_LOCATION` 구조를 해석하는 방법을 보여 주습니다.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(BP_RESOLUTION_LOCATION bprl)
        {
            if (bprl.bpType == (uint)enum_BP_TYPE.BPT_CODE)
            {
                IDebugCodeContext2 pContext = (IDebugCodeContext2)Marshal.GetObjectForIUnknown(bp.unionmember1);
            }
            else if (bprl.bpType == (uint)enum_BP_TYPE.BPT_DATA)
            {
                string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);
                string functionName = Marshal.PtrToStringBSTR(bp.unionmember2);
                string imageName = Marshal.PtrToStringBSTR(bp.unionmember3);
                enum_BP_RES_DATA_FLAGS numElements = (enum_BP_RES_DATA_FLAGS)bp.unionmember4;
            }
        }
    }
}
```

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)
- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)
