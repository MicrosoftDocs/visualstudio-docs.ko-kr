---
title: 부하 테스트를 위한 카운터 세트에 대한 카운터 추가
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: e17d0e71-f982-4fc1-a2df-a1065d37473d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 754c88bd6dbe76736148718d2f1ad32888623c34
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288379"
---
# <a name="how-to-add-counters-to-counter-sets-using-the-load-test-editor"></a>방법: 부하 테스트 편집기를 사용하여 카운터 집합에 카운터 추가

**부하 테스트 마법사**를 사용하여 부하 테스트를 만들 때 초기 카운터 집합을 추가합니다. 이때 부하 테스트에 사용할 미리 정의된 카운터 집합이 제공됩니다. 자세한 내용은 [부하 테스트에서 컴퓨터에 대한 카운터 집합 및 임계값 규칙 지정](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)을 참조하세요.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> 부하 테스트가 원격 컴퓨터에 분산된 경우 컨트롤러 및 에이전트 카운터가 컨트롤러 및 에이전트 카운터 집합에 매핑됩니다. 부하 테스트에서 원격 컴퓨터를 사용하는 방법에 대한 자세한 내용은 [테스트 컨트롤러 및 테스트 에이전트](configure-test-agents-and-controllers-for-load-tests.md)를 참조하세요.

**부하 테스트 편집기**에서 카운터를 관리합니다. 테스트에 이미 추가된 카운터 집합은 부하 테스트의 **카운터 집합** 노드에 표시됩니다. 부하 테스트를 만든 후 기존 카운터 집합에 새 카운터를 추가할 수 있습니다.

## <a name="to-add-counters-to-a-counter-set"></a>카운터 집합에 카운터를 추가하려면

1. 부하 테스트를 엽니다.

2. **카운터 집합** 노드를 확장합니다. 부하 테스트에 추가된 모든 카운터 집합을 볼 수 있습니다.

    > [!NOTE]
    > 부하 테스트 계층 구조 트리에는 **실행 설정** 노드도 들어 있습니다. 이 노드에는 모든 컴퓨터 및 해당 컴퓨터에 매핑된 카운터 집합을 보여 주는 **카운터 집합 매핑** 노드가 들어 있습니다.

3. 기존 카운터 집합을 마우스 오른쪽 단추로 클릭한 다음, **카운터 추가**를 선택합니다.

     **성능 카운터 선택** 대화 상자가 표시됩니다.

4. **컴퓨터** 드롭다운 콤보 상자에서 매핑할 컴퓨터 이름을 입력합니다. 또는 드롭다운 목록에 있는 컴퓨터 중 하나를 선택합니다.

    > [!NOTE]
    > 카운터 집합을 컴퓨터에 매핑해야 성능 데이터를 수집할 수 있으므로 성능 데이터를 수집할 컴퓨터를 지정해야 합니다.

5. **성능 범주**를 선택하여 성능 데이터 카운터 범주를 필터링합니다. 성능 카운터를 선택할 수 있는 두 개의 데이터 열이 표시됩니다.

    > [!NOTE]
    > 일부 카운터 범주의 경우 인스턴스를 함께 선택해야 합니다. 예를 들어 SQL 카운터를 선택한 경우 대상 컴퓨터에 SQL 인스턴스가 둘 이상 설치되어 있을 수 있으므로 SQL 인스턴스를 선택해야 합니다.

6. 카운터와 인스턴스를 선택하여 사용자 지정 카운터 집합에 추가합니다.

     \- 또는-

     **모든 카운터** 라디오 단추를 선택하여 사용 가능한 카운터를 모두 선택합니다.

7. **확인**을 선택합니다.

    > [!NOTE]
    > 기존 카운터 또는 카운터 범주를 선택하고 복사를 선택한 다음, 다른 카운터 집합 노드에 붙여넣어 카운터 집합에 카운터를 추가할 수도 있습니다. 필요하지 않은 카운터가 추가로 복사된 경우 이를 삭제할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [부하 테스트에서 컴퓨터에 대한 카운터 집합 및 임계값 규칙 지정](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [부하 테스트 실행 설정 구성](../test/configure-load-test-run-settings.md)
