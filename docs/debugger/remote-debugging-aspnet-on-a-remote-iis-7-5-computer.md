---
title: IIS 컴퓨터의 원격 디버그 ASP.NET
ms.custom:
- remotedebugging
- seodec18
ms.date: 05/21/2018
ms.topic: conceptual
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 86b035164c4d34f4ce0182ea51fdfe6381ad2d4f
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72536026"
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>원격 IIS 컴퓨터의 ASP.NET 원격 디버그
IIS에 배포된 ASP.NET 애플리케이션을 디버그하려면 앱을 배포한 컴퓨터에 원격 도구를 설치하고 실행한 다음, Visual Studio에서 실행 중인 앱에 연결합니다.

![원격 디버거 구성 요소](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

이 가이드에서는 Visual Studio ASP.NET MVC 4.5.2 애플리케이션을 설정 및 구성하고, IIS에 배포하고, Visual Studio에서 원격 디버거를 연결하는 방법을 설명합니다.

> [!NOTE]
> 대신 ASP.NET Core를 원격 디버그하려면 [IIS 컴퓨터의 원격 디버그 ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)를 참조하세요. Azure App Service의 경우 [스냅샷 디버거](../debugger/debug-live-azure-applications.md)(.NET 4.6.1 필요)를 사용하거나 [서버 탐색기에서 디버거를 연결](../debugger/remote-debugging-azure.md)하여 미리 구성된 IIS 인스턴스에서 쉽게 배포하고 디버그할 수 있습니다.

## <a name="prerequisites"></a>사전 요구 사항

::: moniker range=">=vs-2019"
이 문서에 표시된 단계를 수행하려면 Visual Studio 2019가 필요합니다.
::: moniker-end
::: moniker range="vs-2017"
이 문서에 표시된 단계를 수행하려면 Visual Studio 2017이 필요합니다.
::: moniker-end

이러한 절차는 다음 서버 구성에서 테스트되었습니다.
* Windows Server 2012 R2 및 IIS 8(참고로, Windows Server 2008 R2의 경우 서버 단계가 다름)

## <a name="network-requirements"></a>네트워크 요구 사항

원격 디버거는 Windows Server 2008 서비스 팩 2부터 Windows Server에서 지원됩니다. 요구 사항 전체 목록은 [요구 사항](../debugger/remote-debugging.md#requirements_msvsmon)을 참조하세요.

> [!NOTE]
> 프록시를 통해 연결된 두 컴퓨터 간의 디버깅은 지원되지 않습니다. 대기 시간이 길거나 대역폭이 낮은 연결(예: 전화 접속 인터넷) 또는 해외 인터넷을 통해 디버그하면 오류가 발생하거나 지나치게 느릴 수 있으므로 권장하지 않습니다.

## <a name="app-already-running-in-iis"></a>앱을 IIS에서 이미 실행 중인 경우

이 문서에는 Windows Server에서 IIS의 기본 구성을 설정하고 Visual Studio에서 앱을 배포하는 단계가 포함되어 있습니다. 이러한 단계는 서버에 필수 구성 요소가 설치되어 있는지, 앱이 올바르게 실행될 수 있는지, 원격 디버그할 준비가 되었는지 확인하기 위해 포함된 것입니다.

* 앱이 IIS에서 실행 중이고 원격 디버거를 다운로드하여 디버깅을 시작하려는 경우 [Windows Server에서 원격 도구 다운로드 및 설치](#BKMK_msvsmon)로 이동합니다.

* 디버깅을 위해 IIS에서 애플리케이션이 올바르게 설정, 배포 및 실행되는지 확인하려면 이 항목의 모든 단계를 수행합니다.

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Visual Studio 컴퓨터에서 ASP.NET 4.5.2 애플리케이션 만들기

1. 새 MVC ASP.NET 애플리케이션을 만듭니다.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019에서 **Ctrl+Q**를 입력하여 검색 상자를 열고 **asp.net**을 입력하고 **템플릿**을 선택한 다음, **새 ASP.NET 웹 애플리케이션 만들기(.NET Framework)** 를 선택합니다. 대화 상자가 나타나면 프로젝트 이름을 **MyASPApp**으로 지정한 다음, **만들기**를 선택합니다. **MVC**를 선택한 후 **만들기**를 선택합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017에서 이렇게 하려면 **파일 > 새로 만들기 > 프로젝트**를 선택한 다음, **Visual C# > 웹 > ASP.NET 웹 애플리케이션**을 선택합니다. **ASP.NET 4.5.2** 템플릿 섹션에서 **MVC**를 선택합니다. **Docker 지원 사용**이 선택되어 있고 **인증**이 **인증 없음**으로 설정되어 있는지 확인합니다. 프로젝트 이름을 **MyASPApp**으로 지정합니다.
    ::: moniker-end

2. *HomeController.cs* 파일을 열고 `About()` 메서드에 중단점을 설정합니다.

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a> Windows Server에서 IIS 설치 및 구성

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Windows Server에서 브라우저 보안 설정 업데이트

Internet Explorer에서 보안 강화 구성이 사용하도록 설정되어 있으면(기본적으로 사용하도록 설정되어 있음) 일부 웹 서버 구성 요소를 다운로드할 수 있도록 일부 도메인을 신뢰할 수 있는 사이트로 추가해야 할 수 있습니다. **인터넷 옵션 > 보안 > 신뢰할 수 있는 사이트 > 사이트**로 이동하여 신뢰할 수 있는 사이트를 추가합니다. 다음 도메인을 추가합니다.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

소프트웨어를 다운로드하는 경우 다양한 웹 사이트 스크립트 및 리소스를 로드하는 권한을 부여하라는 요청을 받게 됩니다. 이러한 리소스 중 일부는 필요하지 않지만 프로세스를 간소화하기 위해 메시지가 표시되면 **추가**를 클릭합니다.

## <a name="install-aspnet-45-on-windows-server"></a><a name="BKMK_deploy_asp_net"></a> Windows Server에 ASP.NET 4.5 설치

IIS에 ASP.NET을 설치하는 방법에 대한 자세한 내용은 [ASP.NET 3.5 및 ASP.NET 4.5를 사용하는 IIS 8.0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)을 참조하세요.

1. 서버 관리자의 왼쪽 창에서 **IIS**를 선택합니다. 서버를 마우스 오른쪽 단추로 클릭하고 **IIS(인터넷 정보 서비스) 관리자**를 선택합니다.

1. WebPI(웹 플랫폼 설치 관리자)를 사용하여 ASP.NET 4.5를 설치합니다(Windows Server 2012 R2의 서버 노드**Get New Web Platform Components**(새 웹 플랫폼 구성 요소 가져오기)를 선택한 후 ASP.NET 검색).

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Windows Server 2008 R2를 사용 중인 경우 다음 명령을 사용하여 ASP.NET 4를 대신 설치하세요.

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. 시스템을 다시 시작하거나 명령 프롬프트에서 **net stop was /y**에 이어 **net start w3svc**를 실행하여 시스템 PATH에 대한 변경 내용을 선택합니다.

## <a name="choose-a-deployment-option"></a>배포 옵션 선택

IIS에 앱을 배포하는 데 도움이 필요한 경우 다음 옵션을 고려합니다.

* IIS에서 게시 설정 파일을 만들고 Visual Studio에서 설정을 가져와서 배포합니다. 일부 시나리오에서는 이 방법이 앱을 배포하기에 가장 빠릅니다. 게시 설정 파일을 만들면 IIS에서 사용 권한이 자동으로 설정됩니다.

* 로컬 폴더에 게시하고 선호하는 방법으로 출력을 IIS에 준비된 앱 폴더에 복사하여 배포합니다.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(선택 사항) 게시 설정 파일을 사용하여 배포

이 옵션을 사용하여 게시 설정 파일을 만들고 Visual Studio로 가져올 수 있습니다.

> [!NOTE]
> 이 배포 방법은 웹 배포를 사용합니다. 설정을 가져오는 대신 Visual Studio에서 웹 배포를 직접 구성하려는 경우 호스팅 서버용 웹 배포 3.6 대신 웹 배포 3.6을 설치하면 됩니다. 단, 웹 배포를 직접 구성하는 경우 서버의 앱 폴더가 올바른 값과 권한으로 구성되어 있는지 확인해야 합니다([ASP.NET 웹 사이트 구성](#BKMK_deploy_asp_net)참조).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Windows Server에서 호스팅 서버용 웹 배포 설치 및 구성

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Windows Server의 IIS에서 게시 설정 파일 만들기

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio에서 게시 설정 가져오기 및 배포

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

앱을 성공적으로 배포한 후 자동으로 시작해야 합니다. 앱이 Visual Studio에서 시작되지 않는 경우 IIS에서 앱을 시작합니다.

1. **설정** 대화 상자에서 **다음**을 클릭하여 디버깅을 사용하도록 설정하고 **디버그** 구성을 선택한 다음, **파일 게시** 옵션 아래에서 **대상에서 추가 파일 제거**를 선택합니다.

    > [!NOTE]
    > 릴리스 구성을 선택하는 경우 게시할 때 *web.config* 파일에서 디버깅을 사용하지 않도록 설정합니다.

1. **저장**을 클릭한 다음, 앱을 다시 게시합니다.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(선택 사항) 로컬 폴더에 게시하여 배포

PowerShell, RoboCopy를 사용하여 앱을 IIS에 복사하거나 수동으로 파일을 복사하려는 경우 이 옵션을 사용하여 앱을 배포할 수 있습니다.

### <a name="configure-the-aspnet-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a> Windows Server 컴퓨터에서 ASP.NET 웹 사이트 구성

1. Windows 탐색기를 열고 **C:\Publish**라는 새 폴더를 만듭니다. 여기에서 나중에 ASP.NET 프로젝트를 배포합니다.

2. **IIS(인터넷 정보 서비스) 관리자**가 아직 열려있지 않으면 엽니다. (서버 관리자의 왼쪽 창에서 **IIS**를 선택합니다. 서버를 마우스 오른쪽 단추로 클릭하고 **IIS(인터넷 정보 서비스) 관리자**를 선택합니다.)

3. 왼쪽 창의 **연결** 아래 **사이트**로 이동합니다.

4. **기본 웹 사이트**를 선택하고 **기본 설정**을 선택한 다음, **실제 경로**를 **C:\Publish**로 설정합니다.

5. **기본 웹 사이트** 노드를 마우스 오른쪽 단추로 클릭하고 **애플리케이션 추가**를 선택합니다.

6. **별칭** 필드를 **MyASPApp**으로 설정하고 기본 애플리케이션 풀(**DefaultAppPool**)을 적용한 후 **실제 경로**를 **C:\Publish**로 설정합니다.

7. **연결**에서 **애플리케이션 풀**을 선택합니다. **DefaultAppPool**을 열고 애플리케이션 풀 필드를 **ASP.NET v4.0**으로 설정합니다(ASP.NET 4.5는 애플리케이션 풀의 옵션이 아님).

8. IIS 관리자에서 사이트를 선택하여 **사용 권한 편집**을 선택하고 IUSR, IIS_IUSRS 또는 애플리케이션 풀에 구성된 사용자가 읽기 및 실행 권한이 있는 사용자인지 확인합니다. 이러한 사용자가 없는 경우에는 읽기 및 실행 권한이 있는 사용자로 IUSR을 추가합니다.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Visual Studio에서 로컬 폴더에 게시하여 앱을 게시 및 배포

파일 시스템 또는 기타 도구를 사용하여 앱을 게시하고 배포할 수도 있습니다.

1. (ASP.NET 4.5.2) web.config 파일에 올바른 버전의 .NET이 나열되는지 확인합니다.  예를 들어 ASP.NET 4.5.2를 대상으로 하는 경우 이 버전이 web.config에 나열되는지 확인합니다.

    ```xml
    <system.web>
      <compilation debug="true" targetFramework="4.5.2" />
      <httpRuntime targetFramework="4.5.2" />
      <httpModules>
        <add name="ApplicationInsightsWebTracking" type="Microsoft.ApplicationInsights.Web.ApplicationInsightsHttpModule, Microsoft.AI.Web" />
      </httpModules>
    </system.web>

    ```

    예를 들어 4.5.2가 아닌 ASP.NET 4를 설치하는 경우 버전은 4.0이어야 합니다.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a> Windows Server에서 원격 도구 다운로드 및 설치

Visual Studio 버전과 일치하는 원격 도구 버전을 다운로드합니다.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a> Windows Server에서 원격 디버거 설정

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 추가 사용자의 사용 권한을 추가하거나 원격 디버거의 인증 모드 또는 포트 번호를 변경해야 하는 경우 [원격 디버거 구성](../debugger/remote-debugging.md#configure_msvsmon)을 참조하세요.

원격 디버거를 서비스로 실행하는 방법에 대한 정보는 [원격 디버거를 서비스로 실행](../debugger/remote-debugging.md#bkmk_configureService)을 참조하세요.

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a> Visual Studio 컴퓨터에서 ASP.NET 애플리케이션에 연결

1. Visual Studio 컴퓨터에서 디버그하려는 솔루션(이 문서의 단계를 수행하는 경우 **MyASPApp**)을 엽니다.
2. Visual Studio에서 **디버그 > 프로세스에 연결**(Ctrl+Alt+P)을 클릭합니다.

    > [!TIP]
    > Visual Studio 2017 이상 버전에서는 **디버그 > 프로세스에 다시 연결...** (Shift+Alt+P)을 사용하여 이전에 연결한 프로세스에 다시 연결할 수 있습니다.

3. 한정자 필드를 **\<원격 컴퓨터 이름>** 으로 설정하고 **Enter** 키를 누릅니다.

    Visual Studio에서 **\<원격 컴퓨터 이름>:포트** 형식으로 표시되는 컴퓨터 이름에 필요한 포트를 추가하는지 확인합니다.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019에서는 **\<원격 컴퓨터 이름>:4024**가 표시됩니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017에서는 **\<원격 컴퓨터 이름>:4022**가 표시됩니다.
    ::: moniker-end
    이 포트는 필수입니다. 포트 번호가 표시되지 않으면 수동으로 추가하세요.

4. **새로 고침**을 클릭합니다.
    일부 프로세스가 **사용 가능한 프로세스** 창에 표시됩니다.

    프로세스가 보이지 않으면 원격 컴퓨터 이름 대신 IP 주소를 사용해 보세요(포트가 필요함). 명령줄에서 `ipconfig`를 사용하여 IPv4 주소를 가져올 수 있습니다.

5. **모든 사용자의 프로세스 표시**를 선택합니다.

6. 프로세스 이름의 첫 글자를 입력하면 ASP.NET 4.5의 **w3wp.exe**를 신속하게 찾을 수 있습니다.

    **w3wp.exe**가 표시되는 프로세스가 여러 개인 경우 **사용자 이름** 열을 확인합니다. 일부 시나리오에서는 **사용자 이름** 열에 **IIS APPPOOL\DefaultAppPool**과 같은 앱 풀 이름이 표시됩니다. 앱 풀이 표시되는 경우 올바른 프로세스를 식별하는 간편한 방법은 디버그할 앱 인스턴스에 대한 새 명명된 앱 풀을 만든 다음, **사용자 이름** 열에서 손쉽게 찾는 것입니다.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. **연결**을 클릭합니다.

8. 원격 컴퓨터의 웹 사이트를 엽니다. 브라우저에서 **http://\<원격 컴퓨터 이름>** 으로 이동합니다.

    ASP.NET 웹 페이지가 표시됩니다.
9. 실행 중인 ASP.NET 애플리케이션에서 **정보** 페이지 링크를 클릭합니다.

    Visual Studio에서 중단점이 적중됩니다.

## <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> 문제 해결: Windows Server에서 필수 포트 열기

대부분의 설정에서는 ASP.NET 및 원격 디버거를 설치하여 필요한 포트를 엽니다. 하지만 포트가 열려있는지 확인해야 합니다.

> [!NOTE]
> Azure VM에서는 [네트워크 보안 그룹](/azure/virtual-machines/windows/nsg-quickstart-portal)을 통해 포트를 열어야 합니다.

필수 포트:

* 80 - IIS에 필요합니다.
::: moniker range=">=vs-2019"
* 4024 - Visual Studio 2019에서 원격 디버깅에 필요합니다(자세한 내용은 [원격 디버거 포트 할당](../debugger/remote-debugger-port-assignments.md) 참조).
::: moniker-end
::: moniker range="vs-2017"
* 4022 - Visual Studio 2017에서 원격 디버깅에 필요합니다(자세한 내용은 [원격 디버거 포트 할당](../debugger/remote-debugger-port-assignments.md) 참조).
::: moniker-end
* UDP 3702 - (선택 사항) 검색 포트를 사용하면 Visual Studio에서 원격 디버거에 연결할 때 **찾기** 단추를 사용할 수 있습니다.

1. Windows Server에서 포트를 열려면 **시작** 메뉴를 열고 **고급 보안이 포함된 Windows 방화벽**을 검색합니다.

2. 그런 다음, **인바운드 규칙 > 새 규칙 > 포트**를 선택합니다. **다음**을 선택하고 **특정 로컬 포트**에서 포트 번호를 입력하고 **다음**을 클릭한 다음, **연결 허용**과 다음을 클릭하고 인바운드 규칙의 이름(**IIS**, **웹 배포** 또는 **msvsmon**)을 추가합니다.

    Windows 방화벽을 구성에 대한 자세한 내용은 [원격 디버깅을 위해 Windows 방화벽 구성](../debugger/configure-the-windows-firewall-for-remote-debugging.md)을 참조하세요.

3. 다른 필수 포트에 대한 추가 규칙을 만듭니다.