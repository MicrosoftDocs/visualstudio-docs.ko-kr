---
title: 안정성 규칙
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- rules, reliability
- reliability rules
- managed code analysis rules, reliability rules
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0a35b9c49f2eb5655eeb67721b0fafdbbe1e087
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808274"
---
# <a name="reliability-rules"></a>안정성 규칙

안정성 규칙은 올바른 메모리 및 스레드 사용과 같은 라이브러리 및 응용 프로그램 안정성을 지원 합니다.

|규칙|설명|
|----------|-----------------|
|[CA2000: 범위를 벗어나기 전에 개체를 삭제하세요.](../code-quality/ca2000.md)|개체의 종료자가 실행되지 못하도록 하는 예외 이벤트가 발생할 수 있기 때문에 개체에 대한 모든 참조가 범위를 벗어나기 전에 개체를 명시적으로 삭제해야 합니다.|
|[CA2002: 약한 ID를 가진 개체를 잠그지 마십시오.](../code-quality/ca2002.md)|애플리케이션 도메인 경계를 가로질러 직접 액세스할 수 있는 개체를 약한 ID를 가진 개체라고 합니다. 약한 ID를 가진 개체에 대해 잠금을 가져오려고 시도하는 스레드는 같은 개체에 대해 잠금을 가진 다른 애플리케이션 도메인의 스레드에 의해 차단될 수 있습니다.|
|[CA2007: 작업을 직접 대기하지 마세요.](../code-quality/ca2007.md)|비동기 메서드는를 직접 [기다립니다](/dotnet/csharp/language-reference/keywords/await) <xref:System.Threading.Tasks.Task> 합니다.|
|[CA2008: TaskScheduler를 전달하지 않은 상태에서 작업을 만들지 않음](../code-quality/ca2008.md)|작업 만들기 또는 연속 작업에서 매개 변수를 지정 하지 않는 메서드 오버 로드를 사용 <xref:System.Threading.Tasks.TaskScheduler> 합니다.|
|[CA2009: ImmutableCollection 값의 ToImmutableCollection을 호출하지 마세요.](../code-quality/ca2009.md)|`ToImmutable` 네임 스페이스의 변경할 수 없는 컬렉션에 대해 메서드를 불필요 하 게 호출 했습니다 <xref:System.Collections.Immutable> .|
|[CA2011: Setter 내에서 속성을 할당하지 마세요.](../code-quality/ca2011.md) | 속성에 해당 하는 자체 [set 접근자](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor)내에 값이 실수로 할당 되었습니다. |
|[CA2012: ValueTasks를 올바르게 사용하세요.](../code-quality/ca2012.md) | 멤버 호출에서 반환 되는 ValueTasks는 직접 대기 합니다.  는 특정 기능을 여러 번 사용 하거나 완료 되기 전에 한 결과에 직접 액세스 하려고 시도 하 여 예외 또는 손상이 발생할 수 있습니다.  이러한 것을 무시 하면 기능적 버그를 나타낼 수 있으며 성능이 저하 될 수 있습니다. |
|[CA2013: 값 형식과 함께 ReferenceEquals를 사용하지 마세요.](../code-quality/ca2013.md) | 를 사용 하 여 값을 비교할 때 <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> objA와 Obja가 값 형식이 면 메서드로 전달 되기 전에 boxing 됩니다 <xref:System.Object.ReferenceEquals%2A> . 즉, objA와 Obja가 모두 값 형식의 동일한 인스턴스를 나타내는 경우에도 <xref:System.Object.ReferenceEquals%2A> 메서드에서 false를 반환 합니다. |
|[CA2014: 루프에서 stackalloc을 사용 하지 마십시오.](../code-quality/ca2014.md) | Stackalloc에 의해 할당 된 스택 공간은 현재 메서드 호출의 끝 에서만 해제 됩니다.  루프에서이를 사용 하면 바인딩되지 않은 스택 증가 및 최종 스택 오버플로 조건이 발생할 수 있습니다. |
|[CA2015: MemoryManager T에서 파생 된 형식에 대 한 종료자를 정의 하지 않습니다. &lt;&gt;](../code-quality/ca2015.md) | 에서 파생 된 형식에 종료자를 추가 하면에서 <xref:System.Buffers.MemoryManager%601> 아직 사용 중인 메모리를 해제할 수 있습니다 <xref:System.Span%601> . |
|[CA2016: 인수 하나를 사용하는 메서드에 CancellationToken 매개 변수를 전달하세요.](ca2016.md) | `CancellationToken`매개 변수를 사용 하 여 작업 취소 알림이 제대로 전파 되는지 확인 하거나 `CancellationToken.None` 의도적으로 토큰을 전파 하지 않도록 명시적으로 전달 하는 메서드에 매개 변수를 전달 합니다. |
