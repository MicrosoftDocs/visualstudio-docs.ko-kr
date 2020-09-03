---
title: IntelliTrace 데이터
ms.date: 10/13/2016
ms.topic: how-to
helpviewer_keywords:
- IntelliTrace, configuring test settings
- Diagnostic Data Adapter, InteliTrace
- debugging [Visual Studio ALM], difficult issues using IntelliTrace
- Test Runner, InteliTrace
ms.assetid: 02b6716f-569e-4961-938a-e790a0c74b5c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d0983967d42c6daa89b9a690b93fb97872e98603
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288262"
---
# <a name="how-to-collect-intellitrace-data-to-help-debug-difficult-issues"></a>방법: 어려운 문제 디버그에 도움이 되는 IntelliTrace 데이터 수집

Visual Studio에서 특정 진단 추적 정보를 수집하도록 IntelliTrace용 진단 데이터 어댑터를 구성할 수 있습니다. 테스트에서 이 어댑터를 사용하여 애플리케이션에 대한 중요한 진단 이벤트를 수집할 수 있습니다. 개발자는 나중에 이 데이터를 사용하여 코드를 추적하여 버그의 원인을 찾을 수 있습니다. IntelliTrace의 진단 데이터 어댑터는 수동 테스트나 자동화된 테스트에 사용할 수 있습니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> IntelliTrace는 관리 코드를 사용하여 작성된 애플리케이션에 대해서만 작동합니다. 브라우저를 클라이언트로 사용하는 웹 애플리케이션을 테스트할 때는 추적할 수 있는 관리 코드가 없으므로 테스트 설정에서 클라이언트에 대해 IntelliTrace를 사용하지 않도록 설정해야 합니다. 이 경우 웹 서버에서 원격으로 환경을 설정하고 IntelliTrace 데이터를 수집할 수 있습니다.

IntelliTrace 데이터는 확장명이 *.iTrace*인 파일에 저장됩니다. 테스트를 실행했을 때 테스트 단계가 실패하는 경우 버그를 만들 수 있습니다. 진단 정보를 포함하는 IntelliTrace 파일이 이 버그에 자동으로 연결됩니다.

> [!NOTE]
> 테스트가 성공적으로 통과하면 IntelliTrace의 진단 데이터 어댑터에서 IntelliTrace 파일이 만들어지지 않습니다. 이 파일은 테스트 사례가 실패하거나 테스터가 버그를 제출하는 경우에만 저장됩니다.

IntelliTrace 파일에 수집된 데이터를 활용하면 코드의 오류를 재현하고 진단하는 데 필요한 시간을 줄일 수 있으므로 디버깅 생산성을 향상시키는 데 도움이 됩니다. 또한 IntelliTrace 파일을 다른 사용자와 공유하면 각 사용자가 자신의 컴퓨터에서 로컬 세션을 복제할 수 있으므로 버그를 대부분의 환경에서 큰 어려움 없이 동일하게 재현할 수 있습니다.

> [!NOTE]
> 테스트 설정에서 IntelliTrace를 사용하도록 지정한 경우 코드 검사 데이터는 수집되지 않습니다.

> [!WARNING]
> IntelliTrace의 진단 데이터 어댑터가 작동하려면 테스트 실행을 위해 테스트가 로드된 후 관리되는 프로세스를 계측해야 합니다. 모니터링할 프로세스가 이미 시작된 경우 프로세스가 이미 실행 중이므로 IntelliTrace 파일이 수집되지 않습니다. 이를 해결하려면 테스트가 로드되기 전에 프로세스를 중지한 다음, 테스트가 로드된 후 또는 첫 번째 테스트가 시작되기 전에 프로세스를 시작해야 합니다.

::: moniker range="vs-2017"
다음 절차에서는 수집할 IntelliTrace 데이터를 구성하는 방법을 설명합니다. 이러한 단계는 Microsoft Test Manager의 구성 편집기와 Visual Studio의 테스트 설정 대화 상자에 모두 적용됩니다.
::: moniker-end
::: moniker range=">=vs-2019"
다음 절차에서는 수집할 IntelliTrace 데이터를 구성하는 방법을 설명합니다. 이러한 단계는 Visual Studio의 테스트 설정 대화 상자에 적용됩니다.
::: moniker-end

> [!NOTE]
> IntelliTrace 데이터를 수집하는 데 사용되는 테스트 에이전트의 사용자 계정은 Administrators 그룹의 멤버여야 합니다. 자세한 내용은 [테스트 에이전트 설치 및 구성](../test/lab-management/install-configure-test-agents.md)을 참조하세요.

## <a name="configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>IntelliTrace 진단 데이터 어댑터를 사용하여 수집할 데이터 구성

::: moniker range="vs-2017"
이 절차의 단계를 수행하기 전에 Microsoft Test Manager 또는 Visual Studio에서 테스트 설정을 열고 **데이터 및 진단** 페이지를 선택해야 합니다.
::: moniker-end
::: moniker range=">=vs-2019"
이 절차의 단계를 수행하려면 먼저 Visual Studio에서 테스트 설정을 연 다음, **데이터 및 진단** 페이지를 선택해야 합니다.
::: moniker-end

### <a name="to-configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>IntelliTrace 진단 데이터 어댑터를 사용하여 수집할 데이터를 구성하려면

1. IntelliTrace 데이터를 수집하는 데 사용할 역할을 선택합니다.

2. **IntelliTrace**를 선택합니다.

3. 웹 클라이언트 역할 또는 ASP.NET 웹 애플리케이션에 대해 IntelliTrace를 추가하는 경우 **IntelliTrace 및 테스트 영향용 ASP.NET 클라이언트 프록시**도 선택해야 합니다.

     이 프록시를 사용하면 IntelliTrace 및 테스트 영향 진단 데이터 어댑터와 관련하여 클라이언트에서 웹 서버로 보내는 HTTP 호출에 대한 정보를 수집할 수 있습니다.

    > [!WARNING]
    > IntelliTrace 데이터를 수집할 IIS(Internet Information Server)의 애플리케이션 풀에 사용되는 ID에 사용자 지정 계정을 사용하려는 경우, 사용할 사용자 지정 계정에 대한 로컬 사용자 프로필을 IIS 머신에 만들어야 합니다. 사용자 지정 계정 자격 증명을 사용하여 로컬로 한 번 IIS 컴퓨터에 로그온하거나 다음 명령줄을 실행하면 사용자 지정 계정에 대한 로컬 프로필을 만들 수 있습니다.
    >
    > **runas /user:domain\name /profile cmd.exe**

4. **IntelliTrace**의 **구성**을 선택하고 기본 IntelliTrace 설정을 수정합니다.

     수집할 데이터를 구성하는 데 사용할 대화 상자가 나타납니다.

    > [!WARNING]
    > IntelliTrace 데이터를 수집하도록 설정한 경우 코드 검사 데이터는 수집되지 않습니다.

5. **일반** 탭을 선택합니다. 테스트할 때 성능에 미치는 영향을 최소화하기 위해 중요 진단 이벤트만 기록하려면 **IntelliTrace 이벤트만**을 선택합니다.

     또는

     호출 정보를 표시하는 메서드 수준 추적 정보와 진단 이벤트를 모두 기록하려면 **IntelliTrace 이벤트 및 호출 정보**를 선택합니다. 이 수준의 추적을 사용하면 테스트를 실행할 때 성능이 저하될 수 있습니다.

6. 인터넷 정보 서비스에서 실행되는 ASP.NET 애플리케이션의 데이터를 수집하려면 **인터넷 정보 서비스에서 실행되는 ASP.NET 애플리케이션의 데이터 수집**을 선택합니다. 웹 서버 역할에 대해 테스트 에이전트를 설정 및 구성합니다. [테스트 에이전트 설치 및 구성](../test/lab-management/install-configure-test-agents.md)을 참조하세요.

7. **모듈** 탭을 선택합니다. **다음을 제외한 모든 모듈에서 데이터 수집**을 선택하고 **추가**를 사용하여 목록에 모듈을 추가하거나, **제거**를 사용하여 모듈을 제거합니다. 이 방법을 사용하면 지정한 모듈을 제외하고 시스템에서 실행되는 모든 모듈을 포함할 수 있습니다.

     또는

     **다음 모듈에서만 데이터 수집**을 선택하고 **추가**를 사용하여 목록에 모듈을 추가하거나 **제거**를 사용하여 모듈을 제거합니다. 이 방법을 사용하면 필요한 모듈을 정확하게 지정할 수 있습니다.

    > [!NOTE]
    > 가능한 경우 최적의 성능을 위해 모니터링할 특정 프로세스를 선택하는 것이 좋습니다.

8. **프로세스** 탭을 선택합니다. **다음을 제외한 모든 프로세스에서 데이터 수집**을 선택하고 **추가**를 사용하여 목록에 프로세스를 추가하거나 **제거**를 사용하여 프로세스를 제거합니다. 이 옵션을 사용하면 지정한 프로세스를 제외하고 시스템에서 실행되는 모든 프로세스를 포함할 수 있습니다.

     또는

     **지정한 프로세스에서만 데이터 수집**을 선택하고 **추가**를 사용하여 목록에 프로세스를 추가하거나 **제거**를 사용하여 프로세스를 제거합니다. 이 방법을 사용하면 필요한 프로세스를 정확하게 지정할 수 있습니다.

9. (선택 사항) **IntelliTrace 이벤트** 탭을 선택합니다. 진단 이벤트를 수집할 때 포함하거나 제외할 각 IntelliTrace 이벤트 범주를 선택하거나 선택 취소합니다.

10. (선택 사항) 각 IntelliTrace 이벤트 범주를 확장하고 IntelliTrace 이벤트에 포함하거나 IntelliTrace 이벤트에서 제외할 특정 이벤트를 각각 선택 또는 선택 취소합니다.

11. (선택 사항) **고급** 탭을 선택합니다. 그런 다음, **기록할 수 있는 최대 디스크 공간** 옆에 있는 화살표를 선택하고 IntelliTrace 파일에 사용할 수 있도록 설정할 최대 크기를 선택합니다.

    > [!NOTE]
    > 기록 크기를 늘리면 테스트 결과와 함께 이 기록을 저장할 때 시간 초과 문제가 발생할 수 있습니다.

12. Microsoft Test Manager(Visual Studio 2017에서 사용 중단됨)를 사용하는 경우 **저장**을 선택합니다. Visual Studio를 사용하는 경우 **확인**을 선택합니다. 테스트 설정에 대해 IntelliTrace 설정이 구성 및 저장됩니다.

    ::: moniker range="vs-2017"
    > [!NOTE]
    > 이 진단 데이터 어댑터의 구성을 다시 설정하려면 Visual Studio의 경우 **기본 구성으로 다시 설정**을 선택하고 Microsoft Test Manager의 경우에는 **기본값으로 다시 설정**을 선택합니다.
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    > [!NOTE]
    > 이 진단 데이터 어댑터의 구성을 다시 설정하려면 Visual Studio에서 **기본 구성으로 다시 설정**를 선택합니다.
    ::: moniker-end

## <a name="see-also"></a>참조

- [테스트하는 동안 진단 데이터 수집(Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts)
- [수동 테스트에서 진단 데이터 수집(Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)
- [테스트 설정을 사용하여 진단 정보 수집](../test/collect-diagnostic-information-using-test-settings.md)
- [IntelliTrace 데이터 수집](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)
