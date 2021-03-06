---
description: 이 항목에서는 System.Runtime.CompilerServices.AsyncTaskMethodBuilder 클래스의 내부 멤버에 대해 설명합니다.
title: AsyncTaskMethodBuilder &lt; TResult &gt; 구조체 - 내부 멤버 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ca9d5ccfcd5870902cc40a623aabb93a3115f469
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903803"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder &lt; TResult &gt; 구조체 - 내부 멤버
이 항목에서는 클래스의 내부 멤버에 대해 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> 설명합니다. 이 클래스에 대한 일반적인 내용은 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> 참조 항목을 참조하세요.

 **네임스페이스:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **어셈블리:** mscorlib(mscorlib.dll)

 .NET Framework 이러한 내부 멤버에 액세스할 수 없으므로 다음 구문은 CIL(공용 중간 언어)로 제공됩니다.

## <a name="syntax"></a>구문

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>내부 멤버

|속성|설명|
|----------|-----------------|
|[ObjectIdForDebugger 속성](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|디버거에서 이 작성기를 고유하게 식별하는 데 사용할 수 있는 개체를 가져옵니다.|
|[m_task 필드](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|초기화가 요동치는 빌드된 작업을 나타냅니다.|

## <a name="see-also"></a>참조
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>
- [.NET Framework 대한 병렬 확장 내부](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
