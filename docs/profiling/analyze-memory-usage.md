---
title: 메모리 사용량 분석
ms.custom: seodec18
ms.date: 01/02/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43126f4bba8afc50fc5c1e4cf6a3b9a67c6f340c
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233058"
---
# <a name="analyze-memory-usage"></a>메모리 사용량 분석

메모리 누수 및 비효율적인 메모리 사용을 찾기 위해 디버거 통합 메모리 사용량 진단 도구 및 .NET 개체 할당 도구나 사후 분석 메모리 사용량 도구와 같은 성능 프로파일러의 도구를 사용할 수 있습니다.

메모리 사용량 도구를 통해 관리되는 메모리 및 네이티브 메모리 힙의 *스냅샷* 을 하나 이상 만들 수 있습니다. .NET, ASP.NET, 네이티브 또는 혼합 모드(.NET 및 네이티브) 앱의 스냅샷을 수집할 수 있습니다. **메모리 사용량** 도구는 열려 있는 Visual Studio 프로젝트, 설치된 Microsoft Store 앱에서 실행하거나 실행 중인 앱 또는 프로세스에 연결할 수 있습니다. 로컬이나 원격 머신에서 또는 시뮬레이터나 에뮬레이터에서 도구를 실행할 수 있습니다. 디버깅을 사용하거나 사용하지 않고 **메모리 사용량** 도구를 실행할 수 있습니다. 자세한 내용은 [디버거를 사용하거나 사용하지 않고 프로파일링 도구 실행](../profiling/running-profiling-tools-with-or-without-the-debugger.md)을 참조하세요. 디버거에서 메모리 프로파일링을 설정하거나 해제할 수 있으며 메모리 사용량에 대한 개체별 분석을 볼 수 있습니다. 실행이 일시 중지된 경우 메모리 사용량 결과를 볼 수 있습니다(예: 중단점에서).

**.NET 개체 할당 도구**를 사용하면 .NET 코드의 할당 패턴과 비정상 요소를 식별하는 데 도움이 됩니다. 이 도구는 사후 분석 도구로만 실행됩니다.

메모리 분석 도구를 사용하는 방법을 설명하는 자세한 지침은 [메모리 사용량 분석](../profiling/memory-usage.md) 자습서 및 [.NET 개체 할당 도구](../profiling/dotnet-alloc-tool.md)를 참조하세요.

Windows 7 이상에서 디버거 없이 프로파일링 도구를 사용할 수 있습니다. Windows 8 이상에서는 디버거(**진단 도구** 창)를 포함한 프로파일링 도구를 실행해야 합니다.

## <a name="blogs-and-videos"></a>블로그 및 동영상

[디버그하는 동안 CPU와 메모리 분석](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ 블로그: Visual C++ 2015의 메모리 프로파일링](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>참고 항목

- [Visual Studio의 프로파일링](../profiling/index.yml)
- [프로파일링 도구 살펴보기](../profiling/profiling-feature-tour.md)
- [디버거 없이 메모리 사용량 분석](../profiling/memory-usage-without-debugging2.md)
