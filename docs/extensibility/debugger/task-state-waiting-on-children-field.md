---
description: 태스크가 대리자 실행을 완료 하 고 연결 된 자식 작업이 완료 될 때까지 암시적으로 대기 합니다.
title: TASK_STATE_WAITING_ON_CHILDREN 필드 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_WAITING_ON_CHILDREN field, Task class [.NET Framework debug engines]
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1533ef28b32450d9b039c27e49ba655dddfd6ebe
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223208"
---
# <a name="task_state_waiting_on_children-field"></a>TASK_STATE_WAITING_ON_CHILDREN 필드
태스크가 대리자 실행을 완료 하 고 연결 된 자식 작업이 완료 될 때까지 암시적으로 대기 합니다.

 **네임스페이스:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **어셈블리:** mscorlib ( *mscorlib.dll*)

 .NET Framework에서이 내부 멤버에 액세스할 수 없기 때문에 다음 구문이 CIL (공용 중간 언어)에서 제공 됩니다.

## <a name="syntax"></a>구문

```csharp
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)
```

## <a name="remarks"></a>설명
 [M_stateFlags](../../extensibility/debugger/m-stateflags-field.md) 필드에이 값이 포함 되어 있으면 <xref:System.Threading.Tasks.Task.Status%2A> 속성은을 반환 합니다 <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>참고 항목
- [Task 클래스](../../extensibility/debugger/task-class-internal-members.md)
