---
title: Azure App Service에 ASP.NET Core 컨테이너 배포
description: Visual Studio Container Tools를 사용하여 Azure App Service에 Docker 컨테이너의 ASP.NET Core 웹앱을 배포하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: how-to
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: c0f45f14bc8b363a0c7c4e298effa67c5fccde18
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036342"
---
# <a name="deploy-an-aspnet-core-container-to-azure-app-service-using-visual-studio"></a>Visual Studio를 사용하여 Azure App Service에 ASP.NET Core 컨테이너 배포

이 자습서에서는 Visual Studio를 사용하여 컨테이너화된 ASP.NET Core 웹 애플리케이션을 [Azure App Service](/azure/app-service)에 게시하는 방법을 설명합니다. Azure App Service는 Azure에 호스트된 단일 컨테이너 웹앱에 적합한 서비스입니다.

Azure 구독이 아직 없는 경우 시작하기 전에 [체험 계정](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs)을 만듭니다.

## <a name="prerequisites"></a>사전 요구 사항

이 자습서를 완료하려면 다음이 필요합니다.

::: moniker range="vs-2017"
- "ASP.NET 및 웹 개발" 워크로드가 포함된 최신 버전의 [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)을 설치합니다.
::: moniker-end
::: moniker range=">=vs-2019"
- *ASP.NET 및 웹 개발* 워크로드가 설치된 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)입니다.
::: moniker-end
- [Docker Desktop](https://docs.docker.com/docker-for-windows/install/) 설치

## <a name="create-an-aspnet-core-web-app"></a>ASP.NET Core 웹앱 만들기

다음 단계에서는 이 자습서에서 사용할 기본적인 ASP.NET Core 앱을 만드는 과정을 안내합니다.

::: moniker range="vs-2017"
1. Visual Studio 메뉴에서 **파일 > 새로 만들기 > 프로젝트**를 선택합니다.
2. **새 프로젝트** 대화 상자의 **템플릿** 섹션에서 **Visual C# > 웹**을 선택합니다.
3. **새 ASP.NET Core 웹 애플리케이션**을 선택합니다.
4. 새 애플리케이션에 이름을 지정(또는 기본값 사용)하고 **확인**을 선택합니다.
5. **웹 애플리케이션**을 선택합니다.
6. **Docker 지원 사용** 확인란을 선택합니다.
7. **Linux** 컨테이너 형식을 선택하고 **확인**을 클릭합니다. Windows 컨테이너는 Azure App Service에 컨테이너로 배포할 수 없습니다.
::: moniker-end
::: moniker range=">= vs-2019"
1. Visual Studio 시작 창에서 **새 프로젝트 만들기**를 선택합니다.
1. **ASP.NET Core 웹 애플리케이션**을 선택하고 **다음**을 선택합니다.
1. 새 애플리케이션에 이름을 지정(또는 기본값 사용)하고 **만들기**를 선택합니다.
1. **웹 애플리케이션**을 선택합니다.
1. **HTTPS에 대한 구성** 확인란을 사용하여 SSL 지원의 사용 여부를 선택합니다.
1. **Docker 지원 사용** 확인란을 선택합니다.
1. 컨테이너 형식을 선택하고 **만들기**를 클릭합니다.
::: moniker-end

## <a name="deploy-the-container-to-azure"></a>Azure에 컨테이너 배포

::: moniker range="vs-2017"

1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **게시**를 선택합니다.
1. 게시 대상 대화 상자에서 **App Service Linux** 또는 **App Service**를 선택합니다. 웹 서버를 호스트하는 운영 체제입니다.
1. App Service에만 게시하거나, App Service와 ACR(Azure Container Registry)에 모두 게시할 수 있습니다. ACR(Azure Container Registry)에 컨테이너를 게시하려면 **컨테이너에 대한 새 App Service 만들기**를 선택하고 **게시**를 클릭합니다.

   ![게시 대화 상자 스크린샷](media/deploy-app-service/publish-app-service-linux.PNG)

   Azure Container Registry를 사용하지 않고 Azure App Service에만 게시하려면 **새로 만들기**를 선택하고 **게시**를 클릭합니다.

1. Azure 구독과 연결된 계정으로 로그인했는지 확인하고 고유 이름, 구독, 리소스 그룹, 호스팅 계획 및 컨테이너 레지스트리(해당하는 경우)를 선택하거나 기본값을 적용합니다.

   ![게시 설정 스크린샷](media/deploy-app-service/publish-app-service-linux2.png)

1. **만들기**를 선택합니다. 컨테이너는 Azure의 선택한 리소스 그룹 및 컨테이너 레지스트리에 배포됩니다. 이 프로세스는 시간이 걸립니다. 작업이 완료되면, **게시** 탭에 사이트 URL을 포함하여 게시된 항목에 대한 정보가 표시됩니다.

   ![게시 탭 스크린샷](media/deploy-app-service/publish-succeeded.PNG)

1. 사이트 링크를 클릭하여 Azure에서 앱이 예상대로 작동하는지 확인합니다.

   ![웹 애플리케이션 스크린샷](media/deploy-app-service/web-application-running.png)

1. 리소스 그룹 및 컨테이너 레지스트리와 같은 선택한 모든 세부 정보와 함께 게시 프로필이 저장됩니다.

1. 동일한 게시 프로필을 사용하여 다시 배포하려면 **게시** 단추 또는 **웹 게시 작업** 창의 **게시** 단추를 사용하거나, **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 상황에 맞는 메뉴에서 **게시** 항목을 선택합니다.
:::moniker-end
:::moniker range=">=vs-2019"
1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **게시**를 선택합니다.
1. **게시** 대화 상자에서 **Azure** 대상을 선택합니다.

   ![게시 마법사 스크린샷](media/deploy-app-service/publish-choices.png)

1. **특정 대상** 탭에서 컨테이너 유형에 따라 **App Service(Windows)** 또는 **App Service(Linux)** 같은 적절한 배포 대상을 선택합니다.

   ![게시 마법사의 특정 대상 탭 스크린샷](media/deploy-app-service/publish-app-service-windows.png)

1. 사용하려는 구독을 보유한 올바른 Azure 계정에 로그인하지 않은 경우 **게시** 창의 왼쪽 위에 있는 단추를 사용하여 로그인합니다.

1. 기존 App Service를 사용하거나 **새 Azure App Service 만들기** 링크를 클릭하여 새로 만들 수 있습니다. 해당 리소스 그룹을 확장하여 트리 보기에서 기존 App Service를 찾거나 **보기** 설정을 **리소스 유형**으로 설정하여 유형별 정렬합니다.

   ![App Service 선택을 보여 주는 스크린샷](media/deploy-app-service/publish-app-service-windows2.png)

1. 새 App Service를 만드는 경우 리소스 그룹 및 App Service가 Azure에 생성됩니다. 원하는 경우 이름을 변경할 수 있습니다(고유해야 함).

   ![App Service 만들기를 보여 주는 스크린샷](media/deploy-app-service/publish-app-service-windows3.png)

1. 기본 호스팅 계획을 수락하거나, 지금 또는 나중에 Azure Portal에서 호스팅 계획을 변경할 수 있습니다. 기본값은 지원되는 지역 중 하나에서 `S1`(소형)입니다. 호스팅 계획을 만들려면 **호스팅 계획** 드롭다운 옆에 있는 **새로 만들기**를 선택합니다. **호스팅 계획** 창이 표시됩니다.

   ![호스팅 계획 옵션을 보여 주는 스크린샷](media/deploy-app-service/hosting-plan.png)

   [Azure App Service 계획 개요](/azure/app-service/overview-hosting-plans)에서 이러한 옵션에 대한 세부 정보를 볼 수 있습니다.

1. 이러한 리소스를 선택하거나 만든 후 **마침**을 선택합니다. 컨테이너는 선택한 리소스 그룹 및 App Service에서 Azure에 배포됩니다. 이 프로세스는 시간이 걸립니다. 작업이 완료되면, **게시** 탭에 사이트 URL을 포함하여 게시된 항목에 대한 정보가 표시됩니다.

   ![게시 탭 스크린샷](media/deploy-app-service/publish-succeeded-windows.png)

1. 사이트 링크를 클릭하여 Azure에서 앱이 예상대로 작동하는지 확인합니다.

   ![웹 애플리케이션 스크린샷](media/deploy-app-service/web-application-running2.png)

1. 리소스 그룹 및 App Service와 같은 선택한 모든 세부 정보와 함께 게시 프로필이 저장됩니다.

1. 동일한 게시 프로필을 사용하여 다시 배포하려면 **게시** 단추 또는 **웹 게시 작업** 창의 **게시** 단추를 사용하거나, **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 상황에 맞는 메뉴에서 **게시** 항목을 선택합니다.
:::moniker-end

## <a name="view-container-settings"></a>컨테이너 설정 보기

[Azure Portal](https://portal.azure.com)에서 배포된 App Service를 열 수 있습니다.

Visual Studio 2019 버전 16.4 이상을 사용하는 경우 **컨테이너 설정** 메뉴를 열어 배포된 App Service 설정을 볼 수 있습니다.

![Azure Portal의 컨테이너 설정 메뉴 스크린샷](media/deploy-app-service/container-settings-menu.png)

여기에서 컨테이너 정보를 보거나, 로그를 보거나 다운로드하거나, 지속적인 배포를 설정할 수 있습니다. [Azure App Service 지속적인 배포 CI/CD](/azure/app-service/containers/app-service-linux-ci-cd)를 참조하세요.

## <a name="clean-up-resources"></a>리소스 정리

이 자습서와 관련된 Azure 리소스를 모두 제거하려면 [Azure Portal](https://portal.azure.com)을 사용하여 해당 리소스 그룹을 삭제합니다. 게시된 웹 애플리케이션과 관련된 리소스 그룹을 찾으려면 **보기** > **다른 창** > **웹 게시 작업**을 선택한 다음, 기어 아이콘을 선택합니다. 리소스 그룹이 포함된 **게시** 탭이 열립니다.

Azure Portal에서 **리소스 그룹**을 선택한 다음, 리소스 그룹을 선택하여 세부 정보 페이지를 엽니다. 올바른 리소스 그룹인지 확인한 다음, **리소스 그룹 제거**를 선택하고 이름을 입력한 후 **삭제**를 선택합니다.

## <a name="next-steps"></a>다음 단계

[Azure App Service](/azure/app-service/overview)에 대해 자세히 알아봅니다.

## <a name="see-also"></a>참조

[Azure Container Registry에 배포](hosting-web-apps-in-docker.md)