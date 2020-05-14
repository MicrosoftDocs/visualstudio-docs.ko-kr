---
title: 부하 테스트의 인지 시간
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, think times
- load tests, adding delays
- load tests, changing think times
ms.assetid: 8e03bee5-ab7b-4b40-9497-9dbe91ccb90e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 887d2af9e60be914bd74141041ecc375cfea4f00
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590035"
---
# <a name="edit-think-times-to-simulate-website-human-interaction-delays-in-load-tests-scenarios"></a>부하 테스트 시나리오에서 인지 시간을 편집하여 웹 사이트 사용자 상호 작용 지연 시뮬레이트

인지 시간을 사용하여 웹 사이트와의 상호 작용 간에 대기하게 되는 사람의 동작을 시뮬레이트할 수 있습니다. 인지 시간은 웹 성능 테스트의 요청 간이나 부하 테스트 시나리오의 테스트 반복 간에 발생합니다. 부하 테스트에서 인지 시간 사용은 보다 정확한 부하 시뮬레이션을 만드는 데 유용합니다. 부하 테스트에서 인지 시간을 사용할 것인지, 아니면 인지 시간을 무시할 것인지 여부를 변경할 수 있습니다. **부하 테스트 편집기**에서 인지 시간을 부하 테스트에 사용할지 여부를 변경합니다.

*인지 시간 프로필*은 부하 테스트의 시나리오에 적용되는 설정입니다. 이 설정은 개별 웹 성능 테스트에 저장된 인지 시간을 부하 테스트 중에 사용할지 여부를 결정합니다. 일부 웹 성능 테스트에서만 인지 시간을 사용하려면 웹 테스트를 서로 다른 시나리오에 넣어야 합니다. 시나리오에 대한 자세한 내용은 [부하 테스트 시나리오 편집](../test/edit-load-test-scenarios.md)을 참조하세요.

**부하 테스트 새로 만들기 마법사**를 사용하여 부하 테스트를 만드는 경우 처음에 부하 테스트에 인지 시간을 사용할지 여부를 설정합니다. 자세한 내용은 [부하 테스트 시나리오 편집](../test/edit-load-test-scenarios.md)을 참조하세요.

다음 목록에서는 **인지 시간 프로필** 옵션을 보여줍니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Off**

인지 시간이 무시됩니다. 최대 부하를 생성하여 웹 서버를 최대한 이용하려면 이 설정을 사용합니다. 사용자와 웹 서버 간에 보다 현실적인 상호 작용을 만들려면 이 설정을 사용하지 마세요.

**위치**

인지 시간이 웹 성능 테스트에 기록된 대로 정확히 사용됩니다. 웹 성능 테스트를 실행하는 여러 사용자를 기록된 대로 정확하게 시뮬레이트합니다. 부하 테스트에서는 여러 사용자를 시뮬레이션하므로 동일한 인지 시간을 사용하면 동기화된 여러 가상 사용자에 대해 부자연스러운 부하 패턴이 만들어질 수 있습니다.

**정규 분포**

정규 분포 곡선에 따라 달라지는 인지 시간이 사용됩니다. 요청 간에 인지 시간을 조금씩 달리 하여 가상 사용자에 대해 보다 현실적인 시뮬레이션을 제공합니다.

> [!NOTE]
> 부하 테스트 시나리오 속성의 전체 목록과 해당 설명을 보려면 [부하 테스트 시나리오 속성](../test/load-test-scenario-properties.md)을 참조하세요.

## <a name="change-the-think-profile"></a>인지 시간 프로필 변경

### <a name="to-change-a-think-profile-in-a-load-test-scenario"></a>부하 테스트 시나리오에서 인지 시간 프로필을 변경하려면

1. 웹 성능 및 부하 테스트 프로젝트에서 부하 테스트를 엽니다.

2. **부하 테스트 편집기**에서 **인지 시간 프로필**을 변경하려는 시나리오 노드를 선택합니다. **속성** 창에 **인지 시간 프로필**이 표시됩니다. **F4** 키를 눌러 **속성** 창을 표시합니다.

3. **속성** 창에서 **인지 시간 프로필** 속성을 변경합니다.

4. 속성 변경을 마친 다음, **파일** 메뉴에서 **저장**을 선택합니다. 그러면 새 인지 시간 프로필로 부하 테스트를 실행할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [부하 테스트 시나리오 편집](../test/edit-load-test-scenarios.md)
