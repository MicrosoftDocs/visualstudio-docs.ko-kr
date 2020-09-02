---
title: GPU 작업 그래프 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f4546c3be480349f3e2cb36f483fa8711bc2ac49
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434219"
---
# <a name="gpu-activity-graph"></a>GPU 작업 그래프
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

동시성 시각화 도우미에서 GPU 작업 그래프는 시간 경과에 따라 사용 중인 DirectX 엔진의 개수로 측정되는 시스템의 DirectX 작업 수준을 표시합니다.  그래프에는 사용된 특정 엔진이 표시되지 않습니다.  엔진은 GPU 작업을 처리 중일 때 사용 중인 것으로 간주됩니다.  
  
## <a name="gpu-activity-graph-colors"></a>GPU 작업 그래프 색상  
 녹색은 현재 프로세스에서 DirectX 엔진이 사용되었음을 나타냅니다.  
  
 밝은 회색은 시스템에서 다른 프로세스가 DirectX 엔진을 사용되었음을 나타냅니다. 다른 프로세스의 DirectX 엔진 사용을 줄이려면 시스템에서 실행되는 다른 프로세스 수를 줄입니다.  
  
 흰색은 시스템에서 사용하지 않는 DirectX 엔진의 가용성을 나타냅니다. 이러한 엔진은 이를 활용할 수 있는 더 많은 기회를 발견할 경우 프로세스에 사용할 수 있습니다. 일부 엔진은 특정 종류의 작업에만 사용할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [사용률 뷰](../profiling/utilization-view.md)
