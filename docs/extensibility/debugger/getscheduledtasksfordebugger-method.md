---
description: 모든 예약 된 작업의 배열을 검색 합니다.
title: GetScheduledTasksForDebugger 메서드 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dd70db6f6fd9eb1558a21e50f3d2f63137fe8e1d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167817"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger 메서드
모든 예약 된 작업의 배열을 검색 합니다.

 **네임스페이스:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **어셈블리:** mscorlib ( *mscorlib.dll*)

 .NET Framework에서이 내부 멤버에 액세스할 수 없기 때문에 다음 구문이 CIL (공용 중간 언어)에서 제공 됩니다.

## <a name="syntax"></a>구문

```csharp
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed
```

## <a name="return-value"></a>Return Value
 모든 예약 된 작업의 배열입니다. 각 태스크가 실행 중이거나 실행이 완료 되었습니다.

## <a name="remarks"></a>설명
 이 메서드는 스레드로부터 안전 하지 않으며의 다른 인스턴스와 동시에 사용할 수 없습니다 <xref:System.Threading.Tasks.TaskScheduler> . 디버거가 다른 모든 스레드를 일시 중단 한 경우에만 디버거에서이 메서드를 호출 합니다.

## <a name="see-also"></a>참고 항목
- [TaskScheduler 클래스](../../extensibility/debugger/taskscheduler-class-internal-members.md)
