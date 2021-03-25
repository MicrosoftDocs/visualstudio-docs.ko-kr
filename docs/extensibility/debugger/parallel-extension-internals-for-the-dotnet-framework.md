---
title: .NET Framework에 대 한 병렬 확장 내부 구조 Microsoft Docs
description: 이러한 리소스는 .NET Framework에 대 한 병렬 확장을 위한 사용자 지정 디버거를 구현 하는 데 사용 되는 클래스의 내부 형식, 메서드 및 필드에 대해 설명 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9aec52f354043dabb3bf816bbd35352f0c3a28bb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067831"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>.NET Framework에 대 한 병렬 확장 내부
이 섹션에서는 .NET Framework에 대 한 병렬 확장을 위한 사용자 지정 디버거를 구현 하는 데 도움이 되는 클래스의 내부 형식, 메서드 및 필드에 대해 설명 합니다.

## <a name="in-this-section"></a>단원 내용
 [작업 클래스](../../extensibility/debugger/task-class-internal-members.md) 클래스의 내부 데이터 멤버에 대해 설명 합니다 <xref:System.Threading.Tasks.Task?displayProperty=fullName> .

 [TaskScheduler 클래스](../../extensibility/debugger/taskscheduler-class-internal-members.md) 클래스의 내부 데이터 멤버에 대해 설명 합니다 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> .

 [ContingentProperties 클래스](../../extensibility/debugger/contingentproperties-class-internal-members.md) 클래스의 내부 데이터 멤버에 대해 설명 합니다 `System.Threading.Tasks.ContingentProperties` .

 [AsyncTaskMethodBuilder 구조체](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md) 구조체의 내부 멤버를 설명 합니다 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> .

 [AsyncTaskMethodBuilder \<TResult> 구조체](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md) 는 구조체의 내부 멤버를 설명 합니다 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> .

 [AsyncVoidMethodBuilder 구조체](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md) 구조체의 내부 멤버를 설명 합니다 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> .

## <a name="see-also"></a>참조
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Visual Studio 디버거 확장성](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [병렬 프로그래밍](/dotnet/standard/parallel-programming/index)
