---
title: 게시 설정을 가져와서 Azure에 게시
description: Visual Studio에서 Azure App Service로 애플리케이션을 배포하기 위한 게시 프로필 만들기 및 가져오기
ms.date: 05/07/2018
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd040b613a5b982050d651f341456c5fafc2954b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "65679182"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Visual Studio에서 게시 설정을 가져와서 Azure App Service에 애플리케이션 게시

**게시** 도구를 사용하여 게시 설정을 가져온 다음, 앱을 배포할 수 있습니다. 이 문서에서는 Azure App Service에 대한 게시 설정을 사용하지만 비슷한 단계를 사용하여 [IIS](../deployment/tutorial-import-publish-settings-iis.md)에서 게시 설정을 가져올 수 있습니다. 일부 시나리오에서는 게시 설정 프로필을 사용하는 것이 Visual Studio를 설치할 때마다 서비스에 대한 배포를 수동으로 구성하는 것보다 빠를 수 있습니다.

이러한 단계는 Visual Studio에서 ASP.NET, ASP.NET Core 및 .NET Core 앱에 적용됩니다. [Python](../python/publishing-python-web-applications-to-azure-from-visual-studio.md) 앱에 대한 게시 설정을 가져올 수도 있습니다.

이 자습서에서는 다음을 수행합니다.

> [!div class="checklist"]
> * Azure App Service에서 게시 설정 파일 생성
> * Visual Studio로 게시 설정 파일 가져오기
> * 앱을 Azure App Service에 배포

게시 설정 파일(*\*.publishsettings*)은 Visual Studio에서 생성되는 게시 프로필(*\*.pubxml*)과 다릅니다. 게시 설정 파일은 Azure App Service에서 만들어진 다음, Visual Studio로 가져올 수 있습니다.

> [!NOTE]
> Visual Studio의 한 설치에서 다른 설치로 Visual Studio 게시 프로필(*\*.pubxml* 파일)을 복사해야 하는 경우 관리되는 프로젝트 형식에 대한 *\<<projectname\>\Properties\PublishProfiles* 폴더에서 게시 프로필, *\\profilename\>.pubxml*을 찾을 수 있습니다. 웹 사이트의 경우 *\App_Data* 폴더 아래에서 확인합니다. 게시 프로필은 MSBuild XML 파일입니다.

## <a name="prerequisites"></a>사전 요구 사항

::: moniker range=">=vs-2019"

* **ASP.NET 및 웹 개발** 워크로드와 Visual Studio 2019가 설치되어 있어야 합니다.

    아직 Visual Studio를 설치하지 않은 경우  [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads/)  페이지로 이동하여 체험용으로 설치합니다.
::: moniker-end

::: moniker range="vs-2017"

* **ASP.NET 및 웹 개발** 워크로드와 Visual Studio 2017이 설치되어 있어야 합니다.

    아직 Visual Studio를 설치하지 않은 경우  [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads/)  페이지로 이동하여 체험용으로 설치합니다.
::: moniker-end

* Azure App Service를 만듭니다. 자세한 지침은 [Visual Studio를 사용하여 Azure에 ASP.NET Core 웹앱 배포](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)를 참조하세요.

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Visual Studio에서 새로운 ASP.NET 프로젝트 만들기

1. Visual Studio를 실행하는 컴퓨터에서 새 프로젝트를 선택합니다.

    올바른 템플릿을 선택합니다. 이 예제에서 **ASP.NET 웹 애플리케이션(.NET Framework)** 또는 (C# 전용인 경우) **ASP.NET Core 웹 애플리케이션**을 선택한 다음, **확인**을 클릭합니다.

    지정된 프로젝트 템플릿이 표시되지 않으면 **새 프로젝트** 대화 상자의 왼쪽 창에서 **Open Visual Studio 설치 관리자** 링크를 클릭합니다. Visual Studio 설치 관리자가 시작됩니다. **ASP.NET 및 웹 개발** 워크로드를 설치합니다.

    선택한 프로젝트 템플릿(ASP.NET 또는 ASP.NET Core)은 웹 서버에 설치된 ASP.NET의 버전과 일치해야 합니다.

1. **MVC**(.NET Framework) 또는 **웹 애플리케이션(Model-View-Controller)**(.NET Core용)을 선택하고, **인증 안 함**이 선택되었는지 확인한 다음, **확인**을 클릭합니다.

1. **MyWebApp**과 같은 이름을 입력하고 **확인**을 클릭합니다.

    Visual Studio가 프로젝트를 만듭니다.

1. **빌드** > **솔루션 빌드**를 선택하여 프로젝트를 빌드합니다.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Azure App Service에서 게시 설정 파일 만들기

1. Azure Portal에서 Azure App Service를 엽니다.

1. **게시 프로필 가져오기**를 클릭하고 프로필을 로컬로 저장합니다.

    ![게시 프로필 가져오기](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    *.publishsettings* 파일 확장명이 있는 파일이 저장한 위치에서 생성되었습니다. 다음 코드는 파일의 일부 예제를 보여줍니다(보다 읽기 쉬운 형식으로).

    ```xml
    <publishData>
      <publishProfile
        profileName="DeployASPDotNetCore - Web Deploy"
        publishMethod="MSDeploy"
        publishUrl="deployaspdotnetcore.scm.azurewebsites.net:443"
        msdeploySite="DeployASPDotNetCore"
        userName="$DeployASPDotNetCore"
        userPWD="abcdefghijklmnopqrstuzwxyz"
        destinationAppUrl="http://deployaspdotnetcore20180508031824.azurewebsites.net"
        SQLServerDBConnectionString=""
        mySQLDBConnectionString=""
        hostingProviderForumLink=""
        controlPanelLink="http://windows.azure.com"
        webSystem="WebSites">
        <databases />
      </publishProfile>
    </publishData>
    ```

    일반적으로 이전 *.publishsettings 파일은 Visual Studio에서 사용할 수 있는 두 개의 게시 프로필을 포함합니다(웹 배포를 사용하여 배포하는 것 하나, FTP를 사용하여 배포하는 것 하나). 위의 코드는 웹 배포 프로필을 보여줍니다. 나중에 프로필을 가져올 때 두 프로필을 모두 가져옵니다.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio에서 게시 설정 가져오기 및 배포

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>다음 단계

이 자습서에서는 게시 설정 파일을 생성하고, Visual Studio로 가져오고, Azure App Service에 ASP.NET 앱을 배포했습니다. Visual Studio에서 게시 옵션의 개요를 확인할 수 있습니다.

> [!div class="nextstepaction"]
> [배포 소개](../deployment/deploying-applications-services-and-components.md)
