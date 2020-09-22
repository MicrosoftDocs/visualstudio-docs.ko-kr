---
title: 성능 데이터 수집 방법 이해 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.methodpage
helpviewer_keywords:
- Profiling Tools, profiling methods
ms.assetid: ea4881fd-bd04-4875-9b7b-28490d6706f9
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e398d7e5e297daa68663902efb8a9fa0775c86fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841466"
---
# <a name="understanding-performance-collection-methods"></a>성능 데이터 수집 방법 이해
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 프로파일링 도구는 성능 데이터를 수집하는 데 사용할 수 있는 5가지 방법을 제공합니다. 이 항목에서는 각 방법에 대해 설명하고, 특정 방법으로 데이터를 수집하는 것이 적절한 몇 가지 시나리오를 제시합니다.  
  
> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. Windows 스토어 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.  
  
|메서드|설명|  
|------------|-----------------|  
|[샘플링](#sampling)|애플리케이션에서 수행하는 작업에 대한 통계 데이터를 수집합니다.|  
|[계측](#instrumentation)|각 함수 호출에 대한 상세 타이밍 정보를 수집합니다.|  
|[동시성](#concurrency)|다중 스레드 애플리케이션에 대한 상세 정보를 수집합니다.|  
|[.NET 메모리](#net_memory)|.NET 메모리 할당 및 가비지 수집에 대한 상세 정보를 수집합니다.|  
|[계층 상호 작용](#tier_interaction)|SqlServer 데이터베이스에 대한 비동기 ADO.NET 함수 호출 관련 정보를 수집합니다.<br /><br /> [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] 또는 [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]를 사용하여 계층 상호 작용 프로파일링을 수집할 수 있습니다. 그러나 계층 상호 작용 프로파일링 데이터는 [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] 또는 [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]에서만 볼 수 있습니다.|  
  
 일부 프로파일링 방법을 사용하는 경우에는 소프트웨어 및 하드웨어 성능 카운터와 같은 추가 데이터도 수집할 수 있습니다. 자세한 내용은 [추가 성능 데이터 수집](../profiling/collecting-additional-performance-data.md)을 참조하세요.  
  
## <a name="sampling"></a><a name="sampling"></a> 샘플링  
 샘플링 프로파일링 방법은 프로파일링 실행 중에 애플리케이션이 수행하는 작업에 대한 통계 데이터를 수집합니다. 샘플링 방법은 간단하며 애플리케이션 메서드 실행에 거의 영향을 주지 않습니다.  
  
 샘플링은 Visual Studio 프로파일링 도구의 기본 방법이며 다음과 같은 경우 유용합니다.  
  
- 애플리케이션 성능을 처음으로 파악하려는 경우  
  
- 프로세서(CPU) 사용률과 관련된 성능 문제를 조사하려는 경우  
  
  샘플링 프로파일링 방법은 설정된 간격으로 컴퓨터 프로세서를 중단하여 함수 호출 스택을 수집합니다. 실행 중인 함수에 대해 전용 샘플 개수가 증가하며, 호출 스택의 모든 호출 함수에 대해 포괄 샘플 개수가 증가합니다. 샘플링 보고서에서는 프로파일링된 모듈, 함수, 소스 코드 줄 및 명령에 대해 이러한 개수의 합계를 제공합니다.  
  
  기본적으로 프로파일러는 샘플링 간격을 CPU 주기로 설정합니다. 간격 유형을 다른 CPU 성능 카운터로 변경할 수 있으며, 간격에 대해 카운터 이벤트 수를 설정할 수 있습니다. 또한 ADP.NET을 통해 SQL Server 데이터베이스에 대해 수행하는 쿼리에 대한 정보를 제공하는 TIP(계층 상호 작용 프로파일링) 데이터도 수집할 수 있습니다.  
  
  [샘플링을 사용하여 성능 통계 수집](../profiling/collecting-performance-statistics-by-using-sampling.md)  
  
  [샘플링 데이터 값 이해](../profiling/understanding-sampling-data-values.md)  
  
  [샘플링 방법 데이터 뷰](../profiling/profiler-sampling-method-data-views.md)  
  
## <a name="instrumentation"></a><a name="instrumentation"></a> 계층  
 계측 프로파일링 방법은 프로파일링된 애플리케이션의 함수 호출에 대한 상세 타이밍을 수집합니다. 다음과 같은 경우 계측 프로파일링이 유용합니다.  
  
- 디스크 I/O와 같은 입/출력 병목 현상을 조사하려는 경우  
  
- 특정 모듈 또는 함수 집합을 자세히 검사하려는 경우  
  
  계측 방법에서는 계측된 파일의 각 함수에 대한 타이밍 정보를 캡처하는 이진 파일과 이러한 함수가 수행하는 각 함수 호출에 코드를 주입합니다. 계측 파일에 쓰기와 같은 작업에 대 한 작동에 함수를 호출 하는 경우에 식별 합니다. 계측 보고서에서는 4개 값을 사용하여 함수 또는 소스 코드 줄에서 소요된 총 시간을 나타냅니다.  
  
- 경과된 포괄 시간 - 함수 또는 소스 줄을 실행하는 데 소요되는 총 시간입니다.  
  
- 애플리케이션 포괄 시간 - 운영 체제를 호출하는 데 소요된 시간을 제외하고 함수 또는 소스 줄을 실행하는 데 소요된 시간입니다.  
  
- 경과된 전용 시간 - 함수 또는 소스 코드 줄의 본문에 있는 코드를 실행하는 데 소요된 시간입니다. 함수 또는 소스 줄이 호출한 함수를 실행하는 데 소요된 시간은 제외됩니다.  
  
- 애플리케이션 전용 시간 - 함수 또는 소스 코드 줄의 본문에 있는 코드를 실행하는 데 소요된 시간입니다. 운영 체제 호출을 실행하는 데 소요된 시간과 함수 또는 소스 줄이 호출한 함수를 실행하는 데 소요된 시간은 제외됩니다.  
  
  계측 방법을 사용하여 CPU 및 소프트웨어 성능 카운터를 둘 다 수집할 수도 있습니다.  
  
  [계측 데이터 값 이해](../profiling/understanding-instrumentation-data-values.md)  
  
  [계측을 사용하여 자세한 타이밍 데이터 수집](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)  
  
  [계측 방법 데이터 뷰](../profiling/instrumentation-method-data-views.md)  
  
## <a name="concurrency"></a><a name="concurrency"></a> 동시성  
 동시성 프로파일링은 다중 스레드 애플리케이션에 대한 정보를 수집합니다. 리소스 경합 프로파일링에서는 경쟁하는 스레드가 공유 리소스에 액세스하기 위해 대기해야 할 때마다 자세한 호출 스택 정보를 수집합니다. 또한 동시성 시각화는 다중 스레드 애플리케이션이 자체적으로, 그리고 하드웨어/운영 체제/호스트 컴퓨터의 다른 프로세스와 상호 작용하는 방식에 대한 보다 일반적인 정보도 수집합니다.  
  
- 리소스 경합 보고서에는 총 경합 수와 대기가 발생한 모듈, 함수, 소스 코드 줄 및 명령에서 리소스를 대기하는 데 소요된 총 시간이 표시됩니다. 시간 표시 막대 그래프에도 발생하는 경합이 표시됩니다.  
  
- Concurrency 시각화에는 성능 병목 지점, CPU 미달 사용, 스레드 경합, 스레드 마이그레이션, 동기화 지연, 겹치는 I/O 영역 및 기타 정보를 찾는 데 사용할 수 있는 그래픽 정보가 표시됩니다. 가능한 경우 그래픽 출력은 호출 스택 및 소스 코드 데이터에 연결됩니다. 명령줄 및 Windows 애플리케이션에 대해서만 동시성 시각화 데이터를 수집할 수 있습니다.  
  
  [리소스 경합 데이터 값 이해](../profiling/understanding-resource-contention-data-values.md)  
  
  [스레드 및 프로세스 동시성 데이터 수집](../profiling/collecting-thread-and-process-concurrency-data.md)  
  
  [리소스 경합 데이터 뷰](../profiling/resource-contention-data-views.md)  
  
  [동시성 시각화 도우미](../profiling/concurrency-visualizer.md)  
  
## <a name="net-memory"></a><a name="net_memory"></a> .NET 메모리  
 .NET 메모리 할당 프로파일링 방법은 프로파일링된 애플리케이션에서 .NET Framework 개체를 할당할 때마다 컴퓨터 프로세서를 중단합니다. 개체 수명 데이터도 수집되는 경우 프로파일러는 각 .NET Framework 가비지 수집 후에 프로세서를 중단합니다.  
  
 프로파일러는 할당에서 생성되었거나 가비지 수집에서 삭제된 개체의 형식/크기/수에 대한 정보를 수집합니다.  
  
- 할당 이벤트가 발생하면 프로파일러는 함수 호출 스택에 대한 추가 정보를 수집합니다. 현재 실행 중인 함수에 대해 전용 할당 개수가 증가하며, 호출 스택의 모든 호출 함수에 대해 포괄 할당 개수가 증가합니다. .NET 보고서에서는 프로파일링된 형식, 모듈, 함수, 소스 코드 줄 및 명령에 대해 이러한 개수의 합계를 제공합니다.  
  
- 가비지 수집이 수행되면 프로파일러는 삭제된 개체에 대한 데이터와 각 가비지 수집 세대의 개체에 대한 정보를 수집합니다. 프로파일러는 프로파일링 실행이 끝나면 명시적으로 삭제되지 않은 개체에 대한 데이터를 기록합니다. 개체 수명 보고서에는 프로파일링 실행에서 할당된 각 형식의 합계가 표시됩니다.  
  
  .NET 메모리 프로파일링은 샘플링 또는 계측 모드에서 사용할 수 있습니다. 선택하는 모드는 .NET 메모리 프로파일링에서 고유하게 생성되는 할당 및 개체 수명 보고서에 영향을 주지 않습니다.  
  
- 샘플링 모드에서 .NET 메모리 프로파일링을 실행하면 profiler.NET이 메모리 할당 이벤트를 간격으로 사용하여 할당된 개체 수와 포괄/전용 값으로 할당된 총 바이트 수를 보고서에 표시합니다.  
  
- .NET 메모리 프로파일링을 계측 모드에서 실행하는 경우에는 포괄/전용 할당 값과 함께 자세한 타이밍 정보가 수집됩니다.  
  
  [메모리 할당 및 개체 수명 데이터 값 이해](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)  
  
  [.NET 메모리 할당 및 수명 데이터 수집](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)  
  
  [.NET 메모리 데이터 뷰](../profiling/dotnet-memory-data-views.md)  
  
## <a name="tier-interaction"></a><a name="tier_interaction"></a> 계층 상호 작용  
 계층 상호 작용 프로파일링에서는 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 페이지 또는 기타 애플리케이션과 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스 간의 동기 [!INCLUDE[vstecado](../includes/vstecado-md.md)] 호출에 대한 정보를 프로파일링 데이터 파일에 추가합니다. 데이터에는 호출의 수와 시간, 그리고 최대/최소 시간이 포함됩니다. 샘플링, 계측, .NET 메모리 또는 동시성 방법을 통해 수집되는 프로파일링 데이터에 계층 상호 작용 데이터를 추가할 수 있습니다.  
  
 ![계층 상호 작용 프로파일링 데이터](../profiling/media/tierinteraction-profilingtools.png "TierInteraction_ProfilingTools")  
프로파일링 도구에서 수집되는 계층 상호 작용 데이터  
  
 [계층 상호 작용 데이터 수집](../profiling/collecting-tier-interaction-data.md)  
  
 [계층 상호 작용 뷰](../profiling/tier-interaction-views.md)  
  
## <a name="see-also"></a>참고 항목  
 [방법: 웹 사이트에 대 한 성능 데이터 수집](../profiling/how-to-collect-performance-data-for-a-web-site.md)   
 [초보자를 위한 성능 프로 파일링 지침](../profiling/beginners-guide-to-performance-profiling.md)
