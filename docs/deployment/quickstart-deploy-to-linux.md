---
title: Linux의 App Service에 게시
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 1e05862aa57c24bfa8f17d551762054278dd6e52
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "72806868"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Visual Studio를 사용하여 Linux의 App Service에 ASP.NET Core 앱 게시

Visual Studio 2017 버전 15.7부터 다음 방법 중 하나를 사용하여 ASP.NET Core 앱을 Azure App Service Linux(컨테이너 사용)에 게시할 수 있습니다.

* 연속(또는 자동) 배포 앱의 경우 Azure DevOps를 [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops)과 함께 사용합니다.

* 일회성(또는 수동) 배포 앱의 경우 Visual Studio의 **게시** 도구를 사용하여 ASP.NET Core 앱을 Linux용 App Service(컨테이너 사용)에 게시합니다.

이 문서에서는 일회성 배포를 위해 **게시** 도구를 사용하는 방법을 설명합니다.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-app-service-on-linux"></a>Linux의 App Service에 게시

1. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **게시**를 선택합니다(또는 **빌드** > **게시** 메뉴 항목 사용).

    ![솔루션 탐색기의 프로젝트 상황에 맞는 메뉴에서 게시 명령](../deployment/media/quickstart-publish.png "게시 선택")

1. 게시 프로필을 이전에 구성한 경우 **게시** 창이 나타납니다. 이 경우 **새 프로필 만들기**를 선택합니다.

1. **게시 대상 선택** 대화 상자에서 **App Service Linux**를 선택합니다.

    ![Azure App Service 선택](../deployment/media/quickstart-publish-linux.png "Azure App Service 선택")

1. **게시**를 선택합니다. **App Service 만들기** 대화 상자가 나타납니다. 필요한 경우 Azure 계정으로 로그인하면 기본 앱 서비스 설정에서 필드를 채웁니다.

    ![App Service 만들기](../deployment/media/quickstart-publish-settings-app-service-linux.png "Azure App Service 만들기")

1. **만들기**를 선택합니다. Visual Studio는 Azure App Service에 앱을 배포하고, 브라우저에 웹앱이 로드됩니다. 프로젝트 속성 **게시** 창은 사이트 URL 및 기타 세부 정보를 표시합니다.

    ![프로필 요약을 표시하는 게시 속성 창](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>리소스 정리

이전 단계에서 Azure 리소스를 리소스 그룹에 만들었습니다. 이러한 리소스가 나중에 필요하지 않을 경우에는 리소스 그룹을 삭제하여 해당 리소스를 삭제할 수 있습니다.
Azure Portal의 왼쪽 메뉴에서 **리소스 그룹**을 선택한 다음 **myResourceGroup**을 선택합니다.
리소스 그룹 페이지에서 나열된 리소스가 삭제하려는 리소스인지 확인합니다.
**삭제**를 선택하고, 텍스트 상자에서 **myResourceGroup**을 입력한 다음, **삭제**를 선택합니다.

## <a name="next-steps"></a>다음 단계

이 빠른 시작에서는 Visual Studio를 사용하여 Linux의 App Service에 배포를 위해 게시 프로필을 만드는 방법을 알아보았습니다. Azure를 사용하여 Linux에 게시에 대한 자세한 정보를 확인할 수 있습니다.

> [!div class="nextstepaction"]
> [Linux App Service](/azure/app-service/containers/app-service-linux-intro)
