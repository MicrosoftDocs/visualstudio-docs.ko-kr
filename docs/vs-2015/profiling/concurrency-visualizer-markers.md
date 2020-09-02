---
title: 동시성 시각화 도우미 표식 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markersui
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 43b6115c45f9583b90711ef030834da662106f08
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704361"
---
# <a name="concurrency-visualizer-markers"></a>동시성 시각화 도우미 표식
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

동시성 시각화 도우미에서 표식은 응용 프로그램의 이벤트를 나타내는 아이콘입니다.  일반적으로 애플리케이션은 애플리케이션에서의 단계 또는 발생 작업을 지정하기 위해 이러한 이벤트를 생성합니다.  이벤트는 응용 프로그램에서 생성되거나 응용 프로그램에서 사용되는 라이브러리 및 런타임에 의해 생성될 수 있습니다.  
  
## <a name="kinds-of-markers"></a>표식 종류  
 동시성 시각화 도우미는 애플리케이션 이벤트를 나타내기 위해 플래그, 메시지 및 범위의 세 가지 표식을 사용합니다.  
  
1. *플래그*를 사용하여 앱에서 특정 시점을 나타낼 수 있습니다.  예를 들어 플래그를 사용하면 변수 값이 특정 임계값에 도달한 시점 또는 예외가 throw된 시점을 나타낼 수 있습니다.  
  
2. *메시지*도 특정 시점을 표시하지만 메시지는 장기적인 추적을 위해 사용할 수 있습니다.  예를 들어 로그 파일에 무엇이 덤프되었더라도 지금 메시지 호출에 래핑하여 동시성 시각화 도우미에서 이를 추적하고 볼 수 있습니다. 또한 동시성 시각화 도우미를 사용해서 이 데이터를 CSV 파일로 내보낼 수 있습니다.  
  
3. *범위*는 여러 단계 중 한 단계와 같이 앱에서의 시간 간격을 나타냅니다.  
  
## <a name="marker-linkage-to-threads"></a>스레드에 표식 링크  
 표식을 생성하는 각 스레드에는 별도의 타임라인 채널이 포함됩니다.  표식 이벤트를 생성하는 스레드의 ID는 표식 채널의 설명 옆에 표시됩니다.  표식 채널의 왼쪽에 표시되는 ID는 현재 프로세스의 다른 스레드 ID와 일치합니다.  
  
## <a name="marker-importance"></a>표식 중요도  
 표식의 네 가지 중요도 수준은 낮음, 보통, 높음 및 중요입니다.  표식의 소스는 중요도 수준을 기준으로 필터링할 수 있습니다.  예를 들어 중요도 수준이 보통 또는 중요인 특정 소스의 표식만 보려면 [고급 설정](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) 대화 상자에서 필터를 구성할 수 있습니다. 표식의 중요도는 해당 도구 설명 및 [표식 보고서](../profiling/markers-report.md)에 표시됩니다.  
  
## <a name="marker-category"></a>표식 범주  
 표식 범주는 동일한 소스에서 시작되는 표식 이벤트의 그룹을 나타냅니다.  동시성 시각화 도우미는 색상을 사용해서 여러 범주의 플래그 및 범위를 구분합니다. 범주를 사용해서 특정 이벤트 공급자의 표식 이벤트를 필터링하도록 동시성 시각화 도우미를 구성할 수 있습니다.  [고급 설정](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) 대화 상자에서 필터를 구성할 수 있습니다.  
  
## <a name="known-sources-of-markers"></a>표식의 알려진 소스  
 공급자가 특정 제약 조건을 준수하는 한 모든 ETW 공급자는 표식을 생성할 수 있습니다. 표식에 대해 추가 이벤트 소스를 수신하도록 동시성 시각화 도우미를 구성할 수 있습니다. 기본적으로 다음과 같은 이벤트 소스를 수신합니다.  
  
- [동시성 시각화 도우미 SDK](../profiling/concurrency-visualizer-sdk.md)  
  
- [TPL(작업 병렬 라이브러리)](https://msdn.microsoft.com/library/b8f99f43-9104-45fd-9bff-385a20488a23)  
  
- [데이터 흐름](https://msdn.microsoft.com/library/643575d0-d26d-4c35-8de7-a9c403e97dd6)  
  
- [PLINQ(병렬 LINQ)](https://msdn.microsoft.com/library/3d4d0cd3-bde4-490b-99e7-f4e41be96455)  
  
- [동시성 런타임](https://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)  
  
- [시나리오 표식 지원](https://msdn.microsoft.com/e3b55bc2-b451-4214-ae00-0c7f5a5baec8)  
  
- [C++ AMP(C++ Accelerated Massive Parallelism)](https://msdn.microsoft.com/library/e27824cb-3167-409b-8c3f-a0e476d8f349)  
  
  [고급 설정](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) 대화 상자의 표식 탭에서 여러 소스의 표식을 동시성 시각화 도우미에 표시할지 여부를 제어할 수 있으며, 중요도 및 범주에 따라 표식을 필터링할 수 있습니다.  
  
## <a name="markers-from-eventsource"></a>EventSource의 표식  
 동시성 시각화 도우미는 EventSource 이벤트도 표시할 수 있습니다.  자세한 내용은 [EventSource 이벤트를 표식으로 시각화](../profiling/visualizing-eventsource-events-as-markers.md)를 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [플래그 표식](../profiling/flag-markers.md)   
 [메시지 표식](../profiling/message-markers.md)   
 [범위 표식](../profiling/span-markers.md)   
 [EventSource 이벤트를 표식으로 시각화](../profiling/visualizing-eventsource-events-as-markers.md)
