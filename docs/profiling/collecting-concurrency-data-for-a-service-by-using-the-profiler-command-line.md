---
title: 프로파일러 명령줄을 사용하여 서비스에 대한 동시성 데이터 가져오기
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0bd4eb54a5356f7b98846191fb2a9a5f26cc4235
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85331934"
---
# <a name="collect-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>프로파일러 명령줄을 사용하여 서비스에 대한 동시성 데이터 수집
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구의 동시성 방법을 사용하면 CPU 사용률, 스레드 경합, 스레드 마이그레이션, 동기화 지연, 겹친 IO 영역 및 기타 시스템 이벤트를 보여 주는 리소스 경합 데이터 및 스레드 작업 데이터를 수집할 수 있습니다.

> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. 또한 UWP 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.

## <a name="common-tasks"></a>일반 작업

|Task|관련 내용|
|----------|---------------------|
|**실행 중인.NET 서비스에 연결**|-   [방법: .NET 서비스에 프로파일러를 연결하여 동시성 데이터 수집](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|
|**계층 상호 작용 데이터 추가**|-   [계층 상호 작용 데이터 수집](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**실행 중인 C/C++ 서비스에 연결**|-   [방법: 네이티브 서비스에 프로파일러를 연결하여 동시성 데이터 수집](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="related-tasks"></a>관련 작업

### <a name="profile-windows-services"></a>Windows 서비스 프로파일링

|Task|관련 내용|
|----------|---------------------|
|**샘플링 방법을 사용하여 프로파일링**|-   [샘플링을 사용하여 애플리케이션 통계 수집](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|
|**계측 방법을 사용하여 프로파일링**|-   [계측을 사용하여 자세한 타이밍 데이터 수집](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Profile.NET 메모리 할당 및 가비지 수집**|-   [.NET 메모리 데이터 수집](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="profile-concurrency-data"></a>동시성 데이터 프로파일링

|Task|관련 내용|
|----------|---------------------|
|**독립 실행형 애플리케이션 프로파일링**|-   [동시성 데이터 수집](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|
|**ASP.NET 웹 애플리케이션 프로파일링**|-   [동시성 데이터 수집](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>동시성 데이터 뷰 및 보고서 분석
- [리소스 경합 데이터 뷰](../profiling/resource-contention-data-views.md)

- [Concurrency 시각화 도우미](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>참조
- [명령줄 프로파일링 도구 참조](../profiling/command-line-profiling-tools-reference.md)
