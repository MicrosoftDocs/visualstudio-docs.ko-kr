---
title: 부하 테스트 만들기 및 실행
ms.date: 10/01/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, in load tests
- unit tests, load test walkthrough
- load tests, walkthrough
ms.assetid: bbf075a5-96d5-48ed-a03c-330f0fc04748
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 780485a4d42cad574cddaaa5a9ae51a65a1a9b7d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093627"
---
# <a name="walkthrough-create-and-run-a-load-test-that-contains-unit-tests"></a>연습: 단위 테스트를 포함하는 부하 테스트 만들기 및 실행

이 연습에서는 단위 테스트를 포함하는 부하 테스트를 만듭니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

이 연습에서는 Visual Studio Enterprise를 사용하여 부하 테스트를 만든 다음 실행하는 과정을 단계별로 설명합니다. 부하 테스트는 웹 성능 테스트와 단위 테스트의 컨테이너입니다. **부하 테스트 새로 만들기 마법사**를 사용하여 부하 테스트를 만듭니다.

또한 부하 테스트는 원하는 부하 시뮬레이션을 생성하도록 수정할 수 있는 많은 런타임 속성을 노출합니다. 이 연습에서는 **부하 테스트 새로 만들기 마법사**를 사용하여 부하 테스트에 단위 테스트를 추가합니다.

이 연습에서는 다음 작업을 수행합니다.

- 단위 테스트를 사용하는 부하 테스트를 만듭니다.

- 부하 테스트의 일부 설정을 변경합니다.

- 부하 테스트를 실행합니다.

- 다음의 단계 수행 [연습: 관리 코드에 대한 단위 테스트 만들기 및 실행](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) 일부 단위 테스트가 있는 웹 성능 및 부하 테스트 프로젝트를 포함하는 간단한 C# 클래스 라이브러리를 만듭니다.

## <a name="create-a-load-test-containing-unit-tests-using-the-new-load-test-wizard"></a>부하 테스트 새로 만들기 마법사를 사용하여 단위 테스트를 포함하는 부하 테스트 만들기

### <a name="to-start-the-new-load-test-wizard"></a>부하 테스트 새로 만들기 마법사를 시작하려면

1. [하 테스트 프로젝트 만들기](../test/quickstart-create-a-load-test-project.md)에 설명된 **웹 성능 및 부하 테스트 도구** 구성 요소를 설치했는지 확인합니다.

1. 다음 [에서 만든 Bank 솔루션을 엽니다. 연습: 관리 코드에 대한 단위 테스트 만들기 및 실행](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).

1. **솔루션 탐색기**에서 은행 솔루션 노드의 바로 가기 메뉴를 열고 **추가**를 선택한 다음, **새 프로젝트**를 선택합니다.

     **새 프로젝트 추가** 대화 상자가 표시됩니다.

1. **새 프로젝트 추가** 대화 상자에서 **Visual C#** 을 확장하고, **테스트**를 선택합니다. 템플릿 목록에서 **웹 성능 및 부하 테스트 프로젝트**를 선택하고 **이름** 필드에 `BankLoadTest`를 입력합니다. **확인**을 선택합니다.

     BankLoadTest 웹 성능 및 부하 테스트 프로젝트가 솔루션에 추가됩니다.

1. 새 BankLoadTest 웹 성능 및 부하 테스트 프로젝트의 바로 가기 메뉴를 열고 **추가**를 선택한 다음, **부하 테스트**를 선택합니다.

1. **부하 테스트 새로 만들기 마법사**가 시작됩니다.

1. **부하 테스트 새로 만들기 마법사**의 **시작** 페이지가 첫 번째 페이지입니다.

1. **다음**을 선택합니다.

### <a name="to-edit-settings-for-load-test-scenario"></a>부하 테스트 시나리오의 설정을 편집하려면

1. **부하 테스트 시나리오의 이름 입력** 텍스트 상자에 **ScenarioSample**을 입력합니다.

     *시나리오*는 그룹화 메커니즘으로 테스트 집합과 부하에서 해당 테스트를 실행하기 위한 속성으로 구성됩니다.

2. **프로필 인지 시간**을 `Use normal distribution centered on recorded think times`로 설정합니다. 인지 시간은 사용자가 다음 페이지로 이동하기 전에 웹 페이지를 살펴보는 시간을 나타냅니다.

1. 완료되면 **다음**을 클릭합니다.

### <a name="to-edit-load-pattern-setting-for-test-scenario"></a>테스트 시나리오의 부하 패턴 설정을 편집하려면

1. **단계 부하**를 선택합니다.

    > [!NOTE]
    > 일정 부하와 단계 부하라는 두 가지 부하 패턴 유형 중에서 선택할 수 있습니다. 부하 테스트의 기능에 따라 다른 형식을 사용하지만 이 연습에서는 **단계 부하**를 선택합니다.

2. **시작 사용자 수**를 10명으로 설정합니다.

3. **단계 지속 시간**을 10초로 설정합니다.

4. **단계 사용자 수**를 단계별 10명으로 설정합니다.

5. **최대 사용자 수**를 100명으로 설정합니다.

6. **다음**을 선택합니다.

### <a name="to-select-test-mix-model-for-the-scenario"></a>시나리오에 대한 테스트 조합 모델을 선택하려면

1. **테스트 조합을 모델링하는 방법** 아래에서 **총 테스트 횟수 기반**을 선택합니다.

2. **다음**을 선택합니다.

### <a name="to-add-unit-tests-to-the-scenario"></a>시나리오에 단위 테스트를 추가하려면

1. 다음 단계는 **부하 테스트 시나리오에 테스트 추가 및 테스트 조합 편집**입니다.

2. **추가**를 선택하여 테스트를 선택합니다.

3. 웹 성능 및 부하 테스트 프로젝트의 모든 웹 성능 테스트와 단위 테스트를 나열하는 **사용 가능한 테스트** 창에 나열된 **CreditTest** 단위 테스트를 선택합니다.

4. 화살표 단추를 선택하여 **선택한 테스트** 창에 **CreditTest** 단위 테스트를 추가합니다.

5. **DebitTest** 및 **FreezeAccountTest** 단위 테스트에 대해 3단계와 4단계를 반복합니다.

6. 세 단위 테스트를 모두 추가한 후 **확인**을 선택합니다.

     테스트 조합이 표시됩니다.

7. **CreditTest**에 대한 **분포** 아래의 슬라이더를 오른쪽으로 약간 이동하여 테스트 분포를 조정합니다. 그러면 분포가 100%로 유지되도록 다른 슬라이더가 자동으로 왼쪽으로 이동합니다.

8. **다음**을 선택합니다.

### <a name="to-select-network-mix-for-test-scenario"></a>테스트 시나리오에 대한 네트워크 조합을 선택하려면

1. 네트워크 대역폭 목록에 추가할 LAN 연결 형식을 선택합니다.

     네트워크 형식을 추가할 수 있습니다. 슬라이더를 사용하여 테스트 배포와 가중치를 조정합니다.

2. **다음**을 선택합니다.

### <a name="to-specify-computers-to-monitor-with-counter-sets-during-load-test-run"></a>부하 테스트를 실행하는 동안 카운터 집합으로 모니터링할 컴퓨터를 지정하려면

1. **다음**을 선택합니다.

     카운터 집합에 대한 자세한 내용은 [부하 테스트에서 컴퓨터에 대한 카운터 집합 및 임계값 규칙 지정](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)을 참조하세요.

### <a name="to-edit-run-setting-for-load-test"></a>부하 테스트에 대한 실행 설정을 편집하려면

1. 부하 테스트를 *스모크 테스트*하려면 **부하 테스트 지속 시간**을 선택한 다음, **실행 지속 시간**을 2분으로 설정합니다.

     부하 테스트를 빌드할 때 짧고 간단한 부하 테스트를 실행하여 모두 제대로 구성되었고 예상한 대로 실행되고 있는지 확인하는 것이 좋습니다. 이 프로세스를 *스모크 테스트*라고 합니다.

2. **마침**을 선택합니다. 부하 테스트가 **부하 테스트 편집기**에서 열립니다.

## <a name="run-the-load-test"></a>부하 테스트 실행
 부하 테스트를 만든 다음 이를 실행하여 금융 관련 애플리케이션이 부하 시뮬레이션에 어떻게 반응하는지 확인합니다. 부하 테스트를 실행하는 동안 **부하 테스트 분석기** 창이 표시됩니다.

### <a name="to-run-the-load-test"></a>부하 테스트를 실행하려면

1. **부하 테스트 편집기**에 부하 테스트가 열려 있는 상태에서 도구 모음에서 녹색 **테스트 실행** 단추를 선택합니다. 부하 테스트 실행이 시작됩니다.

2. 테스트 시뮬레이션이 임계값을 초과하면 트리 컨트롤 노드에 아이콘이 표시되어 임계값 위반을 나타냅니다. 오류의 경우에는 빨간색 원이 겹쳐 표시되며 경고의 경우에는 노란색 삼각형이 겹쳐 표시됩니다. 임계값을 초과한 카운터를 찾아 아이콘을 그래프 위로 끌어 그래프로 그릴 수 있습니다. 이 작업은 테스트 실행 중에 수행할 수 있습니다.

## <a name="see-also"></a>참조

- [테스트 조합을 편집하여 부하 테스트 시나리오에 포함할 테스트 지정](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [가상 네트워크 형식 지정](../test/specify-virtual-network-types-in-a-load-test-scenario.md)
- [부하 테스트 시나리오 편집](../test/edit-load-test-scenarios.md)
- [모델 가상 사용자 동작에 대한 부하 패턴 편집](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [텍스트 조합 모델을 편집하여 가상 사용자의 테스트 실행 가능성 지정](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
