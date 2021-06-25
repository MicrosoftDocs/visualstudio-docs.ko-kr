---
description: 예약된 모든 작업의 배열을 검색합니다.
title: GetScheduledTasksForDebugger 메서드 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 51da481edb636450770d0cff569b9ef411e17cf6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900956"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger 메서드
예약된 모든 작업의 배열을 검색합니다.

 **네임스페이스:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **어셈블리:** mscorlib(mscorlib.dll) **

 .NET Framework 이 내부 멤버에 액세스할 수 없으므로 다음 구문은 CIL(공용 중간 언어)로 제공됩니다.

## <a name="syntax"></a>구문

```csharp
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed
```

## <a name="return-value"></a>Return Value
 예약된 모든 작업의 배열입니다. 각 태스크가 실행 중이거나 실행이 완료되었습니다.

## <a name="remarks"></a>설명
 이 메서드는 스레드에서 안전하지 않으며 다른 인스턴스와 동시에 사용하면 안 <xref:System.Threading.Tasks.TaskScheduler> 됩니다. 디버거가 다른 모든 스레드를 일시 중단한 경우에만 디버거에서 이 메서드를 호출합니다.

## <a name="see-also"></a>참조
- [TaskScheduler 클래스](../../extensibility/debugger/taskscheduler-class-internal-members.md)
