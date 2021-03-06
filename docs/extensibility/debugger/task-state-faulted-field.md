---
description: 작업이 처리되지 않은 예외로 인해 완료되었습니다.
title: TASK_STATE_FAULTED 필드 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_FAULTED field, Task class [.NET Framework debug engines]
ms.assetid: ced826ae-09a9-4acf-af00-a2343d396bb8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a5a8113f6145706d2863a4f0060a8627952eb0b3
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223188"
---
# <a name="task_state_faulted-field"></a>TASK_STATE_FAULTED 필드
작업이 처리되지 않은 예외로 인해 완료되었습니다.

 **네임스페이스:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **어셈블리:** mscorlib ( *mscorlib.dll*)

 .NET Framework에서이 내부 멤버에 액세스할 수 없기 때문에 다음 구문이 CIL (공용 중간 언어)에서 제공 됩니다.

## <a name="syntax"></a>구문

```csharp
.field static assembly literal int32 TASK_STATE_FAULTED = int32(0x00400000)
```

## <a name="remarks"></a>설명
 [M_stateFlags](../../extensibility/debugger/m-stateflags-field.md) 필드에이 값이 포함 되어 있으면 <xref:System.Threading.Tasks.Task.Status%2A> 속성은을 반환 합니다 <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>참고 항목
- [Task 클래스](../../extensibility/debugger/task-class-internal-members.md)
