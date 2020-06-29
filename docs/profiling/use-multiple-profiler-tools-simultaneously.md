---
title: 동시에 여러 프로파일러 도구 사용 | Microsoft Docs
ms.date: 4/29/2020
ms.topic: conceptual
helpviewer_keywords:
- Profiler, multiple tools
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 7844d81af02211d1c9f4e444c6367152e73392e9
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290970"
---
# <a name="using-multiple-profiler-tools-simultaneously"></a>동시에 여러 프로파일러 도구 사용

성능 프로파일러는 동일한 세션에서 여러 도구를 사용하여 성능 문제를 이해하는 데 도움을 주도록 설계되었습니다. [CPU 사용량](../profiling/cpu-usage.md), [.NET Async 도구](../profiling/analyze-async.md), [데이터베이스](../profiling/analyze-database.md) 도구와 같은 대부분의 성능 프로파일러 도구는 동시 실행을 지원합니다. 동일한 진단 세션에서 동시에 도구를 실행하려면 도구 옆의 확인란을 클릭한 다음 진단 세션을 시작합니다.

![진단 허브 모든 도구 선택됨](../profiling/media/diaghuballtoolsselected.png "진단 허브 모든 도구 선택됨")

>[!NOTE]
>[.NET 개체 할당](../profiling/dotnet-alloc-tool.md) 도구 등 일부 도구는 높은 오버헤드 또는 기타 기술적 제한으로 인해 다른 도구와 함께 실행할 수 없습니다.

## <a name="time-filtering"></a>시간 필터링 

분석하는 동안 도구 간에 시간 필터링 작업이 적용되므로 한 도구에서 정보를 사용하여 시간 범위를 좁히고 다른 도구에서 데이터를 필터링할 수 있습니다. 이 기능은 추적의 특정 지점에 대한 분석을 안내하고 애플리케이션의 상태를 이해하는 데 도움이 됩니다.

![진단 허브 시간 필터링](../profiling/media/diaghubtimefiltering.png "진단 허브 시간 필터링")

## <a name="see-also"></a>참조

- [프로파일러 설정 최적화](../profiling/optimize-profiler-settings.md)
- [디버거를 사용하거나 사용하지 않고 프로파일링 도구 실행](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [성능 데이터 수집 방법 이해](../profiling/understanding-performance-collection-methods-perf-profiler.md)
