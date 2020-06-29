---
title: .NET 비동기 코드 성능 분석 | Microsoft Docs
ms.date: 5/5/2020
ms.topic: conceptual
helpviewer_keywords:
- asynchronous, async, profiling
author: esteban-herrera
ms.author: esherrer
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 49091ba472637d480c04c39f0170c2aee00595d2
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85291002"
---
# <a name="analyze-performance-of-net-asynchronous-code"></a>.NET 비동기 코드 성능 분석

.NET Async 도구를 사용하여 앱에서 비동기 코드의 성능을 분석할 수 있습니다.

> [!NOTE]
> .NET Async 도구를 사용하려면 Visual Studio 2019 버전 16.7 이상과 **async** 및 **await**를 사용하는 .NET 프로젝트가 필요합니다.

## <a name="setup"></a>설정

1. Visual Studio에서 **Alt+F2** 키를 눌러 성능 프로파일러를 엽니다.

1. **.NET Async** 확인란을 선택합니다.

   ![.NET Async 도구 선택됨](../profiling/media/async-tool-selected.png ".NET Async 도구 선택됨")

1. **시작** 단추를 클릭하여 도구를 실행합니다.

1. 도구가 시작되면 앱에서 프로파일링하려는 시나리오를 진행합니다. 그런 다음 **수집 중지**를 선택하거나 앱을 닫아 데이터를 확인합니다.

1. 수집이 중지된 후에는 프로파일링 세션 중에 발생한 활동의 테이블이 표시됩니다.

   ![.NET Async 도구 중지됨](../profiling/media/async-tool-opened.png ".NET Async 도구 중지됨")

비동기 이벤트는 시간순으로 활동으로 구성됩니다. 각 이벤트에는 시작 시간, 종료 시간 및 기간이 표시됩니다.

[작업](https://docs.microsoft.com/dotnet/api/system.threading.tasks)에 해당하는 각 행은 **이름** 열에 레이블이 지정됩니다. 확인할 수 없는 작업 이름에 대해서는 **Task in** 레이블이 표시됩니다. 그런 다음 작업에서 발생하는 메서드의 이름을 차례로 입력합니다. 비동기 활동이 수집 세션 내에서 완료되지 않으면 **미완료** 레이블이 **종료 시간** 열에 표시됩니다.

특정 작업 또는 활동을 추가로 조사하려면 행을 마우스 오른쪽 단추로 클릭합니다. 그런 다음 **소스 파일로 이동**을 선택하여 활동이 발생한 코드의 위치를 확인합니다.

![소스 파일로 이동이 선택된 .NET Async 도구](../profiling/media/async-tool-gotosource.png "소스 파일로 이동이 선택된 .NET Async 도구")

## <a name="see-also"></a>참조

- [프로파일러 설정 최적화](../profiling/optimize-profiler-settings.md)
