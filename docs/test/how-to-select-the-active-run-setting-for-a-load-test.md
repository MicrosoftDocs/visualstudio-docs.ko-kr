---
title: 부하 테스트에 대한 실행 설정 선택
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings, active
ms.assetid: ed6ff546-acfa-4dd8-b3a2-6e7455930ca4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 91ac811c1f55fdb9a662db679ebd2d038ecdd5dd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588982"
---
# <a name="how-to-select-the-active-run-setting-for-a-load-test"></a>방법: 부하 테스트에 대한 활성 실행 설정 선택

**부하 테스트 새로 만들기 마법사**를 사용하여 부하 테스트를 만든 다음, **부하 테스트 편집기**를 사용하여 시나리오 속성을 테스트 요구 사항 및 목표에 맞게 변경할 수 있습니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

부하 테스트에는 부하 테스트가 실행되는 방식에 영향을 미치는 속성 집합인 *실행 설정*이 하나 이상 포함될 수 있습니다. 실행 설정은 **속성** 창에서 범주별로 구성됩니다. 부하 테스트가 실행될 때 현재 활성 상태로 설정되어 있는 실행 설정이 사용됩니다.

> [!NOTE]
> 실행 설정 속성의 전체 목록과 해당 설명을 보려면 [부하 테스트 실행 설정 속성](../test/load-test-run-settings-properties.md)을 참조하세요.

부하 테스트의 **실행 설정** 폴더 아래에 실행 설정 노드가 하나만 있는 경우 해당 노드가 항상 활성 노드가 됩니다. 부하 테스트에 여러 실행 설정 노드가 있는 경우에는 부하 테스트를 실행할 때 사용할 노드 하나를 선택할 수 있습니다. [방법: 부하 테스트에 실행 설정 추가](../test/how-to-add-additional-run-settings-to-a-load-test.md)를 참조하세요.

**부하 테스트 편집기**에서 활성 실행 설정은 "[Active]" 접미사로 식별됩니다.

## <a name="select-the-active-run-setting"></a>활성 실행 설정 선택

1. 부하 테스트를 엽니다.

2. **실행 설정** 폴더를 확장합니다.

3. 활성화할 실행 설정 노드를 마우스 오른쪽 단추로 클릭한 다음, **활성 상태로 설정**을 선택합니다.

     **부하 테스트 편집기**에서 영향을 받는 실행 설정 노드는 "[Active]" 접미사로 업데이트됩니다.

     선택한 실행 설정은 활성화되고 다른 실행 설정을 선택하여 활성화할 때까지 활성 상태로 유지됩니다.

> [!NOTE]
> `Test.UseRunSetting=<run setting name>`이라는 환경 변수를 설정하면 활성 실행 설정을 재정의할 수 있습니다. 이 방법은 명령줄이나 배치 파일을 통해 부하 테스트를 실행하는 경우에 유용합니다. 이렇게 하면 부하 테스트를 열지 않고도 다른 실행 설정을 선택할 수 있습니다.

## <a name="specify-the-run-setting-to-use-from-the-command-line"></a>명령줄에서 사용할 실행 설정 지정

명령줄에서 환경 변수를 설정하여 부하 테스트의 기본 실행 설정을 재정의할 수 있습니다.

**Test.UseRunSetting=PreProdEnvironment 설정**

또한 테스트를 실행하려면:

**mstest /testcontainer:loadtest1.loadtest**

## <a name="see-also"></a>참고 항목

- [부하 테스트 실행 설정 구성](../test/configure-load-test-run-settings.md)
- [부하 테스트에서 컴퓨터에 대한 카운터 집합 및 임계값 규칙 지정](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [방법: 부하 테스트에 실행 설정 추가](../test/how-to-add-additional-run-settings-to-a-load-test.md)
