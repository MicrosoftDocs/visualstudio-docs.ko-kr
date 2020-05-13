---
title: TASK_STATE_CANCELED 필드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_CANCELED field, Task class [.NET Framework debug engines]
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d59335a418febef45ebe35d4590c72b486921639
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712754"
---
# <a name="task_state_canceled-field"></a>TASK_STATE_CANCELED 필드
작업이 실행 상태에 도달하기 전에 취소되거나 취소를 확인하여 예외 없이 완료되었습니다.

 **네임스페이스:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **어셈블리:** mscorlib (mscorlib.dll)

 .NET Framework에서 이 내부 멤버에 액세스할 수 없으므로 CIL(일반 중간 언어)에서 다음 구문이 제공됩니다.

## <a name="syntax"></a>구문

```csharp
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)
```

## <a name="remarks"></a>설명
 [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) 필드에 이 값이 포함되어 <xref:System.Threading.Tasks.Task.Status%2A> 있으면 <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>속성이 반환됩니다.

## <a name="see-also"></a>참조
- [Task 클래스](../../extensibility/debugger/task-class-internal-members.md)
