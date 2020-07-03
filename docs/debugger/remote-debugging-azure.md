---
title: Azure 및 IIS의 ASP.NET Core 원격 디버그 | Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/06/2020
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: debf44bfe8187a7fd84e04b4362283658f636f17
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85536788"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>Visual Studio 2017에서 Azure 및 IIS의 ASP.NET Core 원격 디버그

이 가이드에서는 Visual Studio 2017 ASP.NET Core 앱을 설정 및 구성하고, Azure를 사용하여 IIS에 배포하고, Visual Studio에서 원격 디버거를 연결하는 방법을 설명합니다.

Azure에서 원격으로 디버그하는 권장 방법은 시나리오에 따라 달라집니다.

* Azure App Service의 ASP.NET Core를 디버그하려면 [스냅샷 디버거를 사용하여 Azure 앱 디버그](../debugger/debug-live-azure-applications.md)를 참조하세요. 이것이 권장된 방법입니다.
* 보다 일반적인 디버깅 기능을 사용하여 Azure App Service에서 ASP.NET Core를 디버그하려면 이 항목의 단계를 수행합니다([Azure App Service에서 원격 디버그](#remote_debug_azure_app_service) 섹션 참조).

    이 시나리오에서는 Visual Studio에서 Azure에 앱을 배포해야 하지만, 다음 그림과 같이 IIS 또는 원격 디버거를 수동으로 설치하거나 구성할 필요가 없습니다(이러한 구성 요소는 점선으로 표시됨).

    ![원격 디버거 구성 요소](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Azure VM에서 IIS를 디버그하려면 이 항목의 단계를 수행합니다([Azure VM 원격 디버그](#remote_debug_azure_vm) 섹션 참조). 이렇게 하면 IIS의 사용자 지정 구성을 사용할 수 있지만 설치 및 배포 단계가 더 복잡해집니다.

    Azure VM의 경우 다음 그림과 같이 Visual Studio에서 Azure에 앱을 배포하고 IIS 역할 및 원격 디버거를 수동으로 설치해야 합니다.

    ![원격 디버거 구성 요소](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Azure Service Fabric의 ASP.NET Core를 디버그하려면 [원격 Service Fabric 애플리케이션 디버그](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)를 참조하세요.

> [!WARNING]
> 이 자습서의 단계를 완료했으면 만든 Azure 리소스를 삭제해야 합니다. 그러면 불필요한 요금이 발생하지 않습니다.

## <a name="prerequisites"></a>사전 요구 사항

::: moniker range=">=vs-2019"
이 문서에 표시된 단계를 수행하려면 Visual Studio 2019가 필요합니다.
::: moniker-end
::: moniker range="vs-2017"
이 문서에 표시된 단계를 수행하려면 Visual Studio 2017이 필요합니다.
::: moniker-end

### <a name="network-requirements"></a>네트워크 요구 사항

프록시를 통해 연결된 두 컴퓨터 간의 디버깅은 지원되지 않습니다. 대기 시간이 길거나 대역폭이 낮은 연결(예: 전화 접속 인터넷) 또는 해외 인터넷을 통해 디버그하는 것은 오류가 발생하거나 지나치게 느릴 수 있으므로 권장하지 않습니다. 요구 사항 전체 목록은 [요구 사항](../debugger/remote-debugging.md#requirements_msvsmon)을 참조하세요.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Visual Studio 컴퓨터에서 ASP.NET Core 애플리케이션 만들기

1. 새 ASP.NET Core 애플리케이션을 만듭니다.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019에서 **Ctrl + Q**를 입력하여 검색 상자를 열고 **asp.net**을 입력하고 **템플릿**을 선택한 다음, **새 ASP.NET Core 웹 애플리케이션 만들기**를 선택합니다. 대화 상자가 나타나면 프로젝트 이름을 **MyASPApp**으로 지정한 다음, **만들기**를 선택합니다. 다음으로 **웹 애플리케이션(Model-View-Controller)** 을 선택하고 **만들기**를 선택합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017에서 **파일 > 새로 만들기 > 프로젝트**를 선택한 다음, **Visual C# > 웹 > ASP.NET Core 웹 애플리케이션**을 선택합니다. ASP.NET Core 템플릿 섹션에서 **웹 애플리케이션(Model-View-Controller)** 을 선택합니다. ASP.NET Core 2.1이 선택되어 있고, **Docker 지원 사용**이 선택되어 있지 않고, **인증**이 **인증 안 함**으로 설정되어 있는지 확인합니다. 프로젝트 이름을 **MyASPApp**으로 지정합니다.
    ::: moniker-end

1. About.cshtml.cs 파일을 열고 `OnGet` 메서드에 중단점을 설정합니다(이전 템플릿에서는 HomeController.cs를 대신 열고 `About()` 메서드에 중단점을 설정함).

## <a name="remote-debug-aspnet-core-on-an-azure-app-service"></a><a name="remote_debug_azure_app_service"></a> Azure App Service의 ASP.NET Core 원격 디버그

Visual Studio에서 완전히 프로비전된 IIS 인스턴스에 애플리케이션을 신속하게 게시하고 디버그할 수 있습니다. 그러나 IIS의 구성이 미리 설정되며 사용자 지정할 수 없습니다. 자세한 지침은 [Visual Studio를 사용하여 Azure에 ASP.NET Core 웹앱 배포](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)를 참조하세요. (IIS를 사용자 지정하는 기능이 필요한 경우 [Azure VM](#remote_debug_azure_vm)에서 디버그하세요.)

#### <a name="to-deploy-the-app-and-remote-debug-using-cloud-explorer"></a>클라우드 탐색기를 사용하여 앱을 배포하고 및 원격 디버그하려면

1. Visual Studio에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **게시**를 선택합니다.

    게시 프로필을 이전에 구성한 경우 **게시** 창이 나타납니다. **새 프로필**을 클릭합니다.

1. **게시** 대화 상자에서 **Azure App Service**를 선택하고 **새로 만들기**를 선택한 다음 메시지에 따라 프로필을 만듭니다.

    자세한 지침은 [Visual Studio를 사용하여 Azure에 ASP.NET Core 웹앱 배포](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)를 참조하세요.

    ![Azure App Service에 게시](../debugger/media/remotedbg_azure_app_service_profile.png)

1. 게시 창에서 **구성 편집**을 선택하고 디버그 구성으로 전환한 다음 **게시**를 선택합니다.

   디버그 구성은 앱을 디버그하는 데 필요합니다.

1. **클라우드 탐색기**를 엽니다(**보기** > **클라우드 탐색기**). App Service 인스턴스를 마우스 오른쪽 단추로 클릭하고 **디버거 연결**을 선택합니다.

   클라우드 탐색기를 사용할 수 없는 경우 대신 서버 탐색기를 엽니다. 그런 다음 서버 탐색기에서 App Service 인스턴스를 마우스 오른쪽 단추로 클릭하고 **디버거 연결**을 선택합니다.

1. 실행 중인 ASP.NET 애플리케이션에서 **정보** 페이지에 대한 링크를 클릭합니다.

    Visual Studio에서 중단점이 적중됩니다.

    정말 간단하죠. 이 항목의 나머지 단계는 Azure VM 원격 디버깅에 적용됩니다.

## <a name="remote-debug-aspnet-core-on-an-azure-vm"></a><a name="remote_debug_azure_vm"></a> Azure VM의 ASP.NET Core 원격 디버그

Windows Server용 Azure VM을 만든 다음 IIS 및 기타 필수 소프트웨어 구성 요소를 설치하고 구성할 수 있습니다. 이는 Azure App Service에 배포하는 것보다 오래 걸리며 이 자습서의 나머지 단계를 수행할 필요가 있습니다.

이러한 절차는 다음 서버 구성에서 테스트되었습니다.
* Windows Server 2012 R2 및 IIS 8
* Windows Server 2016 및 IIS 10
* Windows Server 2019 및 IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>앱이 이미 Azure VM의 IIS에서 실행 중인가요?

이 문서에는 Windows Server에서 IIS의 기본 구성을 설정하고 Visual Studio에서 앱을 배포하는 단계가 포함되어 있습니다. 이러한 단계는 서버에 필수 구성 요소가 설치되어 있는지, 앱이 올바르게 실행될 수 있는지, 원격으로 디버그할 준비가 되었는지 확인하기 위해 포함된 것입니다.

* 앱이 IIS에서 실행 중이고 원격 디버거를 다운로드하여 디버깅을 시작하려는 경우 [Windows Server에서 원격 도구 다운로드 및 설치](#BKMK_msvsmon)로 이동합니다.

* 디버깅을 위해 IIS에서 애플리케이션이 올바르게 설정, 배포 및 실행되는지 확인하려면 이 항목의 모든 단계를 수행합니다.

  * 시작하기 전에 [IIS설치 및 실행](/azure/virtual-machines/windows/quick-create-portal)에 설명된 모든 단계를 수행합니다.

  * 네트워크 보안 그룹에서 포트 80을 여는 경우 원격 디버거의 [올바른 포트](#bkmk_openports)(4024 또는 4022)도 엽니다. 이렇게 하면 나중에 열 필요가 없습니다. 웹 배포를 사용하는 경우 포트 8172도 엽니다.

### <a name="update-browser-security-settings-on-windows-server"></a>Windows Server에서 브라우저 보안 설정 업데이트

Internet Explorer에서 보안 강화 구성이 사용하도록 설정되어 있으면(기본적으로 사용하도록 설정되어 있음) 일부 웹 서버 구성 요소를 다운로드할 수 있도록 일부 도메인을 신뢰할 수 있는 사이트로 추가해야 할 수 있습니다. **인터넷 옵션 > 보안 > 신뢰할 수 있는 사이트 > 사이트**로 이동하여 신뢰할 수 있는 사이트를 추가합니다. 다음 도메인을 추가합니다.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

소프트웨어를 다운로드하는 경우 다양한 웹 사이트 스크립트 및 리소스를 로드하는 권한을 부여하라는 요청을 받게 됩니다. 이러한 리소스 중 일부는 필요하지 않지만 프로세스를 간소화하기 위해 메시지가 표시되면 **추가**를 클릭합니다.

### <a name="install-aspnet-core-on-windows-server"></a>Windows Server에 ASP.NET Core 설치

1. 호스팅 시스템에 .NET Core 호스팅 번들을 설치합니다. 번들은 .NET Core 런타임, .NET Core 라이브러리 및 ASP.NET Core 모듈을 설치합니다. 자세한 지침은 [IIS에 게시](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)를 참조하세요.

    .NET Core 3의 경우 [.NET Core 호스팅 번들](https://dotnet.microsoft.com/permalink/dotnetcore-current-windows-runtime-bundle-installer)을 설치합니다.
    .NET Core 2의 경우 [.NET Core Windows Server 호스팅](https://aka.ms/dotnetcore-2-windowshosting)을 설치합니다.

    > [!NOTE]
    > 시스템이 인터넷에 연결되지 않은 경우 *[Microsoft Visual C++ 2015 재배포 가능 패키지](https://www.microsoft.com/download/details.aspx?id=53840)* 를 설치한 후에 .NET Core Windows Server 호스팅 번들을 설치합니다.

3. 시스템을 다시 시작하거나 명령 프롬프트에서 **net stop was /y**에 이어 **net start w3svc**를 실행하여 시스템 PATH에 대한 변경 내용을 선택합니다.

## <a name="choose-a-deployment-option"></a>배포 옵션 선택

IIS에 앱을 배포하는 데 도움이 필요한 경우 다음 옵션을 고려합니다.

* IIS에서 게시 설정 파일을 만들고 Visual Studio에서 설정을 가져와서 배포합니다. 일부 시나리오에서는 이 방법이 앱을 배포하기에 가장 빠릅니다. 게시 설정 파일을 만들면 IIS에서 사용 권한이 자동으로 설정됩니다.

* 로컬 폴더에 게시하고 선호하는 방법으로 출력을 IIS에 준비된 앱 폴더에 복사하여 배포합니다.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(선택 사항) 게시 설정 파일을 사용하여 배포

이 옵션을 사용하여 게시 설정 파일을 만들고 Visual Studio로 가져올 수 있습니다.

> [!NOTE]
> 이 배포 방법에서는 서버에 설치되어 있어야 하는 웹 배포를 사용합니다. 설정을 가져오는 대신 웹 배포를 직접 구성하려는 경우 호스팅 서버용 웹 배포 3.6 대신 웹 배포 3.6을 설치하면 됩니다. 단, 웹 배포를 직접 구성하는 경우 서버의 앱 폴더가 올바른 값과 권한으로 구성되어 있는지 확인해야 합니다([ASP.NET 웹 사이트 구성](#BKMK_deploy_asp_net)참조).

### <a name="configure-the-aspnet-core-web-site"></a>ASP.NET Core 웹 사이트 구성

1. IIS 관리자의 왼쪽 창에 있는 **연결**에서 **애플리케이션 풀**을 선택합니다. **DefaultAppPool**을 열고 **.NET CLR 버전**을 **관리 코드 없음**으로 설정합니다. 이는 ASP.NET Core에 필요합니다. 기본 웹 사이트는 DefaultAppPool을 사용합니다.

2. DefaultAppPool을 중지했다가 다시 시작합니다.

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Windows Server에서 호스팅 서버용 웹 배포 설치 및 구성

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Windows Server의 IIS에서 게시 설정 파일 만들기

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio에서 게시 설정 가져오기 및 배포

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

> [!NOTE]
> Azure VM을 다시 시작하면 IP 주소가 변경될 수 있습니다.

앱을 성공적으로 배포한 후 자동으로 시작해야 합니다. 앱이 Visual Studio에서 시작되지 않는 경우 IIS에서 앱을 시작하여 올바로 실행되는지 확인합니다. ASP.NET Core의 경우 **DefaultAppPool**에 대한 애플리케이션 풀 필드가 **관리 코드 없음**으로 설정되었는지도 확인해야 합니다.

1. **설정** 대화 상자에서 **다음**을 클릭하여 디버깅을 사용하도록 설정하고 **디버그** 구성을 선택한 다음, **파일 게시** 옵션 아래에서 **대상에서 추가 파일 제거**를 선택합니다.

    > [!IMPORTANT]
    > 릴리스 구성을 선택하는 경우 게시할 때 *web.config* 파일에서 디버깅을 사용하지 않도록 설정합니다.

1. **저장**을 클릭한 다음, 앱을 다시 게시합니다.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(선택 사항) 로컬 폴더에 게시하여 배포

PowerShell, RoboCopy를 사용하여 앱을 IIS에 복사하거나 수동으로 파일을 복사하려는 경우 이 옵션을 사용하여 앱을 배포할 수 있습니다.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a> Windows Server 컴퓨터에서 ASP.NET Core 웹 사이트 구성

게시 설정을 가져오는 경우 이 섹션을 건너뛸 수 있습니다.

1. **IIS(인터넷 정보 서비스) 관리자** 를 열고 **사이트**로 이동합니다.

2. **기본 웹 사이트** 노드를 마우스 오른쪽 단추로 클릭하고 **애플리케이션 추가**를 선택합니다.

3. **별칭** 필드를 **MyASPApp**으로 설정하고 애플리케이션 풀 필드를 **관리 코드 없음**으로 설정합니다. **실제 경로**를 **C:\Publish**로 설정합니다. 나중에 여기로 ASP.NET Core 프로젝트를 배포할 수 있습니다.

4. IIS 관리자에서 사이트를 선택하여 **사용 권한 편집**을 선택하고 IUSR, IIS_IUSRS 또는 애플리케이션 풀에 대해 구성된 사용자가 읽기 및 실행 권한을 가진 사용자인지 확인합니다.

    액세스 권한이 있는 사용자 중 하나가 표시되지 않으면 읽기 및 실행 권한이 있는 사용자로 IUSR을 추가하는 단계를 진행합니다.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(선택 사항) Visual Studio에서 로컬 폴더에 게시하여 앱을 게시 및 배포

웹 배포를 사용하지 않는 경우 파일 시스템 또는 기타 도구를 사용하여 앱을 게시하고 배포해야 합니다. 먼저 파일 시스템을 사용하여 패키지를 만든 다음 수동으로 패키지를 배포하거나 PowerShell, RoboCopy 또는 XCopy와 같은 다른 도구를 사용할 수 있습니다. 이 섹션에서는 웹 배포를 사용하지 않는 경우 패키지를 수동으로 복사한다고 가정합니다.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a> Windows Server에서 원격 도구 다운로드 및 설치

Visual Studio 버전과 일치하는 원격 도구 버전을 다운로드합니다.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a> Windows Server에서 원격 디버거 설정

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 추가 사용자를 위해 사용 권한을 추가하거나 원격 디버거의 인증 모드 또는 포트 번호를 변경해야 하는 경우 [원격 디버거 구성](../debugger/remote-debugging.md#configure_msvsmon)을 참조하세요.

### <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a> Visual Studio 컴퓨터에서 ASP.NET 애플리케이션에 연결

1. Visual Studio 컴퓨터에서 디버그하려는 솔루션(이 문서의 단계를 수행하는 경우 **MyASPApp**)을 엽니다.
2. Visual Studio에서 **디버그 > 프로세스에 연결**(Ctrl + Alt + P)을 클릭합니다.

    > [!TIP]
    > Visual Studio 2017 이상 버전에서는 **디버그 > 프로세스에 다시 연결** (Shift+Alt+P)을 사용하여 이전에 연결한 프로세스에 다시 연결할 수 있습니다.

3. 한정자 필드를 **\<remote computer name>** 으로 설정하고 **Enter** 키를 누릅니다.

    Visual Studio에서 **\<remote computer name>:포트** 형식으로 표시되는 컴퓨터 이름에 필요한 포트를 추가하는지 확인합니다.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019에서는 **\<remote computer name>:4024**가 표시되고,
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017에서는 **\<remote computer name>:4022**가 표시됩니다.
    ::: moniker-end
    이 포트는 필수입니다. 포트 번호가 표시되지 않으면 수동으로 추가하세요.

4. **새로 고침**을 클릭합니다.
    일부 프로세스가 **사용 가능한 프로세스** 창에 표시됩니다.

    프로세스가 보이지 않으면 원격 컴퓨터 이름 대신 IP 주소를 사용해 보세요(포트가 필요함). 명령줄에서 `ipconfig`를 사용하여 IPv4 주소를 가져올 수 있습니다.

    **찾기** 단추를 사용하려면 서버에서 [UDP 포트 3702를 열어야](#bkmk_openports) 합니다.

5. **모든 사용자의 프로세스 표시**를 선택합니다.

6. 앱을 신속하게 찾으려면 프로세스 이름의 첫 글자를 입력합니다.

    * IIS에서 [In-Process 호스팅 모델](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1#hosting-models)을 사용하는 경우 올바른 **w3wp.exe** 프로세스를 선택합니다. .NET Core 3부터는 이것이 기본값입니다.

    * 그렇지 않으면 **dotnet.exe** 프로세스를 선택합니다. (이것은 Out-of-process 호스팅 모델입니다.)

    *w3wp.exe* 또는 *dotnet.exe*가 표시되는 프로세스가 여러 개인 경우 **사용자 이름** 열을 확인합니다. 일부 시나리오에서는 **사용자 이름** 열에 **IIS APPPOOL\DefaultAppPool**과 같은 앱 풀 이름이 표시됩니다. 앱 풀이 보이지만 고유하지 않으면, 디버그할 앱 인스턴스에 대해 새로 명명된 앱 풀을 만듭니다. 그러면 **사용자 이름** 열에서 쉽게 찾을 수 있습니다.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. **연결**을 클릭합니다.

8. 원격 컴퓨터의 웹 사이트를 엽니다. 브라우저에서 **http://\<remote computer name>** 으로 이동합니다.

    ASP.NET 웹 페이지가 표시됩니다.
9. 실행 중인 ASP.NET 애플리케이션에서 **정보** 페이지 링크를 클릭합니다.

    Visual Studio에서 중단점이 적중됩니다.

### <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> 문제 해결: Windows Server에서 필수 포트 열기

대부분의 설치에서는 ASP.NET 및 원격 디버거를 설치하여 필요한 포트를 엽니다. 그러나 배포 문제를 해결하는 중이고 앱이 방화벽 뒤에서 호스트되는 경우 올바른 포트가 열려 있는지 확인해야 할 수 있습니다.

Azure VM에서는 [네트워크 보안 그룹](/azure/virtual-machines/windows/nsg-quickstart-portal)을 통해 포트를 열어야 합니다.

필수 포트:

* 80 - IIS에 필요합니다.
::: moniker range=">=vs-2019"
* 4024 - Visual Studio 2019에서 원격 디버깅에 필요합니다(자세한 내용은 [원격 디버거 포트 할당](../debugger/remote-debugger-port-assignments.md) 참조).
::: moniker-end
::: moniker range="vs-2017"
* 4022 - Visual Studio 2017에서 원격 디버깅에 필요합니다(자세한 내용은 [원격 디버거 포트 할당](../debugger/remote-debugger-port-assignments.md) 참조).
::: moniker-end
* UDP 3702 - (선택 사항) 검색 포트를 열면 Visual Studio에서 원격 디버거에 연결할 때 **찾기** 버튼을 사용할 수 있습니다.

이러한 포트는 ASP.NET 설치 중 이미 열려 있을 것입니다.
- 8172 - (선택 사항) Visual Studio에서 앱을 배포하기 위해 웹 배포에 필요합니다.
