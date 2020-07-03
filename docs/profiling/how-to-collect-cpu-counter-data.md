---
title: 방법 - CPU 카운터 데이터 수집 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.cpucounters
helpviewer_keywords:
- profiling tools, using portable CPU counters
- performance tools, portable CPU counters
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c500316bd53ddce8bf731876e5963e6ef253bb27
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85330922"
---
# <a name="how-to-collect-cpu-counter-data"></a>방법: CPU 카운터 데이터 수집

CPU 이벤트 카운터는 하드웨어 관련 성능 데이터를 수집하는 데 사용됩니다. 이 문서에서는 계측 프로파일링 방법을 사용하는 경우 이벤트 카운터 데이터를 수집하는 방법을 보여 줍니다.

두 가지 형식의 CPU 카운터 이벤트가 발생합니다.

- Portable events - 특정 CPU에 관계없이 수집할 수 있는 CPU 이벤트입니다.

- Platform events - 특정 CPU에 연결된 CPU 이벤트입니다.

  Portable events에는 Instructions Retired 및 Non Halted Cycles 등의 일반적인 이벤트, CPU 버퍼 이벤트, 분기 이벤트, L2 캐시 이벤트가 포함됩니다. 사용 가능한 플랫폼 이벤트 카운터는 프로세서 제조업체에서 결정합니다.

  이식 가능한 카운터와 플랫폼 카운터 간에 이벤트 범주를 공유할 수 있습니다. 예를 들어 다음 데이터 범주는 두 형식에 공통적인 경우가 많습니다.

- 메모리 이벤트.

- 프런트 엔드 이벤트.

- 분기 이벤트.

  프로파일러에서 두 가지 방법으로 성능 카운터 데이터를 수집할 수 있습니다.

- 계측을 통해 프로파일링할 경우 하나 이상의 카운터에서 데이터를 수집합니다.

- 샘플링을 통해 프로파일링할 경우 카운터 이벤트를 샘플링 간격으로 지정합니다. 자세한 내용은 [방법: 샘플링 이벤트 선택](../profiling/how-to-choose-sampling-events.md)을 참조하세요.

## <a name="to-collect-cpu-performance-counter-data-when-you-profile-by-instrumentation"></a>계측을 통해 프로파일링할 경우 CPU 성능 카운터 데이터를 수집하려면

1. 성능 세션 **속성 페이지**에서 **CPU 카운터**를 클릭합니다.

2. **CPU 카운터 수집** 확인란을 선택합니다.

3. 수집할 샘플 이벤트를 찾을 때까지 **사용 가능한 성능 카운터** 트리를 확장합니다.

4. 수집할 각 이벤트에 대해 이벤트를 선택하고 오른쪽 화살표를 클릭하여 **선택한 카운터** 목록에 이벤트를 추가합니다.

    > [!NOTE]
    > **사용 가능한 성능 카운터**는 **CPU 카운터 수집** 확인란을 선택한 경우에만 사용하도록 설정됩니다.

## <a name="see-also"></a>참조

[성능 세션 구성](../profiling/configuring-performance-sessions.md)
[성능 세션 속성](../profiling/performance-session-properties.md)
[CPU 및 Windows 카운터](../profiling/cpu-and-windows-counters.md)
[방법: 샘플링 이벤트 선택](../profiling/how-to-choose-sampling-events.md)
