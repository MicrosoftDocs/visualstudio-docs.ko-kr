---
description: 태스크가 대리자 실행을 완료했으며 연결된 자식 작업이 완료되길 암시적으로 기다리고 있습니다.
title: 필드 | TASK_STATE_WAITING_ON_CHILDREN Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TASK_STATE_WAITING_ON_CHILDREN field, Task class [.NET Framework debug engines]
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b795a20ba19b1309b3f3bf972beed70549d72d88
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900163"
---
# <a name="task_state_waiting_on_children-field"></a>TASK_STATE_WAITING_ON_CHILDREN 필드
태스크가 대리자 실행을 완료했으며 연결된 자식 작업이 완료되길 암시적으로 기다리고 있습니다.

 **네임스페이스:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **어셈블리:** mscorlib(mscorlib.dll) **

 .NET Framework 이 내부 멤버에 액세스할 수 없으므로 다음 구문은 CIL(공용 중간 언어)로 제공됩니다.

## <a name="syntax"></a>구문

```csharp
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)
```

## <a name="remarks"></a>설명
 [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) 필드에 이 값이 포함되어 있으면 <xref:System.Threading.Tasks.Task.Status%2A> 속성은 를 반환합니다. <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>

## <a name="see-also"></a>참조
- [Task 클래스](../../extensibility/debugger/task-class-internal-members.md)
