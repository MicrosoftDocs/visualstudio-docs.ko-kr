---
title: '부하 테스트: 웹 캐시 데이터를 사용하여 가상 사용자 비율 설정'
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, virtual users
ms.assetid: f66d5d43-4121-4487-b27f-d0a0baaf7601
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0a31ea50cdedbeb825d03de38a89200b6e8e5200
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287404"
---
# <a name="how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data"></a>방법: 웹 캐시 데이터를 사용하는 가상 사용자 비율 지정

**부하 테스트 새로 만들기 마법사**를 사용하여 부하 테스트를 만든 다음, **부하 테스트 편집기**를 사용하여 시나리오 속성을 테스트 요구 사항 및 목표에 맞게 변경할 수 있습니다. 부하 테스트 시나리오 속성과 해당 설명의 전체 목록을 보려면 [부하 테스트 시나리오 속성](../test/load-test-scenario-properties.md)을 참조하세요.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**속성** 창에서 **새 사용자의 백분율** 속성을 설정하고 **부하 테스트 편집기**에서는 부하 테스트 시나리오 속성을 편집합니다.

**새 사용자의 백분율** 속성은 부하 테스트에서 웹 브라우저가 수행하는 캐시 작업을 시뮬레이트하는 방식에 영향을 줍니다. 기본적으로 **새 사용자의 백분율** 속성은 0%로 설정됩니다. **새 사용자의 백분율** 속성 값을 100%로 설정하면 부하 테스트에서 웹 성능 테스트를 실행할 때마다 사용자가 웹 사이트에 처음 방문하는 것으로 간주되므로 이전에 웹 사이트를 방문하여 브라우저 캐시에 남겨진 콘텐츠가 전혀 없는 것으로 처리됩니다. 따라서 웹 테스트에서 이미지 등의 모든 종속 요청을 비롯한 모든 요청이 다운로드됩니다.

> [!NOTE]
> 웹 테스트에서 동일한 캐시 가능 리소스가 두 번 이상 요청되면 요청이 다운로드되지 않습니다.

이미지 등의 캐시 가능한 콘텐츠가 로컬에 캐시되어 있을 가능성이 큰 재방문 사용자가 많은 웹 사이트의 부하를 테스트하는 경우 **새 사용자의 백분율** 속성의 설정이 100%이면 실제 사용 환경에서 발생하는 것보다 많은 다운로드 요청이 생성됩니다. 이 경우 웹 사이트의 전체 방문자 중 처음으로 방문하는 사용자의 백분율을 예측하여 이에 따라 **새 사용자의 백분율** 속성을 적절하게 설정해야 합니다.

## <a name="to-specify-the-percentage-of-new-users-for-a-scenario"></a>시나리오에 대한 새 사용자의 백분율을 지정하려면

1. 부하 테스트를 엽니다.

     **부하 테스트 편집기**가 나타납니다. 부하 테스트 트리가 표시됩니다.

2. 부하 테스트 트리 **시나리오** 폴더에서 새 사용자의 백분율 값을 변경할 시나리오 노드를 선택합니다.

3. **보기** 메뉴에서 **속성 창**을 선택합니다.

     시나리오의 범주와 속성이 **속성** 창에 표시됩니다.

4. 새 사용자의 백분율을 나타내는 숫자를 입력하여 **새 사용자의 백분율** 속성 값을 설정합니다.

5. 속성 변경을 마친 다음, **파일** 메뉴에서 **저장**을 선택합니다. 그러면 **새 사용자의 백분율**의 새 값을 사용하여 부하 테스트를 실행할 수 있습니다.

## <a name="see-also"></a>참조

- [부하 테스트 시나리오 편집](../test/edit-load-test-scenarios.md)
- [연습: 부하 테스트 만들기 및 실행](../test/walkthrough-create-and-run-a-load-test.md)
- [테스트 컨트롤러 및 테스트 에이전트](configure-test-agents-and-controllers-for-load-tests.md)
- [부하 테스트 시나리오 속성](../test/load-test-scenario-properties.md)
- [모델 가상 사용자 동작에 대한 부하 패턴 편집](../test/edit-load-patterns-to-model-virtual-user-activities.md)
