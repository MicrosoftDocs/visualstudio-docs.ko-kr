---
title: 실행 시간(스레드 뷰) | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b4306e030c2f48d87b12ba6338a847dc9e9aa892
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179038"
---
# <a name="execution-time-threads-view"></a>실행 시간(스레드 뷰)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

스레드가 시스템의 논리 코어에서 활발히 작업을 수행할 경우 스레드 뷰 타임라인의 이러한 세그먼트는 실행 시간을 나타냅니다.  
  
 스레드 상태가 변경되면 커널 컨텍스트 스위치 이벤트를 통해 감지됩니다. ETW(Windows용 이벤트 추적)는 밀리초마다 샘플 스택을 캡처합니다. 매우 짧은 녹색 세그먼트에서는 샘플이 수집되지 않을 수 있습니다. 따라서 일부 짧은 실행 세그먼트는 호출 스택을 표시하지 않을 수 있습니다.  
  
 실행 세그먼트를 클릭하면 동시성 시각화 도우미가 클릭 위치에 가장 가까운 샘플 스택을 표시합니다. 해당 샘플 스택의 위치는 검은색 화살표 또는 캐럿으로 표시되고 샘플 스택이 **현재** 탭에 나타납니다.  
  
 현재 뷰에서 모든 실행 세그먼트에 대한 기존 방식의 샘플링 프로필을 보려면 표시되는 시간 표시 막대 프로필에서 **실행**을 클릭합니다.  
  
## <a name="see-also"></a>관련 항목  
 [실행 프로필 보고서](../profiling/execution-profile-report.md)   
 [스레드 뷰](../profiling/threads-view-parallel-performance.md)
