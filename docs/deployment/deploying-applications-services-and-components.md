---
title: 배포 소개
description: Visual Studio에서 앱을 배포하기 위한 옵션에 대해 알아봅니다.
ms.custom: mvc
ms.date: 01/29/2019
ms.topic: quickstart
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- .NET applications, deploying
- components [Visual Studio], deploying
- installers
- publishing
- deploying applications [Visual Studio]
- deploying applications [Visual Studio], about deploying applications
- components [.NET Framework], deploying
ms.assetid: 63fcdd5b-2e54-4210-9038-65bc23167725
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8eeb44d08f4b966bed4aef526c12263bdd1a2b77
ms.sourcegitcommit: 1803a67b516f67b209d8f4cf147314e604ef1927
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89641666"
---
# <a name="first-look-at-deployment-in-visual-studio"></a>먼저 Visual Studio의 배포 살펴보기

다른 컴퓨터, 디바이스, 서버 또는 클라우드에 설치하기 위해 애플리케이션, 서비스 또는 구성 요소를 배포할 수 있습니다. Visual Studio에서 필요한 배포 유형에 적합한 방법을 선택할 수 있습니다. (여러 앱 유형은 명령 줄 배포 또는 여기에 설명되지 않은 NuGet 같은 기타 배포 도구를 지원합니다.)

단계별 배포 지침은 빠른 시작 및 자습서를 참조하세요. 배포 옵션의 개요는 [내게 적합한 게시 옵션은?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)을 참조하세요.

## <a name="deploy-to-local-folder"></a>로컬 폴더에 배포

로컬 폴더에 배포는 일반적으로 테스트에 또는 다른 도구가 최종 배포에 사용되는 스테이징된 배포를 시작하는 데 사용됩니다.

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python** 및 **.NET Core**: 게시 도구를 사용하여 로컬 폴더에 배포합니다. 사용 가능한 정확한 옵션은 앱 형식에 따라 달라집니다. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **게시**를 선택합니다. (모든 게시 프로필을 이전에 구성하지 않은 경우 **새 프로필 만들기**를 클릭해야 합니다.) 다음으로 **폴더**를 선택합니다. 자세한 내용은 [로컬 폴더에 배포](quickstart-deploy-to-local-folder.md)를 참조하세요.

    ![게시 선택](../deployment/media/quickstart-publish.png)

- **Windows 데스크톱** ClickOnce 배포를 사용하여 Windows 데스크톱 애플리케이션을 게시할 수 있습니다. 이렇게 하면 사용자가 클릭 한 번으로 애플리케이션을 설치할 수 있습니다. 자세한 내용은 [ClickOnce를 사용하여 데스크톱 앱 배포](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)(C# 및 Visual Basic)를 참조하세요. C++/CLR의 경우 [ClickOnce를 사용하여 네이티브 앱 배포](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) 또는 C/C++의 경우 [설치 프로젝트를 사용하여 네이티브 앱 배포](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project)를 참조하세요.

## <a name="publish-to-azure"></a>Azure에 게시

- **ASP.NET**, **ASP.NET Core**, **Python** 및 **Node.js.** : 다음 방법 중 하나를 사용하여 Azure App Service 또는 Azure App Service Linux(컨테이너 사용)에 게시합니다.

  - 연속(또는 자동) 배포 앱의 경우 Azure DevOps를 [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops)과 함께 사용합니다.

  - 일회성(또는 수동) 배포 앱의 경우 Visual Studio의 **게시** 도구를 사용합니다.

  서버의 사용자 지정된 구성을 더 많이 제공하는 배포의 경우 **게시** 도구를 사용하여 Azure Virtual Machine에 앱을 배포할 수도 있습니다.

  **게시** 도구를 사용하려면 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **게시**를 선택합니다. (모든 게시 프로필을 이전에 구성한 경우 **새 프로필 만들기**를 클릭해야 합니다.) 게시 대화 상자에서 **App Service** 또는 **Azure Virtual Machines** 중 하나를 선택한 다음, 구성 단계를 따릅니다.

  ![Azure App Service 선택](../deployment/media/quickstart-publish-azure-new.png "Azure App Service 선택")

  Visual Studio 2017 버전 15.7부터 ASP.NET Core 앱을 **Linux용 App Service**에 배포할 수 있습니다.

  Python 앱은 [Python - Azure App Service에 게시](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)도 참조하세요.

  간략한 소개는 [Azure에 게시](quickstart-deploy-to-azure.md) 및 [Linux에 게시](quickstart-deploy-to-linux.md)를 참조하세요. 또한 [Azure에 ASP.NET Core 앱 게시](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)도 참조하세요. Git를 사용한 배포는 [Git를 사용하여 Azure에 ASP.NET Core 연속 배포](/aspnet/core/publishing/azure-continuous-deployment)를 참조하세요.

  Azure App Service에서 Visual Studio로 게시 프로필을 가져오는 방법에 대한 자세한 내용은 [게시 설정 가져오기 및 Azure에 배포](../deployment/tutorial-import-publish-settings-azure.md)를 참조하세요.

  > [!NOTE]
  > Azure 계정이 없는 경우 [여기에 등록](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio)할 수 있습니다.

## <a name="publish-to-web-or-deploy-to-network-share"></a>웹에 게시 또는 네트워크 공유에 배포

- **ASP.NET**, **ASP.NET Core**, **Node.js.** 및 **Python**: FTP 또는 Web Deploy를 사용하여 웹 사이트에 배포하려면 게시 도구를 사용할 수 있습니다. 자세한 내용은 [웹 사이트에 배포](quickstart-deploy-to-a-web-site.md)를 참조하세요.

    솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **게시**를 선택합니다. (모든 게시 프로필을 이전에 구성한 경우 **새 프로필 만들기**를 클릭해야 합니다.) 게시 도구에서 원하는 옵션을 선택하고 구성 단계를 따릅니다.

    ![IIS 선택](../deployment/media/quickstart-publish-iis.png)

    Visual Studio에서 게시 프로필을 가져오는 방법에 대한 자세한 내용은 [게시 설정 가져오기 및 IIS에 배포](../deployment/tutorial-import-publish-settings-iis.md)를 참조하세요.

    ASP.NET 애플리케이션 및 서비스는 여러 가지 다른 방법으로 배포할 수 있습니다. 자세한 내용은 [ASP.NET 웹 애플리케이션 및 서비스 배포](/aspnet/overview/deployment)를 참조하세요.

- **Windows 데스크톱** ClickOnce 배포를 사용하여 웹 서버 또는 네트워크 파일 공유에 Windows 데스크톱 애플리케이션을 게시할 수 있습니다. 이렇게 하면 사용자가 클릭 한 번으로 애플리케이션을 설치할 수 있습니다. 자세한 내용은 [ClickOnce를 사용하여 데스크톱 앱 배포](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)(C# 및 Visual Basic)를 참조하세요. C++/CLR의 경우 [ClickOnce를 사용하여 네이티브 앱 배포](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) 또는 C/C++의 경우 [설치 프로젝트를 사용하여 네이티브 앱 배포](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project)를 참조하세요.

## <a name="publish-to-microsoft-store"></a>Microsoft Store에 게시

Visual Studio에서 Microsoft Store에 배포하기 위한 앱 패키지를 만들 수 있습니다.

- **UWP**: 메뉴 항목을 사용하여 앱을 패키지 및 배포할 수 있습니다. 자세한 내용은 [Visual Studio를 사용하여 UWP 앱 패키지](/windows/uwp/packaging/packaging-uwp-apps)를 참조하세요.

    ![앱 패키지 만들기](../deployment/media/feature-tour-create-app-package.png)

- **Windows 데스크톱**: Visual Studio 2017 버전 15.4부터 데스크톱 브리지를 사용하여 Microsoft Store에 배포할 수 있습니다. 이 작업을 수행하려면 Windows 애플리케이션 패키징 프로젝트를 만들어 시작합니다. 자세한 내용은 [Microsoft Store의 데스크톱 앱 패키지(데스크톱 브리지)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net)를 참조하세요.

    ![데스크톱 브리지](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>디바이스에 배포(UWP)

디바이스에서 테스트를 위해 UWP 앱을 배포하는 경우 [Visual Studio의 원격 머신에서 UWP 앱 실행](../debugger/run-windows-store-apps-on-a-remote-machine.md)을 참조하세요.

## <a name="create-an-installer-package-windows-desktop"></a>설치 관리자 패키지(Windows 데스크톱) 만들기

[ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)가 제공할 수 있는 것보다 더 복잡한 데스크톱 애플리케이션의 설치가 필요한 경우 Windows Installer 패키지(MSI 또는 EXE 설치 파일) 또는 사용자 지정 부트스트래퍼를 만들 수 있습니다.

- [WiX Toolset Visual Studio 2017 확장](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)을 사용하여 MSI 기반 설치 관리자 패키지를 만들 수 있습니다. 이는 명령줄 도구 세트입니다.

- Flexera Software의 [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements)를 사용하여 MSI 또는 EXE 설치 관리자 패키지를 만들 수 있습니다. InstallShield는 Visual Studio 2017 및 이후 버전에서 사용할 수 있습니다(Community Edition은 지원되지 않음). 

  > [!NOTE]
  > InstallShield Limited Edition은 더 이상 Visual Studio에 포함되지 않으며 Visual Studio 2017 및 이후 버전에서 지원되지 않습니다. 추후 가용성은 [Flexera Software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio)에서 확인하세요.

- 설치 프로젝트(vdproj)를 사용하여 MSI 또는 EXE 설치 관리자 패키지를 만들 수 있습니다. 이 옵션을 사용하려면 [Visual Studio 설치 관리자 프로젝트 확장](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview)을 설치합니다.

- 부트스트래퍼로 알려진 일반 설치 관리자를 구성하여 데스크톱 애플리케이션의 필수 구성 요소를 설치할 수도 있습니다. 자세한 내용은 [애플리케이션 배포 필수 구성 요소](../deployment/application-deployment-prerequisites.md)를 참조하세요.

## <a name="deploy-to-test-lab"></a>테스트 랩에 배포

가상 환경에 애플리케이션을 배포하여 더욱 정교한 개발과 테스트를 사용하도록 설정할 수 있습니다. 자세한 내용은 [랩 환경 테스트](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md)를 참조하세요.

## <a name="continuous-deployment"></a>연속 배포

Azure Pipelines를 사용하여 앱의 연속 배포를 사용하도록 설정할 수 있습니다. 자세한 내용은 [Azure Pipelines](/azure/devops/pipelines/index?view=vsts) 및 [Azure에 배포](/azure/devops/deploy-azure/index?view=vsts)를 참조하세요.

## <a name="deploy-a-sql-database"></a>SQL 데이터베이스 배포

- [대상 플랫폼 변경 및 데이터베이스 프로젝트 게시(SSDT(SQL Server Data Tools))](/sql/ssdt/how-to-change-target-platform-and-publish-a-database-project)

- [Analysis Services 프로젝트 배포(SSAS)](/sql/analysis-services/multidimensional-tutorial/lesson-2-5-deploying-an-analysis-services-project)

- [Integration Services(SSIS) 프로젝트 및 패키지 배포](/sql/integration-services/packages/deploy-integration-services-ssis-projects-and-packages)

- [빌드 및 로컬 데이터베이스에 배포](/sql/ssdt/how-to-build-and-deploy-to-a-local-database)

## <a name="deployment-for-other-app-types"></a>다른 앱 형식의 배포

| 앱 형식 | 배포 시나리오 | 링크 |
| --- | --- | --- |
| **Office 앱** | Visual Studio에서 Office용 추가 기능을 게시할 수 있습니다. | [Office 추가 기능 게시 및 배포](https://dev.office.com/docs/add-ins/publish/publish) |
| **WCF 또는 OData 서비스** | 웹 서버에 배포한 WCF RIA 서비스를 다른 애플리케이션에서 사용할 수 있습니다. | [WCF Data Services 개발 및 배포](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch는 Visual Studio 2017부터 더 이상 지원되지 않지만, Visual Studio 2015 및 이전 버전에서는 아직 배포할 수 있습니다. | [LightSwitch 애플리케이션 배포](/previous-versions/ff872288(v=vs.140)) |

## <a name="next-steps"></a>다음 단계

이 자습서에서는 서로 다른 애플리케이션에 대한 배포 옵션을 간략하게 살펴봤습니다.

> [!div class="nextstepaction"]
> [내게 적합한 게시 옵션은?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)