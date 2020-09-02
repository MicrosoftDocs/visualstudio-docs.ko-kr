---
title: BP_RESOLUTION_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_INFO
helpviewer_keywords:
- BP_RESOLUTION_INFO structure
ms.assetid: ba0c162a-61e8-4a0b-811f-4c1d8a5d82f0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1ba3f95372774b811030244a20208edd6f226981
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153299"
---
# <a name="bp_resolution_info"></a>BP_RESOLUTION_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

코드 중단점 또는 데이터 중단점에 대 한 바인딩된 중단점 정보를 설명 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
typedef struct _BP_RESOLUTION_INFO {   
   BPRESI_FIELDS          dwFields;  
   BP_RESOLUTION_LOCATION bpResLocation;  
   IDebugProgram2*        pProgram;  
   IDebugThread2*         pThread;  
} BP_RESOLUTION_INFO;  
```  
  
```csharp  
public struct BP_RESOLUTION_INFO {   
   public uint                   dwFields;  
   public BP_RESOLUTION_LOCATION bpResLocation;  
   public IDebugProgram2         pProgram;  
   public IDebugThread2          pThread;  
};  
```  
  
## <a name="members"></a>멤버  
 `dwFields`  
 입력 하는 필드를 지정 하는 [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md) 열거형의 플래그 컬렉션입니다.  
  
 `bpResLocation`  
 코드 또는 데이터에서 중단점의 위치를 지정 하는 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) 구조체입니다.  
  
 `pProgram`  
 중단점 오류가 발생 한 응용 프로그램을 나타내는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 개체입니다.  
  
 `pThread`  
 중단점 오류를 포함 하는 응용 프로그램이 실행 되 고 있는 스레드를 나타내는 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 개체입니다.  
  
## <a name="remarks"></a>설명  
 이 구조는 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)에서 반환 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)   
 [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
