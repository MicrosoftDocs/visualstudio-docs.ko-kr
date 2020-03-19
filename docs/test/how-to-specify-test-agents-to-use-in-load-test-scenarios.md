---
title: 부하 테스트 시나리오에서 사용할 테스트 에이전트 지정
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- test agents, load tests
- load tests, scenarios
- load tests, specifying for load tests
- tests agents, load tests, specifying
- load tests, test agents
ms.assetid: e86806dd-5897-4e4c-bfd4-8d687fb72a6e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d23d565752d81bff960027090ddaaf88e9d78ed5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588930"
---
# <a name="how-to-specify-test-agents-to-use-in-load-test-scenarios"></a>방법: 부하 테스트 시나리오에서 사용할 테스트 에이전트 지정

**부하 테스트 새로 만들기 마법사**를 사용하여 부하 테스트를 만든 다음, **부하 테스트 편집기**를 사용하여 시나리오 속성을 테스트 요구 사항 및 목표에 맞게 변경할 수 있습니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> 부하 테스트 시나리오 속성과 해당 설명의 전체 목록을 보려면 [부하 테스트 시나리오 속성](../test/load-test-scenario-properties.md)을 참조하세요.

에이전트는 **속성** 창에서 **사용할 에이전트 속성**을 변경하도록 **부하 테스트 편집기**를 사용하여 지정할 수 있습니다.

컨트롤러 및 에이전트를 사용하여 부하 테스트를 원격으로 실행하려는 경우 시나리오에서 사용할 에이전트를 지정할 수 있습니다. 예를 들어 특정 에이전트 집합을 지정하여 성능 추세를 분석할 때 일관성을 유지할 수 있습니다. 또한 에이전트는 지리적으로 분산되어 있을 수 있으므로 에이전트에서 실행하는 스크립트와 에이전트가 있는 위치 간에 밀접한 관계가 있습니다.

> [!TIP]
> 에이전트를 원격 사이트에 실제로 배치하지 않고 네트워크 에뮬레이션을 사용하여 느린 네트워크를 에뮬레이션할 수도 있습니다. 자세한 내용은 [가상 네트워크 형식 지정](../test/specify-virtual-network-types-in-a-load-test-scenario.md)을 참조하세요.

자세한 내용은 [테스트 컨트롤러 및 테스트 에이전트](configure-test-agents-and-controllers-for-load-tests.md)를 참조하세요.

특정 시나리오에 필요한 소프트웨어가 에이전트 전부가 아닌 일부에 설치되어 있다는 것 역시 이유 중 하나입니다.

테스트 설정에서 역할을 사용하여 지정한 테스트 실행에 대한 에이전트 선택을 제어할 수 있습니다. 자세한 내용은 [테스트 설정을 사용하여 진단 정보 수집](../test/collect-diagnostic-information-using-test-settings.md)을 참조하세요.

테스트 에이전트 컴퓨터의 CPU 사용률이 75%를 넘거나 사용 가능한 실제 메모리가 10% 미만인 경우, 부하 테스트에서 에이전트 컴퓨터로 인해 병목 현상이 발생하지 않도록 부하 테스트에 에이전트를 추가해야 합니다.

## <a name="to-specify-the-agents-to-use-for-a-scenario"></a>시나리오에 사용할 에이전트를 지정하려면

1. 부하 테스트를 엽니다.

     **부하 테스트 편집기**가 나타납니다. 부하 테스트 트리가 표시됩니다.

2. 부하 테스트 트리 **시나리오** 폴더에서 사용할 에이전트를 지정할 시나리오 노드를 선택합니다.

3. **보기** 메뉴에서 **속성 창**을 선택합니다.

     시나리오의 범주와 속성이 **속성** 창에 표시됩니다.

4. **사용할 에이전트** 속성의 텍스트 상자에 시나리오가 실행될 수 있는 에이전트 목록을 입력합니다.

     에이전트는 "**Agent1, Agent2, Agent3**"과 같이 쉼표로 구분해야 합니다. 속성을 공백으로 두면 시나리오에서 사용 가능한 모든 에이전트를 사용하도록 지정됩니다.

    > [!NOTE]
    > 로컬 실행의 경우에는 **사용할 에이전트** 속성이 무시됩니다. 원격 실행의 경우에는 **사용할 에이전트**에 에이전트가 지정되어 있지 않으면 시나리오의 테스트가 실행되지 않습니다.

5. 속성을 변경한 후 **파일** 메뉴에서 **저장**을 선택합니다. 그러면 새 **사용할 에이전트** 값을 사용하여 부하 테스트를 실행할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [부하 테스트 시나리오 편집](../test/edit-load-test-scenarios.md)
- [연습: 부하 테스트 생성 및 실행](../test/walkthrough-create-and-run-a-load-test.md)
- [테스트 컨트롤러 및 테스트 에이전트](configure-test-agents-and-controllers-for-load-tests.md)
- [부하 테스트 시나리오 속성](../test/load-test-scenario-properties.md)
