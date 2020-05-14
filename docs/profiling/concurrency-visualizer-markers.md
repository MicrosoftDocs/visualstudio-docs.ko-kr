---
title: 동시성 시각화 도우미 표식 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markersui
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab5e4b65db5c3d96b16a68a7b8e21a2786b9110b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "63001055"
---
# <a name="concurrency-visualizer-markers"></a>동시성 시각화 도우미 표식
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

- [TPL(작업 병렬 라이브러리)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)

- [데이터 흐름](/dotnet/standard/parallel-programming/dataflow-task-parallel-library)

- [PLINQ(병렬 LINQ)](/dotnet/standard/parallel-programming/parallel-linq-plinq)

- [동시성 런타임](/cpp/parallel/concrt/concurrency-runtime)

- [시나리오 표식 지원](/previous-versions/visualstudio/visual-studio-2010/dd984115\(v\=vs.100\))

- [C++ AMP(C++ Accelerated Massive Parallelism)](/cpp/parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism)

  [고급 설정](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) 대화 상자의 표식 탭에서 여러 소스의 표식을 동시성 시각화 도우미에 표시할지 여부를 제어할 수 있으며, 중요도 및 범주에 따라 표식을 필터링할 수 있습니다.

## <a name="markers-from-eventsource"></a>EventSource의 표식
 동시성 시각화 도우미는 EventSource 이벤트도 표시할 수 있습니다.  자세한 내용은 [EventSource 이벤트를 표식으로 시각화](../profiling/visualizing-eventsource-events-as-markers.md)를 참조하세요.

## <a name="see-also"></a>참고 항목
- [플래그 표식](../profiling/flag-markers.md)
- [메시지 표식](../profiling/message-markers.md)
- [범위 표식](../profiling/span-markers.md)
- [EventSource 이벤트를 표식으로 시각화](../profiling/visualizing-eventsource-events-as-markers.md)