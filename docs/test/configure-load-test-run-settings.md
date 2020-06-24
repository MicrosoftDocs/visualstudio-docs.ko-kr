---
title: 부하 테스트 실행 설정 구성
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e8002373b7ad34796df557686c1aff6a417d49ea
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288834"
---
# <a name="configure-load-test-run-settings"></a>부하 테스트 실행 설정 구성

*실행 설정*은 부하 테스트가 실행되는 방식에 영향을 미치는 속성 집합입니다. 실행 설정은 **속성** 창에서 범주별로 구성됩니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

부하 테스트에서 하나 이상의 실행 설정이 있을 수 있지만 하나의 실행 설정만 각 실행에 대해 활성화될 수 있습니다. 다른 실행 설정은 다음 테스트 실행에 사용할 대체 설정을 빠르게 선택하기 위해 제공됩니다.

**부하 테스트 새로 만들기 마법사**를 사용하여 부하 테스트를 만들 때 초기 실행 설정이 만들어집니다.

![부하 테스트 실행 설정](../test/media/loadtestrunsettings.png)

## <a name="tasks"></a>작업

|작업|관련 항목|
|-|-|
|**부하 테스트에 더 많은 실행 설정 추가:** **부하 테스트 새로 만들기 마법사**를 실행할 때 만들어진 실행 설정 외에도 여러 가지 조건에서 테스트를 실행할 수 있도록 더 많은 실행 설정을 부하 테스트에 추가할 수 있습니다.|-   [방법: 부하 테스트에 실행 설정 추가](../test/how-to-add-additional-run-settings-to-a-load-test.md)|
|**부하 테스트에 사용할 활성 실행 설정 지정:** 부하 테스트 편집기를 사용하여 부하 테스트에 사용할 실행 설정을 선택할 수 있습니다. 활성 실행 설정은 "[Active]"라는 접미사로 식별됩니다.|-   [방법: 부하 테스트에 대한 활성 실행 설정 선택](../test/how-to-select-the-active-run-setting-for-a-load-test.md)|
|**실행 설정 속성 편집:** 로깅 옵션(아래 참조)과 같은 실행 설정 속성을 편집하여 테스트 길이, 준비 시간, 보고되는 최대 오류 정보 수, 샘플링 주기, 연결 모델(웹 성능 테스트에만 해당), 결과 스토리지 형식, 유효성 검사 수준, SQL 추적 등을 결정할 수 있습니다. 실행 설정에는 부하 테스트의 목표가 반영되어야 합니다.|-   [부하 테스트 실행 설정 속성](../test/load-test-run-settings-properties.md)<br />-   [실행 설정 속성 변경](../test/load-test-run-settings-properties.md#change-run-setting-properties)|
|**부하 테스트 실행 설정의 테스트 반복 횟수 지정:** **테스트 반복** 속성을 구성하여 부하 테스트의 모든 시나리오에서 모든 웹 성능 및 단위 테스트를 실행할 횟수를 지정할 수 있습니다.|-   [방법: 실행 설정에서 테스트 반복 횟수 지정](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md)|
|**부하 테스트 실행 설정의 샘플링 주기 지정:** **샘플링 주기** 속성을 구성하여 부하 테스트에서 성능 카운터 데이터가 수집되는 빈도를 지정할 수 있습니다.|-   [방법: 샘플링 주기 지정](../test/how-to-specify-the-sample-rate-for-a-load-test.md)|
|**타이밍 정보 스토리지 옵션 지정:** **타이밍 정보 스토리지** 속성을 구성하여 부하 테스트의 정보를 저장할 방식을 지정할 수 있습니다.|-   [방법: 타이밍 정보 스토리지 속성 지정](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)|
|**테스트 리소스 보존 기간 지정:** **리소스 보존 시간** 속성을 설정하여 지정된 기간 동안 테스트 리소스를 보존함으로써 테스트 > 수정 > 설정 주기를 가속화합니다.|-   [부하 테스트를 가속화하려면 리소스 보존](/azure/devops/test/load-test/getting-started-with-performance-testing?view=vsts)|
|**컨텍스트 매개 변수 사용:** 컨텍스트 매개 변수를 사용하여 문자열을 매개 변수화할 수 있습니다. 예를 들어 부하 테스트에 매개 변수화된 웹 서버를 사용하는 웹 성능 테스트가 포함된 경우 다른 서버에 매핑되는 컨텍스트 매개 변수를 실행 설정에 추가할 수 있습니다.|-   [방법: 실행 설정에 컨텍스트 매개 변수 추가](../test/how-to-add-context-parameters-to-a-load-test-run-setting.md)|
|**테스트 로깅 속성 구성:** 부하 테스트 실행 설정과 연결된 로그에 데이터가 기록되는 빈도를 구성할 수 있습니다. 로그는 몇 기가바이트까지 커질 수 있으므로 크거나 복잡한 부하 테스트를 실행 중인 경우 이 속성이 중요할 수 있습니다.<br /><br /> 애플리케이션을 디버깅하고 분석하는 데 유용하도록 부하 테스트가 실패할 경우 로그 파일이 자동으로 저장되도록 구성할 수도 있습니다.|-   [부하 테스트 로깅 설정 수정](../test/modify-load-test-logging-settings.md)|
