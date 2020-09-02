---
title: 선점 시간 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fd209f65464126650106eb4509cd3de39ad8c25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198070"
---
# <a name="preemption-time"></a>선점 시간
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

타임라인의 이러한 세그먼트는 선점 시간으로 분류되는 차단 시간과 관련이 있습니다. 이 범주는 다음과 같은 이유 중 하나로 스레드가 해제됨을 의미합니다.  
  
- 스케줄러가 더 높은 우선 순위 스레드를 사용하여 해당 스레드를 대체했습니다.  
  
- 스레드의 실행 퀀텀이 만료되었고 다른 스레드를 실행할 준비가 되었습니다.  
  
  이 시간 동안 스레드는 동시성 시각화 도우미가 선점 시간으로 계산하는 커널 대기 이유로 인해 차단되었습니다. 선점 시간 세그먼트는 스레드가 논리 코어 외부로 밀려날 때 시작되고 스레드가 실행을 다시 시작할 때 종료됩니다.  
  
  선점된 세그먼트에 대한 도구 설명에는 선점 시간을 야기한 프로세스 또는 스레드의 이름이 표시됩니다. 그러나 인계를 받은 프로세스 또는 스레드가 선점된 기간 동안 실제로 실행되었다는 의미는 아닙니다.  
  
## <a name="see-also"></a>관련 항목  
 [스레드 뷰](../profiling/threads-view-parallel-performance.md)
