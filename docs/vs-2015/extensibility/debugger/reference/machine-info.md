---
title: MACHINE_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MACHINE_INFO
helpviewer_keywords:
- MACHINE_INFO structure
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac571a1e1c7a9d6cff1caaca40f1c6568f99adf1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546790"
---
# <a name="machine_info"></a>MACHINE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

특정 컴퓨터에 대해 설명 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
typedef struct tagMACHINE_INFO {   
   MACHINE_INFO_FIELDS Fields;  
   BSTR                bstrName;  
   MACHINE_INFO_FLAGS  Flags;  
} MACHINE_INFO;  
```  
  
```csharp  
public struct MACHINE_INFO {   
   public uint   Fields;  
   public string bstrName;  
   public uint   Flags;  
};  
```  
  
## <a name="members"></a>멤버  
 `Fields`  
 구조체의 필드를 지정 하는 [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) 열거형의 플래그 조합입니다.  
  
 `bstrName`  
 컴퓨터 이름입니다. [Getmachinename](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)을 호출 하는 것과 같습니다.  
  
 `Flags`  
 컴퓨터 특성을 설명 하는 [MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) 열거형의 플래그 조합입니다.  
  
## <a name="remarks"></a>설명  
 이 구조체는 [Getmachineinfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) 메서드를 호출 하 여 반환 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)   
 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
