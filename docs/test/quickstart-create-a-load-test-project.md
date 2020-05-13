---
title: 웹 성능 및 부하 테스트 프로젝트를 만듭니다.
ms.date: 03/14/2018
ms.topic: quickstart
helpviewer_keywords:
- load testing, quickstart
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f186e8c10d894b98e789480046d43fc957edd8a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75566412"
---
# <a name="quickstart-create-a-load-test-project"></a>빠른 시작: 부하 테스트 프로젝트 만들기

이 10분 분량의 빠른 시작에서는 Visual Studio에서 웹 성능 및 부하 테스트 프로젝트를 만들고 실행하는 방법을 배웁니다. 부하 테스트는 웹 성능 또는 단위 테스트를 실행하여 많은 사용자가 동시에 서버에 액세스하는 것을 시뮬레이트합니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="software-requirements"></a>소프트웨어 요구 사항

웹 성능 및 부하 테스트 프로젝트는 Visual Studio의 **Enterprise 버전**에서만 사용할 수 있습니다.

## <a name="install-the-load-testing-component"></a>부하 테스트 구성 요소 설치

웹 성능 및 부하 테스트 도구 구성 요소를 아직 설치하지 않은 경우 Visual Studio 설치 관리자를 통해 설치해야 합니다.

1. Windows **시작** 메뉴에서 **Visual Studio 설치 관리자**를 엽니다. 새 프로젝트 대화 상자에서 Visual Studio로 액세스하거나 메뉴 모음에서 **도구** > **도구 및 기능 가져오기**를 선택하여 액세스할 수도 있습니다.

1. **Visual Studio 설치 관리자**에서 **개별 구성 요소** 탭을 선택하고 **디버깅 및 테스트** 섹션까지 아래로 스크롤합니다. **웹 성능 및 부하 테스트 도구**를 선택합니다.

   ![웹 성능 및 부하 테스트 도구 구성 요소](media/web-perf-load-testing-tools-component.png)

1. **수정** 단추를 선택합니다.

   웹 성능 및 부하 테스트 도구 구성 요소가 설치됩니다.

## <a name="create-a-load-test-project"></a>부하 테스트 프로젝트 만들기

이 섹션에서는 C# 부하 테스트 프로젝트를 만듭니다. 원하는 경우 Visual Basic 부하 테스트 프로젝트를 만들 수도 있습니다.

::: moniker range="vs-2017"

1. Visual Studio를 엽니다.

2. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

   **새 프로젝트** 대화 상자가 열립니다.

3. **새 프로젝트** 대화 상자에서 **설치됨** 및 **Visual C#** 을 확장한 다음, **테스트** 범주를 선택합니다. **웹 성능 및 부하 테스트 프로젝트** 템플릿을 선택합니다.

   ![웹 성능 및 부하 테스트 프로젝트 템플릿](media/web-perf-load-test-project-template.png)

4. 기본 이름을 사용하지 않으려면 프로젝트의 이름을 입력한 다음, **확인**을 선택합니다.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio를 엽니다.

2. 시작 창에서 **새 프로젝트 만들기**를 선택합니다.

3. **새 프로젝트 만들기** 페이지에서 검색 상자에 **웹 테스트**를 입력하고 C#용 **웹 성능 및 부하 테스트 프로젝트\[사용되지 않음]** 템플릿을 선택합니다. **다음**을 선택합니다.

4. 기본 이름을 사용하지 않으려면 프로젝트의 이름을 입력하고 **만들기**를 선택합니다.

::: moniker-end

   Visual Studio에서 프로젝트를 만들고 **솔루션 탐색기**에 파일을 표시합니다. 프로젝트는 초기에 *WebTest1.webtest*라는 웹 테스트 파일을 포함합니다.

## <a name="add-a-load-test-to-the-project"></a>프로젝트에 부하 테스트 추가

1. **솔루션 탐색기**에서 프로젝트 노드의 오른쪽 클릭 메뉴 또는 컨텍스트 메뉴에서 **추가** > **부하 테스트**를 선택합니다.

   **부하 테스트 새로 만들기 마법사**가 열립니다.

1. **온-프레미스 부하 테스트** 옵션을 선택한 후, **다음**을 선택합니다. [여기](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts)에서 클라우드 기반 부하 테스트에 대해 자세히 알아볼 수 있습니다.

   ![부하 테스트 새로 만들기 마법사 - 첫 페이지](media/load-test-wizard-page-1.png)

1. **부하 테스트 시나리오에 테스트 추가 및 테스트 조합 편집** 페이지에 도달할 때까지 **다음**을 선택하여 마법사를 단계별로 수행합니다. **추가** 단추를 선택합니다.

   **테스트 추가** 대화 상자가 열립니다.

1. **사용 가능한 테스트**에서 **WebTest1**을 선택한 다음, 오른쪽 화살표를 선택하여 **선택한 테스트** 상자로 이동합니다. **확인** 단추를 선택합니다.

   ![테스트 추가 대화 상자](media/add-tests-dialog-box.png)

1. **부하 테스트 새로 만들기 마법사**로 돌아가서 **마침** 단추를 선택합니다.

   부하 테스트가 프로젝트에 추가되고 부하 테스트 파일이 편집기 창에서 열립니다.

## <a name="run-the-load-test"></a>부하 테스트 실행

많은 작업을 수행하지 않는 부하 테스트를 만들었지만 그래도 실행해 봅니다.

편집기에 열려 있는 부하 테스트의 오른쪽 클릭 메뉴 또는 상황에 맞는 메뉴에서 **부하 테스트 실행**을 선택합니다.

![부하 테스트 실행 메뉴](media/run-load-test.png)

부하 테스트가 실행되기 시작합니다. **테스트 결과** 창은 테스트가 진행 중임을 나타내고, 부하 테스트 분석기는 편집기 창에 표시됩니다. 테스트가 완료된 후(기본값을 수락한 경우 5분 소요) 편집기에 요약 정보가 표시됩니다. **그래프**, **테이블** 또는 **세부 정보**를 선택하여 부하 테스트 결과에 대한 다른 정보를 얻을 수 있습니다.

![부하 테스트 분석기 창](media/load-test-analyzer.png)

## <a name="next-steps"></a>다음 단계

이제 간단한 부하 테스트 프로젝트를 만들었으므로 다음 단계는 시나리오, 카운터 집합 및 실행 설정을 구성하는 것입니다.

> [!div class="nextstepaction"]
> [테스트 설정 편집](edit-load-tests.md)
