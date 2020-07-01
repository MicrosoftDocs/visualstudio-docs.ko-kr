---
title: 프로파일러 명령줄을 사용하여.NET Framework 메모리 데이터 가져오기
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 7bce69e2-407c-4342-8516-641586968928
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 62a55c36cd634b9451ad3796e5866d1e3a89b6a2
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85331724"
---
# <a name="collect-net-framework-memory-data-by-using-the-profiler-command-line"></a>프로파일러 명령줄을 사용하여 .NET Framework 메모리 데이터 수집

이 섹션에서는 명령줄 도구에서 샘플링 방법을 사용하여 .NET 클라이언트(독립 실행형) 애플리케이션에 대한 메모리 할당 및 개체 수명 데이터를 수집하기 위한 절차 및 옵션을 설명합니다.

## <a name="common-tasks"></a>일반 작업

|Task|관련 콘텐츠|
|----------|---------------------|
|**애플리케이션 시작 및 .NET 메모리 프로파일링**|-   [방법: 프로파일러를 통해 .NET Framework 애플리케이션을 시작하여 메모리 데이터 수집](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-memory-data.md)|
|**.NET 애플리케이션에 프로파일러 연결**|-   [방법: .NET Framework 애플리케이션에 프로파일러를 연결하여 메모리 데이터 수집](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-app-to-collect-memory-data.md)|
|**애플리케이션을 계측하여 .NET 메모리 데이터 수집**|-   [방법: 프로파일러를 사용하여 독립 실행형 .NET Framework 구성 요소 계측 및 메모리 데이터 수집](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-memory-data.md)|

## <a name="related-tasks"></a>관련 작업

### <a name="profile-stand-alone-applications"></a>독립 실행형 애플리케이션 프로파일링

|Task|관련 콘텐츠|
|----------|---------------------|
|**샘플링 방법을 사용하여 프로파일링**|-   [샘플링을 사용하여 애플리케이션 통계 수집](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**계측 방법을 사용하여 프로파일링**|-   [계측을 사용하여 자세한 타이밍 데이터 수집](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**리소스 경합 및 스레드 작업 프로파일링**|-   [동시성 데이터 수집](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|
|**계층 상호 작용 데이터 추가**|-   [계층 상호 작용 데이터 수집](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

### <a name="profile-net-memory-data"></a>.NET 메모리 데이터 프로파일링

|Task|관련 콘텐츠|
|----------|---------------------|
|**ASP.NET 애플리케이션 프로파일링**|-   [메모리 데이터 수집](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**서비스 프로파일링**|-   [.NET 메모리 데이터 수집](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="analyze-net-memory-data-views-and-reports"></a>.NET 메모리 데이터 뷰 및 보고서 분석
- [.NET 메모리 데이터 뷰](../profiling/dotnet-memory-data-views.md)

## <a name="reference"></a>참조
- [명령줄 프로파일링 도구 참조](../profiling/command-line-profiling-tools-reference.md)
