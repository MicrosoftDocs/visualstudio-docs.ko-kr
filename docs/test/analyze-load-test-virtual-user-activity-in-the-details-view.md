---
title: 부하 테스트 가상 사용자 작업 분석
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.activitychart
helpviewer_keywords:
- virtual user activity chart
- load test, virtual user activity chart
ms.assetid: 63f4bd42-3cfb-4eee-af68-e8334976539e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0289ff0d4a20eacc4f6801d9300d39df594bc79e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591237"
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>부하 테스트 분석기의 세부 정보 뷰에서 부하 테스트 가상 사용자 동작 분석

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**가상 사용자 동작 차트**

![가상 사용자 동작 차트](../test/media/virtual_actchart.png)

**세부 정보** 뷰에는 부하 테스트 동안 개별 가상 사용자가 수행한 작업을 시각적으로 분석하는 데 사용되는 **가상 사용자 동작 차트**가 표시됩니다. **가상 사용자 동작 차트**를 사용하면 사용자 동작의 패턴(부하 패턴)을 확인하고, 실패했거나 느린 테스트를 연결하고, 다른 가상 사용자 동작 요청을 확인할 수 있습니다. **가상 사용자 동작 차트**를 사용하면 CPU 사용량 스파이크, 초당 요청 수 감소 그리고 스파이크 및 감소 중에 실행된 테스트 또는 페이지를 확인할 수도 있습니다.

> [!NOTE]
> **가상 사용자 동작 정보 차트**를 사용할 부하 테스트를 실행하려면 먼저 부하 성능 테스트 편집기를 사용하여 **타이밍 정보 스토리지** 속성이 **AllIndividualDetails** 옵션으로 설정되어 있는지 확인해야 합니다.

**정보 범례 패널**

![정보 범례 패널](../test/media/ltest_detailslegend.png)

정보 범례 패널은 **가상 사용자 동작 차트**에 표시됩니다. 정보 범례 패널을 사용하면 다양한 여러 조건을 기준으로 테스트, 페이지 및 트랜잭션을 필터링할 수 있습니다. 예를 들어 특정 테스트를 뷰에서 제거하거나, 모든 성공한 테스트를 제거하거나, 특정 오류로 실패한 테스트를 제거할 수 있습니다. 또한 로그가 없는 모든 테스트를 제거할 수 있습니다.

실패한 테스트를 강조 표시할 수 있습니다. 이 경우 실패한 테스트는 모두 빨간색으로 표시됩니다. 또한 테스트 로그가 있는 테스트를 강조 표시할 수 있습니다. 로그가 있는 테스트는 녹색으로 표시됩니다.

**필터 결과 패널**

![필터 결과 패널](../test/media/ltest_filterresults.png)

필터 결과 패널은 **가상 사용자 동작 차트**에 표시됩니다. 필터 결과 패널에서는 다음과 같이 항목을 필터링할 수 있습니다.

- **로그 포함 결과만 표시** 테스트 로그가 연결되어 있는 테스트 결과만 표시합니다.

- **성공적인 결과 표시** 성공적인 결과를 표시합니다.

- **오류가 있는 결과 표시** 디버깅하는 데 도움이 되도록 오류가 있는 결과를 표시합니다.

## <a name="tasks"></a>작업

|작업|관련 항목|
|-|-|
|**부하 테스트 실행:** 부하 테스트를 만들고 가상 사용자 동작 데이터를 수집하도록 구성한 후에는 테스트를 실행하고 완료될 때까지 기다려야 **가상 사용자 동작 차트**를 볼 수 있습니다.||
|**가상 사용자 동작 데이터가 들어 있는 부하 테스트 결과 보기:** 부하 테스트를 만들고, 구성하고, 완료한 후에는 **가상 사용자 동작 차트**를 사용하여 가상 사용자 작동 데이터를 볼 수 있습니다.|-   [부하 테스트 결과 분석](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [방법: 부하 테스트 중에 가상 사용자가 수행하는 작업 분석](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**부하 테스트에서 성능 문제 격리:** **가상 사용자 동작 차트**를 사용하여 부하 테스트에서 성능 문제를 격리할 수 있습니다.|-   [연습: 가상 사용자 동작 차트를 사용하여 문제 격리](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>참고 항목

- [부하 테스트 결과 분석](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [테이블 뷰에서 부하 테스트 결과 및 오류 분석](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
