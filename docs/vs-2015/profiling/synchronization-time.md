---
title: 동기화 시간 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 218f333f97e8252993f87893238a0f51f964d6c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151394"
---
# <a name="synchronization-time"></a>동기화 시간
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

타임라인의 이러한 세그먼트는 동기화로 분류되는 차단 시간과 관련이 있습니다. 스레드가 동기화에서 차단된 것으로 표시되면 이러한 것들 중 하나가 포함됩니다.  
  
- 스레드 실행으로 `EnterCriticalSection()` 또는 `WaitForSingleObject()` 등의 잘 알려진 스레드 동기화 API에 대한 호출이 발생했을 수 있습니다.  
  
- API 일치 알고리즘은 완전히 포괄적일 수 없으므로 다른 범주에 매핑될 수 있는 일부 API는 호출 스택의 프레임이 이 범주에 매핑된 기본 커널 차단 기본 형식에 결국 도달했기 때문에 동기화로 나타날 수도 있습니다.  
  
  스레드 차단 이벤트에 대한 근본적인 원인을 이해하려면 차단 호출 스택 및 프로필 보고서를 신중하게 검사합니다.  
  
## <a name="see-also"></a>관련 항목  
 [스레드 뷰](../profiling/threads-view-parallel-performance.md)
