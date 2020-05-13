---
title: 서비스의 명령줄 프로파일링 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling toos,services
- profiling services
ms.assetid: f0d62318-b0e8-49c6-9a30-9f7a6adef2f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b20835eaf8b81bd64bd90aa75d2efb32975a7c53
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772833"
---
# <a name="command-line-profiling-of-services"></a>서비스의 명령줄 프로파일링
이 섹션에서는 명령줄에서 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구를 사용하여 Windows 서비스에 대한 성능 데이터를 수집하기 위한 절차 및 옵션을 설명합니다.

> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. 또한 UWP 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.

## <a name="common-tasks"></a>일반 작업

| Task | 관련 내용 |
| - | - |
| **애플리케이션 통계 수집:** 샘플링 방법을 사용하여 성능 통계를 수집합니다. 샘플링 데이터는 CPU 사용률 문제를 분석하고 애플리케이션의 일반적인 성능 특성을 이해하는 데 유용합니다. | -   [샘플링을 사용하여 애플리케이션 통계 수집](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md) |
| **자세한 타이밍 데이터 수집:** 계측 방법을 사용하여 자세한 타이밍 정보를 수집합니다. 계측 데이터는 IO 문제 분석 및 애플리케이션 시나리오의 세부적인 분석에 유용합니다. | -   [계측을 사용하여 자세한 타이밍 데이터 수집](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md) |
| **.NET 메모리 데이터 수집:** 샘플링 또는 계측을 사용하여 할당된 개체의 크기 및 개수를 보여 주는 .NET 메모리 할당 데이터를 수집합니다. 또한 각 가비지 수집 세대에서 회수된 개체의 크기 및 수를 보여 주는 개체 수명 데이터를 수집할 수 있습니다. | -   [.NET 메모리 데이터 수집](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md) |
| **동시성 데이터 수집:** 동시성 방법을 사용하여 CPU 사용률, 스레드 경합, 스레드 마이그레이션, 동기화 지연, 겹친 IO 영역 및 기타 시스템 이벤트를 보여 주는 리소스 경합 데이터 및 스레드 작업 데이터를 수집할 수 있습니다. | -   [동시성 데이터 수집](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md) |
| **계층 상호 작용 데이터 추가:** 서비스에서 Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] 데이터베이스에 실행하는 동기 ADO.NET 호출에 대한 성능 데이터를 추가할 수 있습니다. | -   [계층 상호 작용 데이터 수집](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>관련 작업

|Task|관련 내용|
|----------|---------------------|
|**독립 실행형(클라이언트) 애플리케이션 프로파일링**|-   [독립 실행형 애플리케이션 프로파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**ASP.NET 애플리케이션 프로파일링**|-   [ASP.NET 웹 애플리케이션 프로파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
