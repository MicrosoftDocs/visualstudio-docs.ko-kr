---
title: 부하 테스트에 대한 테스트 반복 구성
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios, iterations
- load test, iterations
- load tests, scenarios
ms.assetid: ac480fb7-f4f7-47dc-9ae5-98be3aca4fba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e95ca27ace50c7b28d1ffb1d3fc02589daddee2d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590984"
---
# <a name="configure-test-iterations-in-a-load-test-scenario"></a>부하 테스트 시나리오에서 테스트 반복 구성

테스트 반복 설정을 구성하려면 부하 테스트 편집기 및 **속성** 창을 사용하여 부하 테스트 시나리오를 편집합니다. 기본적으로 부하 테스트 시나리오는 최대 테스트 반복 횟수를 지정하지 않고 설정됩니다. 필요할 경우 시나리오의 최대 반복 횟수와 반복 간 일시 중지 시간을 구성할 수 있습니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-maximum-test-iterations-for-a-scenario"></a>시나리오에 대한 최대 테스트 반복 횟수 지정

부하 테스트 편집기의 **속성** 창에서 **최대 테스트 반복 횟수** 속성을 변경하여 시나리오의 테스트에 대해 원하는 최대 실행 횟수를 지정할 수 있습니다.

**최대 테스트 반복 횟수** 속성은 시나리오에 대해 실행할 최대 테스트 반복 횟수를 제어합니다. 이 수치는 부하 테스트 실행 설정의 **테스트 반복** 속성과 마찬가지로 한 사용자에 대한 설정이 아니라 모든 에이전트에서 모든 사용자가 실행할 수 있는 최대값입니다.

> [!NOTE]
> 부하 테스트 시나리오 속성과 해당 설명의 전체 목록을 보려면 [부하 테스트 시나리오 속성](../test/load-test-scenario-properties.md)을 참조하세요.

순차적인 테스트 조합의 경우에는 조합 내 모든 테스트가 실행되어야 한 번의 반복으로 계산됩니다. 다른 모든 테스트 조합에서는 한 번의 테스트 실행이 한 번의 반복으로 계산됩니다. 자세한 내용은 [목록 컨트롤 정보](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)를 참조하십시오.

부하 테스트가 지속 시간 중심의 부하 테스트이고 반복 수가 완료되기 전에 지속 시간이 만료되는 경우 테스트는 중지됩니다. 테스트가 반복 중심이고 최대 시나리오 반복 횟수에 도달하기 전에 최대 테스트 반복 횟수에 도달하는 경우 테스트는 중지됩니다. 지속 시간은 부하 테스트에서 실행 설정과 연결된 **속성** 창의 **실행 지속 시간** 속성을 사용하여 구성합니다.

최대 시나리오 반복 횟수에 도달하면 시나리오가 중지되지만 다른 활성 시나리오는 계속 실행됩니다.

> [!NOTE]
> 관련 속성은 웹 테스트 데이터 소스에 있는 **Unique** 속성으로서 데이터에서 행 단위로 순차적으로 이동하지만 한 레코드에서 한 번만 이동합니다. 자세한 내용은 [웹 성능 테스트에 데이터 소스 추가](../test/add-a-data-source-to-a-web-performance-test.md)를 참조하세요.

**최대 테스트 반복 횟수** 속성은 다양한 상황에 유용합니다. 일부 부하 테스터는 반복 중심의 테스트를 선호하는 반면, 다른 부하 테스터는 지속 시간 중심의 테스트를 선호합니다.

![시나리오의 테스트 반복 횟수 지정](../test/media/loadtest_prop.png)

### <a name="to-specify-the-maximum-test-iterations"></a>최대 테스트 반복 횟수를 지정하려면

1. 부하 테스트를 엽니다.

2. 부하 테스트 편집기가 나타납니다. 부하 테스트 트리가 표시됩니다.

3. 부하 테스트 트리 **시나리오** 폴더에서 최대 테스트 반복 횟수를 지정할 시나리오 노드를 선택합니다.

4. **보기** 메뉴에서 **속성 창**을 선택합니다.

     시나리오의 범주와 속성이 **속성** 창에 표시됩니다.

5. 부하 테스트가 실행될 때 시나리오에 대해 실행할 최대 테스트 횟수를 나타내는 값을 **최대 테스트 반복 횟수** 속성의 텍스트 상자에 입력합니다.

    > [!NOTE]
    > **최대 테스트 반복 횟수** 속성에 0 값을 사용하면 최대 반복 횟수를 없음으로 지정하는 것입니다.

6. 속성 변경을 마친 다음, **파일** 메뉴에서 **저장**을 선택합니다. 그러면 새 **최대 테스트 반복 횟수** 값을 사용하여 부하 테스트를 실행할 수 있습니다.

## <a name="specify-think-times-between-test-iterations-for-a-scenario"></a>시나리오의 테스트 반복 간 인지 시간 지정

**테스트 반복 간 인지 시간** 속성은 부하 테스트 편집기에서 부하 테스트 시나리오 속성을 편집할 때 **속성** 창을 사용하여 설정합니다.

**테스트 반복 간 인지 시간** 속성은 테스트 반복을 시작하기 전에 대기할 시간(초)을 지정하는 데 사용합니다.

> [!NOTE]
> 부하 테스트 시나리오 속성의 전체 목록과 해당 설명을 보려면 [부하 테스트 시나리오 속성](../test/load-test-scenario-properties.md)을 참조하세요.

### <a name="to-specify-the-think-time-between-test-iterations"></a>시나리오의 테스트 반복 간 인지 시간을 지정하려면

1. 부하 테스트를 엽니다.

     **부하 테스트 편집기**가 나타납니다. 부하 테스트 트리가 표시됩니다.

2. 부하 테스트 트리 **시나리오** 폴더에서 인지 시간을 지정할 시나리오 노드를 선택합니다.

3. **보기** 메뉴에서 **속성 창**을 선택합니다.

     시나리오의 범주와 속성이 **속성** 창에 표시됩니다.

4. **테스트 반복 간 인지 시간** 속성 값에 다음 테스트 반복을 시작하기 전에 대기할 시간(초)을 나타내는 숫자를 입력합니다.

5. 속성 변경을 마친 다음, **파일** 메뉴에서 **저장**을 선택합니다. 그러면 새 **테스트 반복 간 인지 시간** 값을 사용하여 부하 테스트를 실행할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [부하 테스트 시나리오 편집](../test/edit-load-test-scenarios.md)
- [부하 테스트에 대한 데스트 에이전트 및 테스트 컨트롤러 구성](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [부하 테스트 시나리오 속성](../test/load-test-scenario-properties.md)
- [인지 시간을 편집하여 웹 사이트 사용자 상호 작용 지연 시뮬레이션](../test/edit-think-times-in-load-test-scenarios.md)
