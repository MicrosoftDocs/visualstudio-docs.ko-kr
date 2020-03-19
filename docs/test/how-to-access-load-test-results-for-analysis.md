---
title: 부하 테스트 결과 분석
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load test results, accessing
- Load Test Viewer
- load tests, accessing
- load tests, analyzing
- load tests, results
- Load Test Viewer, viewing
ms.assetid: b0a3e694-2894-479b-b270-7e61e9fafacd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b6a5da728e24d5d7fdbeccd1e28aa2742e04bf48
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596465"
---
# <a name="how-to-access-load-test-results-for-analysis"></a>방법: 분석을 위한 부하 테스트 결과 액세스

부하 테스트 편집기에서 부하 테스트를 실행할 경우 부하 테스트 결과가 자동으로 열리고 실행 중인 부하 테스트가 **부하 테스트 분석기**에 표시됩니다. 명령줄에서 부하 테스트를 실행할 때 부하 테스트 결과에 직접 액세스 해야 합니다.

완료된 부하 테스트의 결과에는 테스트 대상 컴퓨터에서 주기적으로 수집된 성능 카운터 샘플 및 오류 정보가 포함되어 있습니다. 부하 테스트 실행 과정에서 많은 수의 성능 카운터 샘플이 수집될 수 있습니다. 수집되는 성능 데이터의 양은 테스트 실행의 길이, 샘플링 간격, 테스트 대상 컴퓨터의 수, 수집되는 카운터의 수, 구성된 데이터 수집기 및 로깅 수준에 따라 달라집니다. 대규모 부하 테스트의 경우 수집되는 성능 데이터의 양이 몇 기가바이트가 되기 쉽습니다. 자세한 내용은 [테스트 컨트롤러 및 테스트 에이전트](configure-test-agents-and-controllers-for-load-tests.md)를 참조하세요.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-access-a-load-test-result"></a>부하 테스트 결과에 액세스하려면

1. 웹 성능 및 부하 테스트 프로젝트에서 부하 테스트를 엽니다.

2. 부하 테스트 편집기의 도구 모음에서 **결과 열기 및 관리** 단추를 선택합니다.

     **결과 열기 및 관리** 대화 상자가 나타납니다.

3. **부하 테스트 결과를 찾을 컨트롤러 이름 입력**에서 컨트롤러를 선택합니다. **\<<로컬> – 컨트롤러 없음**을 선택하여 로컬로 저장된 결과에 액세스합니다.

4. **다음 부하 테스트의 결과 표시**에서 결과를 볼 부하 테스트를 선택합니다. 모든 테스트의 결과를 보려면 **\<모든 테스트에 대한 결과 표시>** 를 선택합니다.

     사용 가능한 부하 테스트 결과는 **부하 테스트 결과** 목록에 나타납니다. 여기에는 **시간**, **지속 시간**, **사용자**, **결과**, **테스트** 및 **설명** 열이 있습니다. **테스트**에는 테스트의 이름이 들어 있고 **설명**에는 테스트를 실행하기 전에 추가한 설명(선택 사항)이 들어 있습니다.

    > [!NOTE]
    > 결과는 목록 맨 위에 최신 결과와 함께 표시됩니다.

5. **부하 테스트 결과** 목록에서 분석할 부하 테스트 결과를 선택하고 **열기**를 선택합니다.

6. **부하 테스트 분석기**가 나타나고 선택한 부하 테스트 결과가 요약 뷰에 표시됩니다. 자세한 내용은 [부하 테스트 결과 요약 개요](../test/load-test-results-summary-overview.md)를 참조하세요.

     **결과 열기 및 관리** 대화 상자에서 부하 테스트 결과 가져오기, 내보내기 및 제거를 비롯하여 부하 테스트 결과의 다양한 특성을 관리할 수 있습니다. 자세한 내용은 [부하 테스트 결과 리포지토리에서 부하 테스트 결과 관리](../test/manage-load-test-results-in-the-load-test-results-repository.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

- [부하 테스트 결과 분석](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
