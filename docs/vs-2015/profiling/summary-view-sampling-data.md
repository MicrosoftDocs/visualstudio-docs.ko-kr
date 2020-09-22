---
title: 요약 뷰 - 샘플링 데이터 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method, Summary view
- Summary view
ms.assetid: 79056873-2985-40be-9112-cdbc26a65156
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c759922fcd28ce0b686745fc917c02f41762cae4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841994"
---
# <a name="summary-view---sampling-data"></a>요약 뷰 - 샘플링 데이터
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

요약 뷰에는 프로파일링 실행에서 성능상 가장 많은 비용이 소요된 함수에 대한 정보가 표시됩니다. 알림 링크 및 보고서 목록에 대한 설명을 비롯한 자세한 내용은 [요약 뷰](../profiling/summary-view.md)를 참조하세요.  
  
> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. Windows 스토어 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.  
  
## <a name="timeline-graph"></a>시간 표시 막대 그래프  
 요약 뷰의 시간 표시 막대 그래프에는 프로파일링이 수행된 시간 동안 프로파일링된 애플리케이션의 프로세서(CPU) 사용률 백분율이 표시됩니다. 시간 표시 막대 그래프를 사용하여 보기를 선택한 시간 범위로 필터링할 수 있습니다. 자세한 내용은 [방법: 요약 시간 표시 막대에서 보고서 뷰 필터링](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)을 참조 하세요.  
  
## <a name="hot-path"></a>실행 부하 과다 경로  
 **실행 부하 과다 경로**에는 대부분의 샘플이 수집된 실행 경로가 표시됩니다. 함수를 클릭하면 해당 함수의 함수 정보 뷰를 표시할 수 있습니다. 함수에 대해 다른 뷰를 표시하려면 함수를 마우스 오른쪽 단추로 클릭하고 목록에서 뷰를 클릭합니다.  
  
 **실행 부하 과다 경로**에는 각 함수에 대해 다음 데이터가 표시됩니다.  
  
|열|Description|  
|------------|-----------------|  
|**이름**|함수의 이름입니다.|  
|**포괄 샘플 비율(%)**|이 함수 또는 이 함수가 호출한 함수가 실행 중일 때 발생한 모든 샘플의 비율입니다.|  
|**전용 샘플 비율(%)**|함수가 함수 본문의 코드를 실행할 때 발생한 모든 샘플의 비율입니다. 이 함수가 호출한 함수에서 수집된 샘플은 포함되지 않습니다.|  
  
## <a name="functions-doing-most-individual-work"></a>개별 작업이 가장 많은 함수  
 **개별 작업이 가장 많은 함수** 목록에는 프로파일링 실행에서 전용 샘플의 수가 가장 많은 함수가 표시됩니다. 전용 샘플은 샘플을 수집할 때 함수가 자체 코드를 실행하고 있으면 함수에 할당됩니다. 샘플을 수집할 때 함수가 다른 함수를 호출하고 있으면 해당 함수에 전용 샘플이 할당되지 않습니다. 전용 샘플 수가 많은 경우 함수 자체에 상당한 시간이 소요된 것입니다.  
  
 함수를 클릭하면 해당 함수의 함수 정보 뷰를 표시할 수 있습니다. 함수에 대해 다른 뷰를 표시하려면 함수를 마우스 오른쪽 단추로 클릭하고 목록에서 뷰를 클릭합니다.  
  
 **개별 작업이 가장 많은 함수**에는 각 함수에 대해 다음 데이터가 포함됩니다.  
  
|열|Description|  
|------------|-----------------|  
|**이름**|함수의 이름입니다.|  
|**전용 샘플 비율(%)**|함수가 함수 본문의 코드를 실행 중일 때 수집된 프로파일링 실행 내 모든 샘플의 백분율입니다. 이 함수가 호출한 함수가 실행 중일 때 수집된 샘플은 백분율에서 제외됩니다.|  
  
## <a name="see-also"></a>참고 항목  
 [요약 뷰](../profiling/summary-view-dotnet-memory-data.md)   
 [요약 뷰](../profiling/summary-view-instrumentation-data.md)
