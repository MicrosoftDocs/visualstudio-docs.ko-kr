---
title: 부하 테스트에 대한 카운터 집합 및 임계값 규칙
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- load tests, thresholds
- counter sets
- load tests, performance
- load tests, counter sets
- load tests, threshold rules
ms.assetid: 9e14d955-f3a4-4717-bbfe-7f08cdda5678
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 440bc01b52269c477d9d2f2194fd831041f1d20d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596322"
---
# <a name="specify-counter-sets-and-threshold-rules-for-computers-in-a-load-test"></a>부하 테스트에서 컴퓨터에 대한 카운터 집합 및 임계값 규칙 지정

부하 테스트에서는 명명된 카운터 집합을 제공하며 이러한 카운터 집합은 성능 카운터 데이터를 분석할 때 유용합니다. 카운터 집합은 애플리케이션, ASP.NET, .NET 애플리케이션, IIS, SQL 등과 같은 기술별로 구성됩니다. **부하 테스트 새로 만들기 마법사**를 사용하여 부하 테스트를 만들 때 초기 카운터 집합을 추가합니다. 이러한 초기 카운터 집합에서 부하 테스트를 위해 일련의 미리 정의된 중요한 카운터 집합이 제공됩니다. **부하 테스트 편집기**에서 카운터를 관리합니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> 부하 테스트가 원격 컴퓨터에 분산된 경우 컨트롤러 및 에이전트 카운터가 컨트롤러 및 에이전트 카운터 집합에 매핑됩니다. 부하 테스트에서 원격 컴퓨터를 사용하는 방법에 대한 자세한 내용은 [테스트 컨트롤러 및 테스트 에이전트](configure-test-agents-and-controllers-for-load-tests.md)를 참조하세요.

카운터 집합은 사용자가 지정하는 컴퓨터에서 수집됩니다. 부하 테스트 동안 사용되는 카운터 집합과 컴퓨터 간의 연결은 *카운터 집합 맵*입니다. 예를 들어, 테스트 중인 웹 서버에 ASP.NET, IIS 및 .NET 애플리케이션 카운터 집합 매핑이 있을 수 있습니다.

기본적으로 성능 카운터는 컨트롤러와 에이전트에서 수집됩니다. 자세한 내용은 [테스트 컨트롤러 및 테스트 에이전트](configure-test-agents-and-controllers-for-load-tests.md)를 참조하세요.

테스트 중인 서버를 카운터를 수집할 컴퓨터의 목록에 추가하는 것이 중요합니다. 그러면 부하 테스트를 수행하는 동안 모든 중요한 시스템 데이터가 수집되고 모니터링됩니다.

## <a name="tasks"></a>작업

|작업|관련 항목|
|-|-----------------------|
|**부하 테스트에 대한 카운터 집합 관리:** 부하 테스트를 만든 다음, 부하 테스트 편집기에서 카운터 집합을 편집할 수 있습니다. 카운터 집합을 관리하려면 성능 데이터를 수집할 컴퓨터 집합을 선택하고 개별 컴퓨터에서 각각 수집할 카운터 집합을 할당합니다. 부하 테스트 편집기에서 카운터를 관리합니다.|-   [방법: 카운터 집합 관리](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)|
|**부하 테스트에 카운터 집합 추가:** **부하 테스트 새로 만들기 마법사**를 사용하여 부하 테스트를 만들 때 초기 카운터 집합을 추가합니다. 이때 부하 테스트에 사용할 미리 정의된 카운터 집합이 제공됩니다. 부하 테스트를 만든 후 부하 테스트 편집기를 사용하여 기존 카운터 집합에 새 카운터를 추가할 수 있습니다.|-   [방법: 카운터 집합에 카운터 추가](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md)<br />-   [방법: 사용자 지정 카운터 집합 추가](../test/how-to-add-custom-counter-sets-using-the-load-test-editor.md)|
|**부하 테스트에 대한 카운터를 사용하여 임계값 규칙 지정:** 임계값 규칙은 부하 테스트 도중 시스템 리소스 사용을 모니터링하기 위해 개별 성능 카운터에 설정되는 규칙입니다. 카운터 집합 정의에는 여러 가지 주요 성능 카운터에 대해 미리 정의된 임계값 규칙이 포함되어 있습니다. 부하 테스트에서 임계값 규칙을 통해 성능 카운터 값을 상수 값이나 다른 성능 카운터 값과 비교할 수 있습니다.|-   [방법: 임계값 규칙 추가](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)|
|**카운터 집합을 매핑할 컴퓨터에 이름 할당:** 컴퓨터에 인식하기 쉬운 이름을 적용할 수 있도록 컴퓨터 태그를 추가할 수 있습니다. 이 태그는 부하 테스트 편집기의 트리에 있는 **카운터 집합 매핑** 노드에 표시됩니다. 더욱 중요한 것은 이 태그가 Excel 보고서에 표시된다는 점입니다. 따라서 관련자가 부하 테스트에서 컴퓨터에 할당된 역할(예: "lab2의 Web Server1" 또는 "피닉스 사무실의 SQL Server2")을 쉽게 확인할 수 있습니다.<br /><br /> 자세한 내용은 [테스트 비교 또는 추세 분석을 위한 부하 테스트 결과 보고](../test/compare-load-test-results.md)를 참조하세요.||

## <a name="use-counter-sets"></a>카운터 집합 사용

부하 테스트 도구는 카운터를 사용하여 시간에 따라 성능 데이터를 수집하여 그래프로 표시합니다. 카운터 데이터는 부하 테스트를 실행하는 동안 사용자가 지정한 간격마다 수집됩니다. 자세한 내용은 [방법: 샘플링 주기 지정](../test/how-to-specify-the-sample-rate-for-a-load-test.md)을 참조하세요. 런타임에 카운터를 보거나 부하 테스트 실행 후 *부하 테스트 분석기*를 사용하여 카운터를 볼 수 있습니다.

카운터 데이터는 테스트가 실행되는 서버 및 모든 컴퓨터에서 수집됩니다. 테스트를 실행할 에이전트 컴퓨터 집합을 설정한 경우 이들 컴퓨터에도 카운터가 수집됩니다.

세 가지 카운터 범주는 백분율, 횟수 및 평균입니다. 일부 예제에서는 % CPU 사용량, SQL Server 잠금 횟수 및 초 당 IIS 요청 수입니다.

![부하 테스트 카운터 집합](../test/media/loadtestcountersets.png)

개별 HTTP 요청에 대한 성능 데이터는 에이전트 컴퓨터와 같은 테스트를 실행하는 컴퓨터에 의해 보고됩니다. 요청의 경우 첫 번째 바이트 평균 시간, 응답 시간 및 초 당 요청 수와 같은 데이터를 모니터링할 수 있습니다.

또한 웹 서버에서 성능 데이터를 쉽게 수집할 수 있도록 Visual Studio Enterprise에서는 부하 테스트에 사용되는 기술을 기반으로 미리 정의된 명명된 카운터 집합을 제공합니다. 이러한 집합은 IIS, ASP.NET 또는 SQL Server를 실행하는 서버를 분석할 때 유용합니다. 기본 카운터 집합에서 제공하지 않는 카운터는 부하 테스트 편집기를 사용하여 추가할 수 있습니다. 테스트 중인 컴퓨터 또는 서버를 부하 테스트에 추가하여 이러한 컴퓨터의 리소스 사용을 모니터링하는 것이 중요합니다. 자세한 내용은 [방법: 카운터 집합 관리](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)를 참조하세요.

부하 실행 결과를 분석할 때 수집할 데이터, 임계값 규칙 설정 위치, 측정값이 애플리케이션에서 특정 문제를 일으킬 때 이를 알리는 방법 등을 확인하기 위해 특정 영역의 도메인별 정보가 필요한 경우가 자주 있습니다. 자세한 내용은 [임계값 규칙 정보](#about-threshold-rules)를 참조하세요.

### <a name="performance-counter-sampling-interval-considerations"></a>성능 카운터 샘플링 간격 고려 사항

부하 테스트 실행 설정에서 부하 테스트 길이에 따라 적절한 **샘플링 주기** 속성 값을 선택합니다. 기본값인 5초와 같이 샘플링 주기 값이 작으면 부하 테스트 결과 데이터베이스에 더 많은 공간이 필요합니다. 부하 테스트가 긴 경우 샘플링 주기를 늘리면 수집되는 데이터 양이 줄어듭니다. 자세한 내용은 [방법: 샘플링 주기 지정](../test/how-to-specify-the-sample-rate-for-a-load-test.md)을 참조하세요.

다음은 샘플링 주기에 대한 몇 가지 지침입니다.

|부하 테스트 지속 시간|권장 샘플링 주기|
|-|-----------------------------|
|\< 1시간|5초|
|1-8시간|15초|
|8-24시간|30초|
|24시간 초과|60초|

## <a name="store-performance-data"></a>성능 데이터 저장

부하 테스트를 실행하는 동안 성능 카운터 데이터가 수집되어 *부하 테스트 결과 리포지토리*에 저장됩니다. 자세한 내용은 [부하 테스트 결과 리포지토리에서 부하 테스트 결과 관리](../test/manage-load-test-results-in-the-load-test-results-repository.md)를 참조하세요.

## <a name="about-threshold-rules"></a>임계값 규칙 정보

*임계값 규칙*은 부하 테스트 도중 시스템 리소스 사용을 모니터링하기 위해 개별 성능 카운터에 설정되는 규칙입니다. 카운터 집합 정의에는 여러 가지 주요 성능 카운터에 대해 미리 정의된 임계값 규칙이 포함되어 있습니다. 자세한 내용은 [카운터 집합을 사용하여 부하 테스트에서 성능 카운터 데이터 분석](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)을 참조하세요.

## <a name="threshold-rules-and-levels"></a>임계값 규칙 및 수준

부하 테스트에 임계값 규칙을 만들 때는 두 가지 규칙 유형 중에서 선택합니다.

상수 비교&mdash;성능 카운터 값을 상수 값과 비교합니다.

상수 비교&mdash;성능 카운터 값을 다른 성능 카운터 값과 비교합니다.

임계값 규칙을 만들 때는 규칙 수준도 설정합니다. 수준을 경고 임계값 및 중요 임계값으로 설정할 수 있습니다. 부하 테스트 실행을 표시할 때 경고 수준 임계값 위반은 노란색 기호로, 중요 수준 임계값 위반은 빨간색 기호로 표시됩니다.

## <a name="the-alert-if-over-property"></a>초과하면 경고 속성

**초과하면 경고** 속성을 **True**로 설정하면 임계값을 초과할 때 경고가 표시됩니다. 예를 들어 **% 프로세서 시간**에 임계값 규칙을 설정한 경우 값이 90보다 클 때 경고를 표시하려면 **상수 비교** 규칙 형식을 사용하고 **중요 임계값**을 90으로 설정한 다음, **초과하면 경고**를 **True**로 설정합니다.

**초과하면 경고** 속성을 **False**로 설정하면 임계값 밑으로 떨어질 때 경고가 표시됩니다. 예를 들어 **Requests/Sec**에 임계값 규칙이 설정된 경우 값이 50을 밑돌 때 경고를 표시하려면 **상수 비교** 규칙 형식을 사용하고 **중요 임계값**을 50으로 설정한 다음, **초과하면 경고**를 **False**로 설정합니다.

## <a name="see-also"></a>참고 항목

- [방법: 임계값 규칙 추가](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)
- [임계값 규칙 위반 분석](../test/analyze-threshold-rule-violations-in-load-tests.md)
