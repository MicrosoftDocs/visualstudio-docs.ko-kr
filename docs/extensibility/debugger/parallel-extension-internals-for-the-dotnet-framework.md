---
title: .NET 프레임워크에 대한 병렬 확장 내부 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a3583e94a0bfff4474db03aa9d083add921f3da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738267"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>.NET 프레임워크에 대한 병렬 확장 내부
이 섹션에서는 .NET Framework에 대한 병렬 확장에 대한 사용자 지정 디버거를 구현하는 데 도움이 되는 내부 형식, 메서드 및 클래스 필드에 대해 설명합니다.

## <a name="in-this-section"></a>섹션 내용
 [작업 클래스](../../extensibility/debugger/task-class-internal-members.md) 클래스의 내부 데이터 멤버에 대해 설명합니다. <xref:System.Threading.Tasks.Task?displayProperty=fullName>

 [작업 스케줄러 클래스](../../extensibility/debugger/taskscheduler-class-internal-members.md) 클래스의 내부 데이터 멤버에 대해 설명합니다. <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>

 [우발적 속성 클래스](../../extensibility/debugger/contingentproperties-class-internal-members.md) 클래스의 내부 데이터 멤버에 대해 설명합니다. `System.Threading.Tasks.ContingentProperties`

 [비동기 TaskMethodBuilder 구조](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md) 구조의 내부 멤버에 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> 대해 설명합니다.

 [AsyncTaskMethodBuilder\<TResult> 구조](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md) 구조의 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> 내부 멤버를 설명 합니다.

 [비동기 메서드 빌더 구조](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md) 구조의 내부 멤버에 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> 대해 설명합니다.

## <a name="see-also"></a>참조
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [비주얼 스튜디오 디버거 확장성](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [병렬 프로그래밍](/dotnet/standard/parallel-programming/index)
