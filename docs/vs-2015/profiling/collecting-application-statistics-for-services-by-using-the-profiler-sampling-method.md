---
title: 프로파일러 샘플링 방법을 사용하여 서비스에 대한 애플리케이션 통계 수집 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 07840ab2-3a92-4744-ac87-48b19e0ceecd
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3f556a039ab131a563a90010112009b39f4c981
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841494"
---
# <a name="collecting-application-statistics-for-services-by-using-the-profiler-sampling-method"></a>프로파일러 샘플링 방법을 사용하여 서비스에 대한 애플리케이션 통계 수집
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 섹션에서는 명령줄에서 샘플링 방법을 사용하여 Windows 서비스에 대한 성능 통계를 수집하기 위한 절차 및 옵션을 설명합니다.  
  
> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. Windows 스토어 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.  
  
## <a name="common-tasks"></a>일반 태스크  
  
|Task|관련 내용|  
|----------|---------------------|  
|**.NET 서비스에 프로파일러 연결**|-   [방법: .NET 서비스에 프로파일러를 연결하여 애플리케이션 통계 수집](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)|  
|**계층 상호 작용 데이터 추가**|-   [계층 상호 작용 데이터 수집](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**C/C++ 서비스에 프로파일러 연결**|-   [방법: 네이티브 서비스에 프로파일러를 연결하여 애플리케이션 통계 수집](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>관련 작업  
  
### <a name="profiling-windows-services"></a>Windows 서비스 프로파일링  
  
|Task|관련 내용|  
|----------|---------------------|  
|**계측 방법을 사용하여 프로파일링**|-   [계측을 사용 하 여 자세한 타이밍 데이터 수집](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**.NET 메모리 할당 및 가비지 수집 프로파일링**|-   [.NET 메모리 데이터 수집](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
|**리소스 경합 및 스레드 작업 프로파일링**|-   [동시성 데이터 수집](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### <a name="profiling-by-using-the-sampling-method"></a>샘플링 방법을 사용하여 프로파일링  
  
|Task|관련 내용|  
|----------|---------------------|  
|**독립 실행형(클라이언트) 애플리케이션 프로파일링**|-   [샘플링을 사용 하 여 응용 프로그램 통계 수집](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**ASP.NET 웹 애플리케이션 프로파일링**|-   [샘플링을 사용 하 여 응용 프로그램 통계 수집](/visualstudio/profiling/collecting-concurrency-data-for-an-aspnet-web-application?view=vs-2015)|  
  
### <a name="analyzing-sampling-data-views-and-reports"></a>샘플링 데이터 뷰 및 보고서 분석  
 [샘플링 방법 데이터 뷰](../profiling/profiler-sampling-method-data-views.md)
