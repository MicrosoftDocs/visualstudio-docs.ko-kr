---
description: 현재 활성 상태인 모든 TaskScheduler 개체의 배열을 검색 합니다.
title: GetTaskSchedulersForDebugger 메서드 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7d024e44dee8e7513d862e3d299c2ed2b9e53cd5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054857"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger 메서드
현재 활성 상태인 모든 개체의 배열을 검색 <xref:System.Threading.Tasks.TaskScheduler> 합니다.

 **네임스페이스:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **어셈블리:** mscorlib ( *mscorlib.dll*)

 .NET Framework에서이 내부 멤버에 액세스할 수 없기 때문에 다음 구문이 CIL (공용 중간 언어)에서 제공 됩니다.

## <a name="syntax"></a>구문

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>반환 값
 <xref:System.Threading.Tasks.TaskScheduler>이에서 현재 활성 상태인 모든 개체의 배열입니다 <xref:System.AppDomain> .

## <a name="remarks"></a>설명
 이 메서드는 스레드로부터 안전 하지 않으며의 다른 인스턴스와 동시에 사용할 수 없습니다 <xref:System.Threading.Tasks.TaskScheduler> . 디버거가 다른 모든 스레드를 일시 중단 한 경우에만 디버거에서이 메서드를 호출 합니다.

## <a name="see-also"></a>참조
- [TaskScheduler 클래스](../../extensibility/debugger/taskscheduler-class-internal-members.md)
