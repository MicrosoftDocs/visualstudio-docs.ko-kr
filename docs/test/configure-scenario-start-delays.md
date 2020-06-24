---
title: 부하 테스트의 시나리오 시작 시간 지연 구성
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, scenarios, start delays
ms.assetid: 2f634fba-8dfa-4c7a-a8b9-be867b78d16a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0d425b457056e256c5c9ed927c99adf002b78dd9
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288795"
---
# <a name="configure-scenario-start-delays-in-load-tests"></a>부하 테스트에서 시나리오 시작 시간 지연 구성

부하 테스트 편집기와 **속성** 창을 사용하여 부하 테스트에서 시나리오가 시작되기 전의 지연을 지정합니다.

예를 들어 다른 시나리오에서 사용하는 항목을 만들기 시작할 시나리오가 필요한 경우 **지연 시작 시간** 속성을 사용할 수 있습니다. 항목을 사용하는 시나리오를 지연하여 항목을 만드는 시나리오에 일부 데이터를 만들 시간을 부여할 수 있습니다.

또 다른 예로는 특정 시각에만 실행될 시나리오가 있는 경우를 들 수 있습니다. 시나리오 시작을 지연하여 특정 시간에 시작되도록 만들 수 있습니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-delay-start-time-of-a-scenario"></a>시나리오의 지연 시작 시간 지정

부하 테스트 편집기의 **속성** 창에서 **지연 시작 시간** 속성을 변경하여 부하 테스트에서 시나리오를 시작하기 전의 지연 시간을 지정할 수 있습니다.

> [!NOTE]
> 부하 테스트 시나리오 속성과 해당 설명의 전체 목록을 보려면 [부하 테스트 시나리오 속성](../test/load-test-scenario-properties.md)을 참조하세요.

**지연 시작 시간** 속성을 사용해야 하는 예로는 다른 시나리오가 사용하는 항목을 만들기 시작하는 시나리오가 필요한 경우를 들 수 있습니다. 항목을 사용하는 시나리오를 지연하여 항목을 만드는 시나리오에 일부 데이터를 만들 시간을 부여할 수 있습니다.

또 다른 예로는 특정 시각에만 실행될 시나리오가 있는 경우를 들 수 있습니다. 시나리오 시작을 지연하여 특정 시간에 시작되도록 만들 수 있습니다.

> [!NOTE]
> 실행 설정 속성의 전체 목록과 해당 설명을 보려면 [부하 테스트 시나리오 속성](../test/load-test-scenario-properties.md)을 참조하세요.

### <a name="to-specify-the-delay-start-time-for-a-scenario"></a>시나리오의 지연 시작 시간을 지정하려면

1. 부하 테스트를 엽니다.

     부하 테스트 편집기가 나타납니다. 부하 테스트 트리가 표시됩니다.

2. 부하 테스트 트리 **시나리오** 폴더에서 지연 시작 시간을 지정할 시나리오 노드를 선택합니다.

3. **보기** 메뉴에서 **속성 창**을 선택합니다.

     시나리오의 범주와 속성이 **속성** 창에 표시됩니다.

4. 부하 테스트가 실행될 때 부하 테스트 시작 후 어느 정도의 시간을 기다렸다가 시나리오를 시작할 것인지를 나타내는 시간 값을 **지연 시작 시간** 속성의 텍스트 상자에 입력합니다.

    > [!NOTE]
    > 시나리오에 대한 **준비 시간 동안 사용 안 함** 속성의 값이 **True**로 설정되어 있으면 **지연 시작 시간** 속성 시간 값이 준비 기간 이후에 적용됩니다. **준비 시간 동안 사용 안 함** 시나리오 속성을 사용하여 준비에 포함될 시나리오를 제어할 수 있습니다.

5. 속성을 변경한 후 **파일** 메뉴에서 **저장**을 선택합니다. 그러면 새 **지연 시작 시간** 값을 사용하여 부하 테스트를 실행할 수 있습니다.

## <a name="enable-and-disable-whether-a-scenario-runs-during-the-warm-up-period"></a>준비 시간 동안 시나리오 실행 사용 및 사용 안 함

**준비 시간 동안 사용 안 함** 속성은 **속성** 창을 사용하여 설정할 수 있습니다. 부하 테스트 시나리오 속성은 부하 테스트 편집기에서 편집하여 설정할 수 있습니다.

**준비 시간 동안 사용 안 함** 속성은 **지연 시작 시간** 속성에 지정한 준비 기간 동안 시나리오를 실행해야 하는지 여부를 나타내는 데 사용됩니다. 자세한 내용은 이전 절차인 [시나리오의 지연 시작 시간 지정](#specify-the-delay-start-time-of-a-scenario)을 검토하세요.

> [!NOTE]
> 실행 설정 속성의 전체 목록과 해당 설명을 보려면 [부하 테스트 시나리오 속성](../test/load-test-scenario-properties.md)을 참조하세요.

### <a name="to-enable-or-disable-the-warm-up-period-for-a-scenario"></a>시나리오의 준비 기간을 사용하거나 사용하지 않도록 설정하려면

1. 부하 테스트를 엽니다.

     **부하 테스트 편집기**가 나타납니다. 부하 테스트 트리가 표시됩니다.

2. 부하 테스트 트리 **시나리오** 폴더에서 준비 동작을 변경할 시나리오 노드를 선택합니다.

3. **보기** 메뉴에서 **속성 창**을 선택합니다.

     시나리오의 범주와 속성이 **속성** 창에 표시됩니다.

     **준비 시간 동안 사용 안 함** 속성에서 **True** 또는 **False**를 선택합니다.

4. 속성 변경을 마친 다음, **파일** 메뉴에서 **저장**을 선택합니다. 그러면 새 **준비 시간 동안 사용 안 함** 값을 사용하여 부하 테스트를 실행할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [부하 테스트 시나리오 편집](../test/edit-load-test-scenarios.md)
- [부하 테스트에 대한 데스트 에이전트 및 테스트 컨트롤러 구성](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [부하 테스트 시나리오 속성](../test/load-test-scenario-properties.md)
