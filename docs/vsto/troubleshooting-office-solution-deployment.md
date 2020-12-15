---
title: Office 솔루션 배포 문제 해결
description: Office 솔루션을 배포할 때 발생할 수 있는 일반적인 문제를 해결할 수 있는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: troubleshooting
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- Office development in Visual Studio, troubleshooting
- deploying applications [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b70b03e8342564de828059d1a335f6347c19b5a3
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97522975"
---
# <a name="troubleshoot-office-solution-deployment"></a>Office 솔루션 배포 문제 해결
  이 항목에는 Office 솔루션을 배포할 때 발생할 수 있는 일반적인 문제를 해결하는 방법에 대한 정보가 포함되어 있습니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="troubleshoot-office-solutions-by-using-the-event-viewer"></a>이벤트 뷰어를 사용 하 여 Office 솔루션 문제 해결
 Windows 이벤트 뷰어를 사용하여 Office 솔루션을 설치하거나 제거할 때 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 에서 캡처하는 오류 메시지를 표시할 수 있습니다. 이벤트 로거에서 이러한 메시지를 사용하여 설치 및 배포 문제를 해결할 수 있습니다. 자세한 내용은 [Office 솔루션에 대 한 이벤트 로깅](../vsto/event-logging-for-office-solutions.md)을 참조 하세요.

## <a name="change-the-assembly-name-causes-conflicts"></a>어셈블리 이름 변경 시 충돌 발생
 솔루션을 이미 배포한 후에 **프로젝트 디자이너** 의 **응용 프로그램** 페이지에서 **어셈블리 이름** 값을 변경 하는 경우 게시 도구는 하나의 *Setup.exe* 파일과 두 개의 배포 매니페스트를 포함 하도록 설치 패키지를 수정 합니다. 두 개의 매니페스트 파일을 배포하는 경우 다음 상황이 발생할 수 있습니다.

- 최종 사용자가 두 버전을 모두 설치한 경우 애플리케이션이 두 VSTO 추가 기능을 모두 로드합니다.

- 어셈블리 이름이 변경되기 전에 VSTO 추가 기능이 설치된 경우 최종 사용자에게 업데이트가 전달되지 않습니다.

  이러한 상황을 방지 하려면 솔루션 배포 후 솔루션의 **어셈블리 이름** 값을 변경 하지 마세요.

## <a name="check-for-updates-takes-a-long-time"></a>업데이트 확인 시간이 오래 걸립니다.
 Visual Studio 2010 Tools for Office runtime은 관리자가 매니페스트 및 솔루션 다운로드를 위한 시간 제한 값을 설정 하는 데 사용할 수 있는 레지스트리 항목을 제공 합니다.

#### <a name="to-set-the-time-out-value"></a>시간 제한 값을 설정하려면

1. 레지스트리에서 다음 키로 이동합니다.

     **HKEY_CURRENT_USER\Software\Microsoft\VSTA**

2. **AddInTimeout** 하위 키에서 시간 제한 값을 밀리초 단위로 설정합니다.

     **AddInTimeout** 하위 키가 존재하지 않는 경우 DWORD 값으로 만듭니다.

## <a name="cant-update-or-publish-to-a-network-file-share"></a>네트워크 파일 공유를 업데이트 하거나 게시할 수 없음
 업데이트를 게시 하는 동안 프로세스에서 솔루션의 *Setup.exe* 파일이 잠겨 있으면 업데이트 하는 동안 네트워크 파일 공유에 있는 Office 솔루션에서 잘못 된 메시지를 표시할 수 있습니다. 나타나는 메시지는 "'setup.exe'를 웹 사이트에 추가할 수 없습니다. 이 웹 사이트에 'setup.exe' 파일이 이미 있습니다."입니다.

 파일 잠금을 방지하기 위해 공유를 최종 사용자에 대해 읽기 전용으로 만들 수 있습니다. 그러나 공유에 문서가 있는 경우 해당 문서도 최종 사용자에 대해 읽기 전용으로 설정됩니다.

## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Microsoft Office 필수 구성 요소가 설치 되어 있지 않음
 Office 솔루션과 함께 배포되는 필수 조건으로 .NET Framework, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]및 Office 주 interop 어셈블리를 설치 패키지에 추가할 수 있습니다. 주 interop 어셈블리를 설치 하는 방법에 대 한 자세한 내용은 [office 솔루션을 개발 하도록 컴퓨터 구성](../vsto/configuring-a-computer-to-develop-office-solutions.md) 및 [방법: office 주 interop 어셈블리 설치](../vsto/how-to-install-office-primary-interop-assemblies.md)를 참조 하세요.

## <a name="publish-using-localhost-can-cause-installation-problems"></a>Localhost를 사용 하 여 게시 하면 설치 문제가 발생할 수 있음
 `http://localhost`문서 수준 솔루션의 게시 또는 설치 위치로를 사용 하면 **게시 마법사** 가 문자열을 실제 컴퓨터 이름으로 변환 하지 않습니다. 이 경우 개발 컴퓨터에 솔루션을 설치해야 합니다. 배포된 솔루션에서 개발 컴퓨터의 IIS를 사용하게 하려면 localhost 대신 모든 HTTP/HTTPS/FTP 위치에 대한 정규화된 이름을 사용합니다.

## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>업데이트 된 어셈블리 대신 캐시 된 어셈블리가 로드 됩니다.
 .NET Framework 어셈블리 로더인 Fusion은 프로젝트 출력 경로가 네트워크 파일 공유에 있고, 어셈블리가 강력한 이름으로 서명되고, 사용자 지정의 어셈블리 버전이 변경되지 않은 경우 캐시된 어셈블리 복사본을 로드합니다. 이러한 조건을 충족하는 어셈블리를 업데이트할 경우 다음에 프로젝트를 실행할 때 캐시된 복사본이 로드되기 때문에 업데이트가 나타나지 않습니다.

 프로젝트를 실행할 때마다 Fusion에서 어셈블리를 다운로드하도록 Visual Studio를 구성할 수 있습니다.

### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>캐시된 복사본을 로드하지 않고 어셈블리를 다운로드하려면

1. 메뉴 모음에서 **프로젝트**, _ProjectName_**속성** 을 참조하세요.

2. **애플리케이션** 페이지에서 **어셈블리 정보** 를 선택합니다.

3. **어셈블리 버전** 의 수정 번호 세 번째 필드를 와일드 카드 ()로 설정 \* 합니다. 예를 들면 "1.0. *"입니다.  그런 다음 **확인** 단추를 선택 합니다.

   어셈블리 버전을 변경하면 강력한 이름으로 어셈블리에 서명할 수 있고 Fusion에서 최신 버전의 사용자 지정을 로드합니다.

 [!NOTE]
> Visual Studio 2017부터 어셈블리 버전에서 와일드 카드를 사용 하려고 하면 빌드 오류가 발생 합니다.  이는 어셈블리 버전의 와일드 카드가 MSBuild 결정적 기능을 중단 하기 때문입니다. 어셈블리 버전에서 와일드 카드를 제거 하거나 명확성을 사용 하지 않도록 설정 하 라는 메시지가 표시 됩니다.  결정적 기능에 대해 자세히 알아보려면 [일반적인 MSBuild 프로젝트 속성](../msbuild/common-msbuild-project-properties.md) 및 [빌드 사용자 지정](../msbuild/customize-your-build.md) 을 참조 하세요.

## <a name="installation-fails-when-the-uri-has-characters-that-arent-us-ascii"></a>URI에 US-ASCII가 아닌 문자가 있는 경우 설치가 실패 합니다.
 HTTP/HTTPS/FTP 위치에 Office 솔루션을 게시할 경우 경로에 US-ASCII가 아닌 유니코드 문자를 사용할 수 없습니다. 이러한 문자를 사용하면 설치 프로그램에서 일관되지 않은 동작이 발생할 수 있습니다. 설치 경로에 US-ASCII 문자를 사용합니다.

## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>개발 컴퓨터에 솔루션을 게시 및 설치할 때 수동으로 제거 하 라는 메시지가 표시 됩니다.
 Office 솔루션을 빌드하면 빌드된 버전이 자동으로 등록됩니다. 이전에 개발 컴퓨터에 동일한 솔루션을 게시 및 설치한 적이 있는 경우 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 에서는 게시된 버전 및 빌드된 버전의 설치 경로가 솔루션이 다음에 빌드, 다시 빌드 또는 게시된 이후 달라졌다는 것을 감지합니다. 오류 메시지는 "다른 버전이 현재 설치되어 있고 이 위치에서 업그레이드할 수 없기 때문에 사용자 지정을 설치할 수 없습니다."입니다. 레지스트리 키는 솔루션이 다시 빌드될 때마다 업데이트됩니다. 따라서 새 버전을 게시, 디버그 또는 실행하기 전에 이전 버전을 제거해야 합니다.

 메시지가 나타나지 않게 하려면 개발 컴퓨터에서 다른 사용자 계정을 만들어 배포를 테스트합니다. 또는 다음에 솔루션을 게시, 디버그 또는 다시 빌드하기 전에 컴퓨터에 설치된 프로그램 목록에서 해당 버전을 제거할 수 있습니다.

## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>솔루션을 설치할 때 catch 되지 않은 예외 또는 메서드를 찾을 수 없음 오류 발생
 배포 매니페스트 ( *.vsto* 파일), office 응용 프로그램, 문서 또는 통합 문서를 열어 office 솔루션을 설치할 때 다음 조건에 대 한 오류 메시지가 나타날 수 있습니다.

- 메서드를 찾을 수 없습니다.

- MissingMethodException.

- Catch되지 않은 예외

  이러한 오류 메시지를 방지하려면 설치 프로그램을 실행하여 솔루션을 설치합니다.

  설치 프로그램을 실행하지 않고 솔루션을 설치할 때는 설치 관리자가 필수 조건을 확인하거나 설치하지 않습니다. 필수 조건의 올바른 버전을 확인하고 필요에 따라 설치하는 것은 설치 프로그램의 역할입니다.

## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>InstallShield 제한 된 버전 프로젝트가 빌드된 후 추가 기능에 대 한 매니페스트 레지스트리 키 변경
 VSTO 추가 기능 설치 프로그램의 일부인 매니페스트 레지스트리 키는 InstallShield 제한 된 버전 프로젝트를 빌드할 때 *vsto* 에서 *.dll .manifest* 로 변경 되는 경우가 있습니다.

 이 문제를 해결하려면 다른 솔루션에서 InstallShield Limited Edition 프로젝트를 만들거나, VSTO 추가 기능 이름이 포함된 레지스트리 키 값으로 CompanyName.AddinName을 사용합니다.

## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>Office 솔루션에 대 한 ClickOnce 설치 관리자가 주 interop 어셈블리를 설치 하지 않습니다.
 Office 솔루션에 대해 ClickOnce가 만드는 설치 프로그램을 실행할 때 Office PIA(주 Interop 어셈블리)용 설치 관리자는 PIA가 이미 설치되어 있지 않은 경우에만 실행됩니다.

 설치 프로그램에서 Pia를 올바르게 설치 하지 않는 경우 설치 디렉터리에서 *o2007pia.msi* 이름이 지정 된 설치 관리자 파일을 실행 하 여 수동으로 설치 합니다.

## <a name="reinstall-office-solutions-causes-an-argument-out-of-range-exception"></a>Office 솔루션 다시 설치 시 인수가 범위를 벗어남 예외 발생
 Office 솔루션을 다시 설치할 때 '지정한 인수가 유효한 값 범위를 벗어났습니다.'라는 오류 메시지와 함께 <xref:System.ArgumentOutOfRangeException> 예외가 나타날 수 있습니다.

 이러한 문제는 설치 위치에 대한 URL의 대소문자가 다른 경우 발생합니다. 예를 들어 처음부터 Office 솔루션을 설치 하 `http://fabrikam.com/ExcelSolution.vsto` 고 두 번째로 사용한 경우이 오류가 표시 됩니다 `http://fabrikam.com/excelsolution.vsto` .

 메시지를 표시하지 않으려면 Office 솔루션을 설치할 때 동일한 대/소문자를 사용합니다.

## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>웹에서 배포 매니페스트를 열어 ClickOnce 솔루션을 설치할 수 없습니다.
 사용자는 웹에서 배포 매니페스트를 열어 Office 솔루션을 설치할 수 있습니다. 그러나 인터넷 정보 서비스 (IIS)의 일부 설치는 *.vsto* 파일 이름 확장명을 차단 합니다. Office 솔루션을 배포 하는 데 사용 하기 전에 IIS에서 MIME 형식을 정의 해야 합니다.

 IIS 7에서 MIME 형식을 정의 하는 방법에 대 한 자세한 내용은 [Mime 형식 추가 (IIS7)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc725608(v=ws.10))를 참조 하세요.

 확장명을 **.vsto** 로 설정하고 MIME 형식을 **application/x-ms-vsto** 로 설정합니다.

## <a name="see-also"></a>참고 항목

- [ClickOnce 배포 문제 해결](../deployment/troubleshooting-clickonce-deployments.md)
- [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)
- [Visual Studio 문제 해결](/troubleshoot/visualstudio/welcome-visual-studio/)