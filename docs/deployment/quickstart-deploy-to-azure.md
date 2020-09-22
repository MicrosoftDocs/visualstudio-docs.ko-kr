---
title: Azure App Service에 게시
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 60b3d471191f58a5eb612d9942b72c9d5e90e8af
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036420"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Visual Studio를 사용하여 Azure App Service에 웹앱 게시

ASP.NET, ASP.NET Core, Node.js 및 .NET Core 앱의 경우, 다음 방법 중 하나를 사용하여 Azure App Service 또는 Azure App Service Linux(컨테이너 사용)에 게시합니다.

* 연속(또는 자동) 배포 앱의 경우 Azure DevOps를 [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops)과 함께 사용합니다.

* 일회성(또는 수동) 배포 앱의 경우 Visual Studio의 **게시** 도구를 사용하여 ASP.NET, ASP.NET Core, Node.js 및 .NET Core 앱을 Azure App Service 또는 [Linux용 App Service](../deployment/quickstart-deploy-to-linux.md)(컨테이너 사용)에 배포합니다. Python 앱의 경우 [Python - Azure App Service에 게시](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)의 단계를 따릅니다.

이 문서에서는 일회성 배포를 위해 **게시** 도구를 사용하는 방법을 설명합니다.

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service-on-windows"></a>Windows의 Azure App Service에 게시

1. 솔루션 탐색기에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **게시**를 선택합니다(또는 **빌드** > **게시** 메뉴 항목 사용).

    ![솔루션 탐색기의 프로젝트 상황에 맞는 메뉴에서 게시 명령](../deployment/media/quickstart-publish.png "게시 선택")

1. 게시 프로필을 이전에 구성한 경우 **게시** 창이 나타납니다. **새로 만들기**를 선택합니다.

1. **게시** 창에서 **Azure**를 선택합니다.

    ![게시 대상 선택](../deployment/media/quickstart-publish-azure-new.png)

1. **Azure App Service(Windows)** 를 선택하고 **다음**을 선택합니다.

    ![Azure App Service on Linux 선택](../deployment/media/quickstart-publish-windows-select-azure-service.png)

1. 필요한 경우 Azure 계정으로 로그인합니다. **새 Azure App Service 만들기...** 를 선택합니다.

    ![Azure App Service의 새 인스턴스를 만드는 링크](../deployment/media/quickstart-publish-windows-create-new-link.png)

1. **Azure App Service 만들기(Windows)** 대화 상자에서 **앱 이름**, **리소스 그룹** 및 **App Service 계획** 입력 필드가 채워집니다. 이러한 이름을 유지하거나 변경할 수 있습니다. 준비가 되면 **만들기**를 선택합니다.

    ![Azure App Service 선택](../deployment/media/quickstart-publish-windows-create-new-dialog.png)

1. **게시** 대화 상자에서 새로 만든 인스턴스가 자동으로 선택됩니다. 준비가 되면 **완료**를 선택합니다.

    ![Azure App Service 선택](../deployment/media/quickstart-publish-windows-select-instance.png)

1. **게시**를 선택합니다. Visual Studio는 Azure App Service에 앱을 배포하고, 브라우저에 웹앱이 로드됩니다. 프로젝트 속성 **게시** 창은 사이트 URL 및 기타 세부 정보를 표시합니다.

    ![프로필 요약을 표시하는 게시 속성 창](../deployment/media/quickstart-publish-windows-summary-page.png)

## <a name="clean-up-resources"></a>리소스 정리

이전 단계에서 Azure 리소스를 리소스 그룹에 만들었습니다. 나중에 이러한 리소스가 필요하지 않은 경우에 리소스 그룹을 삭제하여 삭제할 수 있습니다.
Azure Portal의 왼쪽 메뉴에서 **리소스 그룹**을 선택한 다음, **myResourceGroup**을 선택합니다.
리소스 그룹 페이지에서 나열된 리소스가 삭제하려는 항목인지 확인합니다.
**삭제**를 선택하고, 텍스트 상자에 **myResourceGroup**을 입력한 다음, **삭제**를 선택합니다.

## <a name="next-steps"></a>다음 단계

이 빠른 시작에서는 Visual Studio를 사용하여 Azure에 배포를 위해 게시 프로필을 만드는 방법을 알아보았습니다. Azure App Service에서 게시 설정을 가져와서 게시 프로필을 구성할 수도 있습니다.

> [!div class="nextstepaction"]
> [게시 설정 가져오기 및 Azure에 배포](tutorial-import-publish-settings-azure.md)
