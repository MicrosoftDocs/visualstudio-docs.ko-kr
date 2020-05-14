---
title: 부하 테스트 편집기
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Editor
- load tests, Load Test Editor
ms.assetid: ba16ed02-137e-40bf-a4cb-45d87d922d37
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c61c13f6a9eca416a52221ba9da37be820dd4b89
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593228"
---
# <a name="edit-load-tests"></a>부하 테스트 편집

부하 테스트는 웹 성능 테스트 또는 단위 테스트를 실행하여 많은 사용자가 동시에 서버에 액세스하는 것을 시뮬레이트합니다. 부하 테스트를 사용하여 애플리케이션 스트레스 및 성능 데이터에 액세스할 수 있습니다. 부하 테스트에서 사용자 부하 및 네트워크 형식과 같은 여러 부하 조건을 에뮬레이트하도록 구성할 수 있습니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

부하 테스트는 *시나리오*, *카운터 집합* 및 *실행 설정*으로 정의됩니다. 다음 그림은 [시나리오](../test/edit-load-test-scenarios.md), [카운터 집합](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md) 및 [실행 설정](../test/load-test-run-settings-properties.md)의 차이점을 설명합니다.

![부하 테스트 아키텍처](../test/media/load_test_editor.png)

## <a name="software-requirements"></a>소프트웨어 요구 사항

웹 성능 및 부하 테스트 프로젝트는 Visual Studio의 Enterprise Edition에서만 사용할 수 있습니다.

## <a name="edit-load-test-scenario-settings"></a>부하 테스트 시나리오 설정 편집

시나리오는 사용자 그룹이 서버 애플리케이션과 상호 작용하는 방법을 모델링하는 데 사용됩니다. 시나리오는 부하 패턴, 테스트 조합 모델, 테스트 조합, 브라우저 조합 및 네트워크 조합으로 구성됩니다. 부하 테스트에는 두 개 이상의 시나리오가 있을 수 있고 단일 시나리오는 웹 성능 테스트 및 단위 테스트를 포함할 수 있습니다. 유사한 설정을 그룹화하면 시나리오를 사용하여 유사한 특성의 테스트를 그룹화하고 테스트할 수 있습니다.

자세한 내용은 [부하 테스트 시나리오 편집](../test/edit-load-test-scenarios.md) 및 [부하 테스트 시나리오 속성](../test/load-test-scenario-properties.md)을 참조하세요.

## <a name="configure-and-manage-performance-counter-sets"></a>성능 카운터 집합 구성 및 관리

부하 테스트에서는 기술별로 구성된 명명된 카운터 집합을 제공하며 이러한 카운터 집합은 성능 카운터 데이터를 분석할 때 유용합니다. 카운터 집합에는 부하 테스트, IIS, ASP.NET 및 SQL이 포함됩니다. **부하 테스트 새로 만들기 마법사**를 사용하여 부하 테스트를 만들 때 부하 테스트에 포함되도록 지정한 컴퓨터에 대해 미리 정의되고 중요한 초기 카운터 집합이 구성됩니다. **부하 테스트 편집기**에서 카운터를 관리합니다.

자세한 내용은 [부하 테스트에서 컴퓨터에 대한 카운터 집합 및 임계값 규칙 지정](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)을 참조하세요.

## <a name="configure-and-manage-load-test-run-settings"></a>부하 테스트 실행 설정 구성 및 관리

실행 설정은 부하 테스트 실행 방식에 영향을 미치는 속성입니다. 실행 설정은 **속성** 창에서 범주별로 구성됩니다.

자세한 내용은 [부하 테스트 실행 설정 구성](../test/configure-load-test-run-settings.md) 및 [부하 테스트 실행 설정 속성](../test/load-test-run-settings-properties.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [부하 테스트 결과 분석](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [임계값 규칙 위반 분석](../test/analyze-threshold-rule-violations-in-load-tests.md)
