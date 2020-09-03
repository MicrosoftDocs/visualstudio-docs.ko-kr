---
title: 동시성 시각화 도우미 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.viewnavigation
- vs.cv.overview
- vs.cv.performance.gettingstarted
- vs.cv.gettingstarted
helpviewer_keywords:
- Concurrency Visualizer, Concurrency Visualizer
ms.assetid: ae5879a0-1e1a-455a-ba72-148e57f59289
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e7061acabbe5ce18ff6e1f210fe0003bdaf88980
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "82586818"
---
# <a name="concurrency-visualizer"></a>동시성 시각화 도우미
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

참고]
> 동시성 시각화 도우미는 Visual Studio의 선택적 확장입니다. 다음 링크에서 동시성 시각화 도우미와 동시성 시각화 수집 도구를 다운로드하세요.  
> 
> - [동시성 시각화 도우미](https://visualstudiogallery.msdn.microsoft.com/a6c24ce9-beec-4545-9261-293061436ee9) 확장을 다운로드합니다.  
>   - [Visual Studio 2015에 대 한 Concurrency 시각화 수집 도구](https://www.microsoft.com/download/details.aspx?id=49103)를 다운로드 합니다.  
> 
>   [동시성 시각화 도우미 명령줄 유틸리티(CVCollectionCmd.exe)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)를 사용하면 명령줄에서 추적을 수집하여 Visual Studio 2015용 동시성 시각화 도우미에서 확인할 수 있습니다. 이 도구는 Visual Studio가 설치되어 있지 않은 컴퓨터에서도 사용할 수 있습니다.  
  
 동시성 시각화 도우미를 사용하여 다중 스레드 앱이 어떻게 작업을 수행하는지 확인할 수 있습니다. 동시성 시각화 도우미의 뷰에서는 프로그램의 스레드와 시스템 전체의 일시적 관계를 보여 주는 그래픽, 표 및 텍스트 형식의 데이터를 제공합니다. 동시성 시각화 도우미를 사용하여 성능 병목 지점, 불충분한 CPU 사용률, 스레드 경합, 코어 스레드 간 마이그레이션, 동기화 지연, DirectX 동작, 겹쳐 있는 I/O 영역 및 기타 정보를 찾을 수 있습니다. 뷰에서는 항상 그래픽 출력을 호출 스택 및 소스 코드에 연결하여 실행 가능한 데이터를 제공합니다.  
  
 동시성 시각화 도우미는 [Windows용 이벤트 추적](https://msdn.microsoft.com/library/bb968803(VS.85).aspx) 기능에 의존합니다.  
  
> [!NOTE]
> 동시성 시각화 도우미는 웹 프로젝트를 지원하지 않습니다.  
  
## <a name="related-topics"></a>관련 항목  
  
|제목|설명|  
|-----------|-----------------|  
|[사용률 뷰](../profiling/utilization-view.md)|모든 프로세서의 시스템 작업을 보고 분석하는 방법에 대해 설명합니다.|  
|[스레드 뷰](../profiling/threads-view-parallel-performance.md)|프로그램의 스레드 간 상호 작용을 분석하는 방법에 대해 설명합니다.|  
|[코어 뷰](../profiling/cores-view.md)|코어 간의 스레드 마이그레이션을 분석하는 방법에 대해 설명합니다.|  
|[잘못 동작 하는 다중 스레드 응용 프로그램의 일반 패턴](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md)|몇 가지 일반적인 패턴을 설명하고 이러한 패턴이 동시성 시각화 도우미에서 어떻게 나타나는지 보여 줍니다.|  
|[Visual Studio에서 병렬 개발 블로그](https://docs.microsoft.com/archive/blogs/visualizeparallel/)|동시성 시각화 도우미에 대한 팁과 유용한 정보를 제공합니다.|  
|[성능 보고서 뷰](../profiling/performance-report-views.md)|Visual Studio 프로파일링 도구의 보고서 및 뷰에 대한 참조 정보를 제공합니다.|  
|[동시성 시각화 도우미 SDK](../profiling/concurrency-visualizer-sdk.md)|동시성 시각화 도우미에서 추가 정보를 표시하도록 소스 코드를 계측하는 방법을 설명합니다.|  
|[동시성 시각화 도우미 명령줄 유틸리티(CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|동시성 시각화 도우미 명령줄 유틸리티(CVCollectionCmd.exe)를 사용하여 Visual Studio가 설치되지 않은 컴퓨터에서 추적 정보를 수집 및 처리하는 방법을 설명합니다.|  
  
## <a name="see-also"></a>관련 항목  
 [프로파일링 도구](../profiling/profiling-tools.md)
