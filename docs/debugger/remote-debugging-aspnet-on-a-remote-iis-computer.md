---
title: 원격 IIS 컴퓨터의 코어ASP.NET 원격 디버그 | 마이크로 소프트 문서
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: b33ead969456935dab54c042ba4fbaf1f5ff44f4
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385472"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>비주얼 스튜디오에서 원격 IIS 컴퓨터에서 코어를 ASP.NET 원격 디버그

IIS에 배포된 ASP.NET Core 응용 프로그램을 디버깅하려면 앱을 배포한 컴퓨터에서 원격 도구를 설치하고 실행한 다음 Visual Studio에서 실행 중인 앱에 연결합니다.

![원격 디버거 구성 요소](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

이 가이드에서는 Visual Studio ASP.NET Core를 설정하고 구성하고, IIS에 배포하고, Visual Studio에서 원격 디버거를 연결하는 방법을 설명합니다. 4.5.2 ASP.NET 원격 [디버그를 보려면 IIS 컴퓨터에서 원격 디버그 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)참조하십시오. Azure를 사용하여 IIS에서 배포하고 디버깅할 수도 있습니다. Azure App Service의 경우 [스냅숏 디버거를](../debugger/debug-live-azure-applications.md) 사용하거나 [서버 탐색기에서 디버거를 연결하여](../debugger/remote-debugging-azure.md)미리 구성된 IIS 및 원격 디버거 인스턴스에 쉽게 배포하고 디버깅할 수 있습니다.

## <a name="prerequisites"></a>사전 요구 사항

::: moniker range=">=vs-2019"
이 문서에 표시된 단계를 수행하려면 Visual Studio 2019가 필요합니다.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017은 이 문서에 표시된 단계를 수행해야 합니다.
::: moniker-end

이러한 절차는 다음 서버 구성에서 테스트되었습니다.
* 윈도우 서버 2012 R2 및 IIS 8
* 윈도우 서버 2016 및 IIS 10

## <a name="network-requirements"></a>네트워크 요구 사항

프록시를 통해 연결된 두 컴퓨터 간의 디버깅은 지원되지 않습니다. 전화 접속 인터넷과 같이 대기 시간이 많거나 대역폭이 낮은 연결을 통해 디버깅하거나 국가 간 인터넷을 통해 디버깅하는 것은 권장되지 않으며 실패하거나 허용할 수 없을 정도로 느릴 수 있습니다. 요구 사항의 전체 목록은 [요구 사항](../debugger/remote-debugging.md#requirements_msvsmon)을 참조하십시오.

## <a name="app-already-running-in-iis"></a>이미 IIS에서 실행 중인 앱?

이 문서에는 Windows 서버에서 IIS의 기본 구성을 설정하고 Visual Studio에서 앱을 배포하는 단계가 포함되어 있습니다. 이러한 단계는 서버에 필수 구성 요소가 설치되어 있는지, 앱이 올바르게 실행될 수 있는지, 원격 디버깅할 준비가 되었는지 확인하는 데 포함됩니다.

* 앱이 IIS에서 실행 중이고 원격 디버거를 다운로드하고 디버깅을 시작하려는 경우 [Windows Server에서 원격 도구 다운로드 및 설치로](#BKMK_msvsmon)이동합니다.

* 디버깅할 수 있도록 IIS에서 앱을 설정, 배포 및 올바르게 실행하는 데 도움이 되는 경우 이 항목의 모든 단계를 따르십시오.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Visual Studio 컴퓨터에서 ASP.NET 핵심 응용 프로그램 만들기

1. 새 ASP.NET Core 웹 애플리케이션을 만듭니다. 

    ::: moniker range=">=vs-2019"
    Visual Studio 2019에서 **Ctrl + Q를** 입력하여 검색 상자를 열고 **asp.net**입력하고 템플릿을 선택한 다음 새 ASP.NET 핵심 웹 응용 **프로그램 만들기를** **선택합니다.** 표시되는 대화 상자에서 프로젝트 **MyASPApp의**이름을 지정한 다음 **만들기를**선택합니다. 그런 다음 **웹 응용 프로그램(모델-뷰-컨트롤러)을**선택한 다음 **을**선택합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017에서 **파일 > 새로운 > 프로젝트를**선택한 다음 시각적 **C# > 웹 > ASP.NET 핵심 웹 응용 프로그램을**선택합니다. ASP.NET 핵심 템플릿 섹션에서 **웹 응용 프로그램(모델-뷰-컨트롤러)을**선택합니다. ASP.NET 코어 2.1을 선택했는지, **Docker 지원 활성화를** 선택하지 않았는지, **인증이** **인증 없음으로**설정되어 있는지 확인합니다. 프로젝트 **MyASPApp의 이름을 지정합니다.**
    ::: moniker-end

4. About.cshtml.cs 파일을 열고 `OnGet` 메서드에서 중단점을 설정합니다(이전 템플릿에서는 대신 HomeController.cs 열고 메서드에서 `About()` 중단점을 설정합니다).

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a>Windows 서버에서 IIS 설치 및 구성

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Windows 서버에서 브라우저 보안 설정 업데이트

인터넷 익스플로러에서 고급 보안 구성을 사용하도록 설정한 경우(기본적으로 활성화됨) 일부 도메인을 신뢰할 수 있는 사이트로 추가하여 일부 웹 서버 구성 요소를 다운로드할 수 있도록 해야 할 수 있습니다. 신뢰할 수 있는 사이트를 추가하려면 인터넷 옵션 > 신뢰할 수 있는 사이트 > **신뢰할 수 있는 사이트와 >.** 다음 도메인을 추가합니다.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

소프트웨어를 다운로드할 때 다양한 웹 사이트 스크립트 및 리소스를 로드할 수 있는 권한을 부여하는 요청을 받을 수 있습니다. 이러한 리소스 중 일부는 필요하지 않지만 프로세스를 단순화하려면 메시지가 표시될 때 **추가를** 클릭합니다.

## <a name="install-aspnet-core-on-windows-server"></a>Windows 서버에 ASP.NET 코어 설치

1. 호스팅 시스템에 [.NET Core Windows Server 호스팅 번들](https://aka.ms/dotnetcore-2-windowshosting)을 설치합니다. 번들은 .NET Core 런타임, .NET Core 라이브러리 및 ASP.NET Core 모듈을 설치합니다. 자세한 지침은 [IIS에 게시를](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)참조하십시오.

    > [!NOTE]
    > 시스템이 인터넷에 연결되지 않은 경우 *[Microsoft Visual C++ 2015 재배포 가능 패키지](https://www.microsoft.com/download/details.aspx?id=53840)* 를 설치한 후에 .NET Core Windows Server 호스팅 번들을 설치합니다.

3. 시스템을 다시 시작하거나 명령 프롬프트에서 **net stop was /y**에 이어 **net start w3svc**를 실행하여 시스템 PATH에 대한 변경 내용을 선택합니다.

## <a name="choose-a-deployment-option"></a>배포 옵션 선택

IIS에 앱을 배포하는 데 도움이 필요한 경우 다음 옵션을 고려하십시오.

* IIS에서 게시 설정 파일을 만들고 Visual Studio에서 설정을 가져와 배포합니다. 일부 시나리오에서는 앱을 빠르게 배포할 수 있습니다. 게시 설정 파일을 만들면 IIS에서 사용 권한이 자동으로 설정됩니다.

* 로컬 폴더에 게시하고 기본 설정 방법으로 출력을 IIS의 준비된 앱 폴더에 복사하여 배포합니다.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(선택 사항) 게시 설정 파일을 사용하여 배포

이 옵션을 사용하여 게시 설정 파일을 만들고 Visual Studio로 가져올 수 있습니다.

> [!NOTE]
> 이 배포 방법은 웹 배포를 사용합니다. 설정을 가져오는 대신 Visual Studio에서 웹 배포를 수동으로 구성하려는 경우 호스팅 서버에 대한 웹 배포 3.6 대신 웹 배포 3.6을 설치할 수 있습니다. 그러나 웹 배포를 수동으로 구성하는 경우 서버의 앱 폴더가 올바른 값과 사용 권한으로 구성되어 있는지 확인해야 [합니다(웹 사이트 구성](#BKMK_deploy_asp_net)ASP.NET 참조).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Windows 서버에서 서버를 호스팅하기 위한 웹 배포 설치 및 구성

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Windows Server의 IIS에서 게시 설정 파일 만들기

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio에서 게시 설정 가져오기 및 배포

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

앱을 성공적으로 배포한 후 자동으로 시작해야 합니다. 앱이 Visual Studio에서 시작되지 않으면 IIS에서 앱을 시작합니다. ASP.NET Core의 경우 **DefaultAppPool**에 대한 애플리케이션 풀 필드가 **관리 코드 없음**으로 설정되었는지 확인해야 합니다.

1. **설정** 대화 상자에서 **다음을**클릭하여 디버깅을 활성화하고 **디버그** 구성을 선택한 다음 **파일 게시** 옵션에서 **대상에서 추가 파일 제거를** 선택합니다.

    > [!NOTE]
    > 릴리스 구성을 선택하는 경우 게시할 때 *web.config* 파일에서 디버깅을 사용하지 않도록 설정합니다.

1. **저장을** 클릭한 다음 앱을 다시 게시합니다.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(선택 사항) 로컬 폴더에 게시하여 배포

PowerShell, RoboCopy를 사용하여 IIS에 앱을 복사하거나 파일을 수동으로 복사하려는 경우 이 옵션을 사용하여 앱을 배포할 수 있습니다.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a>Windows 서버 컴퓨터에서 ASP.NET 핵심 웹 사이트 구성

1. Windows 탐색기를 열고 새 **폴더인 C:\Publish를**만들고 나중에 ASP.NET Core 프로젝트를 배포합니다.

2. 아직 열려 있지 않은 경우 **IIS(인터넷 정보 서비스) 관리자를**엽니다. 서버 관리자의 왼쪽 창에서 **IIS를**선택합니다. 서버를 마우스 오른쪽 단추로 클릭하고 **IIS(인터넷 정보 서비스) 관리자를**선택합니다.)

3. 왼쪽 창의 **연결** 아래에서 **사이트**로 이동합니다.

4. 기본 **웹 사이트를**선택하고 **기본 설정을**선택하고 물리적 **경로를** **C:\게시로**설정합니다.

4. **기본 웹 사이트** 노드를 마우스 오른쪽 단추로 클릭하고 **애플리케이션 추가**를 선택합니다.

5. **별칭** 필드를 **MyASPApp으로**설정하고 기본 응용 프로그램**풀(DefaultAppPool)을**수락하고 **물리적 경로를** **C:\게시로**설정합니다.

6. **연결에서** **응용 프로그램 풀을 선택합니다.** **DefaultAppPool을** 열고 응용 프로그램 풀 필드를 **관리 코드 없음으로**설정합니다.

7. IIS Manager에서 새 사이트를 마우스 오른쪽 단추로 클릭하고 **권한 편집을**선택하고 IUSR, IIS_IUSRS 또는 웹 앱에 대한 액세스를 위해 구성된 사용자가 읽기 & 실행 권한을 가진 권한이 있는 권한이 있는지 확인합니다.

    액세스 권한이 있는 사용자 중 하나가 표시되지 않으면 읽기 & 실행 권한이 있는 사용자로 IUSR을 추가하는 단계를 진행합니다.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Visual Studio에서 로컬 폴더에 게시하여 앱을 게시하고 배포합니다.

파일 시스템 또는 기타 도구를 사용하여 앱을 게시하고 배포할 수도 있습니다.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>Windows 서버에서 원격 도구 다운로드 및 설치

Visual Studio 버전과 일치하는 원격 도구 버전을 다운로드합니다.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a>Windows 서버에서 원격 디버거 설정

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 추가 사용자에 대한 권한을 추가하거나, 인증 모드를 변경하거나, 원격 디버거에 대한 포트 번호를 변경해야 하는 경우 [원격 디버거 구성](../debugger/remote-debugging.md#configure_msvsmon)을 참조하십시오.

원격 디버거를 서비스로 실행하는 방법에 대한 자세한 내용은 [원격 디버거 를 서비스로 실행을](../debugger/remote-debugging.md#bkmk_configureService)참조하십시오.

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>Visual Studio 컴퓨터에서 ASP.NET 응용 프로그램에 연결

1. Visual Studio 컴퓨터에서 디버깅하려는 솔루션을 엽니다(이 문서의 모든 단계를 따르는 경우**MyASPApp).**
2. Visual Studio에서 **프로세스에 > 연결(Ctrl** + Alt + P)을 디버그를 클릭합니다.

    > [!TIP]
    > Visual Studio 2017 및 이후 버전에서는 디버그 > 다시 연결하여 **프로세스에 다시 연결하여** 이전에 연결한 동일한 프로세스에 다시 연결할 수 있습니다(Shift + Alt + P).

3. [>** \<원격 컴퓨터 이름으로** 한정자 필드를 설정하고 **Enter**를 누릅니다.

    Visual Studio에서 형식에 표시되는 컴퓨터 이름에 필요한 포트를 추가하는지 확인합니다 ** \<>.**

    ::: moniker range=">=vs-2019"
    Visual Studio 2019에서는 ** \<원격 컴퓨터 이름>:4024가 표시됩니다.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017에서는 ** \<원격 컴퓨터 이름>:4022가 표시됩니다.**
    ::: moniker-end
    포트가 필요합니다. 포트 번호가 표시되지 않으면 수동으로 추가합니다.

4. **새로 고침을 클릭합니다.**
    일부 프로세스가 **사용 가능한 프로세스** 창에 표시됩니다.

    프로세스가 표시되지 않으면 원격 컴퓨터 이름 대신 IP 주소를 사용해 보십시오(포트가 필요합니다). `ipconfig` 명령줄에서 IPv4 주소를 얻을 수 있습니다.

    **찾기** 단추를 사용하려면 서버에서 [UDP 포트 3702를 열어야](#bkmk_openports) 할 수 있습니다.

5. **모든 사용자의 프로세스 표시**를 선택합니다.

6. 프로세스 이름의 첫 글자 입력을 입력하여 앱을 빠르게 찾습니다.

    * IIS에서 [인앱 호스팅 모델을](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1#hosting-models) 사용하는 경우 올바른 **w3wp.exe** 프로세스를 선택합니다. .NET 코어 3부터 시작하며 기본값입니다.

    * 그렇지 않으면 **dotnet.exe** 프로세스를 선택합니다. (이 모델은 프로세스 외 호스팅 모델입니다.)

    *w3wp.exe* 또는 *dotnet.exe를*보여주는 여러 프로세스가 있는 경우 **사용자 이름** 열을 확인합니다. 일부 시나리오에서 **사용자 이름** 열에는 **IIS APPPOOL\DefaultAppPool**과 같은 앱 풀 이름이 표시됩니다. 앱 풀이 표시되지만 고유하지 않은 경우 디버깅하려는 앱 인스턴스에 대해 새 이름의 앱 풀을 만든 다음 **사용자 이름** 열에서 쉽게 찾을 수 있습니다.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. **연결**을 클릭합니다.

8. 원격 컴퓨터의 웹 사이트를 엽니다. 브라우저에서 **http://\<원격 컴퓨터 이름>** 으로 이동합니다.

    ASP.NET 웹 페이지가 표시됩니다.

9. 실행 중인 ASP.NET 응용 프로그램에서 **정보** 페이지에 대한 링크를 클릭합니다.

    Visual Studio에서 중단점이 적중됩니다.

## <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> 문제 해결 Windows Server에서 필요한 포트를 열려면

대부분의 설정에서 필요한 포트는 ASP.NET 및 원격 디버거를 설치하여 열립니다. 그러나 포트가 열려 있는지 확인해야 할 수 있습니다.

> [!NOTE]
> Azure VM에서 [네트워크 보안 그룹을](/azure/virtual-machines/windows/nsg-quickstart-portal)통해 포트를 열어야 합니다.

필수 포트:

* 80 - IIS에 필요합니다.
::: moniker range=">=vs-2019"
* 4024 - Visual Studio 2019에서 원격 디버깅에 필요한 경우(자세한 내용은 [원격 디버거 포트 할당](../debugger/remote-debugger-port-assignments.md) 참조).
::: moniker-end
::: moniker range="vs-2017"
* 4022 - Visual Studio 2017의 원격 디버깅에 필요합니다(자세한 내용은 [원격 디버거 포트 할당](../debugger/remote-debugger-port-assignments.md) 참조).
::: moniker-end
* UDP 3702 - (선택 사항) 검색 포트를 사용하면 Visual Studio의 원격 디버거에 연결할 때 **찾기** 단추를 사용할 수 있습니다.

1. Windows Server에서 포트를 열려면 **시작** 메뉴를 열고 **고급 보안을 사용하여 Windows 방화벽을**검색합니다.

2. 그런 다음 **새 규칙 > 새 규칙 >** 선택한 다음 을 **클릭합니다.** UDP 3702의 경우 대신 **아웃바운드 규칙을** 선택합니다.

3. **특정 로컬 포트에서**포트 번호를 입력하고 **다음을**클릭합니다.

4. **연결 허용을**클릭하고 다음 을 **클릭합니다.**

5. 포트에 사용하도록 설정하려면 하나 이상의 네트워크 유형을 선택하고 다음 을 **클릭합니다.**

    선택한 유형은 원격 컴퓨터가 연결된 네트워크를 포함해야 합니다.
6. 인바운드 규칙에 대한 이름(예: **IIS,** **웹 배포**또는 **msvsmon)을**추가하고 **완료를 클릭합니다.**

    인바운드 규칙 또는 아웃바운드 규칙 목록에 새 규칙이 표시되어야 합니다.

    Windows 방화벽 구성에 대한 자세한 내용을 보려면 [원격 디버깅을 위한 Windows 방화벽 구성을](../debugger/configure-the-windows-firewall-for-remote-debugging.md)참조하십시오.

3. 다른 필수 포트에 대한 추가 규칙을 만듭니다.
