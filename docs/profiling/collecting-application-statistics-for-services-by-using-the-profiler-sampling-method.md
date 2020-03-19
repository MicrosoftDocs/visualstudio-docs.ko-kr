---
title: 프로파일러 샘플링 방법을 사용하여 애플리케이션 통계 수집
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 07840ab2-3a92-4744-ac87-48b19e0ceecd
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 17217a51c58e1d30b6e6854ee9dbb0c1fb662a3a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779690"
---
# <a name="collect-application-statistics-for-services-by-using-the-profiler-sampling-method"></a>프로파일러 샘플링 방법을 사용하여 서비스에 대한 애플리케이션 통계 수집
이 섹션에서는 명령줄에서 샘플링 방법을 사용하여 Windows 서비스에 대한 성능 통계를 수집하기 위한 절차 및 옵션을 설명합니다.

> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. 또한 UWP 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.

## <a name="common-tasks"></a>일반 작업

|Task|관련 내용|
|----------|---------------------|
|**.NET 서비스에 프로파일러 연결**|-   [방법: .NET 서비스에 프로파일러를 연결하여 애플리케이션 통계 수집](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)|
|**계층 상호 작용 데이터 추가**|-   [계층 상호 작용 데이터 수집](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**C/C++ 서비스에 프로파일러 연결**|-   [방법: 네이티브 서비스에 프로파일러를 연결하여 애플리케이션 통계 수집](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>관련 작업

### <a name="profile-windows-services"></a>Windows 서비스 프로파일링

|Task|관련 내용|
|----------|---------------------|
|**계측 방법을 사용하여 프로파일링**|-   [계측을 사용하여 자세한 타이밍 데이터 수집](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**.NET 메모리 할당 및 가비지 수집 프로파일링**|-   [.NET 메모리 데이터 수집](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|
|**리소스 경합 및 스레드 작업 프로파일링**|-   [동시성 데이터 수집](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="profile-by-using-the-sampling-method"></a>샘플링 방법을 사용하여 프로파일링

|Task|관련 내용|
|----------|---------------------|
|**독립 실행형(클라이언트) 애플리케이션 프로파일링**|-   [샘플링을 사용하여 애플리케이션 통계 수집](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**ASP.NET 웹 애플리케이션 프로파일링**|-   [샘플링을 사용하여 애플리케이션 통계 수집](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>샘플링 데이터 뷰 및 보고서 분석
- [샘플링 방법 데이터 뷰](../profiling/profiler-sampling-method-data-views.md)
