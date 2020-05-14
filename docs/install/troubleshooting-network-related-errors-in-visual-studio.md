---
title: 네트워크 또는 프록시 오류 문제 해결
description: 방화벽 또는 프록시 서버 배후에서 Visual Studio를 설치하거나 사용할 때 발생할 수 있는 네트워크 또는 프록시 관련 오류에 대한 솔루션을 찾습니다.
ms.date: 10/29/2019
ms.topic: troubleshooting
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs, Visual Studio
- proxy errors, Visual Studio
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 0e127006976c484d1e4fc2fe011af979af7eb7a9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114992"
---
# <a name="troubleshoot-network-related-errors-when-you-install-or-use-visual-studio"></a>Visual Studio 설치 또는 사용 시의 네트워크 관련 오류 문제 해결

방화벽 또는 프록시 서버 배후에서 Visual Studio를 설치하거나 사용할 때 발생할 수 있는 가장 일반적인 네트워크 또는 프록시 관련 오류에 대한 솔루션이 있습니다.

## <a name="error-proxy-authorization-required"></a>오류: “프록시 권한 필요”

일반적으로 사용자가 프록시 서버를 통해 인터넷에 연결할 때 프록시 서버가 Visual Studio에서 네트워크 리소스에 대한 호출을 차단하는 경우 이 오류가 발생합니다.

### <a name="to-fix-this-proxy-error"></a>이 프록시 오류를 해결하려면

- Visual Studio를 다시 시작합니다. 프록시 인증 대화 상자가 나타납니다. 대화 상자에 메시지가 표시되면 자격 증명을 입력합니다.

- Visual Studio를 다시 시작해도 문제가 해결되지 않으면 프록시 서버에서 http:&#47;&#47;go.microsoft.com 주소가 아닌 &#42;.visualStudio.microsoft.com 주소에 대한 자격 증명을 입력하라는 메시지를 표시하기 때문일 수 있습니다. 이러한 서버에 대해 다음 URL을 허용 목록에 포함하여 Visual Studio에서 모든 로그인 시나리오의 차단을 해제하는 것이 좋습니다.

  - &#42;.windows.net

  - &#42;.microsoftonline.com

  - &#42;.visualstudio.microsoft.com

  - &#42;.microsoft.com

  - &#42;.live.com

- 또는 Visual Studio를 다시 시작할 때 http:&#47;&#47;go.microsoft.com 주소 및 서버 엔드포인트 둘 다에 대해 프록시 인증 대화 상자가 표시되도록 허용 목록에서 http:&#47;&#47;go.microsoft.com 주소를 제거할 수 있습니다.

  -또는-

- 프록시에 기본 자격 증명을 사용하려는 경우 다음 작업을 수행할 수 있습니다.

::: moniker range="vs-2017"

  1. **devenv.exe.config** (the devenv.exe configuration file) in: **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** 또는 **%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**를 찾습니다.

  2. 구성 파일에서 `<system.net>` 블록을 찾아 다음 코드를 추가합니다.

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      `proxyaddress="<http://<yourproxy:port#>`에는 네트워크의 올바른 프록시 주소를 삽입해야 합니다.

     > [!NOTE]
     > 자세한 내용은 [&lt;defaultProxy&gt; 요소(네트워크 설정)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) 및 [&lt;프록시&gt; 요소(네트워크 설정)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings) 페이지를 참조하세요.

::: moniker-end

::: moniker range="vs-2019"

  1. **devenv.exe.config** (the devenv.exe configuration file) in: **%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE** 또는 **%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE**를 찾습니다.

  2. 구성 파일에서 `<system.net>` 블록을 찾아 다음 코드를 추가합니다.

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      `proxyaddress="<http://<yourproxy:port#>`에는 네트워크의 올바른 프록시 주소를 삽입해야 합니다.

     > [!NOTE]
     > 자세한 내용은 [&lt;defaultProxy&gt; 요소(네트워크 설정)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) 및 [&lt;프록시&gt; 요소(네트워크 설정)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings) 페이지를 참조하세요.

::: moniker-end

## <a name="error-the-underlying-connection-was-closed"></a>오류: “기본 연결이 닫혔습니다.”

방화벽이 있는 개인 네트워크에서 Visual Studio를 사용하는 경우 Visual Studio가 일부 네트워크 리소스에 연결하지 못할 수 있습니다. 이러한 리소스에는 로그인 및 라이선스용 Azure DevOps Services, NuGet 및 Azure 서비스가 포함될 수 있습니다. Visual Studio가 이러한 리소스 중 하나에 연결하지 못할 경우 다음과 같은 오류 메시지가 표시될 수 있습니다.

  **기본 연결이 닫혔습니다. 전송 시 예기치 않은 오류가 발생했습니다.**

Visual Studio는 TLS(전송 계층 보안) 1.2 프로토콜을 사용하여 네트워크 리소스에 연결합니다. Visual Studio에서 TLS 1.2를 사용하는 경우 일부 개인 네트워크의 보안 어플라이언스는 특정 서버 연결을 차단합니다.

### <a name="to-fix-this-connection-error"></a>이 연결 오류를 해결하려면

다음 URL에 대한 연결을 사용하도록 설정합니다.

- https:&#47;&#47;management.core.windows.net

- https:&#47;&#47;app.vssps.visualstudio.com

- https:&#47;&#47;login.microsoftonline.com

- https:&#47;&#47;login.live.com

- https:&#47;&#47;go.microsoft.com

- https:&#47;&#47;graph.windows.net

- https:&#47;&#47;app.vsspsext.visualstudio.com

- &#42;.azurewebsites.net(Azure 연결의 경우)

- &#42;.visualstudio.microsoft.com

- cdn.vsassets.io(콘텐츠 배달 네트워크 또는 CDN, 콘텐츠 호스트)

- &#42;.gallerycdn.vsassets.io(Azure DevOps Services 확장 호스트)

- static2.sharepointonline.com(Visual Studio가 Office UI Fabric 키트에서 사용하는 리소스(예: 글꼴) 호스트)

- &#42;.nuget.org(NuGet 연결의 경우)

  > [!NOTE]
  > 개인이 소유한 NuGet 서버 URL은 이 목록에 포함되어 있지 않을 수 있습니다. %APPData%\Nuget\NuGet.Config에서 사용 중인 NuGet 서버를 확인할 수 있습니다.

## <a name="error-failed-to-parse-id-from-parent-process"></a>오류: "부모 프로세스에서 ID를 구문 분석하지 못했습니다"

네트워크 드라이브에서 Visual Studio 부트스트래퍼와 response.json 파일을 사용하는 경우 이 오류 메시지가 나타날 수 있습니다. 오류의 소스는 Windows의 UAC(사용자 계정 컨트롤)입니다.

이 오류가 발생하는 이유는 다음과 같습니다. 매핑된 네트워크 드라이브 또는 [UNC](/dotnet/standard/io/file-path-formats#unc-paths) 공유는 사용자의 액세스 토큰에 연결됩니다. UAC를 사용하면 두 개의 사용자 [액세스 토큰](/windows/win32/secauthz/access-tokens)이 생성됩니다. 관리자 액세스 권한이 *있는* 토큰과 *없는* 토큰입니다. 네트워크 드라이브 또는 공유를 만든 경우 사용자의 현재 액세스 토큰이 연결됩니다. 부트스트래퍼는 관리자 권한으로 실행해야 하기 때문에 드라이브나 공유가 관리자 액세스 권한이 있는 사용자 액세스 토큰에 연결되지 않은 경우 네트워크 드라이브 또는 공유에 액세스할 수 없습니다.

### <a name="to-fix-this-error"></a>이 오류를 해결하려면

`net use` 명령을 사용하거나 UAC 그룹 정책 설정을 변경할 수 있습니다. 이러한 해결 방법 및 구현 방법에 대한 자세한 내용은 다음 Microsoft 지원 문서를 참조하세요.

* [Windows에서 UAC가 "자격 증명 확인"으로 구성된 경우 관리자 권한 프롬프트에서 매핑된 드라이브를 사용할 수 없습니다](https://support.microsoft.com/help/3035277/mapped-drives-are-not-available-from-an-elevated-prompt-when-uac-is-co)
* [Windows 운영 체제에서 사용자 계정 컨트롤을 설정한 후 프로그램에서 일부 네트워크 위치에 액세스하지 못할 수 있습니다](https://support.microsoft.com/en-us/help/937624/programs-may-be-unable-to-access-some-network-locations-after-you-turn)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참조

* [방화벽 또는 프록시 서버 뒤에 Visual Studio 설치 및 사용](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Visual Studio 관리자 가이드](visual-studio-administrator-guide.md)
* [Visual Studio 설치](install-visual-studio.md)
