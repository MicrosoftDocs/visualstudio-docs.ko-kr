---
title: Azure App Service에 게시
ms.date: 04/02/2019
helpviewer_keywords:
- deployment, website
ms.assetid: 8524a4c5-97a9-41ac-a2a0-034efb9bfc57
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.custom: video
ms.workload:
- azure
ms.openlocfilehash: e4ce4273b72a57a2b9456974a108809dcd73b4e0
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "70222727"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio-for-mac"></a>Mac용 Visual Studio를 사용하여 Azure App Service에 웹앱 게시

게시 도구를 사용하여 ASP.NET Core 앱을 Azure App Service에 게시할 수 있습니다.

## <a name="prerequisites"></a>사전 요구 사항

- ASP.NET Core가 사용하도록 설정된 상태로 설치된 [Mac용 Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2019).
- Azure 구독. 아직 구독하지 않은 경우 [무료로 등록합니다](https://azure.microsoft.com/free/dotnet/). 이는 30일 동안 $200의 크레딧 및 12개월의 인기 있는 무료 서비스를 포함합니다.
- ASP.NET Core 프로젝트 아직 프로젝트가 없는 경우 [새 프로젝트를 만들 수 있습니다](~/create-new-projects.md).

## <a name="publish-to-azure-app-service"></a>Azure App Service에 게시

 1. 솔루션 패드에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **게시**를 선택합니다.

    ![게시 상황에 맞는 메뉴](media/publish-context-menu.png)

 2. 이전에 Azure App Service에 이 프로젝트를 게시한 적이 있다면 메뉴에 게시 프로필이 표시됩니다. 해당 게시 프로필을 선택하여 게시 프로세스를 시작하세요.

 3. 이 프로젝트를 App Service에 처음으로 게시하려면 **Azure에 게시**를 선택합니다.

    ![App Service에 게시 상황에 맞는 메뉴](media/publish-to-azure-context-menu.png)

 4. **Azure App Service에 게시** 대화 상자가 나타나고 기존 App Services가 표시됩니다. 기존 App Service에 게시하려면 목록에서 App Service를 선택한 후 **게시**를 클릭합니다.

    ![Azure App Service에 게시 대화 상자](media/publish-to-app-service-dialog.png)

 5. 새 App Service를 만들려면 **새로 만들기** 단추를 클릭합니다.

    ![App Service에 게시 대화 상자](media/publish-to-app-service-dialog-new-selected.png)

 6. **새 App Service** 대화 상자가 나타납니다. 이 대화 상자에서 새 App Service에 대한 설정을 구성할 수 있습니다.

    ![새 App Service 대화 상자](media/publish-new-app-service.png)

    여기서 사용자 지정을 수행할 때 고려해야 할 몇 가지 옵션이 있습니다. App Service의 이름은 기본적으로 프로젝트 이름으로 설정됩니다. 이름을 사용할 수 없는 경우 입력 필드의 오른쪽에 경고 기호가 표시됩니다. App Service의 이름은 웹 사이트의 URL에 사용되므로 URL에 사용하기에 적합한 이름이어야 합니다.

    **구독** 드롭다운을 사용하여 App Service와 연결할 구독을 변경할 수 있습니다.

    드롭다운을 사용하여 기존의 **리소스 그룹**을 선택하거나 **+** 단추를 사용하여 새로 만들 수 있습니다.

    App Service 계획에 기존 항목을 선택하거나 **사용자 지정** 라디오 단추를 선택하여 새로 만들 수 있습니다.

    새 App Service를 만들고 프로젝트를 게시하려면 **만들기**를 클릭합니다.

    **만들기**를 클릭하면 **새 App Service** 대화 상자가 무시되고 App Service 만들기가 시작되었음을 알리는 다음과 같은 메시지가 표시됩니다.

      ![App Service 만들기 메시지](media/publish-create-app-service-message.png)

    **확인**을 클릭하면 메시지가 해제되고 프로젝트를 계속 작업할 수 있습니다. IDE 상단의 상태 표시줄을 통해 게시 프로세스의 상태를 볼 수 있습니다. 웹이 성공적으로 게시되면 기본 브라우저에 사이트가 열립니다.

## <a name="related-video"></a>관련 동영상

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Publish-to-Azure/player]
