---
title: CPU 사용률 그래프 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph
helpviewer_keywords:
- CPU Utilization GraphConcurrency Visualizer, CPU Utilization Graph
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8058995c8ae45c40f202aaa1e788891da3eb985d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180496"
---
# <a name="cpu-utilization-graph"></a>CPU 사용률 그래프
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

CPU 사용률 그래프에서는 시간 경과에 따른 응용 프로그램의 사용률 수준을 보여줍니다. x축은 추적의 기간을 나타내고 y축은 시스템의 논리 코어 수를 나타냅니다. 이 그래프에서는 특정 시간에 활성 상태인 코어를 구체적으로 보여주지는 않습니다. 예를 들어 특정 시간 동안 두 개의 코어가 각각 50% 용량으로 실행되는 경우 이 뷰에서는 하나의 논리 코어가 사용되고 있는 것으로 표시됩니다.  
  
## <a name="cpu-utilization-graph-colors"></a>CPU 사용률 그래프 색상  
  
- 녹색은 시스템에서 현재 프로세스의 논리적 코어 사용률을 나타냅니다.  
  
- 밝은 회색은 시스템에서 다른 프로세서의 논리적 코어 사용률을 나타냅니다. CPU 그래프에서 밝은 회색의 비율이 높으면 시스템에서 다른 프로세스의 작업량이 높고 해당 프로세스가 다른 프로세스에 의해 선점될 가능성이 높음을 나타냅니다. 다른 프로세스의 논리적 코어 사용을 줄이려면 시스템에서 실행되는 해당 프로세스 수를 줄입니다.  
  
- 짙은 회색은 시스템 프로세스의 논리적 코어 소비량을 나타냅니다. 이는 직접 제어할 수 없지만 현재 프로세스의 논리 코어 가용성이 영향을 받을 수 있으므로 이러한 논리 코어 소비 형태가 나타나는 경우를 알고 있으면 유용합니다.  
  
- 흰색은 시스템에서 사용되지 않는 논리 코어의 가용성을 나타냅니다. 병렬 처리의 기회가 더 많이 있는 경우 해당 코어를 프로세스에 사용할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [사용률 뷰](../profiling/utilization-view.md)   
 [평균 CPU 사용률](../profiling/average-cpu-utilization.md)
