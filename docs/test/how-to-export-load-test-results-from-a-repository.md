---
title: 부하 테스트 결과 내보내기
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- results, load test
- load tests, exporting results
- Load Test Results Repository
- load test results, exporting
ms.assetid: 716c2af5-8737-4d31-956f-a0273f7c5c0c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f9b20915d5c320ff8db4da849d20267355c26590
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287755"
---
# <a name="how-to-export-load-test-results-from-a-repository"></a>방법: 리포지토리에서 부하 테스트 결과 내보내기

부하 테스트를 실행하면 실행하는 동안 수집된 정보가 부하 테스트 결과 리포지토리에 저장됩니다. 부하 테스트 결과 리포지토리에는 성능 카운터 데이터와 발생한 모든 오류에 대한 정보가 들어 있습니다. 자세한 내용은 [부하 테스트 결과 리포지토리에서 부하 테스트 결과 관리](../test/manage-load-test-results-in-the-load-test-results-repository.md)를 참조하세요.

**부하 테스트 결과 열기 및 관리** 대화 상자를 사용하면 부하 테스트 편집기에서 부하 테스트 결과를 관리할 수 있습니다. 또한 부하 테스트 결과를 열고, 가져오고, 내보내고, 제거할 수 있습니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-export-results-from-a-repository"></a>리포지토리에서 결과를 내보내려면

1. 웹 성능 및 부하 테스트 프로젝트에서 부하 테스트를 엽니다.

2. 포함된 도구 모음에서 **결과 열기 및 관리**를 선택합니다.

     **부하 테스트 결과 열기 및 관리** 대화 상자가 표시됩니다.

3. **부하 테스트 결과를 찾을 컨트롤러 이름 입력**에서 컨트롤러를 선택합니다. **\<Local - No controller>** 을 선택하여 로컬로 저장된 결과에 액세스합니다.

4. **다음 부하 테스트의 결과 표시**에서 결과를 볼 부하 테스트를 선택합니다. **\<Show results for all tests>** 를 선택하여 모든 테스트의 모든 결과를 확인합니다.

     사용 가능한 부하 테스트 결과는 **부하 테스트 결과** 목록에 나타납니다. 여기에는 **시간**, **지속 시간**, **사용자**, **결과**, **테스트** 및 **설명** 열이 있습니다. **테스트**에는 테스트의 이름이 들어 있고 **설명**에는 테스트를 실행하기 전에 추가한 설명(선택 사항)이 들어 있습니다. **설명** 열에는 해당 테스트 결과에 대해 **분석 주석**에 입력한 간략한 설명이 표시됩니다.

5. **부하 테스트 결과** 목록에서 결과를 선택합니다. **Shift** 키, **Ctrl** 키 또는 둘 다를 사용하여 결과를 여러 개 선택한 다음, 단일 파일로 내보낼 수 있습니다.

6. **내보내기**를 선택합니다.

     **부하 테스트 결과 내보내기** 대화 상자가 나타납니다.

7. **파일 이름** 상자에 이름을 입력한 다음, **저장**을 선택합니다.

     결과가 보관 파일로 내보내집니다.

    > [!NOTE]
    > **부하 테스트 결과 열기 및 관리** 대화 상자는 결과가 표시된 후에도 계속 열려 있습니다.

## <a name="see-also"></a>참조

- [부하 테스트 결과 리포지토리에서 부하 테스트 결과 관리](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [방법: 리포지토리에서 부하 테스트 결과 삭제](../test/how-to-delete-load-test-results-from-a-repository.md)
- [부하 테스트 결과 분석](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [방법: 리포지토리로 부하 테스트 결과 가져오기](../test/how-to-import-load-test-results-into-a-repository.md)
