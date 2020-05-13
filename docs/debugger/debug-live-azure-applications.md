---
title: 라이브 ASP.NET Azure 앱 디버그
description: 스냅샷 디버거로 snappoint를 설정하고 스냅샷을 보는 방법을 알아봅니다.
ms.custom: ''
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 6944c930ba6357fffeebba417a32cd167bd4debd
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70179828"
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>스냅샷 디버거를 사용하여 라이브 ASP.NET Azure 앱 디버그

스냅샷 디버거는 관심이 있는 코드가 실행될 때 프로덕션 상태 앱의 스냅샷을 생성합니다. 디버거가 스냅샷을 생성하도록 명령하려면 코드에서 snappoint와 logpoint를 설정합니다. 디버거를 통해 프로덕션 애플리케이션의 트래픽에 영향을 미치지 않으면서 정확히 무엇이 잘못되었는지를 볼 수 있습니다. 스냅샷 디버거를 사용하면 프로덕션 환경에서 발생하는 문제를 해결하는 데 걸리는 시간을 상당히 줄일 수 있습니다.

snappoint 및 logpoint는 중단점과 유사하지만, 중단점과 달리 snappoint는 적중될 때 애플리케이션을 중지시키지 않습니다. 일반적으로 snappoint에서 스냅샷을 캡처하는 데는 10~20 밀리초가 걸립니다.

이 자습서에서 다음을 수행합니다.

> [!div class="checklist"]
> * 스냅샷 디버거 시작
> * snappoint 설정 및 스냅샷 보기
> * logpoint 설정

## <a name="prerequisites"></a>필수 구성 요소

* 스냅샷 디버거는 **Azure 개발 워크로드**를 사용하여 Visual Studio 2017 Enterprise 버전 15.5 이상에서만 사용할 수 있습니다. (**개별 구성 요소** 탭의 **디버깅 및 테스트** > **스냅샷 디버거**에서 찾을 수 있습니다.)

   ::: moniker range=">=vs-2019"
   아직 설치하지 않은 경우 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)를 설치합니다. 이전 Visual Studio 설치에서 업데이트하는 경우 Visual Studio 설치 관리자를 실행하고 **ASP.NET 및 웹 개발 워크로드**에서 스냅샷 디버거 구성 요소를 확인합니다.
   ::: moniker-end
   ::: moniker range="<=vs-2017"
   아직 설치되지 않은 경우 [Visual Studio 2017 Enterprise 버전 15.5](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 이상을 설치하세요. 이전 Visual Studio 2017 설치에서 업데이트하는 경우 Visual Studio 설치 관리자를 실행하고 **ASP.NET 및 웹 개발 워크로드**에서 스냅샷 디버거 구성 요소를 확인합니다.
   ::: moniker-end

* 기본 이상의 Azure App Service 계획이 있어야 합니다.

* 스냅샷 컬렉션은 Azure App Service에서 실행되는 다음 웹앱에서 사용할 수 있습니다.
  * .NET Framework 4.6.1 이상에서 실행되는 ASP.NET 애플리케이션
  * Windows의 .NET Core 2.0 이상에서 실행되는 ASP.NET Core 애플리케이션

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>프로젝트 열기 및 스냅샷 디버거 시작

1. 스냅샷 디버그할 프로젝트를 엽니다.

   > [!IMPORTANT]
   > 스냅샷 디버그하려면 Azure App Service에 게시된 것과 ‘동일한 버전의 소스 코드’를 열어야 합니다.

::: moniker range="<=vs-2017"

2. 클라우드 탐색기(**보기 &gt; 클라우드 탐색기**)에서 프로젝트가 배포된 Azure App Service를 마우스 오른쪽 단추로 클릭하고 **스냅샷 디버거 연결**을 선택합니다.

   ![스냅샷 디버거 시작](../debugger/media/snapshot-launch.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. **디버그 &gt; 스냅샷 디버거 연결...**을 선택합니다. 프로젝트가 배포된 Azure App Service 및 Azure Storage 계정을 선택하고 **연결**을 클릭합니다. 스냅샷 디버거는 [Azure Kubernetes Service](debug-live-azure-kubernetes.md) 및 [AZURE Virtual Machines (VM) & Virtual Machine Scale Sets](debug-live-azure-virtual-machines.md)도 지원합니다.

   ![디버그 메뉴에서 스냅샷 디버거 시작](../debugger/media/snapshot-debug-menu-attach.png)

   ![Azure 리소스 선택](../debugger/media/snapshot-select-azure-resource-appservices.png)

::: moniker-end

   > [!IMPORTANT]
   > 처음 **스냅샷 디버거 연결**을 선택하면 Azure App Service에 스냅샷 디버거 사이트 확장을 설치하라는 메시지가 표시됩니다. 이 설치를 수행하려면 Azure App Service를 다시 시작해야 합니다.

   ::: moniker range="<=vs-2017"
   > [!NOTE]
   > Application Insights 사이트 확장도 스냅샷 디버깅을 지원합니다. "사이트 확장 날짜가 만료 되었습니다." 라는 오류 메시지가 표시 되는 경우 자세한 정보를 업그레이드 하려면 [스냅숏 디버깅에 대 한 문제 해결 팁 및 알려진 문제](../debugger/debug-live-azure-apps-troubleshooting.md) 를 참조 하세요.
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   > [!NOTE]
   > (Visual Studio 2019 버전 16.2 이상) 스냅샷 디버거에서 Azure 클라우드 지원을 사용하도록 설정했습니다. 선택한 Azure 리소스 및 Azure Storage 계정이 모두 동일한 클라우드에서 사용되는지 확인합니다. 기업의 [Azure 규정 준수](https://azure.microsoft.com/overview/trusted-cloud/) 구성에 대해 궁금한 사항이 있으면 Azure 관리자에게 문의하세요.
   ::: moniker-end

   Visual Studio가 이제 스냅샷 디버깅 모드입니다.
   ![스냅숏 디버깅 모드](../debugger/media/snapshot-message.png)

   Azure App Service의 모든 모듈이 로드되면 **모듈** 창에 표시됩니다(이 창을 열려면 **디버그 > Windows > 모듈** 선택).

   ![모듈 창 확인](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>snappoint 설정

1. 코드 편집기에서 관심있는 코드 줄 옆의 왼쪽 여백을 클릭하여 snappoint를 설정합니다. 실행될 것을 알고 있는 코드인지 확인합니다.

   ![snappoint 설정](../debugger/media/snapshot-set-snappoint.png)

2. **컬렉션 시작**을 클릭하여 snappoint를 켭니다.

   ![snappoint 켜기](../debugger/media/snapshot-start-collection.png)

   > [!TIP]
   > 스냅샷을 보는 경우 단계를 진행할 수 없으나 코드에 여러 개의 snappoint를 배치하여 다른 코드 줄에서의 실행을 추적할 수 있습니다. 코드에 여러 개의 snappoint가 있으면 스냅샷 디버거는 해당 스냅샷이 동일한 최종 사용자 세션에서 온 것인지 확인합니다. 스냅샷 디버거는 앱을 사용하는 사용자가 많은 경우에도 이 작업을 수행합니다.

## <a name="take-a-snapshot"></a>스냅샷 가져오기

snappoint가 설정되면 웹 사이트의 브라우저 보기로 이동하여 표시된 코드 줄을 실행하여 수동으로 스냅샷을 생성하거나 사용자가 사이트 사용 중 하나를 생성할 때까지 대기할 수 있습니다.

## <a name="inspect-snapshot-data"></a>스냅샷 데이터 검사

1. snappoint가 적중되면 진단 도구 창에 스냅샷이 표시됩니다. 이 창을 열려면 **디버그 > Windows > 진단 도구 표시**를 선택합니다.

   ![snappoint 열기](../debugger/media/snapshot-diagsession-window.png)

1. snappoint를 두 번 클릭하여 코드 편집기에서 스냅샷을 엽니다.

   ![스냅샷 데이터 검사](../debugger/media/snapshot-inspect-data.png)

   이 보기에서 변수를 가리켜 DataTips를 보고, **로컬**, **조사식** 및 **호출 스택** 창을 사용하고, 식을 평가할 수도 있습니다.

   웹 사이트 자체는 여전히 라이브 상태이며 최종 사용자는 영향을 받지 않습니다. 기본적으로 snappoint당 하나의 스냅샷만 캡처됩니다. 하나의 스냅샷이 캡처되면 해당 snappoint가 꺼집니다. snappoint에서 또 하나의 스냅샷을 캡처하려면 **컬렉션 업데이트**를 클릭하여 snappoint를 다시 켤 수 있습니다.

앱에 snappoint를 더 추가하고 **컬렉션 업데이트** 단추로 켤 수도 있습니다.

**도움이 필요하세요?** [문제 해결 및 알려진 문제](../debugger/debug-live-azure-apps-troubleshooting.md)와 [스냅샷 디버깅 FAQ](../debugger/debug-live-azure-apps-faq.md) 페이지를 참조하세요.

## <a name="set-a-conditional-snappoint"></a>조건부 snappoint 설정

앱에서 특정 상태를 다시 만드는 것이 어려운 경우 조건부 snappoint 사용을 고려합니다. 조건부 snappoint는 검사할 특정 값이 변수에 포함되어 있는 경우와 같이 스냅샷을 만들 시기를 제어하는 데 도움이 됩니다. 조건은 식, 필터 또는 적중 횟수를 사용하여 설정할 수 있습니다.

#### <a name="to-create-a-conditional-snappoint"></a>조건부 snappoint를 만들려면

1. snappoint 아이콘(속이 빈 공)을 마우스 오른쪽 단추로 클릭하고 **설정**을 선택합니다.

   ![설정 선택](../debugger/media/snapshot-snappoint-settings.png)

1. snappoint 설정 창에서 식을 입력합니다.

   ![식 입력](../debugger/media/snapshot-snappoint-conditions.png)

   앞의 그림에서는 `visitor.FirstName == "Dan"`인 경우에만 스냅샷이 생성됩니다.

## <a name="set-a-logpoint"></a>logpoint 설정

snappoint가 적중될 때 스냅샷을 생성하는 것 외에 메시지를 로그하도록(즉, logpoint를 만들도록) snappoint를 구성할 수도 있습니다. 앱을 다시 배포할 필요 없이 logpoint를 설정할 수 있습니다. logpoint는 가상으로 실행되며 실행 중인 애플리케이션에 영향을 미치거나 부작용을 일으키지 않습니다.

#### <a name="to-create-a-logpoint"></a>logpoint를 만들려면

1. snappoint 아이콘(파란색 육각형)을 마우스 오른쪽 단추로 클릭하고 **설정**을 선택합니다.

2. snappoint 설정 창에서 **작업**을 선택합니다.

   ![logpoint 만들기](../debugger/media/snapshot-logpoint.png)

3. **메시지** 필드에 로그할 새 로그 메시지를 입력할 수 있습니다. 로그 메시지에서 변수를 중괄호 안에 배치하여 변수를 평가할 수도 있습니다.

   **출력 창으로 보내기**를 선택하는 경우 logpoint가 적중되면 진단 도구 창에 메시지가 표시됩니다.

   ![진단 도구 창의 logpoint 데이터](../debugger/media/snapshot-logpoint-output.png)

   **애플리케이션 로그로 보내기**를 선택하는 경우 logpoint가 적중되면 [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs)와 같이 `System.Diagnostics.Trace`(또는 .NET Core에서는 `ILogger`)의 메시지를 볼 수 있는 모든 위치에 메시지가 표시됩니다.

## <a name="next-steps"></a>다음 단계

이 자습서에서는 App Services용 스냅샷 디버거를 사용하는 방법을 배웠습니다. 이 기능에 대한 자세한 정보를 알아볼 수 있습니다.

> [!div class="nextstepaction"]
> [스냅샷 디버깅 FAQ](../debugger/debug-live-azure-apps-faq.md)
