---
title: BP_STATE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_STATE
helpviewer_keywords:
- BP_STATE enumeration
ms.assetid: 08aa6a3f-3e5f-4c83-8eca-7b7b5f8e208d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a4de23d462136ad417859d7064fef6b4ace7e59c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153246"
---
# <a name="bp_state"></a>BP_STATE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

바인딩된 중단점의 존재를 지정 하 고 사용 하도록 설정할지 여부도 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum enum_BP_STATE {   
   BPS_NONE     = 0x0000,  
   BPS_DELETED  = 0x0001,  
   BPS_DISABLED = 0x0002,  
   BPS_ENABLED  = 0x0003  
};  
typedef DWORD BP_STATE;  
```  
  
```csharp  
public enum enum_BP_STATE {   
   BPS_NONE     = 0x0000,  
   BPS_DELETED  = 0x0001,  
   BPS_DISABLED = 0x0002,  
   BPS_ENABLED  = 0x0003  
};  
```  
  
## <a name="members"></a>멤버  
 BPS_NONE  
 중단점이 존재 하지 않도록 지정 합니다.  
  
 BPS_DELETED  
 중단점이 삭제 되었음을 지정 합니다.  
  
 BPS_DISABLED  
 중단점을 사용 하지 않도록 지정 합니다.  
  
 BPS_ENABLED  
 중단점을 사용 하도록 지정 합니다.  
  
## <a name="remarks"></a>설명  
 [Getstate](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md) 메서드에서 반환 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)
