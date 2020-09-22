---
title: 원격 IIS 7.5 컴퓨터에서 원격 디버깅 ASP.NET Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c43f392cddfd5ea36180d9b2675db82469f86ce0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841798"
---
# <a name="remote-debugging-aspnet-on-a-remote-iis-computer"></a>원격 IIS 컴퓨터의 원격 디버깅 ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IIS를 사용 하는 Windows Server 컴퓨터에 ASP.NET 웹 응용 프로그램을 배포 하 고 원격 디버깅을 위해 설정할 수 있습니다. 이 가이드에서는 Visual studio 2015 MVC 4.5.2 응용 프로그램을 설정 및 구성 하 고, IIS에 배포 하 고, Visual Studio에서 원격 디버거를 연결 하는 방법을 설명 합니다.

이러한 절차는 다음 서버 구성에서 테스트되었습니다.
* Windows Server 2012 R2 및 IIS 10
* Windows Server 2008 R2 및 IIS 7.5

ASP.NET Core 앱의 배포가 다르고 추가 단계가 필요한 경우를 제외 하 고이 문서에 있는 대부분의 정보는 ASP.NET Core 응용 프로그램의 원격 디버깅에도 적용 됩니다. IIS에 ASP.NET Core 앱을 배포 하려면 [이 문서의](https://docs.asp.net/en/latest/publishing/iis.html)모든 섹션을 완료 해야 합니다.

## <a name="prerequisites-install-the-remote-debugger-on-the-windows-server-computer"></a>필수 조건: Windows Server 컴퓨터에 원격 디버거 설치

원격 디버거를 Windows Server 컴퓨터에 다운로드 하는 방법에 대 한 지침은 [원격 디버깅](../debugger/remote-debugging.md)을 참조 하세요.

ASP.NET 응용 프로그램의 원격 디버깅을 수행 하려면 원격 디버거 응용 프로그램을 관리자 권한으로 실행 하거나 원격 디버거를 서비스로 시작할 수 있습니다. 원격 디버거를 서비스로 실행하는 방법에 대한 자세한 내용은 [Remote Debugging](../debugger/remote-debugging.md)에서 확인할 수 있습니다.

설치 되 면 원격 디버거가 대상 컴퓨터에서 실행 되 고 있는지 확인 합니다. (그렇지 않은 경우 **시작** 메뉴에서 **원격 디버거** 를 검색 합니다. ) 원격 디버거 창이 다음과 같이 표시 됩니다. (기본 포트 번호는 4020입니다.)

![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
## <a name="create-the-application-on-the-visual-studio-computer"></a>Visual Studio 컴퓨터에서 애플리케이션 만들기  
  
1. 새 MVC ASP.NET 애플리케이션을 만듭니다. **파일 / 새로 만들기 / 프로젝트**, **Visual C# / 웹 / ASP.NET 웹 애플리케이션** 을 차례로 선택합니다. **ASP.NET 4.5.2** 템플릿 섹션에서 **MVC**를 선택합니다. Azure 섹션에서 **클라우드의 호스트** 를 선택 하지 않았는지 확인 합니다. 프로젝트 이름을 **MyMVC**로 합니다.
1. HomeController.cs 파일을 열고 `About()` 메서드에 중단점을 설정합니다.
1. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **게시**를 선택합니다.
1. **게시 대상 선택**에 대해 **사용자 지정** 을 선택하고 프로필 이름을 **MyMVC**로 지정합니다. **다음**을 클릭합니다.
1. **연결** 탭에서 **게시 방법** 필드를 **파일 시스템** 으로 설정하고 **대상 위치** 필드를 로컬 디렉터리로 설정합니다. **다음**을 클릭합니다.

    ![RemoteDBG_Publish_Local](../debugger/media/remotedbg-publish-local.png "RemoteDBG_Publish_Local")
1. 구성을 **디버그**로 설정합니다. **게시**를 클릭합니다.

    ![RemoteDBG_Publish_Debug_Config](../debugger/media/remotedbg-publish-debug-config.png "RemoteDBG_Publish_Debug_Config")
    
    로컬 디렉터리에 애플리케이션을 게시해야 합니다.

## <a name="deploy-the-aspnet-application-on-the-windows-server-remote-computer"></a><a name="BKMK_deploy_asp_net"></a> Windows Server 원격 컴퓨터에 ASP.NET 응용 프로그램 배포

 이 섹션에서는 Windows Server 컴퓨터에서 IIS를 이미 사용 하도록 설정 했다고 가정 합니다. Windows Server 2012 r 2에서 iis를 사용 하도록 설정 하려면 [Iis 구성](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration) 을 참조 하세요. ASP.NET Core 앱을 배포 하려는 경우가 아니면이 문서의 다른 섹션을 건너뛸 수 있습니다. ASP.NET Core의 경우 여기에 설명 된 단계 대신 앱을 배포 하려면 문서의 단계를 따르세요.)
1. ASP.NET 설치 웹 플랫폼 구성 요소를 사용 하 여 ASP.NET 4.5을 설치 합니다 (Windows Server 2012 r 2의 서버 노드에서 **새 웹 플랫폼 구성 요소 가져오기** 를 선택한 다음 ASP.NET 검색).

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg-iis-aspnet-45.png "RemoteDBG_IIS_AspNet_45")

    Windows Server 2008 r 2에서이 명령을 사용 하는 대신 ASP.NET 4를 설치 합니다.   **c:\windows\ microsoft.net \framework (64) \v4.0.30319\aspnet_regiis.exe-ir**
1. Visual Studio 컴퓨터의 ASP.NET 프로젝트 디렉터리를 Windows Server 컴퓨터의 로컬 디렉터리( **C:\Publish**라고 함)에 복사합니다. 프로젝트를 수동으로 복사 하거나 Xcopy, 웹 배포, Robocopy, Powershell 또는 기타 옵션을 사용할 수 있습니다.

    > [!CAUTION]
    > 코드를 변경하거나 다시 빌드해야 하는 경우 다시 게시하고 이 단계를 반복해야 합니다. 원격 컴퓨터에 복사한 실행 파일은 로컬 소스 및 기호와 정확히 일치해야 합니다.
1. web.config 파일에 올바른 버전의 .NET Framework가 표시되는지 확인합니다.  예를 들어 Windows Server 2008 r 2에서 기본적으로 설치 되는 .NET Framework 버전은 4.0.30319 ASP.NET 4.5.2 버전을 만들었습니다. Windows Server 컴퓨터에서 ASP.NET 4.0 앱이 실행 되 고 있는 경우 버전을 변경 해야 합니다.
  
    ```xml
    <system.web>
        <authentication mode="None" />  
        <compilation debug="true" targetFramework="4.0.30319" />
        <httpRuntime targetFramework="4.0.30319" />
      </system.web>
  
    ```

1. **IIS(인터넷 정보 서비스) 관리자** 를 열고 **사이트**로 이동합니다.
1. **기본 웹 사이트** 노드를 마우스 오른쪽 단추로 클릭하고 **애플리케이션 추가**를 선택합니다.
1. **별칭** 필드를 **MyMVC** 로 설정 하 고 응용 프로그램 풀 필드를 **ASP.NET v 4.0** 으로 설정 합니다 (ASP.NET 4.5는 응용 프로그램 풀에 대 한 옵션이 아님). **실제 경로** 를 **C:\Publish** (ASP.NET 프로젝트 디렉터리를 복사한 위치)로 설정합니다.

    >[!NOTE] 
    > ASP.NET Core apps의 경우 응용 프로그램 풀 필드를 **관리 코드 없음**으로 설정 합니다.
1. **기본 웹 사이트** 를 마우스 오른쪽 단추로 클릭 하 고 **찾아보기**를 선택 하 여 배포를 테스트 합니다.
    앱을 성공적으로 배포한 경우 웹 페이지가 표시 됩니다.

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a>Visual Studio 컴퓨터에서 ASP.NET 애플리케이션에 연결

1. Visual Studio 컴퓨터에서 **MyMVC** 솔루션을 엽니다.
1. Visual Studio에서 **디버그/프로세스에 연결** (**Ctrl + Alt + P**)을 클릭 합니다.
1. 한정자 필드를 ** \<remote computer name> 4020**로 설정 합니다.
1. **새로 고침**을 클릭합니다.
    일부 프로세스가 **사용 가능한 프로세스** 창에 표시됩니다.

    프로세스가 보이지 않으면 원격 컴퓨터 이름 대신 IP 주소를 사용해 보세요(포트가 필요함). `ipconfig`명령줄에서를 사용 하 여 IPv4 주소를 가져옵니다.
1. **모든 사용자의 프로세스 표시**를 선택합니다.
1. **w3wp.exe** 를 찾은 다음 **연결**을 클릭합니다.

     프로세스 이름을 빠르게 찾으려면 프로세스의 첫 문자를 입력 합니다.
     
    >[!NOTE]
    > ASP.NET Core 앱의 경우 w3wp.exe 대신 dnx.exe 프로세스를 선택 합니다. 이 프로세스 이름은 향후 릴리스에서 변경 될 수 있습니다.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")

1. 원격 컴퓨터의 웹 사이트를 엽니다. 브라우저에서 **http://\<remote computer name>** 으로 이동합니다.
    
    ASP.NET 웹 페이지가 표시됩니다.
1. ASP.NET 웹 페이지에서 정보 페이지에 **대 한** 링크를 클릭 합니다.

    Visual Studio에서 중단점이 적중됩니다.
