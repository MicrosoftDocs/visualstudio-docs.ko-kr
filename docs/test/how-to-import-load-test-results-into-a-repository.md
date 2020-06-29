---
title: '방법: 리포지토리로 부하 테스트 결과 가져오기'
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- results, load test
- load test results, importing
- Load Test Results Repository
- load tests, importing results
ms.assetid: a955b3d2-c8ad-40dd-8ea3-9f1a271e1eed
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f8f0ec6b9f1a5664ac898e525420ec2cc374f5ad
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287742"
---
# <a name="how-to-import-load-test-results-into-a-repository"></a>방법: 리포지토리로 부하 테스트 결과 가져오기

부하 테스트를 실행하면 실행하는 동안 수집된 정보가 부하 테스트 결과 리포지토리에 저장됩니다. 부하 테스트 결과 리포지토리에는 성능 카운터 데이터와 발생한 모든 오류에 대한 정보가 들어 있습니다. 자세한 내용은 [부하 테스트 결과 리포지토리에서 부하 테스트 결과 관리](../test/manage-load-test-results-in-the-load-test-results-repository.md)를 참조하세요.

**부하 테스트 결과 열기 및 관리** 대화 상자를 사용하면 부하 테스트 편집기에서 부하 테스트 결과를 관리할 수 있습니다. 또한 부하 테스트 결과를 열고, 가져오고, 내보내고, 제거할 수 있습니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-import-results-into-a-repository"></a>리포지토리로 결과를 가져오려면

1. 웹 성능 및 부하 테스트 프로젝트에서 부하 테스트를 엽니다.

2. 포함된 도구 모음에서 **결과 열기 및 관리**를 선택합니다.

     **부하 테스트 결과 열기 및 관리** 대화 상자가 표시됩니다.

3. **부하 테스트 결과를 찾을 컨트롤러 이름 입력**에서 컨트롤러를 선택합니다. **\<local>** 을 선택하여 로컬로 저장된 결과에 액세스합니다.

     사용 가능한 부하 테스트 결과는 **부하 테스트 결과** 목록에 나타납니다. 여기에는 **시간**, **지속 시간**, **사용자**, **결과**, **테스트** 및 **설명** 열이 있습니다. **테스트**에는 테스트의 이름이 들어 있고 **설명**에는 테스트를 실행하기 전에 추가한 설명(선택 사항)이 들어 있습니다.

4. **가져오기**를 선택합니다.

     **부하 테스트 결과 가져오기** 대화 상자가 나타납니다.

5. **파일 이름** 상자에 보관된 테스트 결과 파일의 이름을 입력하고 **열기**를 선택합니다.

     \- 또는 -

     파일을 찾은 다음, **열기**를 선택합니다.

    > [!NOTE]
    > 이 단계에서 지정하는 보관된 테스트 결과 파일은 내보내기 작업을 수행하여 만든 것이어야 합니다.

     이렇게 가져온 결과는 **부하 테스트 결과** 목록에 나타납니다.

## <a name="see-also"></a>참조

- [부하 테스트 결과 리포지토리에서 부하 테스트 결과 관리](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [부하 테스트 결과 분석](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [방법: 리포지토리에서 부하 테스트 결과 내보내기](../test/how-to-export-load-test-results-from-a-repository.md)
