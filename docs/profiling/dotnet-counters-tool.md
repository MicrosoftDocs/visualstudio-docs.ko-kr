---
title: dotnet 카운터 시각화 | Microsoft Docs
description: Visual Studio 성능 프로파일러에서 .NET 카운터 도구를 사용하는 방법을 알아봅니다.
ms.date: 12/7/2020
ms.topic: conceptual
helpviewer_keywords:
- dotnet, counters, profiling
author: sagar-shetty
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 7a09cc073b2886ab0d374bccaf8b85f3bb729dd7
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97905075"
---
# <a name="visualize-dotnet-counters-from-the-visual-studio-profiler"></a>Visual Studio 프로파일러에서 dotnet 카운터 시각화


.NET 카운터 도구를 사용하면 Visual Studio 프로파일러 내에서 바로 시간 경과에 따라 [dotnet 카운터](/dotnet/core/diagnostics/dotnet-counters)를 시각화할 수 있습니다.


> [!NOTE]
> .NET 카운터 도구는 Visual Studio 2019 버전 16.7 이상이 필요하며 .NET Core 3.0+를 대상으로 합니다.

## <a name="setup"></a>설치 프로그램

1. Visual Studio에서 성능 프로파일러를 엽니다(**Alt+F2** 또는 **디버그 -> 성능 프로파일러**).

2. **.NET 카운터** 확인란을 선택합니다.

   :::image type="content" source="../profiling/media/dotnet-counters-tool-selected.png" alt-text="카운터 도구 선택됨":::

3. **시작** 단추를 클릭하여 도구를 실행합니다.

도구 성능을 최적화하는 방법에 대한 자세한 내용은 [프로파일러 설정 최적화](../profiling/optimize-profiler-settings.md)를 참조하세요.


## <a name="understand-your-data"></a>데이터 이해

도구에서 처음에 데이터를 수집하면 [dotnet 카운터](/dotnet/core/diagnostics/dotnet-counters)의 라이브 값을 확인할 수 있습니다.

:::image type="content" source="../profiling/media/dotnet-counters-tool-collecting.png" alt-text="수집 중인 .NET 카운터 도구":::

카운터 이름 옆에 있는 확인란을 선택하여 카운터 그래프를 볼 수도 있습니다. 한 번에 여러 카운터의 그래프를 표시할 수 있습니다.


앱 실행 및 데이터 수집을 완료한 후에는 훨씬 더 자세한 보고서를 위한 컬렉션을 중지할 수 있습니다. 이렇게 하려면 **컬렉션 중지** 단추를 누릅니다.


보고서가 로드되면 완성된 보고서가 다음과 유사하게 표시됩니다.

:::image type="content" source="../profiling/media/dotnet-counters-tool-report.png" alt-text=".NET 카운터 도구 보고서":::

보고서에는 다음 값이 표시됩니다.

- Min - 선택한 시간 범위에서 해당 카운터의 최솟값입니다.
- Max - 선택한 시간 범위에서 해당 카운터의 최댓값입니다.
- Average - 선택한 시간 범위에서 해당 카운터의 평균 값입니다.

열 머리글을 마우스 오른쪽 단추로 클릭하고 머리글을 선택하여 테이블의 열을 필터링하거나 추가할 수 있습니다.

:::image type="content" source="../profiling/media/dotnet-counters-tool-columns.png" alt-text=".NET 카운터 도구 열":::

카운터 옆의 확인란을 선택하여 자세한 보고서에서 그래프를 볼 수도 있습니다. 테이블의 데이터는 기본적으로 수집된 추적 전체 기간의 값을 나타냅니다. 특정 시간 범위로 데이터를 필터링하려면 그래프를 클릭하여 끕니다.

:::image type="content" source="../profiling/media/dotnet-counters-tool-time-filtering.png" alt-text=".NET 카운터 도구 시간 필터링":::

테이블은 그래프에서 선택한 시간 관련 값으로 업데이트됩니다. 선택한 시간 범위를 전체 추적으로 다시 설정하려면 **선택 영역 지우기** 단추를 사용합니다.


## <a name="see-also"></a>참조

- [프로파일러 설정 최적화](../profiling/optimize-profiler-settings.md)
- [dotnet 카운터](/dotnet/core/diagnostics/dotnet-counters)
