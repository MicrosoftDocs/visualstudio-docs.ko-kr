---
title: 부하 테스트를 위한 속도 지연에 분포 적용
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, test mix model
ms.assetid: ae8b35f9-d465-4d72-8d7d-7b56ae6ffd22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aa5d3239e3b096a2018d6ef9c9b3c6666dcd31c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288275"
---
# <a name="how-to-apply-distribution-to-pacing-delay-for-a-user-pace-test-mix-model"></a>방법: 사용자 속도 테스트 조합 모델의 속도 지연에 분포 적용

**부하 테스트 새로 만들기 마법사**를 사용하여 부하 테스트를 만든 후에 부하 테스트 편집기를 사용하여 시나리오의 속성을 테스트 요구 사항 및 목표에 맞게 변경할 수 있습니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**속도 지연에 분포 적용** 속성은 **속성** 창을 사용하여 설정할 수 있습니다. 부하 테스트 시나리오 속성은 부하 테스트 편집기를 사용하여 수정할 수 있습니다.

> [!NOTE]
> **속도 지연에 분포 적용** 속성은 *부하 테스트 조합*이 사용자 속도를 기반으로 구성된 경우에만 적용됩니다. 자세한 내용은 [텍스트 조합 모델을 편집하여 가상 사용자가 테스트를 실행할 확률 지정](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)을 참조하세요.

**속도 지연에 분포 적용**의 값은 true 또는 false로 설정할 수 있습니다.

- **True**: **테스트 조합 편집** 대화 상자에서 **시간 및 사용자별 테스트** 열의 값으로 지정된 정규 통계 분포 지연이 시나리오에 적용됩니다. 자세한 내용은 [텍스트 조합 모델을 편집하여 가상 사용자가 테스트를 실행할 확률 지정](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)을 참조하세요.

     예를 들어 **테스트 조합 편집** 대화 상자에서 테스트에 대한 **시간 및 사용자별 테스트** 값이 시간당 두 명의 사용자로 설정되어 있다고 가정합니다. 이 경우 **속도 지연에 분포 적용** 속성을 **True**로 설정하면 테스트 사이의 대기 시간에 정규 통계 분포가 적용됩니다. 즉, 테스트가 시간당 두 개씩 실행되기는 하지만 테스트 사이의 지연 시간은 반드시 30분이 되지는 않습니다. 첫 번째 테스트는 4분 후에 실행되고 두 번째 테스트는 45분 후에 실행될 수도 있습니다.

- **False**: **테스트 조합 편집** 대화 상자에서 **시간 및 사용자별 테스트** 열의 값으로 지정된 속도로 테스트가 실행됩니다. 자세한 내용은 [텍스트 조합 모델을 편집하여 가상 사용자가 테스트를 실행할 확률 지정](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)을 참조하세요.

     예를 들어 **테스트 조합 편집** 대화 상자에서 테스트에 대한 **시간 및 사용자별 테스트** 값이 시간당 두 명의 사용자로 설정되어 있다고 가정합니다. 이 경우 **속도 지연에 분포 적용** 속성을 **False**로 설정하면 테스트가 실행될 때 변동 여지를 두지 않게 됩니다. 즉, 테스트가 30분마다 실행되므로 항상 한 시간에 두 개의 테스트를 실행하게 됩니다.

## <a name="to-specify-the-apply-distribution-to-pacing-delay-property-setting-for-a-scenario"></a>시나리오에 대한 '속도 지연에 분포 적용' 속성 설정을 지정하려면

1. 부하 테스트를 엽니다.

   **부하 테스트 편집기**가 나타납니다. 부하 테스트 트리가 표시됩니다.

2. 부하 테스트 트리의 **시나리오** 폴더에서 속도 분포를 적용할 시나리오 노드를 선택합니다.

3. **보기** 메뉴에서 **속성 창**을 선택합니다.

   시나리오의 범주와 속성이 **속성** 창에 표시됩니다.

4. **속도 지연에 분포 적용**의 속성 값에서 **True** 또는 **False**를 선택합니다.

5. **파일** > **저장**을 선택합니다. 이제 새 **속도 지연에 분포 적용** 값을 사용하여 부하 테스트를 실행할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [부하 테스트 시나리오 편집](../test/edit-load-test-scenarios.md)
- [연습: 부하 테스트 생성 및 실행](../test/walkthrough-create-and-run-a-load-test.md)
- [테스트 컨트롤러 및 테스트 에이전트](configure-test-agents-and-controllers-for-load-tests.md)
- [부하 테스트 시나리오 속성](../test/load-test-scenario-properties.md)
