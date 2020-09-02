---
title: 독립 실행형 애플리케이션의 명령줄 프로파일링 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profillng tools,stand-alone applications
- profling stand-alone applications
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f4b2b78f7187b7a49b78312a1105a2af884fda3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186633"
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>독립 실행형 애플리케이션의 명령줄 프로파일링
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 섹션에서는 명령줄에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로파일링 도구를 사용하여 독립 실행형(클라이언트) 애플리케이션의 성능 데이터를 수집하기 위한 절차 및 옵션을 설명합니다.  
  
## <a name="common-tasks"></a>일반 태스크  
  
|Task|관련 콘텐츠|  
|----------|---------------------|  
|**애플리케이션 통계 수집:** 샘플링 방법을 사용하여 성능 통계를 수집합니다. 샘플링 데이터는 CPU 사용률 문제를 분석하고 애플리케이션의 일반적인 성능 특성을 이해하는 데 유용합니다.|-   [샘플링을 사용 하 여 응용 프로그램 통계 수집](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**자세한 타이밍 데이터 수집:** 계측 방법을 사용하여 자세한 타이밍 정보를 수집합니다. 계측 데이터는 I/O 문제 분석 및 애플리케이션 시나리오의 세부적인 분석에 유용합니다.|-   [계측을 사용 하 여 자세한 타이밍 데이터 수집](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**.NET 메모리 데이터 수집:** 샘플링 또는 계측을 사용하여 할당된 개체의 크기 및 개수를 보여 주는 .NET 메모리 할당 데이터를 수집합니다. 또한 각 가비지 수집 세대에서 회수된 개체의 크기 및 수를 보여 주는 개체 수명 데이터를 수집할 수 있습니다.|-   [.NET Framework 메모리 데이터 수집](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**동시성 데이터 수집:** 동시성 방법을 사용하여 CPU 사용률, 스레드 경합, 스레드 마이그레이션, 동기화 지연, 겹친 I/O 영역 및 기타 시스템 이벤트를 보여 주는 리소스 경합 데이터 및 스레드 작업 데이터를 수집할 수 있습니다.|-   [동시성 데이터 수집](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**계층 상호 작용 데이터 추가:** 애플리케이션에서 Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스에 실행하는 동기 ADO.NET 호출에 대한 성능 데이터를 추가할 수 있습니다. 프로파일링 실행에 계층 상호 작용 데이터를 추가하려면 명령줄 프로파일링 도구를 사용해서 특정 절차를 수행해야 합니다.|-   [계층 상호 작용 데이터 수집](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**사용해 보기:** 단계별 절차에 따라 샘플링 또는 계측 방법을 사용하여 샘플 클라이언트 애플리케이션을 프로파일링합니다.|-   [연습: 샘플링을 사용 하 여 명령줄 프로 파일링](../profiling/walkthrough-command-line-profiling-using-sampling.md)<br />-   [연습: 계측을 사용 하 여 명령줄 프로 파일링](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)|  
  
## <a name="related-tasks"></a>관련 작업  
  
|Task|관련 내용|  
|----------|---------------------|  
|**ASP.NET 애플리케이션 프로파일링**|-   [ASP.NET 웹 응용 프로그램 프로 파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)|  
|**서비스 프로파일링**|-   [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)|
