---
title: 부하 테스트 시나리오 속성
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, properties
- load tests, scenarios
ms.assetid: 4414a638-1fa2-40ad-b1f4-b99f90b62e62
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c2011438f1fcb0230cde0de527216456553e7c64
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584441"
---
# <a name="load-test-scenario-properties"></a>부하 테스트 시나리오 속성

부하 테스트 요구 사항에 맞게 Visual Studio에서 부하 테스트 시나리오 속성 설정을 변경합니다. 이 아티클에서는 범주별로 다양한 부하 테스트 시나리오 속성을 나열합니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="general"></a>일반

|속성|정의|
|-|----------------|
|**이름**|시나리오의 이름입니다.|

## <a name="mix"></a>조합

|속성|정의|
|-|----------------|
|**브라우저 조합**|부하 테스트의 웹 브라우저 조합을 지정합니다. 여러 웹 브라우저 종류와 해당 부하 분포를 지정할 수 있습니다.<br /><br />줄임표 **(…)** 단추를 선택하여 **브라우저 조합 편집** 대화 상자를 열고 **추가** 및 **제거**를 사용하여 부하 테스트의 웹 브라우저 종류를 선택합니다.<br /><br />자세한 내용은 [웹 브라우저 형식 지정](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)을 참조하세요.|
|**네트워크 조합**|부하 테스트의 네트워크 조합을 지정합니다. 포함할 네트워크 형식과 해당 부하 분포를 지정할 수 있습니다.<br /><br />줄임표 **(…)** 단추를 선택하여 **네트워크 조합 편집** 대화 상자를 열고 **추가** 및 **제거**를 사용하여 부하 테스트의 네트워크 형식을 선택합니다.<br /><br />자세한 내용은 [가상 네트워크 형식 지정](../test/specify-virtual-network-types-in-a-load-test-scenario.md)을 참조하세요.|
|**테스트 조합**|부하 테스트의 웹 성능 및 단위 테스트 조합을 지정합니다. 포함할 테스트와 해당 부하 분포를 지정할 수 있습니다.<br /><br />줄임표 **(…)** 단추를 선택하여 **테스트 조합 편집** 대화 상자를 열고 **추가** 및 **제거**를 사용하여 부하 테스트의 테스트를 선택합니다.<br /><br />자세한 내용은 [부하 테스트 시나리오에 대한 테스트 조합 편집](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)을 참조하세요.|
|**테스트 조합 형식**|부하 테스트에 대한 테스트 조합 모델을 지정합니다.<br /><br />줄임표 **(…)** 단추를 선택하여 **테스트 조합 편집** 대화 상자를 열고 **테스트 조합 모델** 아래의 드롭다운을 사용하여 부하 테스트에 사용할 테스트 조합 모델을 선택합니다.<br /><br />자세한 내용은 [텍스트 조합 모델 편집](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)을 참조하세요.|

## <a name="options"></a>옵션

|속성|정의|
|-|----------------|
|**사용할 에이전트**|부하 테스트를 원격으로 실행하려는 경우 시나리오에 사용할 에이전트를 지정합니다. 예를 들어 특정 에이전트 집합을 지정하여 성능 추세를 분석할 때 일관성을 유지할 수 있습니다. 또한 에이전트는 지리적으로 분산되어 있을 수 있으므로 에이전트에서 실행할 스크립트와 에이전트가 있는 위치 간에는 밀접한 관계가 있습니다.<br /><br />에이전트는 "**Agent1, Agent2, Agent3**"과 같이 쉼표로 구분해야 합니다. 속성을 공백으로 두면 시나리오에서 사용 가능한 모든 에이전트를 사용하도록 지정됩니다.<br /><br />자세한 내용은 [방법: 사용할 테스트 에이전트 지정](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md)을 참조하세요.|
|**속도 지연에 분포 적용**|사용자 속도 테스트 조합 모델에 일반적인 분포의 지연을 적용할지 여부를 지정하는 데 사용되는 부울 값입니다. 이 속성은 **테스트 조합 형식** 속성을 **사용자 속도 기반**으로 설정한 경우에만 적용됩니다.<br /><br />자세한 내용은 [방법: 속도 지연에 분포 적용](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)을 참조하세요.|
|**IP 전환**|IP 전환이 사용되는지 여부를 지정하는 데 사용되는 부울 값입니다.<br /><br />IP 전환 기능을 사용하면 테스트 에이전트에서 다른 IP 주소 범위를 사용하여 서버에 요청을 보낼 수 있습니다. 이를 통해 여러 클라이언트 컴퓨터에서 발생하는 호출을 시뮬레이션할 수 있습니다. 부하 분산된 웹 팜에 대해 테스트하는 경우 IP 전환이 중요합니다. 대부분의 부하 분산 장치에서는 클라이언트의 IP 주소를 사용하여 클라이언트와 특정 웹 서버 사이의 선호도를 설정합니다. 모든 요청이 클라이언트 하나에서 생성되면 부하 균형 도구에서 부하 균형을 조정하지 않습니다. 웹 팜에서 부하를 잘 분산하려면 요청이 특정 IP 주소에 편중되지 않도록 해야 합니다.<br /><br />IP 전환은 테스트 에이전트에서만 사용할 수 있습니다.|
|**최대 테스트 반복 횟수**|시나리오에서 실행할 최대 테스트 횟수를 지정하는 데 사용되는 숫자 값입니다. 값 0은 최대값이 없음을 지정합니다.<br /><br />자세한 내용은 [시나리오에 대한 테스트 반복 구성](../test/configure-test-iterations-in-a-load-test-scenario.md)을 참조하세요.|
|**새 사용자의 백분율**|시나리오에서 새 사용자 또는 처음 방문하는 사용자가 차지하는 백분율을 지정하는 숫자 값입니다.<br /><br />자세한 내용은 [방법: 웹 캐시 데이터를 사용하는 가상 사용자 비율 지정](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)을 참조하세요.|
|**인지 시간 프로필**|시나리오에 **정규 분포**를 사용하거나 인지 시간 프로필을 **설정** 또는 **해제**하도록 지정합니다.<br /><br />자세한 내용은 [인지 시간을 편집하여 웹 사이트 사용자 상호 작용 지연 시뮬레이션](../test/edit-think-times-in-load-test-scenarios.md)을 참조하세요.|

## <a name="timing"></a>타이밍

|속성|정의|
|-|----------------|
|**지연 시작 시간**|부하 테스트가 시작된 후 시나리오가 시작되기 전까지의 지연 시간(시간, 분 및 초)을 나타내는 시간 값입니다. **준비 시간 동안 사용 안 함** 속성을 **True**로 설정한 경우에는 준비 시간이 지난 후에 대기 시간이 적용됩니다.<br /><br />자세한 내용은 [시나리오 시작 시간 지연 구성](../test/configure-scenario-start-delays.md)을 참조하세요.|
|**준비 시간 동안 사용 안 함**|부하 테스트의 실행 설정에서 **준비 시간** 속성 값으로 지정한 시간 동안 시나리오를 실행할지 여부를 지정하는 데 사용되는 부울 값입니다.<br /><br />부하 테스트 실행 설정의 속성에 대한 자세한 내용은 [부하 테스트 실행 설정 속성](../test/load-test-run-settings-properties.md)을 참조하세요.<br /><br />자세한 내용은 [시나리오 시작 시간 지연 구성](../test/configure-scenario-start-delays.md)을 참조하세요.|
|**테스트 반복 간 인지 시간**|테스트 반복 사이의 대기 시간(초)을 지정하는 데 사용되는 숫자 값입니다.<br /><br />자세한 내용은 [인지 시간을 편집하여 웹 사이트 사용자 상호 작용 지연 시뮬레이션](../test/edit-think-times-in-load-test-scenarios.md)을 참조하세요.|

## <a name="see-also"></a>참고 항목

- [부하 테스트 시나리오 편집](../test/edit-load-test-scenarios.md)
