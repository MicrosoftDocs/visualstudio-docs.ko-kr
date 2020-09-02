---
title: 요약 뷰 - 계측 데이터 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5dc0b4195d33a7bf72d17681b6d71e78f1bacfe5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157771"
---
# <a name="summary-view---instrumentation-data"></a>요약 뷰 - 계측 데이터
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

요약 뷰에는 프로파일링 실행에서 성능상 가장 많은 비용이 소요된 함수에 대한 정보가 표시됩니다. 알림 링크 및 보고서 목록에 대한 설명을 비롯한 자세한 내용은 [요약 뷰](../profiling/summary-view.md)를 참조하세요.  
  
## <a name="timeline-graph"></a>시간 표시 막대 그래프  
 요약 뷰의 시간 표시 막대 그래프에는 프로파일링이 수행된 시간 동안 프로파일링된 애플리케이션의 프로세서(CPU) 사용률이 표시됩니다. 시간 표시 막대 그래프를 사용하여 보기를 선택한 시간 범위로 필터링할 수 있습니다. 자세한 내용은 [방법: 요약 시간 표시 막대에서 보고서 뷰 필터링](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)을 참조 하세요.  
  
## <a name="hot-path"></a>실행 부하 과다 경로  
 **실행 부하 과다 경로**에는 시간이 가장 많이 소요된 실행 경로가 표시됩니다. 함수를 클릭하면 해당 함수의 함수 정보 뷰를 표시할 수 있습니다. 함수에 대해 다른 뷰를 표시하려면 함수를 마우스 오른쪽 단추로 클릭하고 목록에서 뷰를 클릭합니다.  
  
 **실행 부하 과다 경로**에는 각 함수에 대해 다음 데이터가 표시됩니다.  
  
|열|Description|  
|------------|-----------------|  
|**이름**|함수의 이름입니다.|  
|**경과된 포괄 시간 비율(%)**|함수가 함수 본문과 자신이 호출한 함수의 코드를 실행하는 데 소요된 프로파일링 데이터 내 모든 시간의 백분율입니다.|  
|**경과된 전용 시간 비율(%)**|함수가 함수 본문의 코드를 실행하는 데 소요된 프로파일링 데이터 내 모든 시간의 백분율입니다. 해당 함수가 호출한 함수에서 소요된 시간은 포함되지 않습니다.|  
  
## <a name="functions-with-most-individual-work"></a>개별 작업이 가장 많은 함수  
 자신이 호출한 함수가 아니라 함수 자체의 본문에 있는 코드를 실행하는 데 가장 많은 시간을 사용한 함수의 목록입니다.  
  
 **개별 작업이 가장 많은 함수**에는 각 함수에 대해 다음 데이터가 포함됩니다.  
  
|열|Description|  
|------------|-----------------|  
|**이름**|함수의 이름입니다.|  
|**전용 시간 비율(%)**|함수가 함수 본문의 코드를 실행하는 데 소요된 프로파일링 데이터 내 모든 시간의 백분율입니다. 해당 함수가 호출한 함수에서 소요된 시간은 포함되지 않습니다.|  
  
## <a name="see-also"></a>관련 항목  
 [요약 뷰](../profiling/summary-view-sampling-data.md)   
 [요약 뷰](../profiling/summary-view-dotnet-memory-data.md)
