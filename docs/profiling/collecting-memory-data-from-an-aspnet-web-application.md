---
title: 프로파일러 명령줄 - ASP.NET 웹앱 메모리 데이터 가져오기
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- .NET memory profiling method
- profiling tools,.NET memory method
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 690b3cd03d245281b488f2bb2b77ebdebedd00c2
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809416"
---
# <a name="collect-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>프로파일러 명령줄을 사용하여 ASP.NET 웹 애플리케이션의 메모리 데이터 수집
이 섹션에서는 **VSPerfCmd** 명령줄 도구를 사용하여 ASP.NET 웹 애플리케이션에 대한 메모리 할당 및 개체 수명 데이터를 수집하기 위한 절차 및 옵션을 설명합니다.

> [!NOTE]
> **VSPerfCmd** 도구를 통해 프로파일링 일시 중지 및 재개와 프로세서 및 Windows 성능 카운터의 추가 데이터 수집을 비롯하여 프로파일링 도구 기능에 완전히 액세스할 수 있습니다. 이 기능이 필요하지 않은 경우에는 **VSPerfASPNETCmd** 명령줄 도구를 사용할 수도 있습니다. [VSPerfCmd](../profiling/vsperfcmd.md) 명령줄 도구와 비교하면 환경 변수를 설정할 필요가 없으며, 컴퓨터를 다시 부팅하지 않아도 됩니다. 자세한 내용은 [VSPerfASPNETCmd를 사용한 빠른 웹 사이트 프로파일링](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)을 참조하세요.

## <a name="common-tasks"></a>일반 작업

|Task|관련 내용|
|----------|---------------------|
|**실행 중인 ASP.NET 애플리케이션에 프로파일러 연결**|-   [방법: ASP.NET 웹 애플리케이션에 프로파일러를 연결하여 메모리 데이터 수집](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|
|**정적으로 컴파일된 이진 파일 계측**|-   [방법: 정적으로 컴파일된 ASP.NET 애플리케이션 계측 및 메모리 데이터 수집](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)|
|**동적으로 컴파일된 이진 파일 계측**|-   [방법: 동적으로 컴파일된 ASP.NET 애플리케이션 계측 및 메모리 데이터 수집](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)|

## <a name="related-tasks"></a>관련 작업

### <a name="profile-aspnet-web-applications"></a>ASP.NET 웹 애플리케이션 프로파일링

|Task|관련 내용|
|----------|---------------------|
|**샘플링 방법을 사용하여 프로파일링**|-   [샘플링을 사용하여 애플리케이션 통계 수집](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**계측 방법을 사용하여 프로파일링**|-   [계측을 사용하여 자세한 타이밍 데이터 수집](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**리소스 경합 및 스레드 작업 프로파일링**|-   [동시성 데이터 수집](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-net-framework-memory-data"></a>.NET Framework 메모리 데이터 프로파일링

|Task|관련 내용|
|----------|---------------------|
|**독립 실행형(클라이언트) 애플리케이션 프로파일링**|-   [.NET Framework 메모리 데이터 수집](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**서비스 프로파일링**|-   [.NET 메모리 데이터 수집](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="analyze-net-memory-data-views-and-reports"></a>.NET 메모리 데이터 뷰 및 보고서 분석
- [.NET 메모리 데이터 뷰](../profiling/dotnet-memory-data-views.md)

## <a name="reference"></a>참조
- [명령줄 프로파일링 도구 참조](../profiling/command-line-profiling-tools-reference.md)
