---
title: 부하 테스트 결과 요약 개요
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.summary.view
helpviewer_keywords:
- load test results, summary
- load tests, summary in analyzer
- load tests, results summary
- Load Test Viewer, summary
- load tests, summary in Load Test Viewer
ms.assetid: 326b6c3c-5378-452b-8ca3-ba5a06ab3d41
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7df3324c2182c376cb9547a4192fca3e601b3dd5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75584493"
---
# <a name="load-test-results-summary-overview"></a>부하 테스트 결과 요약 개요

부하 테스트 실행이 끝나면 부하 테스트 요약을 통해 결과를 바로 확인할 수 있습니다. 부하 테스트 요약에는 핵심 결과가 간단하고 읽기 쉬운 형식으로 제공됩니다. 부하 테스트 요약은 인쇄가 가능하므로 이해 관계자에게 결과를 편리하게 전달할 수 있습니다. 또한 부하 테스트 요약은 이전에 실행한 부하 테스트의 부하 테스트 결과를 열 때 기본적으로 표시되는 뷰입니다. 자세한 내용은 [방법: 분석을 위한 부하 테스트 결과 액세스](../test/how-to-access-load-test-results-for-analysis.md)를 참조하세요.

![요약 보기](../test/media/ltest_summaryview.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="the-load-test-summary"></a>부하 테스트 요약

부하 테스트 요약은 여러 개의 섹션으로 구분되어 있습니다. 초기 섹션은 요약의 맨 위에 나타나며 항상 표시됩니다. 부하 테스트 요약을 확인하는 경우 다음과 같은 항목이 먼저 표시됩니다.

- 테스트 실행 정보

- 전체 결과

- 주요 통계: 가장 느린 페이지 5개

- 주요 통계: 가장 느린 테스트 5개

- 주요 통계: 가장 느린 SQL 작업 5개

    > [!NOTE]
    > SQL 작업 섹션은 부하 테스트 실행 시 SQL 추적을 사용할 수 있는 경우에만 표시됩니다.

종료 섹션은 요약 끝부분에 나타나며 공간 절약을 위해 축소할 수 있습니다. 부하 테스트 요약의 끝부분에 나타나는 항목은 다음과 같습니다.

- 테스트 결과

- 페이지 결과

- 트랜잭션 결과

- 리소스 테스트 중인 시스템

- 컨트롤러 및 에이전트 리소스

- 오류

## <a name="test-run-information"></a>테스트 실행 정보

테스트 실행 정보 섹션에는 테스트 이름, 시작 및 종료 시간, 테스트를 실행한 컨트롤러를 포함하여 실행과 관련된 일반적인 정보가 나와 있습니다. 또한 이 섹션에는 부하 테스트 실행 시 추가하는 실행에 대한 선택적인 설명도 포함되어 있습니다.

## <a name="overall-results"></a>전체 결과

전체 결과 섹션에는 초당 요청 수, 실패한 총 요청 수, 평균 응답 시간, 평균 페이지 시간을 포함하여 테스트에 대한 요약 결과가 나와 있습니다.

## <a name="key-statistic-top-5-slowest-pages"></a>주요 통계: 가장 느린 페이지 5개

가장 느린 페이지 섹션에는 부하 테스트 실행 시 가장 느린 페이지 5개가 포함됩니다. 또한 페이지별로 URL과 평균 페이지 부하 시간이 표시됩니다. 페이지는 내림차순으로 정리되어 있습니다. 페이지의 URL을 선택하면 **페이지** 테이블이 열려 해당 페이지를 좀 더 자세히 검토할 수 있습니다. 자세한 내용은 [방법: 웹 페이지 응답 보기](../test/how-to-view-web-page-response-time-in-a-load-test.md)를 참조하세요.

**95% 페이지 시간(초)** 의 백분위수 값은 페이지의 95%가 이 시간(초) 미만으로 완료되었음을 나타냅니다.

## <a name="key-statistic-top-5-slowest-tests"></a>주요 통계: 가장 느린 테스트 5개

가장 느린 테스트 섹션에는 부하 테스트 실행 시 가장 느린 테스트 5개가 포함됩니다. 또한 테스트별로 테스트 이름과 평균 테스트 시간이 표시됩니다. 테스트는 내림차순으로 정리되어 있습니다. 테스트 이름을 선택하면 **테스트** 테이블이 열려 해당 테스트를 좀 더 자세히 검토할 수 있습니다. 자세한 내용은 [테이블 뷰에서 부하 테스트 결과 및 오류 분석](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)을 참조하세요.

**95% 테스트 시간(초**)의 백분위수 값은 테스트의 95%가 이 시간(초) 미만으로 완료되었음을 나타냅니다.

## <a name="key-statistic-top-5-slowest-sql-operations"></a>주요 통계: 가장 느린 SQL 작업 5개

부하 테스트에 SQL 추적을 사용할 수 있는 경우 가장 느린 SQL 작업 섹션에 부하 테스트의 가장 느린 SQL 작업 5개가 포함됩니다. 또한 테스트별로 작업 이름과 지속 시간이 표시됩니다. 지속 시간은 마이크로초(SQL Server 2005) 또는 밀리초(SQL Server 2000 이전 버전) 단위로 표시됩니다. 테스트는 지속 시간별로 내림차순으로 정리되어 있습니다. 작업 이름을 선택하면 **SQL 추적** 테이블이 열려 해당 작업을 좀 더 자세히 검토할 수 있습니다. 자세한 내용은 [SQL 추적 데이터 테이블](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table)을 참조하세요.

## <a name="test-results"></a>테스트 결과

테스트 결과 섹션에는 부하 테스트 실행에 사용된 모든 테스트 및 시나리오의 목록이 포함됩니다. 또한 테스트 이름, 시나리오, 실행 횟수, 실패한 횟수, 평균 테스트 시간이 표시됩니다. 테스트 이름을 선택하면 **테스트** 테이블이 열려 해당 테스트를 좀 더 자세히 검토할 수 있습니다. 자세한 내용은 [테이블 뷰에서 부하 테스트 결과 및 오류 분석](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)을 참조하세요.

> [!NOTE]
> 단원 제목의 왼쪽에 표시되는 화살표를 선택하면 이 단원을 축소하거나 확장할 수 있습니다.

## <a name="page-results"></a>페이지 결과

페이지 결과 섹션에는 부하 테스트에 사용된 모든 웹 페이지의 목록이 포함됩니다. 또한 URL, 시나리오, 테스트 이름, 평균 페이지 시간, 카운트가 표시됩니다. 페이지의 URL을 선택하면 **페이지** 테이블이 열려 해당 페이지를 좀 더 자세히 검토할 수 있습니다. 자세한 내용은 [방법: 웹 페이지 응답 보기](../test/how-to-view-web-page-response-time-in-a-load-test.md)를 참조하세요.

> [!NOTE]
> 단원 제목의 왼쪽에 표시되는 화살표를 선택하면 이 단원을 축소하거나 확장할 수 있습니다.

## <a name="transaction-results"></a>트랜잭션 결과

트랜잭션 결과 섹션에는 부하 테스트 실행에 사용된 모든 트랜잭션의 목록이 포함됩니다. 또한 트랜잭션 이름, 시나리오, 테스트, 응답 시간, 경과된 시간, 카운트가 표시됩니다. 트랜잭션 이름을 선택하면 **트랜잭션** 테이블이 열려 해당 트랜잭션을 좀 더 자세히 검토할 수 있습니다. 자세한 내용은 [테이블 뷰에서 부하 테스트 결과 및 오류 분석](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)을 참조하세요.

> [!NOTE]
> 단원 제목의 왼쪽에 표시되는 화살표를 선택하면 이 단원을 축소하거나 확장할 수 있습니다.

백분위수 값은 다음 트랜잭션 정보를 나타냅니다.

- 총 트랜잭션의 90%가 \<time>초 이내에 완료되었습니다.

- 총 트랜잭션의 95%가 \<time>초 이내에 완료되었습니다.

## <a name="system-under-test-resources"></a>리소스 테스트 대상 시스템

리소스 테스트 중인 시스템 섹션에는 부하가 발생하는 대상 컴퓨터 집합에 해당하는 컴퓨터의 목록이 포함됩니다. 여기에는 에이전트나 컨트롤러 이외의 카운터 집합을 수집하는 모든 컴퓨터가 포함됩니다. 또한 컴퓨터 이름, 프로세서 시간(%), 사용 가능한 메모리가 표시됩니다. 컴퓨터 이름을 선택하면 **테스트 중인 시스템** 그래프가 열려 시간 경과에 따른 리소스 사용량을 확인할 수 있습니다. 자세한 내용은 [그래프 뷰에서 부하 테스트 결과 분석](../test/analyze-load-test-results-in-the-graphs-view.md)을 참조하세요.

> [!NOTE]
> 단원 제목의 왼쪽에 표시되는 화살표를 선택하면 이 단원을 축소하거나 확장할 수 있습니다.

## <a name="controller-and-agent-resources"></a>컨트롤러 및 에이전트 리소스

컨트롤러 및 에이전트 리소스 섹션에는 테스트 실행에 사용되는 컴퓨터의 목록이 포함됩니다. 또한 컴퓨터 이름, 프로세서 시간(%), 사용 가능한 메모리가 표시됩니다. 컴퓨터 이름을 선택하면 **컨트롤러 및 에이전트** 그래프가 열려 시간 경과에 따른 리소스 사용량을 확인할 수 있습니다. 자세한 내용은 [그래프 뷰에서 부하 테스트 결과 분석](../test/analyze-load-test-results-in-the-graphs-view.md)을 참조하세요.

> [!NOTE]
> 단원 제목의 왼쪽에 표시되는 화살표를 선택하면 이 단원을 축소하거나 확장할 수 있습니다.

## <a name="errors"></a>오류

오류 섹션에는 부하 테스트 시 발생한 모든 오류의 목록이 포함됩니다. 또한 오류의 형식 및 하위 형식, 카운트, 마지막 메시지가 표시됩니다. 오류를 선택하면 **오류** 테이블이 열려 해당 오류를 좀 더 자세히 검토할 수 있습니다. 자세한 내용은 [테이블 뷰에서 부하 테스트 결과 및 오류 분석](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)을 참조하세요.

> [!NOTE]
> 단원 제목의 왼쪽에 표시되는 화살표를 선택하면 이 단원을 축소하거나 확장할 수 있습니다.

## <a name="print-a-summary"></a>요약 인쇄

요약의 바로 가기 메뉴에서 **인쇄**를 선택하면 부하 테스트 요약을 인쇄할 수 있습니다. 또한 요약의 바로 가기 메뉴에서 **인쇄 미리 보기**를 선택하여 인쇄 내용을 미리 볼 수 있으며, 미리 보기 화면에서 바로 인쇄할 수도 있습니다.

## <a name="see-also"></a>참고 항목

- [임계값 규칙 위반 분석](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [부하 테스트 결과 분석](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
