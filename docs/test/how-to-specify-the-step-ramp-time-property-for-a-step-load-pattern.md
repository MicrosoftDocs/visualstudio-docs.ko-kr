---
title: 부하 테스트에 대한 단계 부하 패턴의 단계 진입 시간
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
ms.assetid: 4a69e857-f93b-4907-9a01-fd1b66291205
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a40f7ce4aacfdc03b5e05becbfc83439945f7e8a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588917"
---
# <a name="how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern"></a>방법: 단계 부하 패턴에 대한 단계 진입 시간 속성 지정

**부하 테스트 새로 만들기 마법사**를 사용하여 부하 테스트를 만든 다음, **부하 테스트 편집기**를 사용하여 시나리오 속성을 테스트 요구 사항 및 목표에 맞게 변경할 수 있습니다. 자세한 내용은 [연습: 부하 테스트 만들기 및 실행](../test/walkthrough-create-and-run-a-load-test.md)을 참조하세요.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> 부하 테스트 시나리오 속성과 해당 설명의 전체 목록을 보려면 [부하 테스트 시나리오 속성](../test/load-test-scenario-properties.md)을 참조하세요.

**단계 진입 시간** 속성은 **속성** 창에서 설정합니다. **부하 테스트 편집기**에서는 부하 테스트 시나리오 속성을 편집합니다.

**단계 진입 시간** 속성은 단계 부하 패턴에만 사용됩니다. 자세한 내용은 [부하 패턴을 편집하여 가상 사용자 작업 모델링](../test/edit-load-patterns-to-model-virtual-user-activities.md)을 참조하세요.

단계 부하 패턴은 사용자 부하가 증가함에 따라 성능이 어떻게 달라지는지를 확인할 수 있도록 부하 테스트가 실행되는 도중 서버의 부하를 증가시키는 데 사용합니다. 예를 들어 사용자 부하가 사용자 수 2,000명으로 증가할 때 서버의 성능을 확인하기 위해 다음 속성이 설정된 단계 부하 패턴을 사용하여 10시간 동안 부하 테스트를 실행할 수 있습니다.

- 초기 사용자 수: 100

- 최대 사용자 수: 2,000

- 단계 지속 시간(초): 1,800

- 단계 진입 시간(초): 20

- 단계 사용자 수: 100

이러한 설정을 사용하면 30분(1,800초) 동안 사용자 수가 100명, 200명, 300명에서 최대 2,000명인 사용자 부하 상태로 부하 테스트가 실행됩니다.

> [!NOTE]
> **단계 진입 시간** 속성은 이러한 속성 중 유일하게 **부하 테스트 새로 만들기 마법사**에서 사용할 수 없는 속성입니다.

**단계 진입 시간** 속성을 사용하면 사용자 수를 100명에서 200명으로 늘리는 것과 같이 한 단계에서 다음 단계로 부하를 증가시키는 작업이 즉각적으로가 아니라 점차적으로 이루어지도록 할 수 있습니다. 이 예에서는 20초 동안 사용자 부하가 100명에서 200명으로 증가하므로 1초에 5명씩 사용자가 늘어납니다.

## <a name="to-edit-the-step-ramp-time-property-for-a-step-load-pattern"></a>단계 부하 패턴의 단계 진입 시간 속성을 편집하려면

1. 부하 테스트를 엽니다.

     **부하 테스트 편집기**가 나타납니다. 부하 테스트 트리가 표시됩니다.

2. 부하 테스트 트리 **시나리오** 폴더에서 단계 진입 시간을 지정할 시나리오 노드를 엽니다.

3. **단계 부하 패턴** 노드를 선택합니다.

    > [!NOTE]
    > 시나리오의 부하 패턴이 단계 부하 패턴이어야 합니다. 그렇지 않으면 시나리오와 현재 연결되어 있는 부하 패턴 유형이 부하 패턴에 표시됩니다. 자세한 내용은 [부하 패턴을 편집하여 가상 사용자 작업 모델링](../test/edit-load-patterns-to-model-virtual-user-activities.md)을 참조하세요.

4. **보기** 메뉴에서 **속성 창**을 선택합니다.

     시나리오의 범주와 속성이 **속성** 창에 표시됩니다.

5. 각 단계에서 **단계 사용자 수** 속성에 지정된 수의 사용자를 추가하는 데 소요되는 시간(초)을 입력하여 **단계 진입 시간** 속성 값을 설정합니다.

6. 속성 변경을 마친 다음, **파일** 메뉴에서 **저장**을 선택합니다. 그러면 새 **단계 진입 시간** 값을 사용하여 부하 테스트를 실행할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [부하 테스트 시나리오 편집](../test/edit-load-test-scenarios.md)
- [테스트 컨트롤러 및 테스트 에이전트](configure-test-agents-and-controllers-for-load-tests.md)
- [부하 테스트 시나리오 속성](../test/load-test-scenario-properties.md)
- [모델 가상 사용자 동작에 대한 부하 패턴 편집](../test/edit-load-patterns-to-model-virtual-user-activities.md)
