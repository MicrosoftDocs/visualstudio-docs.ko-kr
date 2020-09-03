---
title: BPRESI_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 52a4b9719b03c353dd3933c16b6f494f19f9c6ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153194"
---
# <a name="bpresi_fields"></a>BPRESI_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

중단점을 성공적으로 확인 하기 위해 검색할 정보를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
typedef DWORD BPRESI_FIELDS;  
```  
  
```csharp  
public enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
```  
  
## <a name="members"></a>멤버  
 BPRESI_BPRESLOCATION  
 `bpResLocation` [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) 구조체의 (중단점 확인 위치) 필드를 초기화/사용 합니다.  
  
 BPRESI_PROGRAM  
 `pProgram`구조체의 필드를 초기화/사용 `BP_RESOLUTION_INFO` 합니다.  
  
 BPRESI_THREAD  
 `pThread`구조체의 필드를 초기화/사용 `BP_RESOLUTION_INFO` 합니다.  
  
 BPRESI_ALLFIELDS  
 모든 필드를 지정 합니다.  
  
## <a name="remarks"></a>설명  
 초기화할 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) 구조체의 필드를 나타내기 위해 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) 메서드에 전달 됩니다.  
  
 이러한 플래그는 구조체의 필드를 `BP_RESOLUTION_INFO` 사용 하 고 해당 구조가 반환 될 때 유효한 지 여부를 나타내는 데도 사용 됩니다.  
  
 이러한 값은 비트와 함께 사용할 수 있습니다 `OR` .  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
