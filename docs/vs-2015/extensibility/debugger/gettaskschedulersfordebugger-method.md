---
title: GetTaskSchedulersForDebugger 메서드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 995bf40669a4480f6f1ddfe8071a7885a4659c9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152719"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger 메서드
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

현재 활성 상태인 모든 개체의 배열을 검색 <xref:System.Threading.Tasks.TaskScheduler> 합니다.  
  
 **네임스페이스:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **어셈블리:** mscorlib (mscorlib.dll)  
  
 .NET Framework에서이 내부 멤버에 액세스할 수 없기 때문에 다음 구문이 CIL (공용 중간 언어)에서 제공 됩니다.  
  
## <a name="syntax"></a>구문  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Return Value  
 <xref:System.Threading.Tasks.TaskScheduler>이에서 현재 활성 상태인 모든 개체의 배열입니다 <xref:System.AppDomain> .  
  
## <a name="remarks"></a>설명  
 이 메서드는 스레드로부터 안전 하지 않으며의 다른 인스턴스와 동시에 사용 하면 안 됩니다 <xref:System.Threading.Tasks.TaskScheduler> . 디버거가 다른 모든 스레드를 일시 중단 한 경우에만 디버거에서 호출 해야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [TaskScheduler 클래스](../../extensibility/debugger/taskscheduler-class-internal-members.md)
