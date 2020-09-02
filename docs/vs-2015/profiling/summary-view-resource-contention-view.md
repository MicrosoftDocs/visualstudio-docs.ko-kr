---
title: 요약 뷰 - 리소스 경합 뷰 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 6da57b83-7b42-4d7c-9aea-8e0a830faf6b
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 65f659b64b6a1e29e1e25ae344dd8033e631de09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157763"
---
# <a name="summary-view---resource-contention-view"></a>요약 뷰 - 리소스 경합 뷰
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

요약 뷰에는 스레드 또는 프로세스가 리소스 액세스를 대기하던 중 일시 중단된 애플리케이션의 이벤트에 대한 정보가 표시됩니다.  
  
 알림 링크 및 보고서 목록에 대한 설명을 비롯한 자세한 내용은 [요약 뷰](../profiling/summary-view.md)를 참조하세요.  
  
## <a name="timeline-graph"></a>시간 표시 막대 그래프  
 요약 뷰의 시간 표시 막대 그래프에는 프로파일링이 수행된 시간 동안 프로파일링된 애플리케이션의 경합 이벤트 수가 표시됩니다. 시간 표시 막대 그래프를 사용하여 보기를 선택한 시간 범위로 필터링할 수 있습니다. 자세한 내용은 [방법: 요약 시간 표시 막대에서 보고서 뷰 필터링](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)을 참조하세요.  
  
## <a name="most-contended-resources"></a>경합이 가장 많은 리소스  
 **경합이 가장 많은 리소스**에는 가장 많은 경합 이벤트가 발생한 애플리케이션의 리소스 목록이 표시됩니다. 리소스 이름을 클릭하여 경합 뷰를 표시할 수 있습니다. 경합 뷰에서는 리소스 경합의 자세한 시간 표시 막대가 스레드별로 제공됩니다.  
  
 **경합이 가장 많은 리소스**에는 각 리소스에 대해 다음 데이터가 포함됩니다.  
  
|열|Description|  
|------------|-----------------|  
|**이름**|리소스의 이름입니다.|  
|**경합 비율(%)**|이 리소스에 대해 경합이 발생한 프로파일링 데이터 내 모든 경합 이벤트의 백분율입니다.|  
  
## <a name="most-contended-thread"></a>경합이 가장 많은 스레드  
 **경합이 가장 많은 스레드**에는 경합 이벤트 수가 가장 많은 애플리케이션의 스레드 목록이 표시됩니다. 스레드 이름을 클릭하면 표시되는 경합 뷰에서는 리소스 경합의 자세한 시간 표시 막대가 스레드별로 제공됩니다.  
  
 **경합이 가장 많은 스레드**에는 각 스레드에 대해 다음 데이터가 포함됩니다.  
  
|열|Description|  
|------------|-----------------|  
|**ID**|스레드 식별자입니다.|  
|**이름**|스레드를 소유하는 프로세스의 이름입니다.|  
|**경합 비율(%)**|이 리소스에 대해 경합이 발생한 프로파일링 데이터 내 모든 경합 이벤트의 백분율입니다.|
