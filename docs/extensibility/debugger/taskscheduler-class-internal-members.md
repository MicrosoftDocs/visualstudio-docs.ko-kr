---
title: 태스크스케줄러 클래스 - 내부 구성원 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a53abc8b24edb06445c23c19744d00d50de8735d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712574"
---
# <a name="taskscheduler-class---internal-members"></a>작업 스케줄러 클래스 - 내부 구성원
이 문서에서는 사용자 지정 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> 디버거를 구현하는 데 도움이 되는 클래스의 내부 멤버에 대해 설명합니다. 이 클래스에 대한 일반적인 <xref:System.Threading.Tasks.TaskScheduler> 정보는 참조 문서를 참조하십시오.

 **네임스페이스:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **조립:** mscorlib *(mscorlib.dll)*

 .NET Framework에서 이러한 내부 멤버에 액세스할 수 없으므로 CIL(일반 중간 언어)에서 다음 구문이 제공됩니다.

## <a name="syntax"></a>구문

```csharp
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler
       extends System.Object
```

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

|이름|설명|
|----------|-----------------|
|[GetScheduled작업포디버거](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|예약된 모든 작업의 배열을 검색합니다.|
|[겟태스크스케줄러포디버거](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|현재 활성 상태인 <xref:System.Threading.Tasks.TaskScheduler> 모든 개체의 배열을 검색합니다.|

## <a name="remarks"></a>설명

## <a name="see-also"></a>참조
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [.NET 프레임워크에 대한 병렬 확장 내부](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
