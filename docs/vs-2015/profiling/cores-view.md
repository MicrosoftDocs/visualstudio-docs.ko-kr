---
title: 코어 뷰 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cores
helpviewer_keywords:
- Concurrency Visualizer, Cores View
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 869980fe7bbb773d566dffd38088b003e3a97a3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145645"
---
# <a name="cores-view"></a>코어 뷰
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

코어 뷰에는 스레드 실행이 논리적 프로세서 코어에 매핑된 방법을 보여줍니다. 서버 애플리케이션을 작성할 때 이 뷰를 통해 스레드 선호도 또는 스레드 풀 관리를 사용하여 캐시 성능을 최적화할 수 있습니다. 또한 스레드 선호도를 사용해서 코어 간 마이그레이션 문제가 더 심각해질 수 있는 경우를 조사할 수 있습니다. 코어 뷰에는 그래프와 범례의 두 부분이 포함됩니다.  
  
 그래프에서 Y축에는 논리 코어가 표시되고 X축에는 시간이 표시됩니다. 그래프의 모든 스레드에는 시간 경과에 따라 코어 간 이동을 추적할 수 있도록 고유 색상이 포함됩니다. 범례 영역에서 스레드를 선택하면 이 그래프에서 스레드를 필터링할 수 있습니다.  
  
 범례 영역에는 그래프의 각 색상에 대한 항목이 포함됩니다. 각 항목은 스레드 색상과 이름, 코어 간 컨텍스트 전환 횟수, 총 컨텍스트 전환 횟수 및 코어 간 컨텍스트 전환 비율을 보여줍니다. 범례는 코어 간 컨텍스트 전환 횟수를 기준으로 내림차순으로 정렬됩니다. 표시된 시간 범위 중에 실행된 스레드만 나열됩니다.  확대/축소하거나 이동하면 목록이 업데이트됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [동시성 시각화 도우미](../profiling/concurrency-visualizer.md)   
 [사용률 뷰](../profiling/utilization-view.md)   
 [스레드 뷰](../profiling/threads-view-parallel-performance.md)
