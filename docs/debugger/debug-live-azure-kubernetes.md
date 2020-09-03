---
title: 라이브 ASP.NET Azure Kubernetes Service 디버그
description: 스냅샷 디버거로 snappoint를 설정하고 스냅샷을 보는 방법을 알아봅니다.
ms.custom: ''
ms.date: 02/11/2019
ms.topic: how-to
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- aspnet
- azure
ms.openlocfilehash: e0f062108f19b38c6bf6514eda78098f493b3f78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350656"
---
# <a name="debug-live-aspnet-azure-kubernetes-services-using-the-snapshot-debugger"></a>스냅샷 디버거를 사용하여 라이브 ASP.NET Azure Kubernetes Service 디버그

스냅샷 디버거는 관심이 있는 코드가 실행될 때 프로덕션 상태 앱의 스냅샷을 생성합니다. 디버거가 스냅샷을 생성하도록 명령하려면 코드에서 snappoint와 logpoint를 설정합니다. 디버거를 통해 프로덕션 애플리케이션의 트래픽에 영향을 미치지 않으면서 정확히 무엇이 잘못되었는지를 볼 수 있습니다. 스냅샷 디버거를 사용하면 프로덕션 환경에서 발생하는 문제를 해결하는 데 걸리는 시간을 상당히 줄일 수 있습니다.

snappoint 및 logpoint는 중단점과 유사하지만, 중단점과 달리 snappoint는 적중될 때 애플리케이션을 중지시키지 않습니다. 일반적으로 snappoint에서 스냅샷을 캡처하는 데는 10~20밀리초가 걸립니다.

이 자습서에서 다음을 수행합니다.

> [!div class="checklist"]
> * 스냅샷 디버거 시작
> * snappoint 설정 및 스냅샷 보기
> * logpoint 설정

## <a name="prerequisites"></a>사전 요구 사항

* Azure Kubernetes Service용 스냅샷 디버거는 **Azure 개발 워크로드**가 포함된 Visual Studio 2019 Enterprise 이상에서만 사용할 수 있습니다. (**개별 구성 요소** 탭의 **디버깅 및 테스트** > **스냅샷 디버거**에서 찾을 수 있습니다.)

    아직 설치되지 않은 경우 [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/)를 설치하세요.

* 스냅샷 컬렉션은 다음 Azure Kubernetes Service 웹앱에서 사용할 수 있습니다.
  * Debian 9의 .NET Core 2.2 이상에서 실행되는 ASP.NET Core 애플리케이션
  * Alpine 3.8의 .NET Core 2.2 이상에서 실행되는 ASP.NET Core 애플리케이션
  * Ubuntu 18.04의 .NET Core 2.2 이상에서 실행되는 ASP.NET Core 애플리케이션

    > [!NOTE]
    > AKS에서 스냅샷 디버거에 대한 지원을 사용하는 데 도움이 되도록 [Docker 이미지의 설정을 보여 주는 일련의 Dockerfile이 포함된 리포지토리](https://github.com/Microsoft/vssnapshotdebugger-docker)를 제공합니다.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>프로젝트 열기 및 스냅샷 디버거 시작

1. 스냅샷 디버그할 프로젝트를 엽니다.

    > [!IMPORTANT]
    > 스냅샷 디버그하려면 Azure Kubernetes Service에 게시된 것과 ‘동일한 버전의 소스 코드’를 열어야 합니다.

1. **디버그 &gt; 스냅샷 디버거 연결...** 을 선택합니다. 웹앱이 배포된 AKS 리소스 및 Azure Storage 계정을 선택하고 **연결**을 클릭합니다. 스냅샷 디버거는 [Azure App Service](debug-live-azure-applications.md)와 [Azure VM(Virtual Machines) 및 Virtual Machine Scale Sets](debug-live-azure-virtual-machines.md)도 지원합니다.

    ![디버그 메뉴에서 스냅샷 디버거 시작](../debugger/media/snapshot-debug-menu-attach.png)

    ![Azure 리소스 선택](../debugger/media/snapshot-select-azure-resource-aks.png)

    > [!NOTE]
    > (Visual Studio 2019 버전 16.2 이상) 스냅샷 디버거에서 Azure 클라우드 지원을 사용하도록 설정했습니다. 선택한 Azure 리소스와 Azure Storage 계정이 모두 동일한 클라우드에서 지원되는지 확인하세요. 기업의 [Azure 규정 준수](https://azure.microsoft.com/overview/trusted-cloud/) 구성에 대한 질문이 있는 경우 Azure 관리자에게 문의하세요.

Visual Studio가 이제 스냅샷 디버깅 모드입니다.

   ![스냅샷 디버깅 모드](../debugger/media/snapshot-message.png)

   Azure App Service의 모든 모듈이 로드되면 **모듈** 창에 표시됩니다(이 창을 열려면 **디버그 > Windows > 모듈** 선택).

   ![모듈 창 확인](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>snappoint 설정

1. 코드 편집기에서 snappoint를 설정하려는 코드 줄 옆의 왼쪽 제본용 여백을 클릭합니다. 실행 예정임을 알고 있는 코드인지 확인하세요.

   ![snappoint 설정](../debugger/media/snapshot-set-snappoint.png)

1. **컬렉션 시작**을 클릭하여 snappoint를 켭니다.

   ![snappoint 켜기](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > 스냅샷을 보는 경우 단계를 진행할 수 없으나 코드에 여러 개의 snappoint를 배치하여 다른 코드 줄에서의 실행을 추적할 수 있습니다. 코드에 여러 개의 snappoint가 있으면 스냅샷 디버거는 해당 스냅샷이 동일한 최종 사용자 세션에서 온 것인지 확인합니다. 스냅샷 디버거는 앱에 적중하는 사용자가 많은 경우에도 이 작업을 수행합니다.

## <a name="take-a-snapshot"></a>스냅샷 가져오기

snappoint가 설정되면 웹 사이트의 브라우저 뷰로 이동하여 표시된 코드 줄을 실행하여 수동으로 스냅샷을 생성하거나 사용자가 사이트를 사용해 스냅샷을 생성할 때까지 대기할 수 있습니다.

## <a name="inspect-snapshot-data"></a>스냅샷 데이터 검사

1. snappoint가 적중되면 진단 도구 창에 스냅샷이 표시됩니다. 이 창을 열려면 **디버그 > Windows > 진단 도구 표시**를 선택합니다.

    ![snappoint 열기](../debugger/media/snapshot-diagsession-window.png)

1. snappoint를 두 번 클릭하여 코드 편집기에서 스냅샷을 엽니다.

    ![스냅샷 데이터 검사](../debugger/media/snapshot-inspect-data.png)

    이 보기에서 변수를 가리켜 DataTips를 보고, **로컬**, **조사식** 및 **호출 스택** 창을 사용하고, 식을 평가할 수도 있습니다.

    웹 사이트 자체는 계속 라이브 상태이며 최종 사용자는 영향을 받지 않습니다. 기본적으로 snappoint당 하나의 스냅샷만 캡처됩니다. 하나의 스냅샷이 캡처되면 해당 snappoint가 꺼집니다. snappoint에서 또 하나의 스냅샷을 캡처하려면 **컬렉션 업데이트**를 클릭하여 snappoint를 다시 켤 수 있습니다.

앱에 snappoint를 더 추가하고 **컬렉션 업데이트** 단추로 켤 수도 있습니다.

**도움이 필요하세요?** [문제 해결 및 알려진 문제](../debugger/debug-live-azure-apps-troubleshooting.md)와 [스냅샷 디버깅 FAQ](../debugger/debug-live-azure-apps-faq.md) 페이지를 참조하세요.

## <a name="set-a-conditional-snappoint"></a>조건부 snappoint 설정

앱의 특정 상태를 다시 만들기 어려운 경우 조건부 snappoint를 사용해 보세요. 조건부 snappoint를 사용하면 스냅샷을 생성할 시점(예: 검사하려는 특정 값이 변수에 포함되어 있을 때)을 제어할 수 있습니다. 조건은 식, 필터 또는 적중 횟수를 사용하여 설정할 수 있습니다.

#### <a name="to-create-a-conditional-snappoint"></a>조건부 snappoint를 만들려면

1. snappoint 아이콘(속이 빈 공)을 마우스 오른쪽 단추로 클릭하고 **설정**을 선택합니다.

   ![설정 선택](../debugger/media/snapshot-snappoint-settings.png)

1. snappoint 설정 창에서 식을 입력합니다.

   ![식 입력](../debugger/media/snapshot-snappoint-conditions.png)

   앞의 일러스트레이션에서는 `visitor.FirstName == "Dan"`인 경우에만 스냅샷이 생성됩니다.

## <a name="set-a-logpoint"></a>logpoint 설정

snappoint가 적중될 때 스냅샷을 생성하는 것 외에 메시지를 로그하도록(즉, logpoint를 만들도록) snappoint를 구성할 수도 있습니다. 앱을 다시 배포할 필요 없이 logpoint를 설정할 수 있습니다. logpoint는 가상으로 실행되며 실행 중인 애플리케이션에 영향을 미치거나 부작용을 일으키지 않습니다.

#### <a name="to-create-a-logpoint"></a>logpoint를 만들려면

1. snappoint 아이콘(파란색 육각형)을 마우스 오른쪽 단추로 클릭하고 **설정**을 선택합니다.

1. snappoint 설정 창에서 **작업**을 선택합니다.

    ![logpoint 만들기](../debugger/media/snapshot-logpoint.png)

1. **메시지** 필드에 로그할 새 로그 메시지를 입력할 수 있습니다. 로그 메시지에서 변수를 중괄호 안에 배치하여 변수를 평가할 수도 있습니다.

    **출력 창으로 보내기**를 선택하는 경우 logpoint가 적중되면 진단 도구 창에 메시지가 표시됩니다.

    ![진단 도구 창의 logpoint 데이터](../debugger/media/snapshot-logpoint-output.png)

    **애플리케이션 로그로 보내기**를 선택하는 경우 logpoint가 적중되면 [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs)와 같이 `System.Diagnostics.Trace`(또는 .NET Core에서는 `ILogger`)의 메시지를 볼 수 있는 모든 위치에 메시지가 표시됩니다.

## <a name="next-steps"></a>다음 단계

이 자습서에서는 Azure Kubernetes용 스냅샷 디버거를 사용하는 방법을 배웠습니다. 이 기능에 대한 자세한 정보를 알아볼 수 있습니다.

> [!div class="nextstepaction"]
> [스냅샷 디버깅 FAQ](../debugger/debug-live-azure-apps-faq.md)