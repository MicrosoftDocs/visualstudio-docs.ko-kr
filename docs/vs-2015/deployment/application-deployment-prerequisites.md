---
title: 응용 프로그램 배포 필수 구성 요소 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, platform detection
- ClickOnce deployment, prerequisites
- ClickOnce deployment, dependencies
- prerequisites, ClickOnce
- dependencies, ClickOnce
ms.assetid: fc6e047e-ad94-44e8-8ff5-b6d1f4ca7735
caps.latest.revision: 53
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4945efddb91142ce04f5b117129428ec4a054fc3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842103"
---
# <a name="application-deployment-prerequisites"></a>애플리케이션 배포 필수 구성 요소
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

애플리케이션을 올바르게 설치 및 실행하려면 애플리케이션이 사용할 모든 구성 요소가 대상 컴퓨터에 이미 설치되어 있는지를 먼저 확인해야 합니다. 예를 들어 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 사용하여 만드는 대부분의 애플리케이션은 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]를 사용하므로 애플리케이션을 설치하기 전에 올바른 공용 언어 런타임 버전을 대상 컴퓨터에 설치해야 합니다.  
  
 필수 구성 요소 **대화 상자** 에서 이러한 필수 구성 요소를 선택 하 고 설치의 일부로 .NET Framework 및 기타 재배포 가능 패키지를 설치할 수 있습니다. 이러한 방식을 *부트스트래핑*이라고 합니다. 그런 다음 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Setup.exe 이라는 Windows 실행 프로그램을 생성 합니다 ( *부트스트래퍼*라고도 함). 부트스트래퍼는 애플리케이션을 실행하기 전에 이러한 필수 구성 요소를 설치합니다. 이러한 필수 구성 요소 선택에 대 한 자세한 내용은 [필수 구성 요소 대화 상자](../ide/reference/prerequisites-dialog-box.md)를 참조 하세요.  
  
 각 필수 구성 요소는 부트스트래퍼 패키지입니다. 부트스트래퍼 패키지는 필수 구성 요소를 설치해야 하는 방법을 설명하는 매니페스트 파일이 포함된 파일과 디렉터리 그룹입니다. 애플리케이션 필수 구성 요소가 **필수 구성 요소 대화 상자**에 나와 있지 않으면 사용자 지정 부트스트래퍼 패키지를 만들어 Visual Studio에 추가할 수 있습니다. 그런 다음, **필수 구성 요소 대화 상자**에서 해당 필수 구성 요소를 선택할 수 있습니다. 자세한 내용은 [부트스트래퍼 패키지 만들기](../deployment/creating-bootstrapper-packages.md)를 참조 하세요.  
  
 부트스트래핑은 ClickOnce 배포에 기본적으로 사용됩니다. ClickOnce 배포용으로 생성된 부트스트래퍼는 서명되어 있습니다. 모든 대상 컴퓨터에 올바른 구성 요소 버전이 이미 설치되어 있는 경우에 한해 구성 요소에 대해 부트스트래핑을 사용하지 않도록 설정할 수 있습니다.  
  
## <a name="bootstrapping-and-clickonce-deployment"></a>부트스트래핑 및 ClickOnce 배포  
 클라이언트 컴퓨터에 애플리케이션을 설치하기 전에 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]에서 클라이언트가 애플리케이션 매니페스트에 지정된 특정 요구 사항을 포함하는지를 검사합니다. 여기에는 다음이 포함됩니다.  
  
- 필요한 최소 버전의 공용 언어 런타임. 애플리케이션 매니페스트에서 어셈블리 종속성으로 지정합니다.  
  
- 애플리케이션에 필요한 Windows 운영 체제의 최소 버전. `<osVersionInfo>` 요소를 사용하여 애플리케이션 매니페스트에서 지정합니다. ( [ \<dependency> 요소](../deployment/dependency-element-clickonce-application.md)참조)  
  
- GAC(전역 어셈블리 캐시)에 미리 설치해야 하는 모든 어셈블리의 최소 버전. 어셈블리 매니페스트에서 어셈블리 종속성 선언을 통해 지정합니다.  
  
  [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 누락 된 필수 구성 요소를 검색할 수 있으며 부트스트래퍼를 사용 하 여 필수 구성 요소를 설치할 수 있습니다. 자세한 내용은 [방법: ClickOnce 응용 프로그램을 사용 하 여 필수 구성 요소 설치](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)를 참조 하세요.  
  
> [!NOTE]
> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 및 MageUI.exe와 같은 도구를 통해 생성된 매니페스트의 값을 변경하려면 텍스트 편집기에서 애플리케이션 매니페스트를 편집한 다음 애플리케이션 및 배포 매니페스트를 모두 다시 서명해야 합니다. 자세한 내용은 [How to: Re-sign Application and Deployment Manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md)을 참조하세요.  
  
 Visual Studio 및 ClickOnce를 사용하여 애플리케이션을 배포하는 경우 기본적으로 선택되는 부트스트래퍼 패키지는 솔루션의 .NET Framework 버전에 따라 달라집니다. 그러나 대상 .NET Framework 버전을 변경하는 경우에는 **필수 구성 요소 대화 상자**에서 옵션을 수동으로 업데이트해야 합니다.  
  
|대상 .NET Framework|선택되는 부트스트래퍼 패키지|  
|---------------------------|------------------------------------|  
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Windows Installer 3.1|  
|.NET Framework 4|.NET Framework 4<br /><br /> Windows Installer 3.1|  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포에서 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 게시 마법사를 통해 생성되는 Publish.htm 페이지는 애플리케이션만 설치하는 링크 또는 애플리케이션 및 부트스트래핑된 구성 요소를 모두 설치하는 링크를 가리킵니다.  
  
 Visual Studio의 게시 페이지 또는 ClickOnce 게시 마법사를 사용하여 부트스트래퍼를 생성하면 Setup.exe가 자동으로 서명됩니다. 그러나 고객의 인증서를 사용하여 부트스트래퍼에 서명을 하려는 경우에는 나중에 이 파일에 서명할 수 있습니다.  
  
## <a name="bootstrapping-and-msbuild"></a>부트스트래핑 및 MSBuild  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 사용하지 않고 명령줄에서 애플리케이션을 컴파일하는 경우에는 MSBuild(Microsoft Build Engine) 작업을 사용하여 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 부트스트래핑 애플리케이션을 만들 수 있습니다. 자세한 내용은 [Generatebootstrapper 작업](../msbuild/generatebootstrapper-task.md)을 참조 하세요.  
  
 부트스트래핑을 수행하는 대신 Microsoft Systems Management Server(SMS) 등의 전자 소프트웨어 배포 시스템을 사용하여 구성 요소를 미리 배포할 수도 있습니다.  
  
## <a name="bootstrapper-setupexe-command-line-arguments"></a>부트스트래퍼(Setup.exe) 명령줄 인수  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 및 MSBuild 작업을 통해 생성되는 Setup.exe는 다음과 같은 소수의 명령줄 인수 집합을 지원합니다. 부트스트래핑 애플리케이션에 제공되는 이러한 인수 이외의 모든 인수는 애플리케이션 설치 관리자로 전달됩니다.  
  
 부트스트래퍼 옵션을 변경하는 경우에는 서명되지 않은 부트스트래퍼를 변경한 다음 나중에 부트스트래퍼 파일에 서명을 해야 합니다.  
  
|명령줄 인수|Description|  
|---------------------------|-----------------|  
|**-?, -h, -help**|도움말 대화 상자를 표시합니다.|  
|**-url, -componentsurl**|이 설치를 위한 저장된 URL 및 구성 요소 URL을 표시합니다.|  
|**-url =**`location`|Setup.exe가 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션을 찾을 URL을 설정합니다.|  
|**-componentsurl=** `location`|Setup.exe가 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 등의 종속성을 찾을 URL을 설정합니다.|  
|**-homesite=** `true` **&#124;** `false`|`true`인 경우 공급 업체 사이트의 기본 위치에서 종속성을 다운로드 합니다. 이렇게 하면 **-componentsurl** 설정이 재정의 됩니다. `false`인 경우 **-componentsurl**에서 지정한 URL에서 종속성을 다운로드 합니다.|  
  
## <a name="operating-system-support"></a>운영 체제 지원  
 기능이 제한되는 저가형 유지 관리 서버 환경을 제공하는 Windows Server 2008 Server Core 또는 Windows Server 2008 R2 Server Core에서는 Visual Studio 부트스트래퍼가 지원되지 않습니다. 예를 들어 Server Core 설치 옵션을 사용하는 경우 .NET Framework 3.5 Server Core 프로필만 지원되므로 전체 .NET Framework를 사용하는 Visual Studio 기능을 실행할 수 없습니다.  
  
## <a name="see-also"></a>참고 항목  
 [ClickOnce 배포 전략 선택](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [ClickOnce 보안 및 배포](../deployment/clickonce-security-and-deployment.md)
