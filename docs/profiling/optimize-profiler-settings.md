---
title: 프로파일러 설정 최적화 | Microsoft Docs
ms.date: 4/29/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, improve performance
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 1ef802958817b43dd66973db66a80d328454aa83
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85329252"
---
# <a name="optimizing-profiler-settings"></a>프로파일러 설정 최적화

Visual Studio의 성능 프로파일러 및 진단 도구 창에는 도구의 전반적인 성능에 영향을 주는 다양한 설정이 있습니다. 일부 설정을 변경하면 분석을 신속하게 실행할 수 있거나 도구에서 결과를 처리하는 동안 추가 대기 시간이 발생할 수 있습니다. 다음은 특정 설정과 성능에 미치는 영향에 대한 요약입니다.

## <a name="symbol-settings"></a>기호 설정

디버거 옵션(**디버그 > 옵션 > 기호**)에 있는 기호 설정은 도구에서 결과를 생성하는 데 걸리는 시간에 상당한 영향을 줍니다. 기호 서버를 활성화하거나 **_NT_SYMBOL_PATH**를 사용하면 프로파일러가 보고서에서 로드된 각 모듈에 대해 기호를 요청합니다. 현재, 프로파일러는 자동 기호 로드 기본 설정에 관계없이 항상 모든 기호를 자동으로 로드합니다.

![기호 로드 페이지](../profiling/media/symbolloading.png "기호 로드")

기호 로드 진행률은 **진단 도구** 제목 아래의 **출력** 창에서 볼 수 있습니다.

![기호 로드 진행률](../profiling/media/symbolloadingprogress.png "기호 로드 진행률")

다운로드가 완료되면 기호가 캐시되어 향후의 분석 속도는 향상되지만 여전히 파일을 로드하고 분석해야 합니다. 기호를 로드하여 분석 속도가 느려지는 경우 기호 서버를 비활성화하고 기호 캐시를 삭제합니다. 대신, 로컬로 빌드된 기호를 프로젝트에 사용합니다.

## <a name="show-external-code"></a>외부 코드 표시

**성능 프로파일러** 및 **진단 도구** 창에 포함된 대부분의 도구에는 사용자 코드와 외부 코드의 개념이 있습니다. 사용자 코드는 열려 있는 솔루션 또는 열려 있는 작업 영역에서 빌드된 모든 코드입니다. 외부 코드는 그 외의 모든 코드입니다. **외부 코드 표시** 설정을 사용하지 않도록 유지하거나 **내 코드만 표시** 설정을 사용하도록 유지하면 도구가 외부 코드를 하나의 첫 번째 수준 프레임으로 집계하여 결과를 표시하는 데 필요한 처리를 크게 줄일 수 있습니다. 그러면 사용자는 데이터를 최소한으로 처리하면서 속도 저하를 초래한 외부 코드에서 호출된 항목을 확인할 수 있습니다. 가능하면 **외부 코드 표시**를 사용 안 함으로 유지하고 솔루션 또는 작업 영역이 분석하고 있는 diagsession에 대해 열려 있도록 합니다.

## <a name="trace-duration"></a>추적 기간

더 작은 기간을 프로파일링하면 데이터가 줄어들고, 따라서 분석 속도가 빨라집니다. 일반적으로 5분 이하의 성능 데이터로 추적을 제한하는 것이 좋습니다. [CPU 사용량](../profiling/cpu-usage.md) 도구와 같은 일부 도구에서는 도구를 실행하는 동안 데이터 수집을 일시 중지하여 분석하려는 시나리오로 수집되는 데이터 양을 제한할 수 있습니다.

## <a name="sampling-frequency"></a>샘플링 빈도

[CPU 사용량](../profiling/cpu-usage.md) 도구 및 [NET 개체 할당](../profiling/dotnet-alloc-tool.md) 도구와 같은 특정 도구에서는 샘플링 빈도를 조정할 수 있습니다. 이 샘플링 빈도를 높이면 더 정확하게 측정할 수 있지만 생성되는 데이터의 양이 늘어납니다. 일반적으로 특정 문제를 조사하는 경우를 제외하면 이 설정을 기본 속도로 그대로 두는 것이 좋습니다.

![진단 허브 속성 페이지](../profiling/media/diaghubpropertiespage.png "진단 허브 속성 페이지")

## <a name="see-also"></a>참조

- [디버거를 사용하거나 사용하지 않고 프로파일링 도구 실행](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [동시에 여러 프로파일러 도구 사용](../profiling/use-multiple-profiler-tools-simultaneously.md)
- [성능 데이터 수집 방법 이해](../profiling/understanding-performance-collection-methods-perf-profiler.md)
