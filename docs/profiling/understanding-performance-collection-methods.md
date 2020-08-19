---
title: 성능 데이터 수집 방법 이해 | Microsoft Docs
ms.date: 4/30/2020
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.methodpage
helpviewer_keywords:
- Profiling tools, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ecbabae86b762c9143dba6be5aa0e4683a92b0dd
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88250775"
---
# <a name="understand-performance-collection-methods"></a>성능 데이터 수집 방법 이해

Visual Studio 프로파일링 도구는 성능 데이터를 수집하는 5가지 방법을 제공합니다. 이 문서에서는 각 방법을 설명하고 특정 방법으로 데이터를 수집하는 것이 적절한 시나리오를 제시합니다.

> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. 또한 UWP 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.

|메서드|설명|
|------------|-----------------|
|[샘플링](#sampling)|앱이 수행한 작업에 대한 통계 데이터를 수집합니다.|
|[계측](#instrumentation)|각 함수 호출에 대한 상세 타이밍 정보를 수집합니다.|
|[동시성](#concurrency)|다중 스레드 앱에 대한 자세한 정보를 수집합니다.|
|[.NET 메모리](#net-memory)|.NET 메모리 할당 및 가비지 수집에 대한 상세 정보를 수집합니다.|
|[계층 상호 작용](#tier-interaction)|SQL Server 데이터베이스에 대한 비동기 ADO.NET 함수 호출 관련 정보를 수집합니다.<br /><br /> 모든 버전의 Visual Studio는 계층 상호 작용 프로필 데이터를 수집할 수 있습니다. 그러나 Visual Studio Enterprise에서만 해당 데이터를 볼 수 있습니다.|

일부 프로파일링 방법을 사용하는 경우에는 소프트웨어 및 하드웨어 성능 카운터와 같은 추가 데이터도 수집할 수 있습니다. 자세한 내용은 [추가 성능 데이터 수집](../profiling/collecting-additional-performance-data.md)을 참조하세요.

## <a name="sampling"></a>샘플링

샘플링 프로파일링 방법은 프로파일링 실행 중에 앱이 수행하는 작업에 대한 통계 데이터를 수집합니다. 샘플링 방법은 간단하며 앱 메서드 실행에 거의 영향을 주지 않습니다.

샘플링은 Visual Studio 프로파일링 도구의 기본 방법이며 다음 작업에 유용합니다.

- 앱 성능에 대한 초기 탐색
- 마이크로프로세서(CPU) 사용률과 관련된 성능 문제를 조사하려는 경우

샘플링 프로파일링 방법은 설정된 간격으로 컴퓨터 CPU를 중단하여 함수 호출 스택을 수집합니다. 실행 중인 함수에 대해 전용 샘플 수가 증가합니다. 호출 스택의 모든 호출 함수에 대해 포함 횟수가 증가합니다. 샘플링 보고서에서는 프로파일링된 모듈, 함수, 소스 코드 줄 및 명령에 대해 이러한 개수의 합계를 제공합니다.

기본적으로 프로파일러는 샘플링 간격을 CPU 주기로 설정합니다. 간격 유형을 다른 CPU 성능 카운터로 변경하거나 간격에 대해 카운터 이벤트 수를 설정할 수 있습니다. 또한 TIP(계층 상호 작용 프로파일링) 데이터를 수집할 수 있습니다. 이 데이터는 ADO.NET을 통해 SQL Server 데이터베이스에 수행된 쿼리에 대한 정보를 제공합니다.

[샘플링을 사용하여 성능 통계 수집](../profiling/collecting-performance-statistics-by-using-sampling.md)

[샘플링 데이터 값 이해](../profiling/understanding-sampling-data-values.md)

[샘플링 방법 데이터 뷰](../profiling/profiler-sampling-method-data-views.md)

## <a name="instrumentation"></a>계측

계측 프로파일링 방법은 프로파일링된 앱의 함수 호출에 대한 상세 타이밍을 수집합니다. 계측 프로파일링은 다음과 같은 작업에 유용합니다.

- 디스크 I/O와 같은 입출력 병목 현상을 조사하려는 경우
- 특정 모듈 또는 함수 집합을 자세히 검사하려는 경우

계측 방법은 이진 파일에 코드를 삽입합니다. 이 코드는 계측된 파일의 모든 함수 및 해당 함수가 수행하는 각 함수 호출에 대한 타이밍 정보를 캡처합니다. 또한 계측은 파일에 쓰기와 같은 작업을 위해 함수가 운영 체제로 호출되는 경우를 식별합니다.

계측 보고서에서는 다음 4개 값을 사용하여 함수 또는 소스 코드 줄에서 소요된 총 시간을 나타냅니다.

- 경과된 포괄 - 함수 또는 소스 코드 줄을 실행하는 데 소요된 총 시간입니다.

- 애플리케이션 포괄 - 함수 또는 소스 코드 줄을 실행하는 데 소요된 시간입니다. 운영 체제에 대한 호출은 제외됩니다.

- 경과된 전용 - 함수 또는 소스 코드 줄을 실행하는 데 소요된 시간입니다. 다른 함수에 대한 호출은 제외됩니다.

- 애플리케이션 전용 - 함수 또는 소스 코드 줄을 실행하는 데 소요된 시간입니다. 운영 체제 또는 다른 함수에 대한 호출은 제외됩니다.

계측 방법을 사용하여 CPU 및 소프트웨어 성능 카운터를 둘 다 수집할 수도 있습니다.

[계측 데이터 값 이해](../profiling/understanding-instrumentation-data-values.md)

[계측을 사용하여 자세한 타이밍 데이터 수집](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)

[계측 방법 데이터 뷰](../profiling/instrumentation-method-data-views.md)

## <a name="concurrency"></a>동시성

동시성 프로파일링은 다중 스레드 앱에 대한 정보를 수집합니다. 리소스 경합 프로파일링에서는 경쟁하는 스레드가 공유 리소스에 액세스하기 위해 대기할 때마다 자세한 호출 스택 정보를 수집합니다. 또한 동시성 시각화는 다중 스레드 앱이 다음과 상호 작용하는 방법에 대한 보다 일반적인 정보를 수집합니다.

- 앱 자체
- 하드웨어
- 운영 체제입니다.
- 호스트 컴퓨터의 다른 프로세스

리소스 경합 보고서에는 총 경합 수가 표시됩니다. 또한 모듈, 함수, 소스 코드 줄 및 명령이 리소스를 대기한 총 시간을 보고합니다. 경합이 발생하면 시간 표시 막대 그래프에 표시됩니다.

동시성 시각화 도우미는 다음을 찾는 데 도움이 되는 그래픽 정보를 표시합니다.

- 성능 병목 상태
- CPU 미달 사용
- 스레드 경합
- 스레드 마이그레이션
- 동기화 지연
- 중첩된 I/O의 영역

  가능한 경우 그래픽 출력은 호출 스택 및 소스 코드의 데이터에 연결됩니다. 명령줄 앱과 Windows 앱에 대해서만 동시성 시각화 데이터를 수집할 수 있습니다.

[리소스 경합 데이터 값 이해](../profiling/understanding-resource-contention-data-values.md)

[스레드 및 프로세스 동시성 데이터 수집](../profiling/collecting-thread-and-process-concurrency-data.md)

[리소스 경합 데이터 뷰](../profiling/resource-contention-data-views.md)

[동시성 시각화 도우미](../profiling/concurrency-visualizer.md)

## <a name="net-memory"></a>.NET 메모리

.NET 메모리 할당에 대한 프로파일링 방법은 프로파일링된 애플리케이션에서 .NET Framework 개체를 할당할 때마다 CPU를 중단합니다. 프로파일러가 개체 수명 데이터도 수집하는 경우 각 .NET Framework 가비지 수집 후에 CPU를 중단합니다.

프로파일러는 할당에서 생성되었거나 가비지 수집에서 삭제된 개체의 형식, 크기, 수에 대한 정보를 수집합니다.

- 할당 이벤트가 발생하면 프로파일러는 함수 호출 스택에 대한 추가 정보를 수집합니다. 프로파일러는 현재 실행 중인 함수에 대한 전용 할당 수를 증가시킵니다. 또한 호출 스택의 모든 호출 함수에 대해 포함 수를 증가시킵니다. .NET 보고서에서는 프로파일링된 형식, 모듈, 함수, 소스 코드 줄 및 명령에 대해 이러한 개수의 합계를 제공합니다.

- 가비지 수집이 발생하면 프로파일러는 제거된 개체에 대한 데이터와 각 가비지 수집 생성의 개체에 대한 데이터를 수집합니다. 프로파일러는 프로파일링 실행이 끝나면 명시적으로 삭제되지 않은 개체에 대한 데이터를 기록합니다. 개체 수명 보고서에는 프로파일링 실행에서 할당된 각 형식의 합계가 표시됩니다.

샘플링 모드 또는 계측 모드에서 .NET 메모리 프로파일링을 사용할 수 있습니다. 선택하는 모드는 .NET 메모리 프로파일링에서 고유하게 생성되는 할당 및 개체 수명 보고서에 영향을 주지 않습니다.

- 샘플링 모드에서 .NET 메모리 프로파일링을 실행하는 경우 프로파일러는 메모리 할당 이벤트를 간격으로 사용합니다. 또한 할당된 개체의 총 수와 바이트를 보고서에 포함 및 전용 값으로 표시합니다.

- 계측 모드에서 .NET 메모리 프로파일링을 실행하는 경우에는 프로파일러가 포괄 및 전용 할당 값과 함께 자세한 타이밍 정보를 수집합니다.

[메모리 할당 및 개체 수명 데이터 값 이해](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)

[.NET 메모리 할당 및 수명 데이터 수집](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

[.NET 메모리 데이터 뷰](../profiling/dotnet-memory-data-views.md)

## <a name="tier-interaction"></a>계층 상호 작용

계층 상호 작용 프로파일링에서는 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 페이지 또는 다른 앱과 [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] 데이터베이스 간의 동기 [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] 호출에 대한 정보를 프로파일링 데이터 파일에 추가합니다. 데이터에는 호출의 수와 시간, 그리고 최대/최소 시간이 포함됩니다. 샘플링, 계측, .NET 메모리 또는 동시성 방법을 통해 수집하는 프로파일링 데이터에 계층 상호 작용 데이터를 추가할 수 있습니다.

![계층 상호 작용 프로파일링 데이터 흐름](../profiling/media/tierinteraction_profilingtools.png "계층 상호 작용 프로파일링 데이터 흐름")

프로파일링 도구를 통해 수집되는 계층 상호 작용 데이터에 대한 자세한 내용은 다음 문서를 참조하세요.

[계층 상호 작용 데이터 수집](../profiling/collecting-tier-interaction-data.md)

[계층 상호 작용 뷰](../profiling/tier-interaction-views.md)

## <a name="see-also"></a>참조

[방법: 웹 사이트에 대한 성능 데이터 수집](../profiling/how-to-collect-performance-data-for-a-web-site.md)

[초보자를 위한 성능 프로파일링 지침](../profiling/beginners-guide-to-performance-profiling.md)
