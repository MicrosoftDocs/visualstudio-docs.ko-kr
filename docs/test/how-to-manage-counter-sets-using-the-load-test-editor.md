---
title: 부하 테스트 카운터 집합
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.load.dialog.countersetmapping
helpviewer_keywords:
- counters, counter sets
- performance counters
- counter sets
- load tests, counter sets
ms.assetid: 64315c2f-a0b2-4378-be16-0774b99beef5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1eeb99d58a9fc0547d118c529878d8b02cc83dda
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287690"
---
# <a name="how-to-manage-counter-sets-using-the-load-test-editor"></a>방법: 부하 테스트 편집기를 사용하여 카운터 집합 관리

**부하 테스트 새로 만들기 마법사**를 사용하여 부하 테스트를 만들 때 초기 카운터 집합을 추가합니다. 이때 부하 테스트에 사용할 미리 정의된 카운터 집합이 제공됩니다.

> [!NOTE]
> 부하 테스트가 원격 컴퓨터에 분산된 경우 컨트롤러 및 에이전트 카운터가 컨트롤러 및 에이전트 카운터 집합에 매핑됩니다. 부하 테스트에서 원격 컴퓨터를 사용하는 방법에 대한 자세한 내용은 [테스트 컨트롤러 및 테스트 에이전트](configure-test-agents-and-controllers-for-load-tests.md)를 참조하세요.

카운터 집합을 관리하려면 성능 데이터를 수집할 컴퓨터 집합을 선택하고 개별 컴퓨터에서 각각 수집할 카운터 집합을 할당합니다. **부하 테스트 편집기**에서 카운터를 관리합니다.

![카운터 집합 관리](../test/media/loadtestmanagecountersets.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-manage-counter-sets"></a>카운터 집합을 관리하려면

1. 부하 테스트를 엽니다.

2. **카운터 집합 관리** 단추를 선택합니다.

     -또는-

     부하 테스트 트리의 **카운터 집합** 폴더를 마우스 오른쪽 단추로 클릭하고 **카운터 집합 관리**를 선택합니다.

     **카운터 집합 관리** 대화 상자가 표시됩니다.

3. (선택 사항) **선택한 컴퓨터 및 카운터 집합이 추가될 실행 설정** 목록 상자에서 다른 실행 설정을 선택합니다.

    > [!NOTE]
    > 이 내용은 부하 테스트에 실행 설정이 둘 이상 있는 경우에만 적용됩니다.

4. (선택 사항) **컴퓨터 추가**를 선택하여 모니터링할 새 컴퓨터를 추가합니다. 이름을 입력하라는 메시지가 표시됩니다. 컴퓨터의 이름을 입력하면 새 항목 아래에 노드가 표시됩니다. 예를 들어 **ASP.NET**, **IIS**, **SQL** 등이 표시됩니다. 선택할 노드 앞에 있는 확인란을 선택합니다. 그러면 **선택 내용 미리 보기** 창에 새 카운터가 표시됩니다.

5. (선택 사항) **컴퓨터 태그** 텍스트 상자에 컴퓨터와 연결할 태그를 입력합니다. 예를 들어 "TestMachine12 in lab3"을 입력합니다.

     컴퓨터 태그를 사용하면 구별하기 쉬운 이름으로 컴퓨터를 식별할 수 있습니다.

     이 태그는 부하 테스트 편집기의 트리에 있는 **카운터 집합 매핑** 노드에 표시됩니다. 더욱 중요한 것은 이 태그가 Excel 보고서에 표시된다는 점입니다. 따라서 관련자가 부하 테스트에서 컴퓨터에 할당된 역할(예: "lab2의 Web Server1" 또는 "피닉스 사무실의 SQL Server2")을 쉽게 확인할 수 있습니다. 자세한 내용은 [테스트 비교 또는 추세 분석을 위한 부하 테스트 결과 보고](../test/compare-load-test-results.md)를 참조하세요.

6. **확인**을 선택합니다.

## <a name="see-also"></a>참고 항목

- [테스트 컨트롤러 및 테스트 에이전트](configure-test-agents-and-controllers-for-load-tests.md)
- [부하 테스트에서 컴퓨터에 대한 카운터 집합 및 임계값 규칙 지정](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [부하 테스트 실행 설정 구성](../test/configure-load-test-run-settings.md)
