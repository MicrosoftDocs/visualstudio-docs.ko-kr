---
title: 겟태스크스케줄러포디버거 방법 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a3b0c8c16b10a4cf2268161d8a2db96c10303b1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738652"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger 메서드
현재 활성 상태인 <xref:System.Threading.Tasks.TaskScheduler> 모든 개체의 배열을 검색합니다.

 **네임스페이스:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **조립:** mscorlib *(mscorlib.dll)*

 .NET Framework에서 이 내부 멤버에 액세스할 수 없으므로 CIL(일반 중간 언어)에서 다음 구문이 제공됩니다.

## <a name="syntax"></a>구문

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>반환 값
 이 <xref:System.AppDomain>에서 <xref:System.Threading.Tasks.TaskScheduler> 현재 활성 상태인 모든 개체의 배열입니다.

## <a name="remarks"></a>설명
 이 메서드는 스레드에서 안전하지 않으며 <xref:System.Threading.Tasks.TaskScheduler>의 다른 인스턴스와 동시에 사용해서는 안 됩니다. 디버거가 다른 모든 스레드를 일시 중단한 경우에만 디버거에서 이 메서드를 호출합니다.

## <a name="see-also"></a>참조
- [작업 스케줄러 클래스](../../extensibility/debugger/taskscheduler-class-internal-members.md)
