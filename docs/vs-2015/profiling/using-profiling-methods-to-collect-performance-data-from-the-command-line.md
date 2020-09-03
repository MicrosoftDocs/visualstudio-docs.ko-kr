---
title: 명령줄에서 프로파일링 방법을 사용하여 성능 데이터 수집 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fe9e8d3dbd1e7395287cd7241f1e6145dffca7e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145395"
---
# <a name="using-profiling-methods-to-collect-performance-data-from-the-command-line"></a>명령줄에서 프로파일링 방법을 사용하여 성능 데이터 수집
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로파일링하는 애플리케이션의 유형, 사용하려는 프로파일링 방법, 그리고 대상 애플리케이션이 네이티브 코드로 작성되었는지 아니면 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 코드로 작성되었는지에 따라 선택하는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로파일링 도구 명령줄 도구 및 옵션이 달라집니다.  
  
 이 항목에서 명령줄 절차 항목은 사용자가 선택하는 프로파일링 방법에 따라 구성되어 있습니다.  
  
## <a name="in-this-topic"></a>항목 내용  
 [샘플링 방법을 사용 하 여 성능 통계 수집](#BKMK_Using_the_sampling_method_to_collect_performance_statistics)  
  
 [계측 방법을 사용 하 여 자세한 타이밍 데이터 수집](#BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data)  
  
 [.NET 메모리 메서드를 사용 하 여 메모리 할당 및 개체 수명 데이터 수집](#BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data)  
  
 [동시성 방법을 사용하여 리소스 경합 및 스레드 작업 데이터 수집](#BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data)  
  
 [프로파일링 실행에 계층 상호 작용 데이터 추가](#BKMK_Adding_tier_interaction_data_to_a_profiling_run)  
  
## <a name="using-the-sampling-method-to-collect-performance-statistics"></a><a name="BKMK_Using_the_sampling_method_to_collect_performance_statistics"></a> 샘플링 방법을 사용하여 성능 통계 수집  
 프로파일링 도구의 샘플링 방법은 프로파일링 실행에서 지정된 간격으로 성능 데이터를 수집합니다. 샘플링 데이터는 CPU 바인딩 성능 문제에 대한 정보를 제공할 수 있으며, 애플리케이션의 성능 파악을 시작하는 효율적인 수단으로 활용할 수 있습니다.  
  
 프로파일러와 애플리케이션은 동시에 시작할 수도 있고 애플리케이션의 실행 중인 인스턴스에 프로파일러를 연결할 수도 있습니다.  
  
|Task|대상 애플리케이션 유형|  
|----------|-----------------------------|  
|**애플리케이션 시작**|-   [독립 실행형 응용 프로그램](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**실행 중인 프로세스에 연결**|-   [.NET Framework 독립 실행형 애플리케이션](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [기본 독립 실행형 애플리케이션](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [ASP.NET 웹 응용 프로그램](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [.NET 서비스](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [네이티브 서비스](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## <a name="using-the-instrumentation-method-to-collect-detailed-timing-data"></a><a name="BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data"></a> 계측 방법을 사용하여 자세한 타이밍 데이터 수집  
 프로파일링 도구의 계측 방법은 소프트웨어 프로브가 포함된 애플리케이션 이진 파일의 복사본에서 성능 데이터를 수집하여 성능 정보를 기록합니다. 계측 데이터는 계측된 각 함수의 시작과 끝, 그리고 계측된 함수에서 다른 함수로의 모든 호출에서 수집됩니다. 계측 방법은 디스크 사용량과 같은 I/O 문제를 통해 성능 문제를 파악하는 데 유용합니다.  
  
 [VInstr.exe](../profiling/vsinstr.md) 도구를 사용하여 계측된 이진 파일을 만듭니다. 프로파일러를 초기화하고 나면 대상 애플리케이션을 실행할 때 계측된 이진 파일에서 데이터가 자동으로 수집됩니다.  
  
 **대상 애플리케이션 유형**  
  
- [.NET Framework 독립 실행형 구성 요소](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
- [기본 독립 실행형 구성 요소](../profiling/how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
- [정적으로 컴파일된 ASP.NET 웹 애플리케이션](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
- [동적으로 컴파일된 ASP.NET 웹 애플리케이션](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
- [.NET 서비스](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
- [기본 서비스](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
## <a name="using-net-memory-methods-to-collect-memory-allocation-and-object-lifetime-data"></a><a name="BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data"></a> .NET 메모리 방법을 사용하여 메모리 할당 및 개체 수명 데이터 수집  
 프로파일링 도구의 .NET 메모리 방법을 사용하면 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]의 개체 수명에 대한 정보 및 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 메모리 할당 데이터를 수집할 수 있습니다.  
  
 프로파일러를 사용하여 대상 애플리케이션을 시작할 수 있고, 애플리케이션의 실행 중인 인스턴스에 프로파일러를 연결할 수 있으며, 애플리케이션의 계측된 버전을 만들어 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 메모리 데이터와 함께 상세한 타이밍 정보를 수집할 수 있습니다.  
  
|Task|대상 애플리케이션 유형|  
|----------|-----------------------------|  
|**애플리케이션 시작**|-   [독립 실행형.NET Framework 애플리케이션](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line.md)|  
|**실행 중인 프로세스에 연결**|-   [.NET Framework 독립 실행형 애플리케이션](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [ASP.NET 웹 응용 프로그램](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [.NET 서비스](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|  
|**계측 모듈**|-   [.NET Framework 독립 실행형 구성 요소](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line.md)<br />-   [정적으로 컴파일된 ASP.NET 웹 애플리케이션](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [동적으로 컴파일된 ASP.NET 웹 애플리케이션](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [.NET 서비스](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## <a name="using-the-concurrency-method-to-collect-resource-contention-and-thread-activity-data"></a><a name="BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data"></a> 동시성 방법을 사용 하 여 리소스 경합 및 스레드 작업 데이터 수집  
 프로파일링 도구의 동시성 방법을 사용하면 다중 스레딩 애플리케이션에서 리소스 경합 및 스레드/프로세스 작업 데이터를 수집할 수 있습니다.  
  
 프로파일러를 사용하여 애플리케이션을 시작할 수도 있고 애플리케이션의 실행 중인 인스턴스에 프로파일러를 연결할 수도 있습니다.  
  
|Task|대상 애플리케이션 유형|  
|----------|-----------------------------|  
|**애플리케이션 시작**|-   [독립 실행형.NET Framework 애플리케이션](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [독립 실행형 기본 애플리케이션](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**실행 중인 프로세스에 연결**|-   [.NET Framework 독립 실행형 애플리케이션](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [독립 실행형 기본 애플리케이션](/visualstudio/profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data?view=vs-2015)<br />-   [ASP.NET 웹 응용 프로그램](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [.NET 서비스](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [기본 서비스](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
## <a name="adding-tier-interaction-data-to-a-profiling-run"></a><a name="BKMK_Adding_tier_interaction_data_to_a_profiling_run"></a> 프로 파일링 실행에 계층 상호 작용 데이터 추가  
 프로파일링 실행에 계층 상호 작용 데이터를 추가하려면 명령줄 프로파일링 도구를 사용해서 특정 절차를 수행해야 합니다. [계층 상호 작용 데이터 수집](../profiling/adding-tier-interaction-data-from-the-command-line.md) 을 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [독립 실행형 응용 프로그램 프로 파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET 웹 응용 프로그램 프로 파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)
