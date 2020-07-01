---
title: ASP.NET 웹앱용 통계 수집 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling tools, sampling method
- sampling profling method
ms.assetid: f8383ab1-eb49-4d3f-8608-d8b4d51a81be
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 8f353f551b3b524cfa49fb2cb638c261dcde660d
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85331917"
---
# <a name="collect-statistics-for-aspnet-web-apps"></a>ASP.NET 웹앱에 대한 통계를 수집합니다.

이 섹션에서는 **VSPerfASPNETCmd** 및 **VSPerfCmd** 명령줄 도구 및 샘플링 프로파일링 방법을 사용하여 ASP.NET 웹 애플리케이션에 대한 성능 통계를 수집하기 위한 절차 및 옵션을 설명합니다.

> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. 또한 UWP 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.

> [!NOTE]
> **VSPerfCmd** 도구를 통해 프로파일링 일시 중지 및 재개와 프로세서 및 Windows 성능 카운터의 추가 데이터 수집을 비롯하여 프로파일링 도구 기능에 완전히 액세스할 수 있지만 이 기능이 필요하지 않은 경우에는 **VSPerfASPNETCmd** 명령줄 도구를 사용해야 합니다. **VSPerfASPNETCmd** 명령줄 도구는 독립 실행형 프로파일러를 사용하여 ASP.NET 웹 사이트를 프로파일링할 때 선호하는 방법입니다. [VSPerfCmd](../profiling/vsperfcmd.md) 명령줄 도구와 비교하면 환경 변수를 설정할 필요가 없으며, 컴퓨터를 다시 부팅하지 않아도 됩니다. 자세한 내용은 [VSPerfASPNETCmd를 사용한 빠른 웹 사이트 프로파일링](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)을 참조하세요.

## <a name="common-tasks"></a>일반 작업

|Task|관련 내용|
|----------|---------------------|
|**ASP.NET 애플리케이션에 프로파일러 연결**|-   [방법: ASP.NET 웹 애플리케이션에 프로파일러를 연결하여 애플리케이션 통계 수집](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>관련 작업

### <a name="profile-aspnet-web-applications"></a>ASP.NET 웹 애플리케이션 프로파일링

|Task|관련 내용|
|----------|---------------------|
|**계측 방법을 사용하여 프로파일링**|-   [계측을 사용하여 자세한 타이밍 데이터 수집](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**메모리 할당 및 가비지 수집 프로파일링**|-   [메모리 데이터 수집](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**리소스 경합 및 스레드 작업 프로파일링**|-   [동시성 데이터 수집](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="sample-method"></a>샘플 메서드

|Task|관련 내용|
|----------|---------------------|
|**독립 실행형(클라이언트) 애플리케이션 프로파일링**|-   [샘플링을 사용하여 애플리케이션 통계 수집](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|-   **서비스 프로파일링**|-   [샘플링을 사용하여 애플리케이션 통계 수집](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>샘플링 데이터 뷰 및 보고서 분석
- [샘플링 방법 데이터 뷰](../profiling/profiler-sampling-method-data-views.md)
