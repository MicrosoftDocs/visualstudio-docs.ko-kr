---
title: 명령줄 프로파일링 방법을 사용하여 성능 데이터 가져오기
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b30aa723ea3014aec2bd05d4bd204b9427b3c218
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779976"
---
# <a name="use-profiling-methods-to-collect-performance-data-from-the-command-line"></a>명령줄에서 프로파일링 방법을 사용하여 성능 데이터 수집
프로파일링하는 애플리케이션의 유형, 사용하려는 프로파일링 방법, 그리고 대상 애플리케이션이 네이티브 코드로 작성되었는지 아니면 .NET Framework 코드로 작성되었는지에 따라 선택하는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구 명령줄 도구 및 옵션이 달라집니다.

 이 항목에서 명령줄 절차 항목은 사용자가 선택하는 프로파일링 방법에 따라 구성되어 있습니다.

## <a name="use-the-sampling-method-to-collect-performance-statistics"></a>샘플링 방법을 사용하여 성능 통계 수집
 프로파일링 도구의 샘플링 방법은 프로파일링 실행에서 지정된 간격으로 성능 데이터를 수집합니다. 샘플링 데이터는 CPU 바인딩 성능 문제에 대한 정보를 제공할 수 있으며, 애플리케이션의 성능 파악을 시작하는 효율적인 수단으로 활용할 수 있습니다.

 프로파일러와 애플리케이션은 동시에 시작할 수도 있고 애플리케이션의 실행 중인 인스턴스에 프로파일러를 연결할 수도 있습니다.

|Task|대상 애플리케이션 유형|
|----------|-----------------------------|
|**애플리케이션 시작**|-   [독립 실행형 애플리케이션](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**실행 중인 프로세스에 연결**|-   [.NET Framework 독립 실행형 애플리케이션](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)<br />-   [기본 독립 실행형 애플리케이션](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)<br />-   [ASP.NET 웹 애플리케이션](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [.NET 서비스](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [기본 서비스](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="use-the-instrumentation-method-to-collect-detailed-timing-data"></a>계측 방법을 사용하여 자세한 타이밍 데이터 수집
 프로파일링 도구의 계측 방법은 소프트웨어 프로브가 포함된 애플리케이션 이진 파일의 복사본에서 성능 데이터를 수집하여 성능 정보를 기록합니다. 계측 데이터는 계측된 각 함수의 시작과 끝, 그리고 계측된 함수에서 다른 함수로의 모든 호출에서 수집됩니다. 계측 방법은 디스크 사용량과 같은 I/O 문제를 통해 성능 문제를 파악하는 데 유용합니다.

 [VInstr.exe](../profiling/vsinstr.md) 도구를 사용하여 계측된 이진 파일을 만듭니다. 프로파일러를 초기화하고 나면 대상 애플리케이션을 실행할 때 계측된 이진 파일에서 데이터가 자동으로 수집됩니다.

 **대상 애플리케이션 유형**

- [.NET Framework 독립 실행형 구성 요소](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-timing-data.md)

- [기본 독립 실행형 구성 요소](../profiling/how-to-instrument-a-native-component-and-collect-timing-data.md)

- [정적으로 컴파일된 ASP.NET 웹 애플리케이션](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)

- [동적으로 컴파일된 ASP.NET 웹 애플리케이션](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)

- [.NET 서비스](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

- [기본 서비스](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

## <a name="use-net-memory-methods-to-collect-memory-allocation-and-object-lifetime-data"></a>.NET 메모리 방법을 사용하여 메모리 할당 및 개체 수명 데이터 수집
 프로파일링 도구의 .NET 메모리 방법을 사용하면 .NET Framework의 개체 수명에 대한 정보 및 .NET 메모리 할당 데이터를 수집할 수 있습니다.

 프로파일러를 사용하여 대상 애플리케이션을 시작할 수 있고, 애플리케이션의 실행 중인 인스턴스에 프로파일러를 연결할 수 있으며, 애플리케이션의 계측된 버전을 만들어 .NET Framework 메모리 데이터와 함께 상세한 타이밍 정보를 수집할 수 있습니다.

|Task|대상 애플리케이션 유형|
|----------|-----------------------------|
|**애플리케이션 시작**|-   [독립 실행형.NET Framework 애플리케이션](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-memory-data.md)|
|**실행 중인 프로세스에 연결**|-   [.NET Framework 독립 실행형 애플리케이션](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-app-to-collect-memory-data.md)<br />-   [ASP.NET 웹 애플리케이션](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [.NET 서비스](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|
|**계측 모듈**|-   [.NET Framework 독립 실행형 구성 요소](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-memory-data.md)<br />-   [정적으로 컴파일된 ASP.NET 웹 애플리케이션](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)<br />-   [동적으로 컴파일된 ASP.NET 웹 애플리케이션](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)<br />-   [.NET 서비스](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|

## <a name="use-the-concurrency-method-to-collect-resource-contention-and-thread-activity-data"></a>동시성 방법을 사용하여 리소스 경합 및 스레드 작업 데이터 수집
 프로파일링 도구의 동시성 방법을 사용하면 다중 스레딩 애플리케이션에서 리소스 경합 및 스레드/프로세스 작업 데이터를 수집할 수 있습니다.

 프로파일러를 사용하여 애플리케이션을 시작할 수도 있고 애플리케이션의 실행 중인 인스턴스에 프로파일러를 연결할 수도 있습니다.

|Task|대상 애플리케이션 유형|
|----------|-----------------------------|
|**애플리케이션 시작**|-   [독립 실행형.NET Framework 애플리케이션](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)<br />-   [독립 실행형 기본 애플리케이션](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**실행 중인 프로세스에 연결**|-   [.NET Framework 독립 실행형 애플리케이션](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)<br />-   [기본 독립 실행형 애플리케이션](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)<br />-   [ASP.NET 웹 애플리케이션](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [.NET 서비스](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [기본 서비스](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="add-tier-interaction-data-to-a-profiling-run"></a>프로파일링 실행에 계층 상호 작용 데이터 추가
 프로파일링 실행에 계층 상호 작용 데이터를 추가하려면 명령줄 프로파일링 도구를 사용해서 특정 절차를 수행해야 합니다. [계층 상호 작용 데이터 수집](../profiling/adding-tier-interaction-data-from-the-command-line.md) 참조

## <a name="see-also"></a>참고 항목
- [독립 실행형 애플리케이션 프로파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET 웹 애플리케이션 프로파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)
