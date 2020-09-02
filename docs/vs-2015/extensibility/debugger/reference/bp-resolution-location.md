---
title: BP_RESOLUTION_LOCATION | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ea6539f2ed790dda5cc4c9de126aa226f4b2686
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153288"
---
# <a name="bp_resolution_location"></a>BP_RESOLUTION_LOCATION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

중단점 확인 위치의 구조를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
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
   public uint bpType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public uint   unionmember4;  
};  
```  
  
## <a name="members"></a>멤버  
 `bpType`  
 공용 구조체 또는 멤버를 해석 하는 방법을 지정 하는 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) 열거형의 값입니다 `bpResLocation` `unionmemberX` .  
  
 `bpResLocation.bpresCode`  
 [C + + 전용] 인 경우 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) 구조를 포함 합니다 `bpType`  =  `BPT_CODE` .  
  
 `bpResLocation.bpresData`  
 [C + + 전용] 인 경우 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) 구조를 포함 합니다 `bpType`  =  `BPT_DATA` .  
  
 `bpResLocation.unused`  
 [C + + 전용] 자리 표시자입니다.  
  
 `unionmember1`  
 [C #만 해당] 해석 방법에 대 한 설명을 참조 하세요.  
  
 `unionmember2`  
 [C #만 해당] 해석 방법에 대 한 설명을 참조 하세요.  
  
 `unionmember3`  
 [C #만 해당] 해석 방법에 대 한 설명을 참조 하세요.  
  
 `unionmember4`  
 [C #만 해당] 해석 방법에 대 한 설명을 참조 하세요.  
  
## <a name="remarks"></a>설명  
 이 구조는 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) 및 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) 구조체의 멤버입니다.  
  
 [C #만 해당] `unionmemberX` 멤버는 다음 표에 따라 해석 됩니다. 값의 왼쪽 열을 아래로 조회 `bpType` 하 여 각 멤버가 나타내는 항목을 확인 하 `unionmemberX` 고이에 `unionmemberX` 따라 마샬링합니다. C #에서이 구조체를 해석 하는 방법에 대해서는 예제를 참조 하세요.  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|  
|`BPT_DATA`|`string` (데이터 식)|`string` (함수 이름)|`string` (이미지 이름)|`enum_BP_RES_DATA_FLAGS`|  
  
## <a name="example"></a>예  
 이 예제에서는 `BP_RESOLUTION_LOCATION` c #의 구조를 해석 하는 방법을 보여 줍니다.  
  
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
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)   
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)   
 [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)
