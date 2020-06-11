---
title: 게시 설정을 가져와서 IIS에 게시
description: Visual Studio에서 IIS로 애플리케이션을 배포하기 위한 게시 프로필 만들기 및 가져오기
ms.date: 05/06/2020
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b18d1b123e32807575ac2c6601166891d6c25be
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183303"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Visual Studio에서 게시 설정을 가져와서 IIS에 애플리케이션 게시

**게시** 도구를 사용하여 게시 설정을 가져온 다음, 앱을 배포할 수 있습니다. 이 문서에서는 IIS에 대한 게시 설정을 사용하지만 비슷한 단계를 사용하여 [Azure App Service](../deployment/tutorial-import-publish-settings-azure.md)에서 게시 설정을 가져올 수 있습니다. 일부 시나리오에서는 게시 설정 프로필을 사용하는 것이 Visual Studio를 설치할 때마다 IIS에 대한 배포를 수동으로 구성하는 것보다 빠를 수 있습니다.

이러한 단계는 Visual Studio에서 ASP.NET, ASP.NET Core 및 .NET Core 앱에 적용됩니다.

이 자습서에서 다음을 수행합니다.

> [!div class="checklist"]
> * 게시 설정 파일을 생성할 수 있도록 IIS 구성
> * 게시 설정 파일 만들기
> * Visual Studio로 게시 설정 파일 가져오기
> * IIS에 앱 배포

게시 설정 파일( *\*.publishsettings*)은 Visual Studio에서 생성되는 게시 프로필( *\*.pubxml*)과 다릅니다. 게시 설정 파일은 IIS 또는 Azure App Service에서 만들어지거나 수동으로 만들어질 수 있습니다. 그런 다음, Visual Studio로 가져올 수 있습니다.

> [!NOTE]
> Visual Studio의 한 설치에서 다른 설치로 Visual Studio 게시 프로필(\*.pubxml 파일)을 복사해야 하는 경우 관리형 프로젝트 형식에 대한 *\\<projectname\>\Properties\PublishProfiles* 폴더에서 게시 프로필 *\<profilename\>.pubxml*을 찾을 수 있습니다. 웹 사이트의 경우 *\App_Data* 폴더 아래에서 확인합니다. 게시 프로필은 MSBuild XML 파일입니다.

## <a name="prerequisites"></a>사전 요구 사항

::: moniker range=">=vs-2019"

* **ASP.NET 및 웹 개발** 워크로드와 Visual Studio 2019가 설치되어 있어야 합니다.

    아직 Visual Studio를 설치하지 않은 경우  [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads/)  페이지로 이동하여 체험용으로 설치합니다.
::: moniker-end

::: moniker range="vs-2017"

* **ASP.NET 및 웹 개발** 워크로드와 Visual Studio 2017이 설치되어 있어야 합니다.

    아직 Visual Studio를 설치하지 않은 경우  [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads/)  페이지로 이동하여 체험용으로 설치합니다.
::: moniker-end

* 서버에서 Windows Server 2012, Windows Server 2016 또는 Windows Server 2019를 실행하고 [IIS 웹 서버 역할](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)이 올바르게 설치되어 있어야 합니다(게시 설정 파일( *\*.publishsettings*)을 생성하는 데 필요함). ASP.NET 4.5 또는 ASP.NET Core도 서버에 설치해야 합니다. ASP.NET 4.5를 설정하려면 [ASP.NET 3.5 및 ASP.NET 4.5를 사용하는 IIS 8.0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)을 참조하세요. ASP.NET Core를 설정하려면 [IIS가 있는 Windows에서 ASP.NET Core 호스팅](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)을 참조하세요. ASP.NET Core의 경우 이 문서에 설명된 대로 **관리 코드 없음**을 사용하도록 애플리케이션 풀을 구성해야 합니다.

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Visual Studio에서 새로운 ASP.NET 프로젝트 만들기

1. Visual Studio를 실행하는 컴퓨터에서 새 프로젝트를 선택합니다.

    올바른 템플릿을 선택합니다. 이 예제에서 **ASP.NET 웹 애플리케이션(.NET Framework)** 또는 (C# 전용인 경우) **ASP.NET Core 웹 애플리케이션**을 선택한 다음, **확인**을 클릭합니다.

    지정된 프로젝트 템플릿이 표시되지 않으면 **새 프로젝트** 대화 상자의 왼쪽 창에서 **Open Visual Studio 설치 관리자** 링크를 클릭합니다. Visual Studio 설치 관리자가 시작됩니다. **ASP.NET 및 웹 개발** 워크로드를 설치합니다.

    선택한 프로젝트 템플릿(ASP.NET 또는 ASP.NET Core)은 웹 서버에 설치된 ASP.NET의 버전과 일치해야 합니다.

1. **MVC**(.NET Framework) 또는 **웹 애플리케이션(Model-View-Controller)** (.NET Core용)을 선택하고, **인증 안 함**이 선택되었는지 확인한 다음, **확인**을 클릭합니다.

1. **MyWebApp**과 같은 이름을 입력하고 **확인**을 클릭합니다.

    Visual Studio가 프로젝트를 생성합니다.

1. **빌드** > **솔루션 빌드**를 선택하여 프로젝트를 빌드합니다.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Windows Server에서 웹 배포 설치 및 구성

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Windows Server의 IIS에서 게시 설정 파일 만들기

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio에서 게시 설정 가져오기 및 배포

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

앱을 성공적으로 배포한 후 자동으로 시작해야 합니다. Visual Studio에서 시작되지 않는 경우 IIS에서 앱을 시작합니다. ASP.NET Core의 경우 **DefaultAppPool**에 대한 애플리케이션 풀 필드가 **관리 코드 없음**으로 설정되었는지 확인해야 합니다.

## <a name="next-steps"></a>다음 단계

이 자습서에서는 게시 설정 파일을 생성하고, Visual Studio로 가져오고, IIS에 ASP.NET 앱을 배포했습니다. Visual Studio에서 기타 게시 옵션의 개요를 확인할 수 있습니다.

> [!div class="nextstepaction"]
> [배포 소개](../deployment/deploying-applications-services-and-components.md)
