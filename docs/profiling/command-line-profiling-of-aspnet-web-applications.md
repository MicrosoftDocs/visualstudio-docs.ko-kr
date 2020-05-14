---
title: ASP.NET 웹 애플리케이션의 명령줄 프로파일링 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: aa184667e5d569bc2662052a29b25bfea6e470a7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779573"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>ASP.NET 웹 애플리케이션의 명령줄 프로파일링
이 섹션에서는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 명령줄에서 프로파일링 도구를 사용하여 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 애플리케이션의 성능 데이터를 수집하기 위한 절차 및 옵션을 설명합니다.

> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. 또한 UWP 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.

## <a name="common-tasks"></a>일반 작업

| 작업 | 관련 내용 |
| - | - |
| **쉽게 기본 ASP.NET 프로파일링 데이터 수집:** **VSPerfASPNETCmd** 도구를 사용하여 **VSPerfCmd**에 필요한 구성 요구 사항 및 IIS(인터넷 정보 서비스) 재시작 없이 샘플링, 계측, .NET 메모리, 경합 또는 계층 상호 작용 데이터를 수집합니다. **VSPerfASPNETCmd**에서는 추가 데이터를 수집하거나 데이터 수집을 제어할 수 없습니다. **참고:**  **VSPerfASPNETCmd**는 ASP.NET 웹 사이트를 프로파일링하기 위해 독립 실행형 프로파일러를 사용할 수 있는 기본 도구입니다. | -   [VSPerfASPNETCmd를 사용한 빠른 웹 사이트 프로파일링](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) |
| **애플리케이션 통계 수집:** 샘플링 메서드를 사용하여 성능 통계를 수집합니다. 샘플링 데이터는 CPU 사용량 문제를 분석하고 애플리케이션의 일반적인 성능 특성을 이해하는 데 유용합니다. | -   [샘플링을 사용하여 애플리케이션 통계 수집](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md) |
| **자세한 타이밍 데이터 수집:** 계측 방법을 사용하여 자세한 타이밍 정보를 수집합니다. 계측 데이터는 IO 문제 분석 및 애플리케이션 시나리오의 세부적인 분석에 유용합니다. | -   [계측을 사용하여 자세한 타이밍 데이터 수집](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md) |
| **.NET 메모리 데이터 수집:** 샘플링 또는 계측을 사용하여 할당된 개체의 크기 및 개수를 보여주는 .NET 메모리 할당 데이터를 수집합니다. 또한 각 가비지 수집 세대에서 회수된 개체의 크기 및 수를 보여 주는 개체 수명 데이터를 수집할 수 있습니다. | -   [메모리 데이터 수집](../profiling/collecting-memory-data-from-an-aspnet-web-application.md) |
| **동시성 데이터 수집:** 동시성 방법을 사용하여 리소스 경합 데이터를 수집합니다. **참고:**  웹 애플리케이션에 대해서는 스레드 작업 및 시각화 데이터를 수집할 수 없습니다. | -   [동시성 데이터 수집](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md) |
| **계층 상호 작용 데이터 추가:** [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 애플리케이션에서 Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] 데이터베이스에 실행하는 동기 [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] 호출에 대한 성능 데이터를 추가할 수 있습니다. | -   [계층 상호 작용 데이터 수집](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>관련 작업

|작업|관련 내용|
|----------|---------------------|
|**독립 실행형(클라이언트) 애플리케이션 프로파일링**|-   [독립 실행형 애플리케이션 프로파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**서비스 프로파일링**|-   [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)|
