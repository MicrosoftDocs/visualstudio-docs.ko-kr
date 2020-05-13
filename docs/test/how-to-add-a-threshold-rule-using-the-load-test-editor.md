---
title: 부하 테스트에 대한 임계값 규칙 추가
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, monitoring
- load tests, thresholds
- load tests, analyzing
- thresholds in load tests
ms.assetid: 3d8fac8f-426f-4155-9ced-f7cd4c79792c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d1389df0c307ad6ec65575fc7934e622928a0ca1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591634"
---
# <a name="how-to-add-a-threshold-rule-using-the-load-test-editor"></a>방법: 부하 테스트 편집기를 사용하여 임계값 규칙 추가

부하 테스트에서 임계값 규칙을 통해 성능 카운터 값을 상수 값이나 다른 성능 카운터 값과 비교할 수 있습니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-threshold-rule"></a>임계값 규칙을 추가하려면

1. 부하 테스트를 엽니다.

2. 부하 테스트 편집기에서 **카운터 집합** 노드를 확장합니다.

3. 카운터 집합 중 하나에서 **카운터 범주** 하나를 확장합니다. 예를 들어 **LoadTest:Scenario**를 선택할 수 있습니다. 노드를 확장합니다.

4. 카운터 중 하나(예: **LoadTest:Scenario**의 **사용자 부하**)를 마우스 오른쪽 단추로 클릭합니다. **임계값 규칙 추가**를 선택합니다.

     **임계값 규칙 추가** 대화 상자가 표시됩니다.

5. **상수 비교**와 **카운터 비교**라는 두 가지 규칙 유형 중에서 선택할 수 있습니다. 적절한 유형을 선택하고 값을 설정합니다.

    > [!NOTE]
    > **초과하면 경고** 속성을 **True**로 설정하면 임계값을 초과할 때 경고가 표시되고 또는 **False**로 설정하면 임계값 밑으로 떨어질 때 경고가 표시됩니다.

## <a name="see-also"></a>참고 항목

- [임계값 규칙 위반 분석](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [부하 테스트에서 컴퓨터에 대한 카운터 집합 및 임계값 규칙 지정](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [부하 테스트 결과 분석](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
