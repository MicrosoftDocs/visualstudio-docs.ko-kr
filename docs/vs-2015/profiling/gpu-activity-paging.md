---
title: GPU 작업(페이징) | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5979ccf8cafedb849b7ae9f7af6b0b35096e624f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434165"
---
# <a name="gpu-activity-paging"></a>GPU 작업(페이징)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

스레드 탭의 **GPU 작업(페이징)** 세그먼트는 GPU가 페이징 요청을 처리한 시간을 나타냅니다.  세그먼트의 길이는 GPU가 DMA(직접 메모리 액세스) 페이징 패킷을 처리한 기간을 나타냅니다. 일반적으로 페이징 패킷은 CPU와 GPU 간의 메모리 전송과 연관됩니다.  
  
 GPU 페이징 세그먼트를 선택하면 **현재** 탭의 보고서에 처리된 DMA 패킷에 대한 정보가 표시됩니다. 여기에는 DirectX 엔진과 연결된 하드웨어 큐에서 대기한 시간, DMA 패킷을 전송한 프로세스, 패킷을 처리하는 데 필요한 시간이 포함됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [사용률 뷰](../profiling/utilization-view.md)
