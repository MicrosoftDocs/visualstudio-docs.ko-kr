---
title: ClickOnce 배포의 특정 오류 문제 해결 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.UncRequired
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.NoInstallUrl
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
ms.assetid: 22dfe8f1-8271-4708-9c25-6bbb13920ac8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fac7f18244aaa32667514766ad6d393408997e51
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87235162"
---
# <a name="troubleshoot-specific-errors-in-clickonce-deployments"></a>ClickOnce 배포 관련 오류 문제 해결
이 문서에서는 응용 프로그램을 배포할 때 발생할 수 있는 다음과 같은 일반적인 오류를 나열 하 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 고 각 문제를 해결 하는 단계를 제공 합니다.

## <a name="general-errors"></a>일반 오류

#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>응용 프로그램 파일을 찾으려고 하거나 Internet Explorer에서 XML 렌더링을 수행 하지 않거나 또는 다른 이름으로 저장 대화 상자를 수신 하는 경우
 이 오류는 서버 또는 클라이언트에서 콘텐츠 형식 (MIME 형식이 라고도 함)이 올바르게 등록 되지 않은 경우에 발생할 수 있습니다.

 먼저, *응용* 프로그램 확장명을 "application/x-y-application" 콘텐츠 형식과 연결 하도록 서버를 구성 했는지 확인 합니다.

 서버가 올바르게 구성 된 경우 컴퓨터에 .NET Framework 2.0가 설치 되어 있는지 확인 합니다. .NET Framework 2.0가 설치 되어 있는 경우이 문제가 계속 발생 하면 .NET Framework 2.0를 제거한 후 다시 설치 하 여 클라이언트에서 콘텐츠 형식을 다시 등록 하십시오.

#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>"응용 프로그램을 검색할 수 없습니다. 라는 오류 메시지가 표시 됩니다. 배포에 누락 된 파일이 있습니다. "또는" 응용 프로그램 다운로드가 중단 되었습니다. 네트워크 오류를 확인 하 고 나중에 다시 시도 하십시오. "
 이 메시지는 매니페스트에서 참조 하는 하나 이상의 파일을 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 다운로드할 수 없음을 나타냅니다. 이 오류를 디버깅 하는 가장 쉬운 방법은 다운로드할 수 없다고 URL을 다운로드 하는 것입니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . 몇 가지 가능한 원인은 다음과 같습니다.

- 로그 파일에 "(403)을 (를) 사용할 수 없음" 또는 "(404) 찾을 수 없음"이 표시 되는 경우 "이 파일의 다운로드를 차단 하지 않도록 웹 서버를 구성 했는지 확인 합니다. 자세한 내용은 [ClickOnce 배포 시 서버 및 클라이언트 구성 문제](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md)를 참조하세요.

- *.Config* 파일이 서버에 의해 차단 되는 경우 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 이 문서의 뒷부분에 나오는 ".config 파일이 있는 응용 프로그램을 설치 하려고 할 때 다운로드 오류" 섹션을 참조 하세요.

- `deploymentProvider`배포 매니페스트의 url이 활성화에 사용 된 url과 다른 위치를 가리키기 때문에이 오류가 발생 했는지 여부를 확인 합니다.

- 모든 파일이 서버에 존재 하는지 확인 합니다. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]로그에서 찾을 수 없는 파일을 알려 줍니다.

- 네트워크 연결 문제가 있는지 여부를 확인 합니다. 다운로드 하는 동안 클라이언트 컴퓨터가 오프 라인 상태가 되 면이 메시지를 수신할 수 있습니다.

#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>.Config 파일이 있는 ClickOnce 응용 프로그램을 설치 하려고 하면 다운로드 오류가 발생 합니다.
 기본적으로 Visual Basic Windows 기반 응용 프로그램에는 App.config 파일이 포함 되어 있습니다. 사용자가 Windows Server 2003를 사용 하는 웹 서버에서를 설치 하려고 하면 운영 체제가 보안상의 이유로 *.config* 파일의 설치를 차단 하기 때문에 문제가 발생 합니다. *.Config* 파일 설치를 사용 하도록 설정 하려면 **게시 옵션** 대화 상자에서 **".deploy" 파일 확장명 사용** 을 클릭 합니다.

 또한 응용 프로그램, .manifest 및 .deploy 파일에 대해 콘텐츠 형식 (MIME 형식이 라고도 함)을 적절 하 게 설정 해야 합니다. 자세한 내용은 웹 서버 설명서를 참조 하세요.

 자세한 내용은 [ClickOnce 배포의 서버 및 클라이언트 구성 문제](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md)에서 "Windows Server 2003: 잠긴 콘텐츠 형식"을 참조 하세요.

#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>오류 메시지: "응용 프로그램의 형식이 잘못 되었습니다." 로그 파일에 "XML 서명이 잘못 되었습니다."가 포함 되어 있습니다.
 매니페스트 파일을 업데이트 하 고 다시 서명 했는지 확인 합니다. 또는를 사용 하 여 응용 프로그램을 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 다시 게시 하 고 응용 프로그램에 다시 서명 합니다.

#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>서버에서 응용 프로그램을 업데이트 했지만 클라이언트는 업데이트를 다운로드 하지 않습니다.
 이 문제는 다음 작업 중 하나를 완료 하 여 해결할 수 있습니다.

- `deploymentProvider`배포 매니페스트에서 URL을 검사 합니다. 가 가리키는 동일한 위치의 비트를 업데이트 하 고 있는지 확인 `deploymentProvider` 합니다.

- 배포 매니페스트에서 업데이트 간격을 확인 합니다. 이 간격이 정기적 간격으로 설정 된 경우 (예: 6 시간 마다 한 번)는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 이 간격이 경과할 때까지 업데이트를 검색 하지 않습니다. 응용 프로그램이 시작 될 때마다 업데이트를 검색 하도록 매니페스트를 변경할 수 있습니다. 업데이트 간격을 변경 하는 것은 업데이트를 설치 하는 것을 확인 하는 개발 시간 동안 편리한 옵션 이지만 응용 프로그램 활성화 속도가 느려집니다.

- 시작 메뉴에서 응용 프로그램을 다시 시작 해 보세요. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]백그라운드에서 업데이트를 검색 했을 수 있지만 다음 활성화 시 비트를 설치할지 묻는 메시지가 표시 됩니다.

#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>업데이트 중에 "배포의 참조가 응용 프로그램 매니페스트에 정의 된 id와 일치 하지 않습니다."와 같은 오류 메시지가 표시 됩니다.
 이 오류는 배포 및 응용 프로그램 매니페스트를 수동으로 편집 하 여 한 매니페스트의 어셈블리 id에 대 한 설명이 다른 매니페스트의 동기화 되지 않기 때문에 발생할 수 있습니다. 어셈블리의 id는 해당 이름, 버전, 문화권 및 공개 키 토큰으로 구성 됩니다. 매니페스트에서 id 설명을 검사 하 고 차이점을 수정 합니다.

#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>로컬 디스크 또는 CD-ROM에서 처음으로 정품 인증에 성공 했지만 시작 메뉴의 후속 활성화에 성공 하지 않음
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]는 배포 공급자 URL을 사용 하 여 응용 프로그램에 대 한 업데이트를 수신 합니다. URL이 가리키는 위치가 올바른지 확인 합니다.

#### <a name="error-cannot-start-the-application"></a>오류: "응용 프로그램을 시작할 수 없습니다."
 이 오류 메시지는 일반적으로 저장소에이 응용 프로그램을 설치 하는 데 문제가 있음을 나타냅니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . 응용 프로그램에 오류가 있거나 저장소가 손상 되었습니다. 로그 파일에서 오류가 발생 한 위치를 알 수 있습니다.

 다음을 수행 해야 합니다.

- 배포 매니페스트의 id, 응용 프로그램 매니페스트의 id 및 주 응용 프로그램 EXE의 id가 모두 고유한 지 확인 합니다.

- 파일 경로가 100 자 보다 길지 않은지 확인 합니다. 응용 프로그램에 너무 긴 파일 경로가 포함 되어 있으면 저장할 수 있는 최대 경로에 대 한 제한 사항을 초과할 수 있습니다. 경로를 단축 하 고 다시 설치 하세요.

#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>응용 프로그램 구성 파일의 PrivatePath 설정이 적용 되지 않습니다.
 PrivatePath (Fusion 검색 경로)를 사용 하려면 응용 프로그램이 완전 신뢰 권한을 요청 해야 합니다. 완전 신뢰를 요청 하도록 응용 프로그램 매니페스트를 변경한 후 다시 시도 하십시오.

#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>제거 하는 동안 "응용 프로그램을 제거 하지 못했습니다." 라는 메시지가 나타납니다.
 이 메시지는 일반적으로 응용 프로그램이 이미 제거 되었거나 저장소가 손상 되었음을 나타냅니다. **확인**을 클릭 하면 **프로그램 추가/제거** 항목이 제거 됩니다.

#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>설치 하는 동안 플랫폼 종속성이 설치 되어 있지 않다는 메시지가 표시 됩니다.
 응용 프로그램을 실행 하는 데 필요한 GAC (전역 어셈블리 캐시)에 필수 구성 요소가 누락 되었습니다.

## <a name="publishing-with-visual-studio"></a>Visual Studio를 사용 하 여 게시

#### <a name="publishing-in-visual-studio-fails"></a>Visual Studio에서 게시 하지 못함
 대상 서버에 게시할 수 있는 권한이 있는지 확인 합니다. 예를 들어 관리자가 아닌 일반 사용자로 터미널 서버 컴퓨터에 로그인 한 경우 로컬 웹 서버에 게시 하는 데 필요한 권한이 없는 것일 수 있습니다.

 URL을 사용 하 여 게시 하는 경우 대상 컴퓨터가 FrontPage Server Extensions 사용 하도록 설정 되었는지 확인 합니다.

#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>오류 메시지: 웹 사이트 ' '을 (를) 만들 수 없습니다 \<site> . FrontPage Server Extensions와 통신 하기 위한 구성 요소가 설치 되어 있지 않습니다.
 게시 중인 컴퓨터에 Microsoft Visual Studio 웹 제작 구성 요소가 설치 되어 있는지 확인 합니다. Express 사용자의 경우이 구성 요소는 기본적으로 설치 되지 않습니다. 자세한 내용은 [http://go.microsoft.com/fwlink/?LinkId=102310](https://support.microsoft.com/help/945358)를 참조하세요.

#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>오류 메시지: 파일 ' 6.0.0.0, Version =, Culture = *, PublicKeyToken = 6595b64144ccf1df, ProcessorArchitecture = \* , Type = win32 '를 찾을 수 없습니다.
 비주얼 스타일을 사용 하 여 WPF 응용 프로그램을 게시 하려고 하면이 오류 메시지가 나타납니다. 이 문제를 해결 하려면 [방법: 비주얼 스타일을 사용 하 여 WPF 응용 프로그램 게시](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)를 참조 하세요.

## <a name="using-mage"></a>Mage 사용

#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>인증서 저장소의 인증서를 사용 하 여 서명 하려고 하 고 빈 메시지 상자를 받았습니다.
 **서명** 대화 상자에서 다음을 수행 해야 합니다.

- **저장 된 인증서로 서명**을 선택 하 고

- 목록에서 인증서를 선택 합니다. 첫 번째 인증서는 기본 선택 사항이 아닙니다.

#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>"서명 안 함" 단추를 클릭 하면 예외가 발생 합니다.
 이 문제는 알려진 버그입니다. 모든 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 매니페스트에 서명 해야 합니다. 서명 옵션 중 하나를 선택한 다음 **확인**을 클릭 하면 됩니다.

## <a name="additional-errors"></a>추가 오류
 다음 표에서는 사용자가 응용 프로그램을 설치할 때 클라이언트 컴퓨터 사용자가 받을 수 있는 몇 가지 일반적인 오류 메시지를 보여 줍니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . 오류의 가장 가능성이 높은 원인에 대 한 설명 옆에 각 오류 메시지가 나열 됩니다.

| 오류 메시지 | Description |
| - | - |
| 응용 프로그램을 시작할 수 없습니다. 응용 프로그램 게시자에 게 문의 하십시오.<br /><br /> 응용 프로그램을 시작할 수 없습니다. 응용 프로그램 공급 업체에 지원을 문의 하십시오. | 이러한 메시지는 응용 프로그램을 시작할 수 없을 때 발생 하는 일반적인 오류 메시지 이며 다른 특정 이유를 찾을 수 없습니다. 이는 응용 프로그램이 손상 되었거나 저장소가 손상 된 것을 의미 하는 경우가 많습니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . |
| 계속할 수 없습니다. 응용 프로그램의 형식이 잘못 되었습니다. 도움이 필요 하면 응용 프로그램 게시자에 게 문의 하십시오.<br /><br /> 응용 프로그램 유효성 검사에 실패 했습니다. 계속할 수 없습니다.<br /><br /> 응용 프로그램 파일을 검색할 수 없습니다. 배포에서 파일이 손상 되었습니다. | 배포의 매니페스트 파일 중 하나가 구문상 잘못 되었거나 해당 파일을 사용 하 여 조정할 수 없는 해시가 포함 되어 있습니다. 이 오류는 어셈블리 내에 포함 된 매니페스트가 손상 되었음을 나타낼 수도 있습니다. 배포를 다시 만들고 응용 프로그램을 다시 컴파일하거나 매니페스트에서 오류를 수동으로 찾아서 수정 합니다. |
| 응용 프로그램을 검색할 수 없습니다. 인증 오류입니다.<br /><br /> 응용 프로그램을 설치 하지 못했습니다. 서버에서 응용 프로그램 파일을 찾을 수 없습니다. 도움이 필요 하면 응용 프로그램 게시자 또는 관리자에 게 문의 하십시오. | 배포에 있는 하나 이상의 파일에 액세스할 수 있는 권한이 없어서 해당 파일을 다운로드할 수 없습니다. 웹 서버에서 403 금지 오류가 반환 되는 경우이 오류가 발생할 수 있습니다 .이는 배포의 파일 중 하나가 웹 서버에서 해당 파일을 보호 된 파일로 처리 하는 확장명으로 끝나는 경우에 발생할 수 있습니다. 또한 하나 이상의 응용 프로그램 파일을 포함 하는 디렉터리는에 액세스 하기 위해 사용자 이름과 암호를 요구할 수 있습니다. |
| 응용 프로그램을 다운로드할 수 없습니다. 응용 프로그램에 필요한 파일이 없습니다. 도움이 필요 하면 응용 프로그램 공급 업체 또는 시스템 관리자에 게 문의 하십시오. | 응용 프로그램 매니페스트에 나열 된 파일 중 하나 이상을 서버에서 찾을 수 없습니다. 모든 배포의 종속 파일을 업로드 했는지 확인 한 후 다시 시도 하십시오. |
| 응용 프로그램 다운로드에 실패 했습니다. 네트워크 연결을 확인 하거나 시스템 관리자나 네트워크 서비스 공급자에 게 문의 하십시오. | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]서버에 대 한 네트워크 연결을 설정할 수 없습니다. 서버의 가용성 및 네트워크 상태를 확인 합니다. |
| URLDownloadToCacheFile에서 HRESULT ' '이 (가) 발생 했습니다 \<number> . ' '을 (를) 다운로드 하는 동안 오류가 발생 했습니다 \<file> . | 사용자가 배포 대상 컴퓨터에서 Internet Explorer 고급 보안 옵션인 "보안 모드를 변경 하는 경우 경고"를 설정 하 고 설치 되는 ClickOnce 응용 프로그램의 설치 URL이 안전 하지 않은 사이트에서 안전한 사이트로 리디렉션되는 경우 (또는 그 반대의 경우), Internet Explorer 경고에서 중단 하기 때문에 설치가 실패 합니다.<br /><br /> 이 오류를 해결 하려면 다음 작업 중 하나를 수행 하면 됩니다.<br /><br /> -보안 옵션을 선택 취소 합니다.<br />-보안 모드를 변경 하는 방식으로 설치 URL이 리디렉션되지 않는지 확인 합니다.<br />-리디렉션을 완전히 제거 하 고 실제 설치 URL을 가리킵니다. |
| 하드 디스크에 쓰는 동안 오류가 발생 했습니다. 디스크에 사용 가능한 공간이 부족할 수 있습니다. 도움이 필요 하면 응용 프로그램 공급 업체 또는 시스템 관리자에 게 문의 하십시오. | 이는 응용 프로그램을 저장 하는 데 충분 한 디스크 공간이 없다는 것을 나타낼 수 있지만 응용 프로그램 파일을 드라이브에 저장 하려고 할 때 더 일반적인 i/o 오류를 나타낼 수도 있습니다. |
| 응용 프로그램을 시작할 수 없습니다. 디스크에 사용 가능한 공간이 부족 합니다. | 하드 디스크가 꽉 찼습니다. 공간을 해제 하 고 응용 프로그램을 다시 실행 해 보십시오. |
| 배포 된 활성화를 한 번에 너무 많이 로드 하려고 합니다. | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]동시에 시작할 수 있는 다른 응용 프로그램의 수를 제한 합니다. 이것은 로컬 서비스에 대해 서비스 거부 공격을 instigate 하는 악의적인 시도 로부터 보호 하는 데 주로 사용 됩니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . 동일한 응용 프로그램을 반복적으로 신속 하 게 시작 하는 사용자는 응용 프로그램의 단일 인스턴스만 종료 합니다. |
| 네트워크를 통해 바로 가기를 활성화할 수 없습니다. | 응용 프로그램에 대 한 바로 가기는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 로컬 하드 디스크 에서만 시작할 수 있습니다. 원격 서버에서 바로 가기 파일을 가리키는 URL을 열어 시작할 수 없습니다. |
| 응용 프로그램이 너무 커서 부분 신뢰로 온라인에서 실행할 수 없습니다. 도움이 필요 하면 응용 프로그램 공급 업체 또는 시스템 관리자에 게 문의 하십시오. | 부분 신뢰로 실행 되는 응용 프로그램은 온라인 응용 프로그램 할당량 크기의 절반 (기본적으로 250 MB) 보다 클 수 없습니다. |

## <a name="see-also"></a>참고 항목
- [ClickOnce 보안 및 배포](../deployment/clickonce-security-and-deployment.md)
- [ClickOnce 배포 문제 해결](../deployment/troubleshooting-clickonce-deployments.md)
- [Visual Studio 문제 해결](/troubleshoot/visualstudio/welcome-visual-studio/)