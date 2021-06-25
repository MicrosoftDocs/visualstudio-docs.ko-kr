---
description: 작업이 실행 상태에 도달하기 전에 취소되거나 취소를 확인하고 예외 없이 완료되었습니다.
title: 필드 | TASK_STATE_CANCELED Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TASK_STATE_CANCELED field, Task class [.NET Framework debug engines]
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 90b3c048edb4e52a426a2fd40d8bfd31168fea7d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900176"
---
# <a name="task_state_canceled-field"></a>TASK_STATE_CANCELED 필드
작업이 실행 상태에 도달하기 전에 취소되거나 취소를 확인하고 예외 없이 완료되었습니다.

 **네임스페이스:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **어셈블리:** mscorlib(mscorlib.dll)

 .NET Framework 이 내부 멤버에 액세스할 수 없으므로 다음 구문은 CIL(공용 중간 언어)로 제공됩니다.

## <a name="syntax"></a>구문

```csharp
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)
```

## <a name="remarks"></a>설명
 [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) 필드에 이 값이 포함되어 있으면 <xref:System.Threading.Tasks.Task.Status%2A> 속성은 를 반환합니다. <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>

## <a name="see-also"></a>참조
- [Task 클래스](../../extensibility/debugger/task-class-internal-members.md)
