---
title: 계측을 사용하여 ASP.NET에 대한 타이밍 데이터 수집
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling tools,instrumentation method
- instrumentation profiling method
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: a73d81eaaef45a9ae97e733a8ae94805106a9ef8
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809637"
---
# <a name="collect-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>명령줄에서 프로파일러 계측 방법을 사용하여 ASP.NET 웹 애플리케이션에 대한 자세한 타이밍 데이터 수집
이 섹션에서는 **VSPerfCmd** 명령줄 도구 및 계측 방법을 사용하여 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 애플리케이션에 대한 자세한 성능 데이터를 수집하기 위한 절차 및 옵션을 설명합니다.

> [!NOTE]
> **VSPerfCmd** 도구를 통해 프로파일링 일시 중지 및 재개와 프로세서 및 Windows 성능 카운터의 추가 데이터 수집을 비롯하여 프로파일링 도구 기능에 완전히 액세스할 수 있습니다. 이 기능이 필요하지 않은 경우에는 **VSPerfASPNETCmd** 명령줄 도구를 사용할 수도 있습니다. [VSPerfCmd](../profiling/vsperfcmd.md) 명령줄 도구와 비교하면 환경 변수를 설정할 필요가 없으며, 컴퓨터를 다시 부팅하지 않아도 됩니다. 자세한 내용은 [VSPerfASPNETCmd를 사용한 빠른 웹 사이트 프로파일링](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)을 참조하세요.

## <a name="common-tasks"></a>일반 작업

|작업|관련 내용|
|----------|---------------------|
|**정적으로 컴파일된 이진 파일 프로파일링**|-   [방법: 정적으로 컴파일된 ASP.NET 애플리케이션 계측 및 자세한 타이밍 데이터 수집](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)|
|**동적으로 컴파일된 이진 파일 프로파일링**|-   [방법: 동적으로 컴파일된 ASP.NET 애플리케이션 계측 및 자세한 타이밍 데이터 수집](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)|

## <a name="related-tasks"></a>관련 작업

### <a name="profile-aspnet-web-applications"></a>ASP.NET 웹 애플리케이션 프로파일링

|작업|관련 내용|
|----------|---------------------|
|**샘플링 방법을 사용하여 프로파일링**|-   [샘플링을 사용하여 애플리케이션 통계 수집](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**메모리 할당 및 가비지 수집 프로파일링**|-   [메모리 데이터 수집](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**리소스 경합 및 스레드 작업 프로파일링**|-   [동시성 데이터 수집](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-by-using-the-instrumentation-method"></a>계측 방법을 사용하여 프로파일링

|작업|관련 내용|
|----------|---------------------|
|**독립 실행형(클라이언트) 애플리케이션 프로파일링**|-   [계측을 사용하여 자세한 타이밍 데이터 수집](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**서비스 프로파일링**|-   [계측을 사용하여 자세한 타이밍 데이터 수집](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|

### <a name="analyze-instrumentation-data-views-and-reports"></a>계측 데이터 뷰 및 보고서 분석
- [계측 방법 데이터 뷰](../profiling/instrumentation-method-data-views.md)
