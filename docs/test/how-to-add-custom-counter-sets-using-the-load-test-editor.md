---
title: 부하 테스트에 대한 사용자 지정 카운터 집합 추가
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: 499aca80-1069-408d-ac68-326da6a50645
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f7438f657af2ba40fbda5afefbd8a12cc56a2a4c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114876"
---
# <a name="how-to-add-custom-counter-sets-using-the-load-test-editor"></a>방법: 부하 테스트 편집기를 사용하여 사용자 지정 카운터 집합 추가

**부하 테스트 새로 만들기 마법사**를 사용하여 부하 테스트를 만들 때 초기 카운터 집합을 추가합니다. 이때 부하 테스트에 사용할 미리 정의된 카운터 집합이 제공됩니다.

> [!NOTE]
> 부하 테스트가 원격 컴퓨터에 분산된 경우 컨트롤러 및 에이전트 카운터가 컨트롤러 및 에이전트 카운터 집합에 매핑됩니다. 부하 테스트에서 원격 컴퓨터를 사용하는 방법에 대한 자세한 내용은 [테스트 컨트롤러 및 테스트 에이전트](configure-test-agents-and-controllers-for-load-tests.md)를 참조하세요.

**부하 테스트 편집기**에서 카운터를 관리합니다. 테스트에 이미 추가된 카운터 집합은 부하 테스트의 **카운터 집합** 노드에 표시됩니다. 부하 테스트를 만든 후 사용자 지정 카운터 집합을 새로 추가할 수 있습니다.

![사용자 지정 카운터 집합](../test/media/loadtestcustomcounter.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-custom-counter-set-to-a-load-test"></a>부하 테스트에 사용자 지정 카운터 집합을 추가하려면

1. 부하 테스트를 엽니다.

2. **카운터 집합** 노드를 확장합니다. 부하 테스트에 추가된 모든 카운터 집합을 볼 수 있습니다.

3. **카운터 집합** 노드를 마우스 오른쪽 단추로 클릭하고 **사용자 지정 카운터 집합 추가**를 선택합니다.

    > [!NOTE]
    > 카운터 집합에 **Custom1** 등의 기본 이름이 지정됩니다. **속성** 창을 사용하여 이 이름을 변경할 수 있습니다. **F4** 키를 눌러 **속성** 창을 표시합니다.

4. 사용자 지정 카운터 집합에 카운터를 추가하려면 새 카운터 집합을 마우스 오른쪽 단추로 클릭하고 **카운터 추가**를 선택합니다. 카운터를 추가하는 방법에 대한 자세한 내용은 [방법: 카운터 집합에 카운터 추가](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md)를 참조하세요.

    > [!NOTE]
    > 기존 카운터 집합을 마우스 오른쪽 단추로 클릭하고 복사를 선택한 다음 카운터 집합 노드에 붙여 넣어 사용자 지정 카운터 집합을 추가할 수도 있습니다. 필요하지 않은 카운터가 추가로 복사된 경우 이를 삭제할 수 있습니다. **속성** 창을 사용하여 새 카운터 집합의 이름을 변경할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [부하 테스트에서 컴퓨터에 대한 카운터 집합 및 임계값 규칙 지정](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [부하 테스트 실행 설정 구성](../test/configure-load-test-run-settings.md)
