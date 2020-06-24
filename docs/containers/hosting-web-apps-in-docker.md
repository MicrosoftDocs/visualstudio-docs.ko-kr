---
title: ACR 레지스트리에 ASP.NET Docker 컨테이너 배포
description: Visual Studio 컨테이너 도구를 사용하여 컨테이너 레지스트리에 ASP.NET 또는 ASP.NET Core 웹앱을 배포하는 방법을 알아봅니다.
author: ghogen
manager: jillfra
ms.assetid: e5e81c5e-dd18-4d5a-a24d-a932036e78b9
ms.devlang: dotnet
ms.topic: how-to
ms.technology: vs-azure
ms.date: 03/14/2019
ms.author: ghogen
ms.openlocfilehash: 9778590d804a72ff896b190a743fc08293f5b9ca
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283140"
---
# <a name="deploy-an-aspnet-container-to-a-container-registry-using-visual-studio"></a>Visual Studio를 사용하여 컨테이너 레지스트리에 ASP.NET 컨테이너 배포

## <a name="overview"></a>개요

Docker는 가상 머신과 몇 가지 측면에서 비슷하며 애플리케이션과 서비스를 호스트하는 데 사용할 수 있는 간단한 컨테이너 엔진입니다.
이 자습서에서는 Visual Studio를 사용하여 컨테이너화된 애플리케이션을 [Azure Container Registry](https://azure.microsoft.com/services/container-registry)에 게시하는 방법을 설명합니다.

Azure 구독이 아직 없는 경우 시작하기 전에 [체험 계정](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs)을 만듭니다.

## <a name="prerequisites"></a>사전 요구 사항

이 자습서를 완료하려면 다음이 필요합니다.

::: moniker range="vs-2017"
* “ASP.NET 및 웹 개발” 워크로드가 있는 최신 버전의 [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 설치
::: moniker-end
::: moniker range=">=vs-2019"
* “ASP.NET 및 웹 개발” 워크로드가 있는 최신 버전의 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) 설치
::: moniker-end
* [Windows용 Docker](https://docs.docker.com/docker-for-windows/install/)를 설치합니다.

## <a name="create-an-aspnet-core-web-app"></a>ASP.NET Core 웹앱 만들기
다음 단계에서는 이 자습서에서 사용할 기본적인 ASP.NET Core 앱을 만드는 과정을 안내합니다. 프로젝트가 이미 있는 경우 이 섹션을 건너뛸 수 있습니다.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">=vs-2019"
[!INCLUDE [create-aspnet5-app](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

## <a name="publish-your-container-to-azure-container-registry"></a>컨테이너를 Azure Container Registry에 게시
1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **게시**를 선택합니다.
2. 게시 대상 대화 상자에서 **컨테이너 레지스트리** 탭을 선택합니다.
3. **새 Azure Container Registry**를 선택하고 **게시**를 클릭합니다.
4. **새 Azure Container Registry 만들기**에 원하는 값을 채웁니다.

    | 설정      | 제안 값  | 설명                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS 접두사** | 전역적으로 고유한 이름 | 컨테이너 레지스트리를 고유하게 식별하는 이름입니다. |
    | **구독** | 구독 선택 | 사용할 Azure 구독입니다. |
    | **[리소스 그룹](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  컨테이너 레지스트리를 만들 리소스 그룹의 이름입니다. **새로 만들기**를 선택하여 새 리소스 그룹을 만듭니다.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | 표준 | 컨테이너 레지스트리의 서비스 계층  |
    | **레지스트리 위치** | 가까운 위치 | 사용자 또는 컨테이너 레지스트리를 사용할 기타 서비스에 가까운 [지역](https://azure.microsoft.com/regions/)의 위치를 선택합니다. |

    ![Visual Studio의 Azure Container Registry 만들기 대화 상자](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

5. **만들기**

이제 레지스트리에서 Docker 이미지를 실행할 수 있는 모든 호스트로 컨테이너를 끌어올 수 있습니다(예: [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app)).

## <a name="see-also"></a>참조

[빠른 시작: Azure CLI를 사용하여 Azure에 컨테이너 인스턴스 배포](/azure/container-instances/container-instances-quickstart)
