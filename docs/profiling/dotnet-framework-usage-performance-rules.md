---
title: .NET Framework 사용 성능 규칙 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ab573755-6370-48aa-853d-a7321c424c79
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5a740885d8876398bf86e279aa259e9169fcf7c2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779289"
---
# <a name="net-framework-usage-performance-rules"></a>.NET Framework 사용 성능 규칙
.NET Framework 사용 범주의 성능 규칙은 최적화할 수 있는 특정 방법을 확인하고 성능 문제가 있는지 조사할 수 있는 가비지 수집 및 잠금 경합과 같은 더 일반적인 사용 패턴도 확인합니다.

|||
|-|-|
|[DA0001: 연결에 StringBuilder를 사용하십시오.](../profiling/da0001-use-stringbuilder-for-concatenations.md)|<xref:System.String.Concat(System.String,System.String)?displayProperty=fullName> 호출이 프로파일링 데이터의 상당한 부분을 차지합니다. 여러 세그먼트에서 문자열을 구성할 때 <xref:System.Text.StringBuilder> 클래스를 사용해 보세요.|
|[DA0005: GC2 컬렉션이 많습니다.](../profiling/da0005-frequent-gc2-collections.md)|비교적 많은 .NET 메모리 개체가 2세대 가비지 수집에서 회수됩니다. 너무 많은 단기 유지 개체가 1세대 수집에서 생존하면 메모리 관리 비용이 쉽게 과도해질 수 있습니다.|
|[DA0006: 값 형식에 대해 Equals()를 재정의하십시오.](../profiling/da0006-override-equals-parens-for-value-types.md)|`Equals` 메서드 또는 공개 값 형식의 같음 연산자에 대한 호출이 프로파일링 데이터의 상당한 부분을 차지합니다. 더 효율적인 메서드를 구현해 보세요.|
|[DA0007: 제어 흐름에는 예외를 사용하지 마십시오.](../profiling/da0007-avoid-using-exceptions-for-control-flow.md)|프로파일링 데이터에서 .NET Framework 예외 처리기가 호출되는 비율이 높았습니다. throw되는 예외 수를 줄일 때 다른 제어 흐름 논리를 사용해 보세요.|
|[DA0010: GetHashCode의 부담이 큽니다.](../profiling/da0010-expensive-gethashcode.md)|해당 형식의 `GetHashCode` 메서드 호출이 프로파일링 데이터의 상당한 부분을 차지하거나 `GetHashCode` 메서드가 메모리를 할당합니다. 메서드의 복잡성을 줄이세요.|
|[DA0011: CompareTo의 부담이 큽니다.](../profiling/da0011-expensive-compareto.md)|해당 형식의 `CompareTo` 메서드가 부담이 크거나 메서드가 메모리를 할당합니다. `CompareTo` 메서드의 복잡성을 줄이세요.|
|[DA0012: 리플렉션 양이 많습니다.](../profiling/da0012-significant-amount-of-reflection.md)|<xref:System.Reflection.IReflect.InvokeMember%2A> 및 <xref:System.Reflection.IReflect.GetMember%2A>와 같은 <xref:System.Reflection?displayProperty=fullName> 메서드 또는 <xref:System.Type.InvokeMember%2A>와 같은 Type 메서드에 대한 호출이 프로파일링 데이터의 상당한 부분을 차지합니다. 가능할 경우 이러한 메서드를 종속 어셈블리의 메서드에 대한 초기 바인딩으로 바꿔 보세요.|
|[DA0013: String.Split 또는 String.Substring 사용률이 높습니다.](../profiling/da0013-high-usage-of-string-split-or-string-substring.md)|<xref:System.String.Split%2A?displayProperty=fullName> 또는 <xref:System.String.Substring%2A> 메서드에 대한 호출이 프로파일링 데이터의 상당한 부분을 차지합니다. 문자열에서 부분 분자열의 존재 여부를 테스트하는 경우 <xref:System.String.IndexOf%2A> 또는 <xref:System.String.IndexOfAny%2A>를 사용하는 것이 좋습니다.|
|[DA0018: 32비트 애플리케이션이 프로세스 관리 메모리 제한에 근접하고 있습니다.](../profiling/da0018-32-bit-application-running-at-process-managed-memory-limits.md)|프로파일링 실행 중에 수집된 시스템 데이터는 .NET Framework 메모리 힙이, 관리되는 힙이 32비트 프로세스에 도달할 수 있는 최대 크기에 도달했음을 나타냅니다. .NET 메모리 프로파일링 방법을 사용하고 애플리케이션의 관리되는 리소스 사용을 최적화하여 다시 프로파일링해 보세요.|
|[DA0021: Gen 1 가비지 컬렉션의 비율이 높습니다.](../profiling/da0021-high-rate-of-gen-1-garbage-collections.md)|비교적 많은 .NET 메모리 개체가 1세대 가비지 수집에서 회수됩니다. 너무 많은 단기 유지 개체가 0세대 수집에서 생존하면 메모리 관리 비용이 쉽게 과도해질 수 있습니다.|
|[DA0022: Gen 2 가비지 수집의 비율이 높습니다.](../profiling/da0022-high-rate-of-gen-2-garbage-collections.md)|많은 .NET 메모리 개체가 2세대 가비지 수집에서 회수됩니다. 너무 많은 단기 유지 개체가 1세대 수집에서 생존하면 메모리 관리 비용이 쉽게 과도해질 수 있습니다. 잠금 경합 비율이 규칙 DA0005의 임계값 상한을 초과할 경우 이 규칙이 실행됩니다.|
|[DA0023: 높은 GC CPU 시간](../profiling/da0023-high-gc-cpu-time.md)|프로파일링 중에 수집되는 시스템 성능 데이터가 가비지 수집에 걸린 시간이 총 애플리케이션 처리 시간에 비해 크다는 것을 나타냅니다.|
|[DA0024: 과도한 GC CPU 시간](../profiling/da0024-excessive-gc-cpu-time.md)|프로파일링 중에 수집되는 시스템 성능 데이터가 가비지 수집에 걸린 시간이 총 애플리케이션 처리 시간에 비해 지나치게 크다는 것을 나타냅니다. 가비지 수집에 걸린 시간이 규칙 DA0023의 임계값 상한을 초과할 경우 이 규칙이 실행됩니다.|
|[DA0038: 높은 비율의 잠금 경합](../profiling/da0038-high-rate-of-lock-contentions.md)|프로파일링 데이터와 함께 수집되는 시스템 성능 데이터가 애플리케이션 실행 중에 발생한 잠금 경합의 비율이 상당히 높다는 것을 나타냅니다. 동시성 프로파일링 방법을 통해 다시 프로파일링하여 경합의 원인을 찾아 보세요.|
|[DA0039: 매우 높은 비율의 잠금 경합](../profiling/da0039-very-high-rate-of-lock-contentions.md)|프로파일링 데이터와 함께 수집되는 시스템 성능 데이터가 애플리케이션 실행 중에 발생한 잠금 경합의 비율이 지나치게 높다는 것을 나타냅니다. 동시성 프로파일링 방법을 통해 다시 프로파일링하여 경합의 원인을 찾아 보세요. 잠금 경합 비율이 규칙 DA0038의 임계값 상한을 초과할 경우 이 규칙이 실행됩니다.|
