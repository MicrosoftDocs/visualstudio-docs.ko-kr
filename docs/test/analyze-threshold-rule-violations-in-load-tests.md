---
title: 부하 테스트의 임계값 규칙 위반 분석
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.threshholdresult
helpviewer_keywords:
- load tests, thresholds
- threshold violations
- threshold counts
- load tests, threshold violations
- load test results, analyzing threshold violations
- thresholds in load tests
ms.assetid: 969ed346-cf2e-4d48-82b3-edb3e075e1c0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0a20c5e3f30a6d006175e78fc70dab79d0b9bf8a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591283"
---
# <a name="analyzing-threshold-rule-violations-in-load-tests-using-the-load-test-analyzer"></a>부하 테스트 분석기를 사용하여 부하 테스트에서 임계값 규칙 위반 분석

임계값 규칙은 특정 성능 카운터와 연결되며, 위반이 발생하면 성능 카운터가 설정된 값을 초과하거나 이러한 값 아래로 떨어진 것입니다. 부하 테스트를 실행할 때 이전에 설정한 임계값 규칙에서 발생하는 위반을 분석할 수 있습니다.

위반이 발생한 경우 **부하 테스트 분석기**의 상태 표시줄에 **임계값 위반** 하이퍼링크가 표시되고 발생한 위반 개수가 지정됩니다. 이 하이퍼링크를 선택하면 임계값 위반 테이블이 표시됩니다. **카운터** 창 및 그래프에서도 임계값 위반을 볼 수 있습니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="view-threshold-violations-in-the-table"></a>테이블에서 임계값 위반 보기

임계값 위반 테이블에는 처음 1,000개의 위반이 표시됩니다. 이 테이블에는 다음과 같은 열이 있습니다.

|열|Description|기본적으로 표시되는지 여부|
|-|-|-|
|Time|부하 테스트 도중 위반이 발생한 시간입니다.|yes|
|Computer|테스트 도중 위반이 발생한 컴퓨터의 이름입니다. **참고:** Rig에서 부하 테스트를 실행하는 경우 이 정보가 중요합니다.|yes|
|Category|위반이 발생한 성능 카운터 범주입니다.|yes|
|카운터|위반이 발생한 성능 카운터 이름입니다.|yes|
|인스턴스|위반이 발생한 성능 카운터 인스턴스입니다.|yes|
|메시지|임계값 위반을 설명하는 메시지입니다. 예: **값 5가 중요 임계값 0을 초과합니다.**|yes|

> [!NOTE]
> 열 머리글을 선택하여 테이블을 정렬할 수 있습니다.

자세한 내용은 [테이블 뷰에서 부하 테스트 결과 및 오류 분석](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)을 참조하세요.

## <a name="view-threshold-violations-in-the-counters-panel"></a>카운터 패널에서 임계값 위반 보기

**카운터** 패널에 있는 부하 테스트의 성능 카운터를 나열하는 트리에서 임계값 위반을 볼 수 있습니다. **카운터** 패널의 아이콘을 통해 임계값 위반이 표시됩니다. 이러한 아이콘은 다음 중 하나입니다.

이러한 아이콘은 다음 중 하나입니다.

![임계값 위반 없음](../test/media/icon_ltest_1.gif) 임계값 위반 없음

![마지막 기간에서 중요한 임계값 위반 발생](../test/media/icon_ltest_2.gif) 마지막 간격에서 중요 임계값 위반이 발생함

![이전 기간에서 중요한 임계값 위반 발생](../test/media/icon_ltest_3.gif) 이전 간격에서 중요 임계값 위반이 발생함

![마지막 기간에서 경고 임계값 위반 발생](../test/media/icon_ltest_4.gif) 마지막 간격에서 경고 임계값 위반이 발생함

![이전 기간에서 경고 임계값 위반 발생](../test/media/icon_ltest_5.gif) 이전 간격에서 경고 임계값 위반이 발생함

그래프에 임계값 위반이 표시될 수도 있습니다. 임계값 아이콘은 그래프에서 임계값 위반이 발생한 데이터 요소 옆에 표시됩니다.

카운터 트리에서 임계값 위반 아이콘은 특정 카운터 노드에서 루트 노드까지 거슬러 올라가면서 전파됩니다. 따라서 트리를 확장하지 않아 카운터가 표시되지 않은 경우에도 카운터에서 위반이 발생했음을 확인할 수 있습니다.

## <a name="view-threshold-violations-on-the-graph"></a>그래프에서 임계값 위반 보기

그래프에서 임계값 위반을 볼 수 있습니다. 그래프에서도 **카운터** 패널과 비슷한 아이콘을 통해 임계값 위반이 표시됩니다. 그래프에서 임계값 위반이 발생한 데이터 요소 옆에 아이콘이 표시됩니다. 그래프에 표시되지 않은 카운터에서 임계값 위반이 발생한 경우 **카운터** 패널에서 그래프로 카운터를 끌어 놓아 그래프에 해당 카운터를 추가할 수 있습니다.

자세한 내용은 [그래프 뷰에서 부하 테스트 결과 분석](../test/analyze-load-test-results-in-the-graphs-view.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [부하 테스트에서 컴퓨터에 대한 카운터 집합 및 임계값 규칙 지정](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [부하 테스트 결과 분석](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [테이블 뷰에서 부하 테스트 결과 및 오류 분석](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
