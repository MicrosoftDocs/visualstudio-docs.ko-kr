---
title: ClickOnce 보안 및 배포 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployment
- deploying applications [ClickOnce]
- ClickOnce deployment
- publishing, ClickOnce
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 592bf358c24bee146290e8b3a00e28a0870f452d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "66263797"
---
# <a name="clickonce-security-and-deployment"></a>ClickOnce 보안 및 배포
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 는 최소한의 사용자 조작으로 설치 하 고 실행할 수 있는 자동 업데이트 Windows 기반 응용 프로그램을 만들 수 있도록 하는 배포 기술입니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Visual Basic 및 Visual c #을 사용 하 여 프로젝트를 개발한 경우 ClickOnce 기술을 사용 하 여 배포 된 응용 프로그램 게시 및 업데이트에 대 한 완전 한 지원을 제공 합니다. Visual C++ 응용 프로그램 배포에 대 한 자세한 내용은 [Visual C++ 응용 프로그램에 대 한 ClickOnce 배포](/cpp/windows/clickonce-deployment-for-visual-cpp-applications)를 참조 하세요.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포는 배포에서 세 가지 주요 문제를 극복 합니다.  
  
- **애플리케이션 업데이트의 어려움.** Microsoft Windows Installer 배포를 사용 하면 응용 프로그램이 업데이트 될 때마다 사용자가 업데이트와 msp 파일을 설치 하 여 설치 된 제품에 적용할 수 있습니다. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포를 사용 하면 업데이트를 자동으로 제공할 수 있습니다. 응용 프로그램에서 변경 된 부분만 다운로드 한 다음 전체 업데이트 된 응용 프로그램이 새 side-by-side 폴더에서 다시 설치 됩니다.  
  
- **사용자의 컴퓨터에 영향을 줍니다.** Windows Installer 배포를 사용 하는 경우 응용 프로그램은 종종 공유 구성 요소를 사용 하므로 버전 관리 충돌이 발생할 수 있습니다. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포를 사용 하는 경우 각 응용 프로그램은 자체 포함 되며 다른 응용 프로그램을 방해할 수 없습니다.  
  
- **보안 권한.** Windows Installer 배포에는 관리 권한이 필요 하 고 제한 된 사용자만 설치할 수 있습니다. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포를 통해 관리자가 아닌 사용자가 설치 하 고 응용 프로그램에 필요한 코드 액세스 보안 권한만 부여할 수 있습니다.  
  
  이전에는 이러한 문제로 인해 개발자가 Windows 기반 응용 프로그램 대신 웹 응용 프로그램을 만들어 쉽게 설치할 수 있도록 다양 한 사용자 인터페이스를 사용 하는 경우가 있습니다. 를 사용 하 여 배포 된 응용 프로그램을 사용 하 여 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 두 가지 기술을 모두 활용할 수 있습니다.  
  
## <a name="what-is-a-clickonce-application"></a>ClickOnce 응용 프로그램 이란?  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]응용 프로그램은 기술을 사용 하 여 게시 된 모든 Windows Presentation Foundation (xbap), Windows Forms (.exe), 콘솔 응용 프로그램 (.exe) 또는 Office 솔루션 (.dll)입니다 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]응용 프로그램은 웹 페이지, 네트워크 파일 공유 또는 cd-rom 등의 미디어에서 세 가지 방법으로 게시할 수 있습니다. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]응용 프로그램은 최종 사용자의 컴퓨터에 설치 하 고 컴퓨터가 오프 라인 상태인 경우에도 로컬로 실행 하거나, 최종 사용자의 컴퓨터에 아무것도 설치 하지 않고 온라인 전용 모드에서 실행할 수 있습니다. 자세한 내용은 [ClickOnce 배포 전략 선택](../deployment/choosing-a-clickonce-deployment-strategy.md)을 참조하세요.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램을 자동으로 업데이트할 수 있습니다. 사용 가능한 최신 버전을 확인 하 고 업데이트 된 파일을 자동으로 바꿀 수 있습니다. 개발자는 업데이트 동작을 지정할 수 있으며, 네트워크 관리자는 강제 업데이트 지정과 같은 업데이트 전략을 제어할 수 있습니다. 최종 사용자나 관리자가 업데이트를 이전 버전으로 롤백할 수도 있습니다. 자세한 내용은 [ClickOnce 업데이트 전략 선택](../deployment/choosing-a-clickonce-update-strategy.md)을 참조하세요.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]응용 프로그램이 격리 되어 있으므로 응용 프로그램을 설치 하거나 실행 하면 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 기존 응용 프로그램을 중단할 수 없습니다. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램은 자체 포함 됩니다. 각 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램은에 설치 되 고 보안 사용자별, 응용 프로그램 별 캐시에서 실행 됩니다. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램은 인터넷 또는 인트라넷 보안 영역에서 실행 됩니다. 필요한 경우 애플리케이션이 승격된 보안 권한을 요청할 수 있습니다. 자세한 내용은 [ClickOnce 애플리케이션 게시](../deployment/securing-clickonce-applications.md)를 참조하세요.  
  
## <a name="how-clickonce-security-works"></a>ClickOnce 보안 작동 방법  
 핵심 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 보안은 인증서, 코드 액세스 보안 정책 및 ClickOnce 신뢰 프롬프트를 기반으로 합니다.  
  
### <a name="certificates"></a>인증서  
 Authenticode 인증서는 응용 프로그램 게시자의 신뢰성을 확인 하는 데 사용 됩니다. ClickOnce는 응용 프로그램 배포에 Authenticode를 사용 하 여 설정 되 고 신뢰할 수 있는 원본에서 들어오는 합법적인 프로그램으로 유해한 프로그램을 portraying 하는 것을 방지 합니다. 필요에 따라 응용 프로그램 및 배포 매니페스트에 서명 하 여 파일이 훼손 되지 않았음을 증명 하는 인증서를 사용할 수도 있습니다. 자세한 내용은 [ClickOnce 및 Authenticode](../deployment/clickonce-and-authenticode.md)를 참조 하세요. 인증서를 사용 하 여 클라이언트 컴퓨터에서 신뢰할 수 있는 게시자 목록을 구성할 수도 있습니다. 신뢰할 수 있는 게시자에서 가져온 응용 프로그램은 사용자 개입 없이 설치할 수 있습니다. 자세한 내용은 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)을 참조하십시오.  
  
### <a name="code-access-security"></a>코드 액세스 보안  
 코드 액세스 보안은 보호 된 리소스에 대 한 코드의 액세스를 제한 하는 데 도움이 됩니다. 대부분의 경우 인터넷 또는 로컬 인트라넷 영역을 선택 하 여 사용 권한을 제한할 수 있습니다. **Projectdesigner** 의 **보안** 페이지를 사용 하 여 응용 프로그램에 적합 한 영역을 요청 합니다. 또한 제한 된 권한으로 응용 프로그램을 디버그 하 여 최종 사용자 환경을 에뮬레이트할 수 있습니다. 자세한 내용은 [ClickOnce 애플리케이션의 코드 액세스 보안](../deployment/code-access-security-for-clickonce-applications.md)을 참조하세요.  
  
### <a name="clickonce-trust-prompt"></a>ClickOnce 신뢰 프롬프트  
 응용 프로그램이 영역에서 허용 하는 것 보다 많은 권한을 요청 하는 경우 최종 사용자에 게 트러스트를 결정 하 라는 메시지가 표시 될 수 있습니다. 최종 사용자는 Windows Forms 응용 프로그램, Windows Presentation Foundation 응용 프로그램, 콘솔 응용 프로그램, XAML 브라우저 응용 프로그램 및 Office 솔루션과 같은 ClickOnce 응용 프로그램을 실행할 수 있는지 여부를 결정할 수 있습니다. 자세한 내용은 [방법: ClickOnce 신뢰 프롬프트 동작 구성](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)을 참조 하세요.  
  
## <a name="how-clickonce-deployment-works"></a>ClickOnce 배포 작동 방법  
 핵심 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포 아키텍처는 응용 프로그램 매니페스트 및 배포 매니페스트와 같은 두 가지 XML 매니페스트 파일을 기반으로 합니다. 파일은 ClickOnce 응용 프로그램이 설치 된 위치, 업데이트 방법 및 업데이트 된 시기를 설명 하는 데 사용 됩니다.  
  
### <a name="publishing-clickonce-applications"></a>ClickOnce 애플리케이션 게시  
 응용 프로그램 매니페스트는 응용 프로그램 자체에 대해 설명 합니다. 여기에는 어셈블리, 응용 프로그램을 구성 하는 종속성 및 파일, 필요한 권한 및 업데이트를 사용할 수 있는 위치가 포함 됩니다. 응용 프로그램 개발자는 Visual Studio의 게시 마법사 또는의 매니페스트 생성 및 편집 도구 (Mage.exe)를 사용 하 여 응용 프로그램 매니페스트를 만든 다음 [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] 자세한 내용은 [방법: 게시 마법사를 사용 하 여 ClickOnce 응용 프로그램 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)를 참조 하세요.  
  
 배포 매니페스트는 애플리케이션이 배포되는 방법을 기술합니다. 여기에는 응용 프로그램 매니페스트의 위치 및 클라이언트에서 실행 해야 하는 응용 프로그램의 버전이 포함 됩니다.  
  
### <a name="deploying-clickonce-applications"></a>ClickOnce 응용 프로그램 배포  
 작성된 배포 매니페스트는 배포 위치에 복사됩니다. 이러한 위치는 웹 서버, 네트워크 파일 공유 또는 CD와 같은 미디어일 수 있습니다. 응용 프로그램 매니페스트와 모든 응용 프로그램 파일은 배포 매니페스트에 지정 된 배포 위치에도 복사 됩니다. 이 위치는 배포 위치와 동일하거나 다른 위치일 수 있습니다. Visual Studio에서 **게시 마법사** 를 사용 하면 복사 작업이 자동으로 수행 됩니다.  
  
### <a name="installing-clickonce-applications"></a>ClickOnce 응용 프로그램 설치  
 배포 위치로 복사한 다음에는 최종 사용자가 웹 페이지 또는 폴더에 있는 배포 매니페스트 파일의 아이콘을 클릭하여 애플리케이션을 다운로드하고 설치할 수 있습니다. 대부분의 경우 최종 사용자에 게 설치를 확인 하는 간단한 대화 상자가 표시 됩니다. 그러면 설치가 진행 되 고 추가 작업 없이 응용 프로그램이 시작 됩니다. 응용 프로그램에 높은 권한이 필요 하거나 응용 프로그램이 신뢰할 수 있는 인증서로 서명 되지 않은 경우에도 대화 상자에서 설치를 계속 하기 전에 사용자에 게 권한을 부여 하 라는 메시지를 표시 합니다. ClickOnce 설치는 사용자 단위 이지만 관리자 권한이 필요한 필수 구성 요소가 있는 경우 권한 상승이 필요할 수 있습니다. 상승 된 권한에 대 한 자세한 내용은 [ClickOnce 응용 프로그램 보안](../deployment/securing-clickonce-applications.md)을 참조 하세요.  
  
 컴퓨터 또는 엔터프라이즈 수준에서 인증서를 신뢰할 수 있으므로 신뢰할 수 있는 인증서로 서명 된 ClickOnce 응용 프로그램을 자동으로 설치할 수 있습니다. 신뢰할 수 있는 인증서에 대 한 자세한 내용은 [신뢰할 수 있는 응용 프로그램 배포 개요](../deployment/trusted-application-deployment-overview.md)를 참조 하세요.  
  
 응용 프로그램을 사용자의 **시작** 메뉴와 **제어판**의 **프로그램 추가/제거** 그룹에 추가할 수 있습니다. 다른 배포 기술과 달리 **Program Files** 폴더 또는 레지스트리에는 아무것도 추가 되지 않으며 설치에는 관리 권한이 필요 하지 않습니다.  
  
> [!NOTE]
> 응용 프로그램이 **시작** 메뉴 및 **프로그램 추가/제거** 그룹에 추가 되는 것을 방지 하 여 웹 응용 프로그램 처럼 동작 하도록 할 수도 있습니다. 자세한 내용은 [ClickOnce 배포 전략 선택](../deployment/choosing-a-clickonce-deployment-strategy.md)을 참조하세요.  
  
### <a name="updating-clickonce-applications"></a>ClickOnce 응용 프로그램 업데이트  
 응용 프로그램 개발자는 응용 프로그램의 업데이트 된 버전을 만들 때 새 응용 프로그램 매니페스트를 생성 하 고 배포 위치에 파일을 복사 합니다. 즉, 일반적으로 원래 응용 프로그램 배포 폴더에 대 한 형제 폴더입니다. 관리자는 애플리케이션의 새 버전 위치를 가리키도록 배포 매니페스트를 업데이트합니다.  
  
> [!NOTE]
> Visual Studio의 **게시 마법사** 를 사용 하 여 이러한 단계를 수행할 수 있습니다.  
  
 배포 위치 외에도 배포 매니페스트에는 애플리케이션이 업데이트된 버전을 확인할 수 있는 업데이트 위치(웹 페이지 또는 네트워크 파일 공유)가 포함됩니다. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]**게시** 속성은 응용 프로그램이 업데이트를 확인 하는 시기 및 빈도를 지정 하는 데 사용 됩니다. 업데이트 동작은 배포 매니페스트에 지정 하거나 api를 통해 응용 프로그램의 사용자 인터페이스에서 사용자 선택 항목으로 표시 될 수 있습니다 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . 또한 **게시** 속성을 사용하여 업데이트를 강제로 수행하거나 이전 버전으로 롤백하도록 지정할 수도 있습니다. 자세한 내용은 [ClickOnce 업데이트 전략 선택](../deployment/choosing-a-clickonce-update-strategy.md)을 참조하세요.  
  
### <a name="third-party-installers"></a>타사 설치 관리자  
 ClickOnce 설치 관리자를 사용자 지정 하 여 응용 프로그램과 함께 타사 구성 요소를 설치할 수 있습니다. 재배포 가능 패키지 (.exe 또는 .msi 파일)가 있어야 하 고 언어 중립적인 제품 매니페스트와 언어별 패키지 매니페스트가 포함 된 패키지를 설명 해야 합니다. 자세한 내용은 [부트스트래퍼 패키지 만들기](../deployment/creating-bootstrapper-packages.md)를 참조 하세요.  
  
## <a name="clickonce-tools"></a>ClickOnce 도구  
 다음 표에서는 응용 프로그램 및 배포 매니페스트를 생성, 편집, 서명 및 다시 서명 하는 데 사용할 수 있는 도구를 보여 줍니다.  
  
|도구|설명|  
|----------|-----------------|  
|[프로젝트 디자이너, 보안 페이지](../ide/reference/security-page-project-designer.md)|응용 프로그램 및 배포 매니페스트에 서명 합니다.|  
|[프로젝트 디자이너, 게시 페이지](../ide/reference/publish-page-project-designer.md)|Visual Basic 및 Visual c # 응용 프로그램에 대 한 응용 프로그램 및 배포 매니페스트를 생성 하 고 편집 합니다.|  
|[Mage.exe(매니페스트 생성 및 편집 도구)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)|Visual Basic, Visual c # 및 Visual C++ 응용 프로그램에 대 한 응용 프로그램 및 배포 매니페스트를 생성 합니다.<br /><br /> 응용 프로그램 및 배포 매니페스트에 서명 하 고 다시 서명 합니다.<br /><br /> 일괄 처리 스크립트와 명령 프롬프트에서 실행할 수 있습니다.|  
|[MageUI.exe(매니페스트 생성 및 편집 도구, 그래픽 클라이언트)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)|응용 프로그램 및 배포 매니페스트를 생성 하 고 편집 합니다.<br /><br /> 응용 프로그램 및 배포 매니페스트에 서명 하 고 다시 서명 합니다.|  
|[GenerateApplicationManifest 작업](../msbuild/generateapplicationmanifest-task.md)|응용 프로그램 매니페스트를 생성 합니다.<br /><br /> MSBuild에서 실행할 수 있습니다. 자세한 내용은 [MSBuild 참조](../msbuild/msbuild-reference.md)를 참조하세요.|  
|[GenerateDeploymentManifest 작업](../msbuild/generatedeploymentmanifest-task.md)|배포 매니페스트를 생성 합니다.<br /><br /> MSBuild에서 실행할 수 있습니다. 자세한 내용은 [MSBuild 참조](../msbuild/msbuild-reference.md)를 참조하세요.|  
|[SignFile 작업](../msbuild/signfile-task.md)|응용 프로그램 및 배포 매니페스트에 서명 합니다.<br /><br /> MSBuild에서 실행할 수 있습니다. 자세한 내용은 [MSBuild 참조](../msbuild/msbuild-reference.md)를 참조하세요.|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|응용 프로그램을 개발 하 여 응용 프로그램 및 배포 매니페스트를 생성 합니다.|  
  
 다음 표에서는 이러한 브라우저에서 ClickOnce 응용 프로그램을 지 원하는 데 필요한 .NET Framework 버전을 보여 줍니다.  
  
|브라우저|.NET Framework 버전|  
|-------------|----------------------------|  
|Internet Explorer|2.0, 3.0, 3.5, 3.5 SP1, 4|  
|Firefox|2.0 SP1, 3.5 SP1, 4|  
  
## <a name="see-also"></a>관련 항목  
 [Windows Vista의 ClickOnce 배포](../deployment/clickonce-deployment-on-windows-vista.md)   
 [ClickOnce 응용 프로그램 게시](../deployment/publishing-clickonce-applications.md)   
 [ClickOnce 응용 프로그램 보안](../deployment/securing-clickonce-applications.md)   
 [ClickOnce를 사용 하 여 COM 구성 요소 배포](../deployment/deploying-com-components-with-clickonce.md)   
 [명령줄에서 ClickOnce 응용 프로그램 빌드](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [System.Deployment.Application을 사용하는 ClickOnce 애플리케이션 디버그](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)
