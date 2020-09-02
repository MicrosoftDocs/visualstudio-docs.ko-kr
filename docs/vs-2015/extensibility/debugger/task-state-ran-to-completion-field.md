---
title: TASK_STATE_RAN_TO_COMPLETION 필드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_RAN_TO_COMPLETION field, Task class [.NET Framework debug engines]
ms.assetid: 0f4830af-fe0c-4141-b768-817f4e426b8c
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f7d5f05a077e5243d5de52c210ae65dbfe3b2850
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428029"
---
# <a name="task_state_ran_to_completion-field"></a>TASK_STATE_RAN_TO_COMPLETION 필드
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

작업이 실행을 완료했습니다.  
  
 **네임스페이스:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **어셈블리:** mscorlib (mscorlib.dll)  
  
 .NET Framework에서이 내부 멤버에 액세스할 수 없기 때문에 다음 구문이 CIL (공용 중간 언어)에서 제공 됩니다.  
  
## <a name="syntax"></a>구문  
  
```  
.field static assembly literal int32 TASK_STATE_RAN_TO_COMPLETION = int32(0x02000000)  
```  
  
## <a name="remarks"></a>설명  
 [M_stateFlags](../../extensibility/debugger/m-stateflags-field.md) 필드에이 값이 포함 되어 있으면 <xref:System.Threading.Tasks.Task.Status%2A> 속성은을 반환 합니다 <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .  
  
## <a name="see-also"></a>관련 항목  
 [작업 클래스](../../extensibility/debugger/task-class-internal-members.md)
