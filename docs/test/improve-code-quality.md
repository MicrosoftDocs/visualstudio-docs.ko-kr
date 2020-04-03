---
title: 테스트 도구
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio]
- unit tests [Visual Studio]
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 0517d03db180ce76940723ca935be258d0cf1818
ms.sourcegitcommit: ee12b14f306ad8f49b77b08d3a16d9f54426e7ca
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80256233"
---
# <a name="first-look-at-testing-tools-in-visual-studio"></a>Visual Studio의 테스트 도구

Visual Studio 테스트 도구를 사용하면 사용자와 팀이 수준 높은 코드를 개발하고 유지할 수 있습니다.

> [!NOTE]
> 단위 테스트는 Visual Studio의 모든 버전에서 사용할 수 있습니다. Live Unit Testing, IntelliTest 및 Coded UI 테스트와 같은 다른 테스트 도구는 Visual Studio Enterprise 버전에서만 사용할 수 있습니다. 버전에 대한 자세한 내용은 [Visual Studio IDE 비교](https://visualstudio.microsoft.com/vs/compare/)를 참조하세요.

## <a name="test-explorer"></a>테스트 탐색기

**테스트 탐색기** 창을 통해 개발자는 단위 테스트를 만들고, 관리하고, 실행할 수 있습니다. Microsoft 단위 테스트 프레임워크를 사용하거나 여러 타사 및 공개 소스 프레임워크 중 하나를 사용할 수 있습니다.

::: moniker range="vs-2017"
![Visual Studio 테스트 탐색기](media/devtest-testexplorer.png)
::: moniker-end

::: moniker range="vs-2019"
![Visual Studio 테스트 탐색기 16.2](media/vs-2019/test-explorer-16-2.PNG)
::: moniker-end

* [유닛 테스트 시작](unit-test-your-code.md)
* [테스트 탐색기를 사용하여 단위 테스트 실행](run-unit-tests-with-test-explorer.md)
* [테스트 탐색기 FAQ](test-explorer-faq.md)
* [타사 단위 테스트 프레임워크 설치](install-third-party-unit-test-frameworks.md)

Visual Studio는 확장 가능하고 이제 NUnit 및 xUnit.net과 같은 타사 유닛 테스트 어댑터에도 사용할 수 있습니다. 또한 코드 복제본 기능은 일반적인 버그 수정 또는 리팩터링의 후보가 될 수 있는 의미상 비슷한 코드 블록을 식별하도록 지원함으로써 고품질 소프트웨어 제공과 관련되어 있습니다.

![타사 테스트 통합](media/devtest-thirdparty.png)

## <a name="live-unit-testing"></a>Live Unit Testing

[Live Unit Testing](../test/live-unit-testing.md)은 자동으로 백그라운드에서 단위 테스트를 실행하고 Visual Studio 코드 편집기의 코드 검사 및 테스트 결과를 그래픽으로 표시합니다.

## <a name="intellitest"></a>IntelliTest

IntelliTest는 단위 테스트와, 관리 코드에 대한 테스트 데이터를 자동으로 생성합니다. IntelliTest는 적용 범위를 개선하고 새 코드나 기존 코드에 대한 단위 테스트를 만들고 유지하기 위한 노력을 대폭 줄여 줍니다.

![작동 중인 IntelliTest](media/devtest-intellitest.png)

* [IntelliTest를 사용하여 코드에 대한 단위 테스트 생성](generate-unit-tests-for-your-code-with-intellitest.md)
* [IntelliTest - 한 번 테스트로 모두 제어](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)
* [IntelliTest 참조 설명서](intellitest-manual/index.md)

## <a name="code-coverage"></a>코드 검사

[코드 검사](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)는 프로젝트의 코드 중 유닛 테스트와 같은 코딩된 테스트를 사용하여 실제로 테스트할 부분을 결정합니다. 버그로부터 효과적으로 보호하려면 코드의 상당한 부분을 실행 또는 "검사"해야 합니다.

코드 검사 분석은 관리되는 코드와 관리되지 않은(네이티브) 코드에 적용할 수 있습니다.

테스트 탐색기를 사용하여 테스트 메서드를 실행하는 경우 코드 검사는 선택 사항입니다. 결과 테이블에는 각 어셈블리, 클래스 및 메서드에서 실행되는 코드의 백분율이 표시됩니다. 또한 소스 편집기에는 테스트된 코드가 표시됩니다.

* [코드 검사를 사용하여 테스트할 코드 범위 결정](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Visual Studio의 유닛 테스트, 코드 검사 및 코드 복제본 분석(랩)](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html)
* [코드 검사 분석 사용자 지정](customizing-code-coverage-analysis.md)

## <a name="microsoft-fakes"></a>Microsoft Fakes

[Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)는 스텁 또는 shim을 사용하는 애플리케이션의 다른 부분을 교체함으로써 사용자가 테스트 중인 코드를 격리시켜 줍니다.

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>코딩된 UI 및 Selenium을 사용하여 사용자 인터페이스 테스트

코딩된 UI 테스트를 통해 완전 자동화된 테스트를 만들어 애플리케이션 사용자 인터페이스 기능과 동작의 유효성을 검사할 수 있습니다. 코딩된 UI 테스트는 XAML 기반 UWP 앱, 브라우저 앱, SharePoint 앱을 포함한 다양한 기술에서 UI 테스트를 자동화할 수 있습니다.

최고 수준의 코딩된 UI 테스트 또는 Selenium을 사용한 제네릭 브라우저 기반 UI 테스트를 선택할지 여부와 관계없이 Visual Studio는 필요한 모든 도구를 제공합니다.

![코딩된 UI를 통해 UI 테스트](media/devtest-codeduitest.png)

* [UI 자동화를 사용하여 코드 테스트](use-ui-automation-to-test-your-code.md)
* [코딩된 UI 테스트 만들기, 편집 및 유지 관리 시작](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [코딩된 UI 테스트를 사용하여 UWP 앱 테스트](test-uwp-app-with-coded-ui-test.md)
* [Visual Studio Enterprise의 코딩된 UI 테스트 소개(랩)](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html)

## <a name="load-testing"></a>부하 테스트

[부하 테스트](../test/quickstart-create-a-load-test-project.md)는 단위 테스트 및 웹 성능 테스트를 실행하여 서버 애플리케이션에서 부하를 시뮬레이트합니다.

## <a name="related-scenarios"></a>관련 시나리오

* [예비 및 수동 테스트(Azure Test Plans)](/azure/devops/test/index?view=vsts)
* [부하 테스트(Azure Test Plans)](/azure/devops/test/load-test/index?view=vsts)
* [지속적인 테스트(Azure Test Plans)](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)
* [코드 분석 도구](../code-quality/code-analysis-for-managed-code-overview.md)
