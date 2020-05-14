---
title: '방법: 부하 테스트 결과 리포지토리 선택'
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.dialog.connectstringmissing
- vs.test.load.dialog.databaseconnectstring
helpviewer_keywords:
- load tests, results repository
- results, load test
- load test results, repository
- Load Test Results Repository
- SQL, Load Test Results Store
ms.assetid: fa0c4dd9-612f-4a57-b8eb-458f129d9cda
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 513dd884f65e041e7ad90dda1483633fec57e100
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589008"
---
# <a name="how-to-select-a-load-test-results-repository"></a>방법: 부하 테스트 결과 리포지토리 선택

로컬 결과 저장소로 제한되지는 않습니다. 부하 테스트는 주로 에이전트 컴퓨터의 원격 집합에서 실행됩니다. 에이전트를 컨트롤러와 함께 사용하면 단일 컴퓨터보다 시뮬레이션된 부하를 더 많이 생성할 수 있습니다. 자세한 내용은 [테스트 컨트롤러 및 테스트 에이전트](configure-test-agents-and-controllers-for-load-tests.md)를 참조하세요.

에이전트나 로컬 컴퓨터의 테스트 결과는 부하 테스트 결과 저장소가 만들어진 모든 SQL 서버에 저장할 수 있습니다. 에이전트나 로컬 컴퓨터 모두 **테스트 컨트롤러 관리** 창을 사용하여 부하 테스트 결과를 저장할 위치를 식별해야 합니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="identify-a-results-store-for-load-test-data"></a>부하 테스트 데이터에 사용될 결과 저장소 식별

1. **솔루션 탐색기**에서 부하 테스트 파일을 엽니다.

2. **부하 테스트** 도구 모음에서 **테스트 컨트롤러 관리**를 선택합니다. **테스트 컨트롤러 관리** 대화 상자가 나타납니다. 에이전트를 원격으로 사용하는 경우 컨트롤러를 선택해야 합니다.

     ![부하 테스트 결과 저장소 연결 속성](../test/media/loadtestconnectionproperties.png) 부하 테스트 결과 저장소 연결 속성

3. **부하 테스트 결과 저장소**에서 **(…)** 를 클릭하여 **연결 속성** 대화 상자를 표시합니다.

4. **서버 이름**에 `LoadTest` 스크립트를 실행한 서버 이름을 입력합니다.

    > [!TIP]
    > 로컬 컴퓨터에서 SQL Express를 부하 테스트 저장소로 사용하는 경우에는 \<computername>\sqlexpress(예: **MyComputer\sqlexpress**)를 입력합니다.

5. **서버에 로그온**에서 **Windows 인증 사용**을 선택할 수 있습니다. 사용자 이름 및 암호를 지정할 수 있지만 지정할 경우 **암호 저장** 옵션을 선택해야 합니다.

6. **데이터베이스에 연결**에서 **데이터베이스 이름 선택 또는 입력**을 선택합니다. 드롭다운 목록 상자에서 **LoadTest**를 선택합니다.

7. **확인**을 선택합니다. **연결 테스트**를 선택하여 연결을 테스트합니다.

8. **테스트 컨트롤러 관리** 대화 상자에서 **닫기**를 선택합니다.

## <a name="see-also"></a>참고 항목

- [부하 테스트 결과 리포지토리에서 부하 테스트 결과 관리](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [테스트 컨트롤러 및 테스트 에이전트](configure-test-agents-and-controllers-for-load-tests.md)
