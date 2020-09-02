---
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 88ff2a1da1f937fd4011932979bd95057eb40dfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205059"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

프로세스의 속성을 설명 하거나 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
typedef DWORD PROCESS_INFO_FLAGS;  
```  
  
```csharp  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
```  
  
## <a name="members"></a>멤버  
 PIFLAG_SYSTEM_PROCESS  
 프로세스가 시스템 프로세스 임을 나타냅니다.  
  
 PIFLAG_DEBUGGER_ATTACHED  
 디버거가 프로세스를 디버깅 하 고 있음을 나타냅니다. [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]디버거 이거나 다른 디버거 (예: WinDbg) 일 수 있습니다.  
  
 PIFLAG_PROCESS_STOPPED  
 프로세스가 중지 되었음을 나타냅니다. `PIFLAG_DEBUGGER_ATTACHED`도 지정 된 경우에만 유효 합니다. 이상에서 사용할 수 있습니다 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] .  
  
 PIFLAG_PROCESS_RUNNING  
 프로세스가 실행 중임을 나타냅니다. `PIFLAG_DEBUGGER_ATTACHED`도 지정 된 경우에만 유효 합니다. 이상에서 사용할 수 있습니다 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] .  
  
## <a name="remarks"></a>설명  
 `Flags` [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) 구조체의 멤버에 사용 됩니다.  
  
 이러한 플래그는 비트와 함께 사용할 수 있습니다 `OR` .  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
