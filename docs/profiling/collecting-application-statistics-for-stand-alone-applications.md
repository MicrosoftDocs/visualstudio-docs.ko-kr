---
title: '프로파일러 명령줄: 독립 실행형 앱 통계 수집'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- sampling profiling method
- profilng tools,sampling method
ms.assetid: be2dbdd0-fc88-45f9-a1d5-bcb4f64e17ad
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 150a1a010a33a3b4fcfe0954ec70db2ff4de7816
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808918"
---
# <a name="collect-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line"></a>프로파일러 명령줄을 사용하여 독립 실행형 애플리케이션에 대한 애플리케이션 통계 수집
이 섹션에서는 명령줄 도구에서 샘플링 방법을 사용하여 클라이언트(독립 실행형) 애플리케이션에 대한 성능 통계를 수집하기 위한 절차 및 옵션을 설명합니다.

> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. 또한 UWP 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.

## <a name="common-tasks"></a>일반 작업

|Task|관련 콘텐츠|
|----------|---------------------|
|**프로파일링을 사용하여 애플리케이션 시작**|-   [방법: 독립 실행형 애플리케이션을 시작하여 애플리케이션 통계 수집](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**실행 중인 .NET Framework 애플리케이션에 프로파일러 연결**|-   [방법: .NET Framework 애플리케이션에 프로파일러 연결 및 애플리케이션 통계 수집](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)|
|**실행 중인 C/C++ 애플리케이션에 프로파일러 연결**|-   [방법: 네이티브 애플리케이션에 프로파일러 연결 및 애플리케이션 통계 수집](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)|
|**계층 상호 작용 데이터 추가**|-   [계층 상호 작용 데이터 수집](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

## <a name="related-tasks"></a>관련 작업

### <a name="profile-stand-alone-applications"></a>독립 실행형 애플리케이션 프로파일링

|Task|관련 콘텐츠|
|----------|---------------------|
|**애플리케이션 계측**|-   [계측을 사용하여 자세한 타이밍 데이터 수집](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**.NET 메모리 할당 및 가비지 수집 데이터**|-   [.NET Framework 메모리 데이터 수집](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**리소스 경합 및 스레드 실행 데이터 수집**|-   [동시성 데이터 수집](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|

### <a name="profile-by-using-the-sampling-method"></a>샘플링 방법을 사용하여 프로파일링

|Task|관련 콘텐츠|
|----------|---------------------|
|**ASP.NET 웹 애플리케이션 프로파일링**|-   [샘플링을 사용하여 애플리케이션 통계 수집](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**서비스 프로파일링**|-   [샘플링을 사용하여 애플리케이션 통계 수집](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md) 샘플링 방법을 사용하여 Windows 서비스에서 성능 통계를 수집하는 방법을 설명합니다.|

### <a name="analyze-sampling-data-views-and-reports"></a>샘플링 데이터 뷰 및 보고서 분석
- [샘플링 방법 데이터 뷰](../profiling/profiler-sampling-method-data-views.md)
