---
title: TaskScheduler 클래스-내부 멤버 | Microsoft Docs
description: 사용자 지정 디버거를 구현 하는 데 도움이 되는 TaskScheduler 클래스의 내부 멤버에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 58b370a6742387f7493e4c6357cffd05f2bd88a5
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900150"
---
# <a name="taskscheduler-class---internal-members"></a>TaskScheduler 클래스-내부 멤버
이 문서에서는 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> 사용자 지정 디버거를 구현 하는 데 도움이 되는 클래스의 내부 멤버에 대해 설명 합니다. 이 클래스에 대 한 일반 정보는 <xref:System.Threading.Tasks.TaskScheduler> 참조 문서를 참조 하세요.

 **네임스페이스:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **어셈블리:** mscorlib ( *mscorlib.dll*)

 .NET Framework에서 이러한 내부 멤버에 액세스할 수 없기 때문에 다음 구문이 CIL (공용 중간 언어)에서 제공 됩니다.

## <a name="syntax"></a>구문

```csharp
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler
       extends System.Object
```

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

|속성|설명|
|----------|-----------------|
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|모든 예약 된 작업의 배열을 검색 합니다.|
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|현재 활성 상태인 모든 개체의 배열을 검색 <xref:System.Threading.Tasks.TaskScheduler> 합니다.|

## <a name="remarks"></a>설명

## <a name="see-also"></a>참조
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [.NET Framework에 대 한 병렬 확장 내부](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
