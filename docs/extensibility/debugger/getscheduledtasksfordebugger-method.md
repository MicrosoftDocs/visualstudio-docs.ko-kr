---
title: GetScheduled작업포디버거 방법 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fca6c8e92cd0b4755bd79b8e142a7e1d283f868d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738657"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger 메서드
예약된 모든 작업의 배열을 검색합니다.

 **네임스페이스:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **조립:** mscorlib *(mscorlib.dll)*

 .NET Framework에서 이 내부 멤버에 액세스할 수 없으므로 CIL(일반 중간 언어)에서 다음 구문이 제공됩니다.

## <a name="syntax"></a>구문

```csharp
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed
```

## <a name="return-value"></a>Return Value
 예약된 모든 작업의 배열입니다. 각 작업이 실행 중이거나 실행이 완료되었습니다.

## <a name="remarks"></a>설명
 이 메서드는 스레드에서 안전하지 않으며 <xref:System.Threading.Tasks.TaskScheduler>의 다른 인스턴스와 동시에 사용해서는 안 됩니다. 디버거가 다른 모든 스레드를 일시 중단한 경우에만 디버거에서 이 메서드를 호출합니다.

## <a name="see-also"></a>참조
- [작업 스케줄러 클래스](../../extensibility/debugger/taskscheduler-class-internal-members.md)
