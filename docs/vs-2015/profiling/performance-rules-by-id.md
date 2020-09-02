---
title: ID별 성능 규칙 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 9a1c934c-4798-4df9-a8ef-eb17ef06b6a2
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3dd28cad3036aaca1445cba7b4531580a2a44812
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691693"
---
# <a name="performance-rules-by-id"></a>ID별 성능 규칙
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Warning|Description|  
|-------------|-----------------|  
|[DA0001: 연결에 StringBuilder를 사용하십시오.](../profiling/da0001-use-stringbuilder-for-concatenations.md)|System.String.Concat 호출이 프로파일링 데이터의 상당한 부분을 차지합니다. 여러 세그먼트에서 문자열을 구성할 때 <xref:System.Text.StringBuilder> 클래스를 사용해 보세요.|  
|[DA0002: VSPerfCorProf.dll이 없습니다.](../profiling/da0002-vsperfcorprof-dll-is-missing.md)|프로파일러는 프로파일링 실행 중 VSPerfCorProf.dll을 찾을 수 없습니다. 이 경고는 필요한 환경 변수를 초기화할 VSPerfCLREnv.cmd 도구를 사용하지 않고 프로파일러 데이터 컬렉션에 대한 명령줄 도구를 사용하는 경우에 발생합니다.|  
|[DA0003: 커널 샘플이 많습니다.](../profiling/da0003-many-kernel-samples.md)|애플리케이션에 대해 수집된 호출 스택 샘플의 상당 비율이 커널 모드에서 실행되었습니다. 다른 프로파일링 방법을 사용하여 애플리케이션을 프로파일링하는 것이 좋습니다.|  
|[DA0004: 프로세서 사용률이 높습니다.](../profiling/da0004-high-processor-usage.md)|계측 방법을 사용하여 수집된 프로파일링 데이터에서 프로세서(CPU) 사용률이 상당히 높았습니다. CPU 바인딩된 애플리케이션을 프로파일링할 경우 샘플링 프로파일링 방법을 사용해 보세요.|  
|[DA0005: GC2 컬렉션이 많습니다.](../profiling/da0005-frequent-gc2-collections.md)|많은 .NET 메모리 개체가 2세대 가비지 수집에서 회수됩니다.|  
|[DA0006: 값 형식에 대해 Equals()를 재정의하십시오.](../profiling/da0006-override-equals-parens-for-value-types.md)|Equals 메서드 또는 공개 값 형식의 같음 연산자에 대한 호출이 프로파일링 데이터의 상당한 부분을 차지합니다. 더 효율적인 메서드를 구현해 보세요.|  
|[DA0007: 제어 흐름에는 예외를 사용하지 마십시오.](../profiling/da0007-avoid-using-exceptions-for-control-flow.md)|프로파일링 데이터에서 .NET Framework 예외 처리기가 호출되는 비율이 높았습니다. throw되는 예외 수를 줄일 때 다른 제어 흐름 논리를 사용해 보세요.|  
|[DA0008: 수집되는 샘플 수가 적습니다.](../profiling/da0008-few-samples-collected.md)|프로파일링 실행에서 샘플이 몇 개만 수집되었습니다. 보다 의미 있는 결과를 위해 실행 시간을 늘리거나 샘플링 주기를 더 빠르게 해보세요.|  
|[DA0009: 높은 % Time in JIT](https://msdn.microsoft.com/b60c1767-515c-41d9-81c2-c70d0b7024fd)|애플리케이션 실행 시간의 상당 부분을 JIT(Just-In-Time) 컴파일러에서 사용합니다.|  
|[DA0010: GetHashCode의 부담이 큽니다.](../profiling/da0010-expensive-gethashcode.md)|해당 형식의 GetHashCode 메서드 호출이 프로파일링 데이터의 상당한 부분을 차지하거나 메서드가 메모리를 할당합니다.|  
|[DA0011: CompareTo의 부담이 큽니다.](../profiling/da0011-expensive-compareto.md)|해당 형식의 CompareTo 메서드가 부담이 크거나 메모리를 할당합니다.|  
|[DA0012: 리플렉션 양이 많습니다.](../profiling/da0012-significant-amount-of-reflection.md)|InvokeMember, GetMember 등의 System.Reflection 메서드 호출이나 MemberInvoke 등의 Type 메서드 호출이 프로파일링 데이터의 상당한 부분을 차지합니다. 가능할 경우 이러한 메서드를 종속 어셈블리의 메서드에 대한 초기 바인딩으로 바꿔 보세요.|  
|[DA0013: String.Split 또는 String.Substring 사용률이 높습니다.](../profiling/da0013-high-usage-of-string-split-or-string-substring.md)|System.String.Split 또는 System.String.Substring 메서드 호출이 프로파일링 데이터의 상당한 부분을 차지합니다. 문자열에 부분 문자열이 있는지 테스트할 경우 System.String.IndexOf 또는 System.String.IndexOfAny를 사용해 보세요.|  
|[DA0014: 활성 메모리를 디스크에 페이징하는 비율이 높습니다.](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|프로파일링 실행에서 수집된 시스템 성능 데이터는 프로파일링 실행 내내 디스크를 대상으로 한 활성 메모리 페이징의 비율이 극도로 높다는 것을 나타냅니다. 이 수준의 페이징 비율은 일반적으로 애플리케이션 성능 및 응답성에 영향을 미칩니다. 알고리즘을 수정하여 메모리 할당을 줄여 보세요. 애플리케이션의 메모리 요구 사항을 고려해야 할 수도 있습니다. 더 많은 메모리가 있는 컴퓨터에서 프로파일링을 다시 실행합니다.|  
|[DA0017: 활성 메모리를 디스크에 페이징하는 비율이 높습니다.](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|프로파일링 실행에서 수집된 시스템 성능 데이터는 프로파일링 실행 내내 디스크를 대상으로 한 활성 메모리 페이징의 비율이 높다는 것을 나타냅니다. 이 수준의 페이징 비율은 일반적으로 애플리케이션 성능 및 응답성에 영향을 미칩니다. 알고리즘을 수정하여 메모리 할당을 줄여 보세요. 애플리케이션의 메모리 요구 사항을 고려해야 할 수도 있습니다. 더 많은 메모리가 있는 컴퓨터에서 프로파일링을 다시 실행합니다.|  
|[DA0018: 32비트 애플리케이션이 프로세스 관리형 메모리 제한에 근접하고 있습니다.](../profiling/da0018-32-bit-application-running-at-process-managed-memory-limits.md)|프로파일링 실행 중에 수집된 시스템 데이터는 .NET Framework 메모리 힙이, 관리되는 힙이 32비트 프로세스로 커질 수 있는 최대 크기에 도달했음을 나타냅니다. 보고된 값은 프로파일링된 프로세스가 활성화되는 동안 관찰된 힙의 최대값입니다. 애플리케이션에 의해 관리되는 리소스의 사용을 최적화하는 것이 좋습니다.|  
|[DA0021: Gen 1 가비지 수집의 비율이 높습니다.](../profiling/da0021-high-rate-of-gen-1-garbage-collections.md)|프로파일링 중에 수집된 시스템 성능 데이터는 0세대 데이터 수집에 비해 .NET Framework 개체용 메모리의 상당한 부분이 가비지 수집의 1세대에서 회수되었음을 나타냅니다.|  
|[DA0022: Gen 2 가비지 수집의 비율이 높습니다.](../profiling/da0022-high-rate-of-gen-2-garbage-collections.md)|프로파일링 중에 수집된 시스템 성능 데이터는 0세대 및 1세대 가비지 수집에 비해 .NET Framework 개체용 메모리의 상당한 부분이 가비지 수집의 2세대에서 회수되었음을 나타냅니다.|  
|[DA0023: GC CPU 시간이 깁니다.](../profiling/da0023-high-gc-cpu-time.md)|프로파일링 중에 수집되는 시스템 성능 데이터가 가비지 수집에 걸린 시간이 총 애플리케이션 처리 시간에 비해 크다는 것을 나타냅니다.|  
|[DA0024: 과도 한 GC CPU 시간](../profiling/da0024-excessive-gc-cpu-time.md)|프로파일링 중에 수집된 시스템 성능 데이터가 가비지 수집에 걸린 시간이 총 애플리케이션 처리 시간에 비해 너무 크다는 것을 나타냅니다.|  
|[DA0026: 커널 CPU 시간 처리 시간이 너무 깁니다.](../profiling/da0026-excessive-kernel-cpu-time-processing.md)|커널 모드에서 실행된 CPU 시간이 사용자 모드에서 걸린 시간을 초과했습니다. 다시 프로파일링하고 시스템 호출(syscall) 수를 샘플링하여 높은 커널 모드 실행 시간의 원인을 확인해 보세요.|  
|[DA0029: 지원되지 않는 CLR 버전입니다.](../profiling/da0029-unsupported-clr-version.md)|프로파일링 도구에서 지원되지 않는 .NET Framework 버전 1.1을 사용하는 애플리케이션 프로파일링하려고 합니다.|  
|[DA0030: 데이터베이스 개체의 계층 상호 작용 측정값 수집](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md)|<xref:System.Data> 메서드 호출이 프로파일링 데이터의 상당한 부분을 차지하고 프로파일링 실행에서 상호 작용 데이터를 수집하지 않았습니다. 다시 프로파일링하고 계층 상호 작용 데이터를 추가해 보세요.|  
|[DA0038: 잠금 경합의 비율이 높습니다.](../profiling/da0038-high-rate-of-lock-contentions.md)|프로파일링 데이터와 함께 수집되는 시스템 성능 데이터가 애플리케이션 실행 중에 발생한 잠금 경합의 비율이 상당히 높다는 것을 나타냅니다. 동시성 프로파일링 방법을 통해 다시 프로파일링하여 경합의 원인을 찾아 보세요.|  
|[DA0039: 잠금 경합의 비율이 매우 높습니다.](../profiling/da0039-very-high-rate-of-lock-contentions.md)|프로파일링 데이터와 함께 수집되는 시스템 성능 데이터가 애플리케이션 실행 중에 발생한 잠금 경합의 비율이 지나치게 높다는 것을 나타냅니다. 동시성 프로파일링 방법을 통해 다시 프로파일링하여 경합의 원인을 찾아 보세요.|  
|[DA0501: 프로파일링되고 있는 프로세스의 평균 CPU 사용입니다.](../profiling/da0501-average-cpu-consumption-by-the-process-being-profiled.md)|이 메시지는 애플리케이션에서 명령을 실행할 때 프로세서가 사용 중이었던 시간의 백분율을 보고합니다. 보고된 값은 프로파일링되는 프로세스가 활성 상태였던 모든 측정 간격에 대한 평균입니다. 프로세서가 두 개 이상 있는 컴퓨터에서 이 값은 100%보다 클 수 있습니다.|  
|[DA0502: 프로파일링되고 있는 프로세스의 최대 CPU 사용입니다.](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|이 메시지는 애플리케이션에서 명령을 실행할 때 프로세서가 사용 중이었던 시간의 최대 백분율을 보고합니다. 보고된 값은 프로파일링되는 프로세스가 활성 상태였던 모든 측정 간격 중에 보고된 최대값입니다. 프로세서가 두 개 이상 있는 컴퓨터에서 이 백분율은 100%보다 클 수 있습니다.|  
|[DA0503: 프로파일링되고 있는 프로세스의 평균 작업 집합(바이트 단위)입니다.](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|이 메시지는 프로세스가 현재 사용 중인 실제 메모리의 평균 크기(바이트)를 보고합니다(작업 집합). 프로세스 작업 집합은 현재 실제 메모리에 있는 프로세스 주소 공간의 페이지를 나타냅니다.|  
|[DA0504: 프로파일링되고 있는 프로세스의 최대 작업 집합(바이트 단위)입니다.](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|이 메시지는 프로세스가 현재 사용 중인 실제 메모리의 최대 크기(바이트)를 보고합니다. 프로세스 작업 집합은 현재 실제 메모리에 있는 프로세스 주소 공간의 페이지를 나타냅니다. 이 규칙은 프로파일링이 활성화된 동안 프로세스 작업 집합의 최대값을 보고합니다.|  
|[DA0505: 프로파일링되고 있는 프로세스에 할당된 평균 전용 바이트입니다.](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|이 메시지는 프로세스가 현재 할당한 가상 메모리의 평균 크기(바이트)를 보고합니다(전용 바이트). 전용 바이트는 프로세스 내에서 실행되는 스레드만 액세스할 수 있는, 프로세스에 의해 할당된 가상 메모리 위치를 나타냅니다.|  
|[DA0506: 프로파일링되고 있는 프로세스에 할당된 최대 전용 바이트입니다.](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|이 메시지는 프로세스가 현재 할당한 가상 메모리의 최대 크기(바이트)를 보고합니다(전용 바이트). 전용 바이트는 프로세스 내에서 실행되는 스레드만 액세스할 수 있는, 프로세스에 의해 할당된 가상 메모리 위치를 나타냅니다.|
