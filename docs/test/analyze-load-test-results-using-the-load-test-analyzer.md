---
title: 부하 테스트 결과 분석
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test results
- load tests, analyzing test results
- load tests, managing test results
ms.assetid: 8a4ba300-425d-447c-91d9-c53f4345feee
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9300dd1ebeaee9d87d2527dbc49fa66e319970c1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591244"
---
# <a name="analyze-load-test-results-using-the-load-test-analyzer"></a>부하 테스트 분석기를 사용하여 부하 테스트 결과 분석

**부하 테스트 분석기**를 사용하는 경우 앱에서 병목 지점을 찾고, 오류를 식별하고, 개선된 정도를 측정합니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

다음과 같은 방법으로 부하 테스트 결과를 분석합니다.

- 부하 테스트 실행 도중 모니터링

- 완료된 부하 테스트 분석

- 이전 부하 테스트의 결과 보기

또한 추세 분석을 위해 두 개 이상의 보고서를 비교하는 보고서를 만들어 관련자와 공유할 수 있습니다. [테스트 비교 또는 추세 분석을 위한 부하 테스트 결과 보고](../test/compare-load-test-results.md)를 참조하세요.

부하 테스트를 Visual Studio Enterprise에서 실행하는지 또는 명령줄에서 실행하는지 여부 및 부하 테스트를 단일 컴퓨터에서 실행하는지 또는 원격 컴퓨터에서 실행하는지 여부에 관계없이 이러한 작업을 완료할 수 있습니다.

## <a name="differences-between-analyzing-a-running-and-a-completed-load-test"></a>실행 중인 부하 테스트와 완료된 부하 테스트의 분석 차이점

부하 테스트를 실행하면 **부하 테스트 분석기**가 부하 테스트의 이름 및 테스트가 시작된 시간(예: **LoadTest1[오후 12:40]** )과 함께 별도의 탭에 표시됩니다. 부하 테스트가 실행될 때는 성능 카운터 데이터 중 일부가 메모리에 유지됩니다. 따라서 부하 테스트가 실행될 때는 이 데이터 집합만 모니터링할 수 있으며 부하 테스트가 완료된 후 데이터베이스에서 전체 데이터 집합을 분석할 수 있습니다. 부하 테스트가 실행될 때 표시되는 데이터와 부하 테스트가 완료된 후에 볼 수 있는 데이터에는 차이가 있습니다. 예를 들어 90% 및 95% 응답 시간 데이터는 부하 테스트가 완료되기 전까지는 계산되지 않습니다. 또한 데이터 분석에 사용할 수 있는 도구의 기능에도 약간의 차이가 있습니다.

부하 테스트를 실행할 때는 **그래프** 뷰와 **테이블** 뷰라는 두 가지 뷰를 사용할 수 있습니다. **그래프** 뷰에서는 수집된 성능 카운터를 그래프로 볼 수 있고, **테이블** 뷰에서는 수집된 각 테스트, 페이지, 트랜잭션 및 요청에 대한 정보를 볼 수 있습니다. 테이블에 오류가 나열되는 경우도 있습니다.

부하 테스트 실행이 완료되었을 때는 기본적으로 **요약** 뷰가 표시됩니다. 도구 모음을 사용하여 **요약 뷰**, **그래프 뷰**, **테이블 뷰** 및 **세부 정보 뷰** 간에 전환할 수 있습니다. 그러나 Visual Studio에서 창을 조작하는 일반적인 방법을 사용하여 **부하 테스트 분석기**를 도킹하거나 이동식으로 설정할 수 있습니다. 완료된 부하 테스트 실행을 분석할 경우 동시에 여러 **부하 테스트 분석기**를 열어 서로 다른 부하 테스트 실행을 비교할 수 있습니다.

## <a name="tasks"></a>작업

|작업|관련 항목|
|-|-|
|**부하 테스트 결과 액세스:** 부하 테스트 편집기에서 부하 테스트를 실행할 경우 부하 테스트 결과가 자동으로 열리고 실행 중인 부하 테스트가 **부하 테스트 분석기**에 표시됩니다.|-   [방법: 분석을 위한 부하 테스트 결과 액세스](../test/how-to-access-load-test-results-for-analysis.md)|
|**부하 테스트에 분석 주석 추가:** 분석을 수행할 때 부하 테스트에 주석을 추가할 수 있습니다. 주석은 부하 테스트 결과와 함께 영구적으로 저장됩니다. 입력하는 설명은 부하 테스트 편집기에서 **부하 테스트 결과 열기 및 관리** 대화 상자의 부하 테스트에 연결된 **설명** 열에도 표시됩니다.<br /><br /> 자세한 내용은 [방법: 분석을 위한 부하 테스트 결과 액세스](../test/how-to-access-load-test-results-for-analysis.md)를 참조하세요.<br /><br /> 또한 주석은 부하 테스트 결과에 대한 Excel 보고서를 만들 때도 표시됩니다.<br /><br /> 자세한 내용은 [테스트 비교 또는 추세 분석을 위한 부하 테스트 결과 보고](../test/compare-load-test-results.md)를 참조하세요.||
|**부하 테스트 결과 분석:** 부하 테스트 실행 데이터에 액세스한 후 결과 데이터를 분석할 수 있습니다. 부하 테스트 요약을 통해 결과를 바로 확인할 수 있습니다. 부하 테스트 요약에는 핵심 결과가 간단하고 읽기 쉬운 형식으로 표시됩니다.<br /><br /> 부하 테스트 요약은 인쇄가 가능하므로 이해 관계자에게 결과를 편리하게 전달할 수 있습니다.<br /><br /> 결과 그래프 및 테이블을 사용하여 부하 테스트 결과의 세부 정보를 분석할 수 있습니다. 여기에는 **오류**, **페이지**, **요청**, **SQL 추적**, **테스트**, **임계값** 및 **트랜잭션**이 포함됩니다.|-   [부하 테스트 결과 요약 개요](../test/load-test-results-summary-overview.md)<br />-   [방법: 웹 페이지 응답 보기](../test/how-to-view-web-page-response-time-in-a-load-test.md)<br />-   [임계값 규칙 위반 분석](../test/analyze-threshold-rule-violations-in-load-tests.md)<br />-   [그래프 뷰에서 부하 테스트 결과 분석](../test/analyze-load-test-results-in-the-graphs-view.md)<br />-   [테이블 뷰에서 부하 테스트 결과 및 오류 분석](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)|
|**부하 테스트 결과에서 가상 사용자 동작을 분석하여 성능 문제 격리:** 가상 사용자 동작 차트를 사용하여 부하 테스트 중에 가상 사용자가 수행하는 작업을 시각화할 수 있습니다. 그러면 CPU 스파이크 또는 초당 요청 수 감소 문제를 격리하고 이러한 스파이크 및 감소 중에 실행 중인 테스트 또는 페이지를 확인할 수 있습니다.|-   [세부 정보 뷰에서 가상 사용자 동작 분석](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)|
