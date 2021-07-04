---
title: 메모리 사용량 분석
description: 메모리 누수 및 비효율적인 메모리 사용, 메모리 사용량 도구 및 .NET 개체 할당 도구와 같은 도구를 찾는 데 사용할 수 있는 도구에 관해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 10/12/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a6af0cd98e69a3c43ba70f5609567243e6285201
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387972"
---
# <a name="analyze-memory-usage"></a>메모리 사용량 분석

메모리 누수 및 비효율적인 메모리 사용을 찾기 위해 디버거 통합 메모리 사용량 진단 도구 및 .NET 개체 할당 도구나 사후 분석 메모리 사용량 도구와 같은 성능 프로파일러의 도구를 사용할 수 있습니다.

메모리 사용량 도구를 통해 관리되는 메모리 및 네이티브 메모리 힙의 *스냅샷* 을 하나 이상 만들 수 있습니다. .NET, ASP.NET, C++ 또는 혼합 모드(.NET 및 네이티브) 앱의 스냅샷을 수집할 수 있습니다. **메모리 사용량** 도구는 열려 있는 Visual Studio 프로젝트, 설치된 Microsoft Store 앱에서 실행하거나 실행 중인 앱 또는 프로세스에 연결할 수 있습니다. 디버깅을 사용하거나 사용하지 않고 **메모리 사용량** 도구를 실행할 수 있습니다. 자세한 내용은 [디버거를 사용하거나 사용하지 않고 프로파일링 도구 실행](../profiling/running-profiling-tools-with-or-without-the-debugger.md)을 참조하세요. 디버거에서 메모리 프로파일링을 설정하거나 해제할 수 있으며 메모리 사용량에 대한 개체별 분석을 볼 수 있습니다. 실행이 일시 중지된 경우 메모리 사용량 결과를 볼 수 있습니다(예: 중단점에서).

.NET 개발자는 .NET 개체 할당 도구와 [메모리 사용량](../profiling/memory-usage.md) 도구 중에서 선택할 수 있습니다.

- [.NET 개체 할당 도구](../profiling/dotnet-alloc-tool.md)를 사용하면 .NET 코드의 할당 패턴과 비정상 요소를 식별하는 데 도움이 되고 가비지 수집의 일반적인 문제를 식별할 수 있습니다. 이 도구는 사후 분석 도구로만 실행됩니다. 로컬 컴퓨터 또는 원격 컴퓨터에서 이 도구를 실행할 수 있습니다.
- [메모리 사용량](../profiling/memory-usage-without-debugging2.md) 도구는 .NET 앱에서 일반적이지 않은 메모리 누수를 식별하는 데 유용합니다. 코드를 단계별로 실행하는 경우와 같이 메모리를 검사하는 동안 디버거 기능을 사용해야 하는 경우 [디버거 통합 메모리 사용량](../profiling/memory-usage.md) 도구를 사용하는 것이 좋습니다.

C++ 개발자는 디버거 통합형 또는 디버거가 없는 메모리 사용량 도구를 사용할 수 있습니다.

- [디버거를 사용하여 메모리 사용량 분석](../profiling/memory-usage.md)
- [디버거 없이 메모리 사용량 분석](../profiling/memory-usage-without-debugging2.md)

Windows 7 이상에서 디버거 없이 프로파일링 도구를 사용할 수 있습니다. Windows 8 이상에서는 디버거(**진단 도구** 창)를 포함한 프로파일링 도구를 실행해야 합니다.

## <a name="blogs-and-videos"></a>블로그 및 동영상

[디버그하는 동안 CPU와 메모리 분석](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ 블로그: Visual C++ 2015의 메모리 프로파일링](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>참조

- [Visual Studio의 프로파일링](../profiling/index.yml)
- [프로파일링 도구 살펴보기](../profiling/profiling-feature-tour.md)
