---
title: BP_LOCATION | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION
helpviewer_keywords:
- BP_LOCATION union
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c98fde516a3e836302cd7eb2c73abd730d5cc8c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737934"
---
# <a name="bp_location"></a>BP_LOCATION
중단점의 위치를 설명하는 데 사용되는 구조유형을 지정합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _BP_LOCATION {
    BP_LOCATION_TYPE bpLocationType;
    union {
        BP_LOCATION_CODE_FILE_LINE   bplocCodeFileLine;
        BP_LOCATION_CODE_FUNC_OFFSET bplocCodeFuncOffset;
        BP_LOCATION_CODE_CONTEXT     bplocCodeContext;
        BP_LOCATION_CODE_STRING      bplocCodeString;
        BP_LOCATION_CODE_ADDRESS     bplocCodeAddress;
        BP_LOCATION_DATA_STRING      bplocDataString;
        BP_LOCATION_RESOLUTION       bplocResolution;
        DWORD                        unused;
    } bpLocation;
} BP_LOCATION;
```

```csharp
public struct BP_LOCATION {
    public uint   bpLocationType;
    public IntPtr unionmember1;
    public IntPtr unionmember2;
    public IntPtr unionmember3;
    public IntPtr unionmember4;
};
```

## <a name="members"></a>멤버
`bpLocationType`\
공용 구조체 또는 멤버를 해석하는 `bpLocation` 데 사용되는 `unionmemberX` [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) 열거형의 값입니다.

`bpLocation`.`bplocCodeFileLine`\
[C++ 전용] [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) 구조를 포함 `bpLocationType`  =  `BPLT_CODE_FILE_LINE`합니다.

`bpLocation.bplocCodeFuncOffset`\
[C++ 전용] [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) 구조를 포함합니다. `bpLocationType`  =  `BPLT_CODE_FUNC_OFFSET`

`bpLocation.bplocCodeContext`\
[C++ 전용] [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) 구조가 `bpLocationType`  =  `BPLT_CODE_CONTEXT`포함되어 있습니다.

`bpLocation.bplocCodeString`\
[C++ 전용] [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) 구조를 포함 `bpLocationType`  =  `BPLT_CODE_STRING`합니다.

`bpLocation.bplocCodeAddress`\
[C++ 전용] [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) 구조를 포함합니다. `bpLocationType`  =  `BPLT_CODE_ADDRESS`

`bpLocation.bplocDataString`\
[C++ 전용] [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) 구조를 포함 `bpLocationType`  =  `BPLT_DATA_STRING`합니다.

`bpLocation.bplocResolution`\
[C++ 전용] [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) 구조를 포함 `bpLocationType`  =  `BPLT_RESOLUTION`합니다.

`unionmember1`\
[C# 만] 해석 방법에 대한 비고를 참조하십시오.

`unionmember2`\
[C# 만] 해석 방법에 대한 비고를 참조하십시오.

`unionmember3`\
[C# 만] 해석 방법에 대한 비고를 참조하십시오.

`unionmember4`\
[C# 만] 해석 방법에 대한 비고를 참조하십시오.

## <a name="remarks"></a>설명
이 구조는 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 및 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 구조의 구성원입니다.

 [C# 만] 멤버는 `unionmemberX` 다음 표에 따라 해석됩니다. 값에 대 한 왼쪽 된 열을 아래로 보고 다음 `unionmemberX` 다른 열을 통해 `unionmemberX` 보고 각 구성원이 나타내는 것을 확인 하 고 그에 따라 마샬링 합니다. `bpLocationType` C#에서 이 구조의 일부를 해석하는 방법에 대한 예제를 참조하십시오.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPLT_CODE_FILE_LINE`|`string`(컨텍스트)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|-|-|
|`BPLT_CODE_FUNC_OFFSET`|`string`(컨텍스트)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|-|-|
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPLT_CODE_STRING`|`string`(컨텍스트)|`string`(조건식)|-|-|
|`BPLT_CODE_ADDRESS`|`string`(컨텍스트)|`string`(모듈 URL)|`string`(기능 이름)|`string`(주소)|
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string`(컨텍스트)|`string`(데이터 표현)|`uint`(요소 수)|
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|-|-|-|

## <a name="example"></a>예제
이 예제에서는 형식에 `BP_LOCATION` 대한 C#의 `BPLT_DATA_STRING` 구조를 해석하는 방법을 보여 주습니다. 이 특정 형식은 가능한 `unionmemberX` 모든 형식(개체, 문자열 및 숫자)으로 네 멤버를 모두 해석하는 방법을 보여 주십니다.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(BP_LOCATION bp)
        {
            if (bp.bpLocationType == (uint)enum_BP_LOCATION_TYPE.BPLT_DATA_STRING)
            {
                IDebugThread2 pThread = (IDebugThread2)Marshal.GetObjectForIUnknown(bp.unionmember1);
                string context = Marshal.PtrToStringBSTR(bp.unionmember2);
                string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);
                uint numElements = (uint)Marshal.ReadInt32(bp.unionmember4);
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
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)
- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)
- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)
- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)
- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)
