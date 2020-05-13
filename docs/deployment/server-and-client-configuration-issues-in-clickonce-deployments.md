---
title: ClickOnce 배포의 서버/클라이언트 구성 문제
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- Windows applications, ClickOnce deployments
ms.assetid: 929e5fcc-dd56-409c-bb57-00bd9549b20b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b1d2512c14c0630d2268adfa465e092555150943
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557873"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>ClickOnce 배포 시 서버 및 클라이언트 구성 문제
Windows Server에서 인터넷 정보 서비스 (IIS)를 사용 하는 경우 Windows에서 인식할 수 없는 파일 형식 (예: Microsoft Word 파일)이 배포에 포함 되어 있으면 IIS에서 해당 파일을 전송 하는 것을 거부 하 고 배포가 실패 합니다.

 또한 일부 웹 서버 및 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]와 같은 웹 응용 프로그램 소프트웨어에는 다운로드할 수 없는 파일 및 파일 형식 목록이 포함 되어 있습니다. 예를 들어 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]는 모든 *web.config* 파일의 다운로드를 방지 합니다. 이러한 파일에는 사용자 이름 및 암호와 같은 중요 한 정보가 포함 될 수 있습니다.

 이러한 제한으로 인해 매니페스트 및 어셈블리와 같은 핵심 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 파일을 다운로드 하는 데 문제가 발생 하지는 않지만 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램의 일부로 포함 된 데이터 파일을 다운로드 하지 못할 수 있습니다. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]IIS 구성 관리자에서 이러한 파일의 다운로드를 금지 하는 처리기를 제거 하 여이 오류를 해결할 수 있습니다. 자세한 내용은 IIS 서버 설명서를 참조 하십시오.

 일부 웹 서버는 *.dll*, *.config*및 *.mdf*와 같은 확장명을 가진 파일을 차단할 수 있습니다. Windows 기반 응용 프로그램에는 일반적으로 이러한 확장 중 일부를 포함 하는 파일이 포함 됩니다. 사용자가 웹 서버에서 차단 된 파일에 액세스 하는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램을 실행 하려고 하면 오류가 발생 합니다. 모든 파일 확장명을 차단 해제 하는 대신 기본적으로 파일 확장명이 *.deploy* 인 모든 응용 프로그램 파일을 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 게시 합니다. 따라서 관리자는 다음 세 가지 파일 확장명을 차단 해제 하도록 웹 서버를 구성 하기만 하면 됩니다.

- *.application*

- *.manifest*

- *.deploy*

  그러나 [게시 옵션 대화 상자](/previous-versions/visualstudio/visual-studio-2010/7z83t16a(v=vs.100))에서 **".deploy" 파일 확장명 사용** 옵션을 선택 취소 하 여이 옵션을 사용 하지 않도록 설정할 수 있습니다 .이 경우 응용 프로그램에 사용 되는 모든 파일 확장명을 차단 해제 하도록 웹 서버를 구성 해야 합니다.

  예를 들어 .NET Framework를 설치 하지 않은 IIS를 사용 하는 경우 또는 다른 웹 서버 (예: Apache)를 사용 하는 경우 *.manifest*, *응용 프로그램*및 *.deploy*를 구성 해야 합니다.

## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce 및 SSL(Secure Sockets Layer) (SSL)
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램은 Internet Explorer에서 SSL 인증서에 대 한 프롬프트를 발생 시키는 경우를 제외 하 고는 SSL을 통해 제대로 작동 합니다. 사이트 이름이 일치 하지 않거나 인증서가 만료 된 경우와 같이 인증서에 문제가 있는 경우 메시지가 표시 될 수 있습니다. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] SSL 연결을 사용 하려면 인증서가 최신 상태이 고 인증서 데이터가 사이트 데이터와 일치 하는지 확인 합니다.

## <a name="clickonce-and-proxy-authentication"></a>ClickOnce 및 프록시 인증
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .NET Framework 3.5부터 Windows 통합 프록시 인증에 대 한 지원을 제공 합니다. 특정 machine.config 지시문이 필요 하지 않습니다. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]는 기본 또는 다이제스트와 같은 다른 인증 프로토콜에 대 한 지원을 제공 하지 않습니다.

 .NET Framework 2.0에 핫픽스를 적용 하 여이 기능을 사용 하도록 설정할 수도 있습니다. 자세한 내용은 [.NET Framework 2.0에서 만든 ClickOnce 응용 프로그램을 프록시 서버를 사용 하도록 구성 된 클라이언트 컴퓨터에 설치 하려고 할 때 수정: 오류 메시지: "프록시 인증 필요"](https://support.microsoft.com/help/917952/fix-error-message-when-you-try-to-install-a-clickonce-application-that)를 참조 하십시오.

 자세한 내용은 [\<defaultProxy > 요소 (네트워크 설정)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings)를 참조 하세요.

## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce 및 웹 브라우저 호환성
 현재 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 설치는 Internet Explorer를 사용 하 여 배포 매니페스트에 대 한 URL을 연 경우에만 시작 됩니다. Internet Explorer가 기본 웹 브라우저로 설정 된 경우에만 Microsoft Office Outlook과 같은 다른 응용 프로그램에서 해당 URL이 시작 되는 배포가 성공적으로 시작 됩니다.

> [!NOTE]
> 배포 공급자가 비어 있지 않거나 Microsoft .NET Framework Assistant 확장이 설치 된 경우 Mozilla Firefox가 지원 됩니다. 이 확장은 .NET Framework 3.5 s p 1로 패키지 됩니다. XBAP를 지원 하기 위해 필요한 경우 NPWPF 플러그 인이 활성화 됩니다.

## <a name="activate-clickonce-applications-through-browser-scripting"></a>브라우저 스크립팅을 통해 ClickOnce 응용 프로그램 활성화
 액티브 스크립팅을 사용 하 여 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램을 시작 하는 사용자 지정 웹 페이지를 개발한 경우 일부 컴퓨터에서 응용 프로그램이 실행 되지 않을 수 있습니다. Internet Explorer에는이 동작에 영향을 주는 **파일 다운로드에 대 한 자동 프롬프트**라는 설정이 포함 되어 있습니다. 이 설정은이 동작에 영향을 주는 **옵션** 메뉴의 **보안** 탭에서 사용할 수 있습니다. 이를 **파일 다운로드에 대 한 자동 프롬프트**라고 하며 **다운로드** 범주 아래에 나열 됩니다. 속성은 인트라넷 웹 페이지에 대해 기본적으로 **사용** 으로 설정 되 고 인터넷 웹 페이지에 대해 기본적으로 **사용 하지 않도록** 설정 됩니다. 이 설정을 **사용 하지 않도록**설정 하면 `document.location` 속성에 해당 URL을 할당 하는 등의 방법으로 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램을 프로그래밍 방식으로 활성화 하려고 하면 차단 됩니다. 이 경우 사용자는 응용 프로그램의 URL로 설정 된 하이퍼링크를 클릭 하는 등 사용자가 시작한 다운로드를 통해서만 응용 프로그램을 시작할 수 있습니다.

## <a name="additional-server-configuration-issues"></a>추가 서버 구성 문제

##### <a name="administrator-permissions-required"></a>관리자 권한 필요
 HTTP를 사용 하 여 게시 하는 경우 대상 서버에 대 한 관리자 권한이 있어야 합니다. IIS를 사용 하려면이 권한 수준이 필요 합니다. HTTP를 사용 하 여 게시 하지 않는 경우 대상 경로에 대 한 쓰기 권한만 있으면 됩니다.

##### <a name="server-authentication-issues"></a>서버 인증 문제
 "익명 액세스"가 해제 된 원격 서버에 게시 하면 다음과 같은 경고가 표시 됩니다.

```
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."
```

> [!NOTE]
> 사이트에서 기본 자격 증명이 아닌 자격 증명을 묻는 메시지가 표시 되는 경우 NTLM (NT 챌린지-응답) 인증을 사용할 수 있으며, 보안 대화 상자에서 이후 세션에 대해 제공 된 자격 증명을 저장할지 묻는 메시지가 표시 되 면 **확인** 을 클릭 합니다. 그러나이 해결 방법은 기본 인증에는 적용 되지 않습니다.

## <a name="use-third-party-web-servers"></a>타사 웹 서버 사용
 IIS 이외의 웹 서버에서 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램을 배포 하는 경우 서버에서 배포 매니페스트와 응용 프로그램 매니페스트와 같은 키 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 파일에 대해 잘못 된 콘텐츠 형식을 반환 하는 경우 문제가 발생할 수 있습니다. 이 문제를 해결 하려면 서버에 새 콘텐츠 유형을 추가 하는 방법에 대 한 웹 서버의 도움말 설명서를 참조 하 고 다음 표에 나열 된 모든 파일 이름 확장명 매핑이 준비 되어 있는지 확인 합니다.

|파일 이름 확장명|내용 유형|
|-------------------------|------------------|
|`.application`|`application/x-ms-application`|
|`.manifest`|`application/x-ms-manifest`|
|`.deploy`|`application/octet-stream`|
|`.msu`|`application/octet-stream`|
|`.msp`|`application/octet-stream`|

## <a name="clickonce-and-mapped-drives"></a>ClickOnce 및 매핑된 드라이브
 Visual Studio를 사용 하 여 ClickOnce 응용 프로그램을 게시 하는 경우에는 매핑된 드라이브를 설치 위치로 지정할 수 없습니다. 그러나 매니페스트 생성기 및 편집기 (Mage.exe 및 Mageui.exe)를 사용 하 여 매핑된 드라이브에서 설치 하도록 ClickOnce 응용 프로그램을 수정할 수 있습니다. 자세한 내용은 [mage.exe (매니페스트 생성 및 편집 도구)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) 및 [mageui.exe (매니페스트 생성 및 편집 도구, 그래픽 클라이언트)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)를 참조 하세요.

## <a name="ftp-protocol-not-supported-for-installing-applications"></a>응용 프로그램 설치에 지원 되지 않는 FTP 프로토콜
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]는 모든 HTTP 1.1 웹 서버 또는 파일 서버에서 응용 프로그램 설치를 지원 합니다. 파일 전송 프로토콜 FTP는 응용 프로그램을 설치 하는 데 지원 되지 않습니다. FTP를 사용 하 여 응용 프로그램을 게시할 수 있습니다. 다음 표에는 이러한 차이점이 요약 되어 있습니다.

| URL 형식 | Description |
|----------| - |
| ftp:// | 이 프로토콜을 사용 하 여 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램을 게시할 수 있습니다. |
| http:// | 이 프로토콜을 사용 하 여 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램을 설치할 수 있습니다. |
| https:// | 이 프로토콜을 사용 하 여 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램을 설치할 수 있습니다. |
| file:// | 이 프로토콜을 사용 하 여 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램을 설치할 수 있습니다. |

## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2: Windows 방화벽
 기본적으로 Windows XP s p 2에서는 Windows 방화벽을 사용 하도록 설정 합니다. Windows XP가 설치 된 컴퓨터에서 응용 프로그램을 개발 하는 경우에도 IIS를 실행 하는 로컬 서버에서 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램을 게시 하 고 실행할 수 있습니다. 그러나 Windows 방화벽을 열지 않으면 다른 컴퓨터에서 IIS를 실행 하는 해당 서버에 액세스할 수 없습니다. Windows 방화벽을 관리 하는 방법은 Windows 도움말을 참조 하십시오.

## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: FrontPage server extensions 사용
 HTTP를 사용 하는 Windows 웹 서버에 응용 프로그램을 게시 하려면 Microsoft에서 FrontPage Server Extensions 해야 합니다.

 기본적으로 Windows Server에는 FrontPage Server Extensions 설치 되어 있지 않습니다. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]를 사용 하 여 FrontPage Server Extensions HTTP를 사용 하는 Windows Server 웹 서버에 게시 하려면 먼저 FrontPage Server Extensions를 설치 해야 합니다. Windows Server에서 서버 관리 관리 도구를 사용 하 여 설치를 수행할 수 있습니다.

## <a name="windows-server-locked-down-content-types"></a>Windows Server: 잠긴 콘텐츠 형식
 [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] IIS는 알려진 특정 콘텐츠 형식 (예: *.htm*, *.html*, *.txt*등)을 제외 하 고 모든 파일 형식을 잠급니다. 이 서버를 사용 하 여 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램을 배포 하려면 응용 프로그램, *.manifest*및 응용 프로그램에서 사용 하는 다른 모든 사용자 지정 파일 형식의 파일을 다운로드할 수 있도록 IIS 설정을 변경 해야 합니다 *.*

 IIS 서버를 사용 하 여를 배포 하는 경우에는 *sn.exe* 를 실행 하 고 기본 웹 페이지에 대 한 새 파일 형식을 추가 합니다.

- *응용 프로그램* 및 *.manifest* 확장의 경우 MIME 형식은 "application/x-y-application" 이어야 합니다. 다른 파일 형식의 경우 MIME 형식은 "응용 프로그램/8 진수 스트림" 이어야 합니다.

- 확장명 "<em>" 및 mime 형식 "응용 프로그램/8 진수 스트림"을 사용 하 여 mime 형식을 만들면 차단 해제 된 파일 형식의 파일을 다운로드할 수 있습니다. 그러나 * .aspx 및 .asmx와 같은 차단 된 파일 형식은</em> 다운로드할 수 없습니다.

  Windows Server에서 MIME 형식을 구성 하는 방법에 대 한 지침은 [웹 사이트 또는 응용 프로그램에 mime 형식을 추가 하는 방법](/iis/configuration/system.webserver/staticcontent/mimemap#how-to-add-a-mime-type-to-a-web-site-or-application)을 참조 하세요.

## <a name="content-type-mappings"></a>콘텐츠 형식 매핑
 HTTP를 통해 게시 하는 경우 *응용 프로그램* 파일에 대 한 콘텐츠 형식 (MIME 형식이 라고도 함)은 "응용 프로그램/x m s-응용 프로그램" 이어야 합니다. 서버에 .NET Framework 2.0가 설치 되어 있으면 자동으로 설정 됩니다. 이 버전이 설치 되어 있지 않으면 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램 vroot 또는 전체 서버에 대 한 MIME 형식 연결을 만들어야 합니다.

 IIS 서버를 사용 하 여 배포 하는 경우 inetmgr을 실행 <em>합니다.</em> exe를 실행 하 고 *응용 프로그램* 확장에 대해 "응용 프로그램/x m s-응용 프로그램"의 새 콘텐츠 형식을 추가 합니다.

## <a name="http-compression-issues"></a>HTTP 압축 문제
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]를 사용 하면 클라이언트에 스트림을 보내기 전에 GZIP 알고리즘을 사용 하 여 데이터 스트림을 압축 하는 웹 서버 기술인 HTTP 압축을 사용 하는 다운로드를 수행할 수 있습니다. 클라이언트 (이 경우 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)])는 파일을 읽기 전에 스트림 압축을 풉니다.

 IIS를 사용 하는 경우 HTTP 압축을 쉽게 사용 하도록 설정할 수 있습니다. 그러나 HTTP 압축을 사용 하도록 설정 하는 경우 특정 파일 형식 (즉, HTML 및 텍스트 파일)에 대해서만 사용할 수 있습니다. 어셈블리 ( *.dll*), xml ( *.xml*), 배포 매니페스트 (*응용 프로그램*) 및 응용 프로그램 매니페스트 ( *.manifest*)에 대해 압축을 사용 하도록 설정 하려면 이러한 파일 형식을 IIS에서 압축할 형식 목록에 추가 해야 합니다. 배포에 파일 형식을 추가할 때까지 텍스트 및 HTML 파일만 압축 됩니다.

 IIS에 대 한 자세한 지침은 [HTTP 압축을 위한 추가 문서 유형을 지정 하는 방법](https://support.microsoft.com/help/234497)을 참조 하세요.

## <a name="see-also"></a>참고 항목
- [ClickOnce 배포 문제 해결](../deployment/troubleshooting-clickonce-deployments.md)
- [ClickOnce 배포 전략 선택](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [애플리케이션 배포 필수 구성 요소](../deployment/application-deployment-prerequisites.md)