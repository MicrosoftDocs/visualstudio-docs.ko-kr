---
title: 채널 관리 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.tools.managechannels
helpviewer_keywords:
- Concurrency Visualizer, Manage Channels
ms.assetid: 507b06e9-bb56-4a72-8fd5-f91f958da6fc
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 894378d6648139b7ec2b587eb0066a5725af7a71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843420"
---
# <a name="manage-channels"></a>채널 관리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

동시성 시각화 도우미의 **스레드 뷰**에서는 특정 패턴을 검사할 수 있도록 프로세스에 대한 채널을 구성할 수 있습니다. 채널을 정렬하고, 이를 위 또는 아래로 이동하고, 표시하거나 숨길 수 있습니다.  
  
## <a name="sort-by"></a>정렬 기준  
 정렬 기준 컨트롤을 사용하면 현재 확대/축소 수준에 따라 서로 다른 기준으로 스레드를 정렬할 수 있습니다. 이 기능은 특히 특정 패턴을 찾고 있는 경우에 유용합니다. 다음과 같은 기준에 따라 정렬할 수 있습니다.  
  
|조건|정의|  
|--------------|----------------|  
|Start Time|시작 시간으로 스레드를 정렬합니다. 기본 정렬 순서입니다.|  
|종료 시간|종료 시간을 기준으로 스레드를 정렬합니다.|  
|실행|실행에 소요된 시간의 백분율을 기준으로 스레드를 정렬합니다.|  
|동기화|동기화에 소요된 시간의 백분율을 기준으로 스레드를 정렬합니다.|  
|I/O|I/O(데이터 읽기 및 쓰기)에 소요된 시간의 백분율을 기준으로 스레드를 정렬합니다.|  
|절전|중지에 소요된 시간의 백분율을 기준으로 스레드를 정렬합니다.|  
|Paging|페이징에 소요된 시간의 백분율을 기준으로 스레드를 정렬합니다.|  
|선점|선점에 소요된 시간의 백분율을 기준으로 스레드를 정렬합니다.|  
|UI 처리|사용자 인터페이스 처리에 소요된 시간의 백분율을 기준으로 스레드를 정렬합니다.|  
  
## <a name="move-selected-channel-up-or-down"></a>선택한 채널을 위 또는 아래로 이동  
 이러한 컨트롤을 사용해서 목록에서 채널을 위 또는 아래로 이동할 수 있습니다. 예를 들어 특정 패턴 또는 크로스 스레드 관계를 조사할 수 있도록 관련 채널을 서로 옆에 배치할 수 있습니다.  
  
## <a name="move-selected-channel-to-top-or-bottom"></a>선택한 채널을 맨 위 또는 맨 아래로 이동  
 특정 패턴을 조사하거나 다른 패턴을 조사할 때의 과정 중에 일부 패턴을 이동할 수 있도록 목록의 맨 위 또는 맨 아래로 선택한 채널을 이동할 수 있습니다.  
  
## <a name="hide-selected-channels"></a>선택한 채널 숨기기  
 채널을 숨기려면 이 컨트롤을 선택합니다. 예를 들어 스레드가 관리되는 프로세스의 수명 주기 동안 100% 동기화된 경우 다른 스레드를 분석할 때 이를 숨길 수 있습니다.  
  
> [!NOTE]
> 스레드를 숨기면 이 스레드는 활성 범례 및 프로필 보고서에 표시되는 계산 시간에서도 제거됩니다.  
  
## <a name="show-all-channels"></a>모든 채널 표시  
 하나 이상의 채널을 숨기면 이 컨트롤이 활성화됩니다. 이 컨트롤을 선택하면 숨겨진 모든 요소가 표시되고 시간 계산에 반환됩니다.  
  
## <a name="move-markers-to-top"></a>표식을 맨 위로 이동  
 추적에 표식 이벤트가 포함된 경우, 이 명령을 사용해서 표식 채널을 타임라인의 맨 위로 이동할 수 있습니다. 상대적인 순서는 보존됩니다.  
  
## <a name="group-markers-by-thread"></a>스레드로 표식 그룹화  
 추적에 표식 이벤트가 포함된 경우 이 명령을 사용해서 표식 이벤트를 생성한 스레드에 따라 표식 채널을 그룹화할 수 있습니다.  디스크 채널은 채널 목록의 맨 위로 이동되고, GPU 채널은 맨 아래로 이동됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [확대/축소 컨트롤 (스레드 뷰)](../profiling/zoom-control-threads-view.md)   
 [측정 모드 켜기/끄기](../profiling/measure-mode-on-off.md)   
 [스레드 뷰](../profiling/threads-view-parallel-performance.md)
