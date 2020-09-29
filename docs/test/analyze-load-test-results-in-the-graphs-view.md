---
title: 부하 테스트 결과 분석 - 그래프 뷰(부하 테스트 분석기)
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.graph.view
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, graphs in Load Test Viewer
- Load Test Viewer, graphs
- load tests, results graphs
- load tests, using graphs
- load test results, graphs
ms.assetid: 4a919cd8-541c-40ee-be3b-352fabc56140
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b48162da7a753516ce0c1ae0dba4cfe1f94387e4
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810655"
---
# <a name="analyze-load-test-results-in-the-graphs-view-of-the-load-test-analyzer"></a>부하 테스트 분석기의 그래프 뷰에서 부하 테스트 결과 분석

부하 테스트의 결과는 서로 다른 몇 개의 창에 데이터로 표시됩니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

테스트 결과를 그래프로 표시하려면 **부하 테스트** 도구 모음에서 **그래프**를 선택합니다. 각 개별 그래프는 드롭다운 목록의 맨 위에 그래프 이름이 표시된 상태로 표시됩니다. 패널에 다른 그래프를 표시하려면 목록에서 다른 그래프 이름을 선택합니다.

한 번에 최대 4개의 그래프 패널을 표시할 수 있습니다. **패널 레이아웃** 도구 모음 단추를 사용하면 패널 레이아웃으로 전환할 수 있습니다.

몇 가지 기본 제공 그래프도 있습니다. 기본 제공 그래프를 그대로 사용하거나 사용자 지정할 수 있습니다. 또한 사용자가 직접 그래프를 만들 수도 있습니다. 자세한 내용은 [방법: 그래프에 카운터 추가 및 삭제](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md) 및 [방법: 사용자 지정 그래프 만들기](../test/how-to-create-custom-graphs-in-load-test-results.md)를 참조하세요.

## <a name="built-in-graphs"></a>기본 제공 그래프

다음 표에서는 부하 테스트 실행 결과를 분석하는 데 사용할 수 있는 기본 제공 그래프를 보여 줍니다.

|그래프 이름|Description|
|-|-|
|핵심 지표|사용자 부하, 처리량 및 응답 시간과 같은 테스트 성능의 기본 특징을 설명하는 카운터입니다.|
|테스트 응답 시간|테스트를 실행하는 데 소요된 시간에 대한 데이터입니다.|
|페이지 응답 시간|부하 테스트 동안 액세스한 웹 페이지의 평균 응답 시간입니다.|
|테스트 중인 시스템|테스트 대상 애플리케이션이 실행된 컴퓨터에 대한 정보입니다. 여기에는 메모리 사용량, 프로세서, 실제 디스크, 프로세스에 대한 데이터가 포함됩니다.<br /><br /> 기본적으로는 Available Mbytes 및 Processor Time 카운터만 수집됩니다.|
|컨트롤러 및 에이전트|부하 테스트가 실행된 컴퓨터에 대한 정보입니다. 여기에는 메모리 사용량, 프로세서, 실제 디스크, 프로세스에 대한 데이터가 포함됩니다.<br /><br /> 기본적으로는 Available Mbytes 및 Processor Time 카운터만 수집됩니다.|
|트랜잭션 응답 시간|부하 테스트 동안 발생한 트랜잭션의 평균 응답 시간입니다.|

테스트를 실행한 이후와 런타임 모두에서 그래프에 서로 다른 카운터를 표시할 수 있습니다.

> [!NOTE]
> 자동으로 생성된 응답 시간 그래프에는 응답 시간 성능 카운터만 추가할 수 있습니다.

카운터 정보는 그래프와 그래프 아래의 범례 모두에 표시됩니다. 그래프의 한 섹션을 확대할 수도 있습니다. 자세한 내용은 [방법: 그래프의 영역으로 확대](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)를 참조하세요.

## <a name="counters-displayed-in-graphs"></a>그래프에 표시되는 카운터

그래프에는 *카운터*가 표시됩니다. 카운터는 초당 테스트 횟수 또는 평균 테스트 시간과 같이 부하 테스트 동안 수집된 데이터를 나타냅니다. 카운터에 대한 자세한 내용은 [부하 테스트에서 컴퓨터에 대한 카운터 집합 및 임계값 규칙 지정](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)을 참조하세요.

그래프에 표시되는 카운터의 범례에는 부하 테스트 실행에 대한 몇 개의 유용한 데이터 열이 표시됩니다. 그래프에서 데이터 표시를 해제하려면 범례의 행에 있는 확인란의 선택을 취소합니다.

범례에는 다음과 같은 열이 있습니다.

|카운터|카운터의 이름입니다.|
|-|-|
|인스턴스|카운터 인스턴스의 이름입니다.|
|Category|카운터 범주의 이름입니다.|
|Computer|카운터가 수집되는 컴퓨터의 이름입니다.|
|색|그래프에 표시되는 선의 색입니다.|
|범위|해당 카운터에 대한 그래프에서 100으로 표현되는 수를 나타냅니다. 예를 들어 상한값이 10,000인 범위의 경우 그래프의 맨 위에 표시된 레이블 100은 10,000을 나타냅니다.|
|최소값|카운터의 최소값을 밀리초 단위로 나타냅니다.|
|최대값|카운터의 최대값을 밀리초 단위로 나타냅니다.|
|Avg|카운터의 평균값을 밀리초 단위로 나타냅니다.|
|마지막|가장 최근 샘플링 간격 동안의 카운터 값을 밀리초 단위로 나타냅니다.|

## <a name="tasks"></a>작업

|작업|관련 항목|
|-|-|
|**범례를 사용하여 그래프 사용자 지정:** 그래프 뷰의 범례에는 그래프와 연결된 각 성능 카운터에 대한 정보가 표시됩니다. 범례를 사용하여 성능 카운터를 제거하고, 그래프에서 성능 카운터를 강조 표시하고, 출력 옵션을 사용자 지정할 수 있습니다.|-   [그래프 뷰 범례를 사용하여 부하 테스트 분석](../test/use-the-graphs-view-legend-to-analyze-load-tests.md)|
|**그래프에 카운터 표시:** 부하 테스트 결과 그래프에 카운터를 배치하여 해당 그래프에 다른 종류의 데이터를 추가할 수 있습니다.|-   [방법: 그래프에서 카운터 추가 및 삭제](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)|
|**그래프 확대:** 부하 테스트가 완료되면 확대/축소 막대를 사용하여 그래프의 영역으로 확대 및 스크롤할 수 있습니다. 확대하면 부하 테스트 실행 동안 생성된 데이터를 보다 자세히 검사할 수 있습니다.|-   [방법: 그래프의 영역으로 확대](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)|
|**그래프 바둑판식 배열:** 부하 테스트 결과 그래프는 몇 가지 패턴으로 배열할 수 있습니다. 최대 네 개의 그래프를 바둑판식으로 배열할 수 있습니다.||
|**사용자 지정 그래프 만들기:** 부하 테스트 결과에 대한 특정 정보를 표시하는 그래프를 디자인할 수 있습니다. 그래프에 표시할 부하 테스트 카운터를 지정하여 사용자 지정 그래프를 디자인합니다.|-   [방법: 사용자 지정 그래프 만들기](../test/how-to-create-custom-graphs-in-load-test-results.md)|
|**그래프의 성능 카운터 데이터 내보내기:** **그래프** 뷰에서 **부하 테스트 분석기** 도구 모음의 **그래프 데이터를 Excel로 내보내기** 단추를 사용하여 그래프 데이터를 Microsoft Excel로 내보낼 수 있습니다.||

## <a name="related-tasks"></a>관련 작업

[테이블 뷰에서 부하 테스트 결과 및 오류 분석](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)

[방법: 분석을 위한 부하 테스트 결과 액세스](../test/how-to-access-load-test-results-for-analysis.md)

[부하 테스트 결과 분석](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

## <a name="see-also"></a>참고 항목

- [방법: 그래프에서 카운터 추가 및 삭제](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
- [방법: 사용자 지정 그래프 만들기](../test/how-to-create-custom-graphs-in-load-test-results.md)
- [방법: 그래프의 영역으로 확대](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)
