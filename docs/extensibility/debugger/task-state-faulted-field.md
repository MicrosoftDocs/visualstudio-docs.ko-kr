---
description: 작업이 처리되지 않은 예외로 인해 완료되었습니다.
title: 필드 | TASK_STATE_FAULTED Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TASK_STATE_FAULTED field, Task class [.NET Framework debug engines]
ms.assetid: ced826ae-09a9-4acf-af00-a2343d396bb8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0a3e1bf4fe6a95bd55cf366d1f5b8f56d7ea9c05
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902841"
---
# <a name="task_state_faulted-field"></a>TASK_STATE_FAULTED 필드
작업이 처리되지 않은 예외로 인해 완료되었습니다.

 **네임스페이스:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **어셈블리:** mscorlib(mscorlib.dll) **

 .NET Framework 이 내부 멤버에 액세스할 수 없으므로 다음 구문은 CIL(공용 중간 언어)로 제공됩니다.

## <a name="syntax"></a>구문

```csharp
.field static assembly literal int32 TASK_STATE_FAULTED = int32(0x00400000)
```

## <a name="remarks"></a>설명
 [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) 필드에 이 값이 포함되어 있으면 <xref:System.Threading.Tasks.Task.Status%2A> 속성은 를 반환합니다. <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>

## <a name="see-also"></a>참조
- [Task 클래스](../../extensibility/debugger/task-class-internal-members.md)
