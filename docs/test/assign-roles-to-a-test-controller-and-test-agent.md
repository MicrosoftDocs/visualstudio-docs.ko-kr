---
title: 테스트 컨트롤러 및 테스트 에이전트 역할
ms.custom: SEO-VS-2020
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- testing, walkthroughs, test controller and test agents
- test agent, walkthrough
- walkthroughs [Visual Studio ALM] testing
- test controller, walkthrough
- walkthroughs, test controller and test agents
ms.assetid: 57ed43ae-4e67-4139-8aec-3e9fceb0a745
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c7f4360772f3962ff60517071dcae4318dc71e56
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809304"
---
# <a name="assign-roles-to-a-test-controller-and-test-agent"></a>역할을 테스트 컨트롤러와 테스트 에이전트에 할당

이 문서에서는 Visual Studio를 사용하는 여러 머신에서 테스트 컨트롤러와 테스트 에이전트를 사용하여 테스트를 배포하는 테스트 설정을 만들고 구성하는 방법에 대해 설명합니다. 또한 테스트 설정에 진단 데이터 어댑터를 추가하는 방법도 보여 줍니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>사전 요구 사항

- 테스트 설정으로 실행하려면 단위 테스트 또는 코딩된 UI 테스트를 만듭니다.

- 테스트 컨트롤러 및 테스트 에이전트를 설치합니다. 테스트 컨트롤러 및 테스트 에이전트를 설치하는 방법에 대한 자세한 내용은 [테스트 에이전트 설치 및 구성](../test/lab-management/install-configure-test-agents.md)을 참조하세요.

## <a name="to-create-and-configure-a-test-setting"></a>테스트 설정을 만들고 구성하려면

1. **솔루션 탐색기**에서 **솔루션 항목**을 마우스 오른쪽 단추로 클릭하고 **추가**를 가리킨 다음, **새 항목**을 선택합니다.

     **새 항목 추가** 대화 상자가 나타납니다.

2. **설치된 템플릿** 창에서 **테스트 설정**을 선택합니다.

3. **이름** 상자에 **TestSettingDistributedTestWalkthrough**를 입력합니다.

4. **추가**를 선택합니다.

     새 테스트의 *TestSettingDistributedTestWalkthrough.testsettings* 파일이 **솔루션 탐색기**의 **솔루션 항목** 폴더 아래에 나타납니다.

     **테스트 설정** 대화 상자가 표시됩니다. **일반** 페이지가 선택되어 있습니다.

     이제 테스트 설정 값을 편집하고 저장할 수 있습니다.

5. **이름** 아래에서 테스트 설정의 이름을 입력합니다.

6. **설명** 아래에 **분산 테스트 설정**을 입력합니다.

7. **기본 이름 지정 체계**를 선택된 상태로 둡니다.

## <a name="to-assign-roles-to-a-test-controller-and-test-agents"></a>테스트 컨트롤러 및 테스트 에이전트에 역할을 할당하려면

1. **역할**을 선택합니다.

     **역할** 페이지가 표시됩니다.

2. 테스트를 원격으로 실행하려면 **테스트 실행 방법** 드롭다운 목록을 사용하고 **원격 실행**을 선택합니다.

3. **컨트롤러** 드롭다운 목록에서 [테스트 컨트롤러](../test/lab-management/install-configure-test-agents.md)의 컴퓨터 이름을 입력합니다.

    > [!NOTE]
    > 컨트롤러를 처음으로 추가하는 경우에는 드롭다운 목록에 컨트롤러가 나열되지 않습니다. 이 목록은 다른 테스트 설정에서 지정한 이전 컨트롤러에 의해 채워집니다.

4. **역할**에서 **추가**를 선택합니다.

5. **이름** 열 아래의 강조 표시된 행에 **분산 테스트**를 입력합니다.

## <a name="to-assign-a-diagnostic-and-data-adapter-to-your-test-setting"></a>진단 및 데이터 어댑터를 테스트 설정에 할당하려면

1. **데이터 및 진단**을 선택합니다.

     **데이터 및 진단** 페이지가 표시됩니다.

2. **역할** 아래에서 **분산 테스트** 역할이 선택되어 있는지 확인합니다.

3. **선택한 역할에 대한 데이터 및 진단** 아래에서 **IntelliTrace** 및 **시스템 정보** 어댑터를 선택합니다.

     이러한 어댑터와 테스트 설정에 사용할 수 있는 그 밖의 어댑터에 대한 자세한 내용은 [단위 테스트 구성](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)을 참조하십시오.

4. **호스트**를 선택합니다.

5. (선택 사항) 컴퓨터가 64비트 버전의 Microsoft Windows에서 실행 중이고 **Any CPU** 구성을 사용하여 테스트를 컴파일한 경우, **32비트 또는 64비트 프로세스에서 테스트 실행** 드롭다운 목록에서 **64비트 컴퓨터의 64비트 프로세스에서 테스트 실행**을 선택합니다.

    > [!TIP]
    > 유연성을 극대화하려면 **Any CPU** 구성으로 테스트 프로젝트를 컴파일해야 합니다. 그러면 32비트 및 64비트 에이전트 모두에서 테스트를 실행할 수 있습니다. **64비트** 구성으로 테스트 프로젝트를 컴파일하는 것은 아무 이점이 없습니다.

6. 새 테스트 설정을 저장하려면 **적용**을 선택합니다.

7. **닫기**를 선택합니다.

::: moniker range="vs-2017"

8. **테스트** 메뉴에서 **테스트 설정** > **테스트 설정 파일 선택**을 선택하고 *TestSettingDistributedTestWalkthrough.testsettings* 파일을 선택합니다.

::: moniker-end

::: moniker range=">=vs-2019"

8. **테스트** 메뉴에서 **설정 파일 선택**을 선택합니다. *TestSettingDistributedTestWalkthrough.testsettings* 파일을 찾아 선택합니다.

::: moniker-end

9. 일반적인 방법으로 테스트를 실행합니다.

     테스트 컨트롤러는 단위 테스트와 코딩된 UI 테스트를 처리할 때 테스트를 100개씩 여러 그룹으로 나눠 테스트 에이전트 컴퓨터로 보냅니다. 예를 들어 단위 테스트가 250개이고 테스트 에이전트가 3개일 경우 처음 100개의 단위 테스트는 agent1로 보내지고 다음 100개의 단위 테스트는 agent2로 보내지며 나머지 50개의 단위 테스트는 agent3으로 보내집니다.

## <a name="see-also"></a>참고 항목

- [테스트 에이전트 설치 및 구성](../test/lab-management/install-configure-test-agents.md)
