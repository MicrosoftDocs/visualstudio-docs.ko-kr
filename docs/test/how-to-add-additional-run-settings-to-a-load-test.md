---
title: 부하 테스트에 실행 설정 추가
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, run settings, adding
- load tests, run settings
ms.assetid: 257d2a24-d582-4cfe-8b2b-51f51ba9cc84
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a2f62b3e9797e411138590fc15b0fe872920d203
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288457"
---
# <a name="how-to-add-additional-run-settings-to-a-load-test"></a>방법: 부하 테스트에 실행 설정 추가

부하 테스트의 실행 설정을 통해 다양한 설정을 지정할 수 있습니다. 실행 설정에는 테스트 기간, 결과 컬렉션 세부 수준 및 테스트 실행 시 수집되는 카운터 집합이 포함됩니다. 부하 테스트마다 여러 실행 설정을 만들어 저장한 다음 테스트를 실행할 때 특정 설정을 하나 선택하여 사용할 수 있습니다. **부하 테스트 새로 만들기 마법사**를 사용하여 부하 테스트를 만들 때 초기 실행 설정이 부하 테스트에 추가됩니다.

여러 가지 조건에서 부하 테스트를 실행할 수 있도록 속성을 다르게 설정하여 더 많은 실행 설정을 부하 테스트에 추가할 수 있습니다. 예를 들어 새 테스트 설정을 추가하면서 샘플링 주기를 다르게 지정하거나, 실행 기간을 더 길게 지정할 수 있습니다. 실행 설정은 한 번에 하나만 사용할 수 있으며, 사용할 실행 설정을 활성 상태로 표시하여 지정해야 합니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-another-run-setting"></a>다른 실행 설정을 추가하려면

1. 부하 테스트를 엽니다.

2. (선택 사항) **실행 설정** 폴더를 확장합니다.

3. **실행 설정** 폴더를 마우스 오른쪽 단추로 클릭한 다음, **실행 설정 추가**를 선택합니다.

     새 실행 설정이 **실행 설정** 폴더에 추가됩니다.

4. **보기** 메뉴에서 **속성 창**을 선택합니다.

     **속성** 창이 선택한 실행 설정의 속성과 함께 표시됩니다.

5. **속성** 창에서 **이름** 속성의 텍스트 상자를 사용하여 **실행 설정: 5분 실행**과 같이 실행 설정의 의도를 설명하는 이름을 새 실행 설정에 지정합니다.

6. **속성** 창을 사용하여 실행 설정을 변경합니다. 예를 들어 실행 지속 시간을 **00:05:00**으로 변경하여 테스트를 5분간 실행합니다.

    > [!NOTE]
    > 실행 설정 속성의 전체 목록과 해당 설명을 보려면 [부하 테스트 실행 설정 속성](../test/load-test-run-settings-properties.md)을 참조하세요.

     추가된 실행 설정을 활성 상태로 설정하여 해당 설정을 사용하도록 지정할 수 있습니다. 자세한 내용은 [방법: 부하 테스트에 대한 활성 실행 설정 선택](../test/how-to-select-the-active-run-setting-for-a-load-test.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [부하 테스트 실행 설정 구성](../test/configure-load-test-run-settings.md)
- [부하 테스트에서 컴퓨터에 대한 카운터 집합 및 임계값 규칙 지정](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
