---
title: .NET Core 프로젝트의 데이터베이스 사용량 분석 | Microsoft Docs
ms.date: 5/5/2020
ms.topic: conceptual
helpviewer_keywords:
- database, profiling
author: esteban-herrera
ms.author: esherrer
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: b369fe6998cd7ef134af765d6d849f41bc93527c
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85291001"
---
# <a name="analyze-database-performance-using-the-database-tool"></a>데이터베이스 도구를 사용하여 데이터베이스 성능 분석

데이터베이스 도구를 사용하여 진단 세션 중에 앱이 수행하는 데이터베이스 쿼리를 기록합니다. 그런 다음 앱의 성능을 향상할 수 있는 지점을 찾기 위해 개별 쿼리에 대한 정보를 분석할 수 있습니다.

> [!NOTE]
> 데이터베이스 도구를 사용하려면 Visual Studio 2019 버전 16.3 이상과 [ADO.NET]( https://docs.microsoft.com/dotnet/framework/data/adonet/ado-net-overview) 또는 [Entity Framework Core](https://docs.microsoft.com/ef/core/)를 사용하는 Windows 기반 .NET Core 프로젝트가 필요합니다.

## <a name="setup"></a>설정

1. Visual Studio에서 **Alt+F2** 키를 눌러 성능 프로파일러를 엽니다.

1. **데이터베이스** 확인란을 선택합니다.

   ![데이터베이스 도구 선택됨](./media/db-launch.png "데이터베이스 도구 선택됨")

   > [!NOTE]
   > 도구를 선택할 수 없는 경우 다른 모든 도구의 확인란을 선택 취소합니다. 일부 도구는 단독으로 실행해야 하기 때문입니다. 도구를 함께 실행하는 방법에 대한 자세한 내용은 [명령줄에서 프로파일링 도구 사용](../profiling/using-the-profiling-tools-from-the-command-line.md)을 참조하세요.
   >
   > 그래도 도구를 사용할 수 없는 경우 프로젝트가 위의 요구 사항을 충족하는지 확인합니다. 가장 정확한 데이터를 캡처하기 위해 프로젝트가 릴리스 모드에 있는지 확인합니다.

1. **시작** 단추를 선택하여 도구를 실행합니다.

1. 도구가 시작되면 앱에서 프로파일링하려는 시나리오를 진행합니다. 그런 다음 **수집 중지**를 선택하거나 앱을 닫아 데이터를 확인합니다.

1. 수집이 중지된 후에는 프로파일링 세션 중에 실행된 쿼리의 테이블이 표시됩니다.

   ![데이터베이스 도구 중지됨](./media/db-after.png "데이터베이스 도구 중지됨")

쿼리는 시간순으로 구성되지만 임의의 열을 기준으로 정렬할 수 있습니다. 열 제목을 마우스 오른쪽 단추로 클릭하여 더 많은 열을 표시할 수 있습니다. **기간** 열을 선택하면 가장 긴 시간에서 가장 짧은 시간까지 쿼리가 정렬됩니다.

조사할 쿼리를 찾았으면 쿼리를 마우스 오른쪽 단추로 클릭합니다. 그런 다음 **소스 파일로 이동**을 선택하여 해당 쿼리를 실행한 코드를 확인합니다.

![소스 파일로 이동 선택됨](./media/db-gotosource.png "소스 파일로 이동 선택됨")

그래프에서 시간 범위를 선택하는 경우 쿼리 테이블에는 해당 시간 범위 동안 발생한 쿼리만 표시됩니다. 이 동작은 [CPU 사용량 도구](https://docs.microsoft.com/visualstudio/profiling/cpu-usage?view=vs-2019)도 함께 실행하는 경우 특히 유용합니다.

## <a name="see-also"></a>참조

- [프로파일러 설정 최적화](../profiling/optimize-profiler-settings.md)
