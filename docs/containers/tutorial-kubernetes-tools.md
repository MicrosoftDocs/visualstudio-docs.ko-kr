---
title: Kubernetes 도구 자습서 | Microsoft Docs
ms.date: 06/08/2018
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.workload:
- azure
ms.openlocfilehash: 931f8c2a6d3be130ef78f59f9b3853d28fad8cd4
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444689"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>Visual Studio Kubernetes 도구 시작

Visual Studio Kubernetes 도구는 Kubernetes를 대상으로 하는 컨테이너화된 애플리케이션의 개발을 간소화하는 데 도움이 됩니다. Visual Studio는 Kubernetes 배포를 지원하는 데 필요한 Dockerfile, Helm 차트 등의 코드로 구성 파일을 자동으로 만들 수 있습니다. Azure Dev Spaces를 사용하여 라이브 AKS(Azure Kubernetes Service) 클러스터에서 코드를 디버그하거나, Visual Studio 내에서 AKS 클러스터로 직접 게시할 수 있습니다.

이 자습서에서는 Visual Studio를 사용하여 프로젝트에 Kubernetes 지원을 추가하고 AKS에 게시하는 방법을 설명합니다. [Azure Dev Spaces](/azure/dev-spaces/)를 사용하여 AKS에서 실행되는 프로젝트를 디버그하고 테스트하는 방법을 알아보려면 [Azure Dev Spaces 자습서](/azure/dev-spaces/get-started-netcore-visualstudio)로 바로 이동할 수 있습니다.

## <a name="prerequisites"></a>사전 요구 사항

이 새로운 기능을 활용하려면 다음 조건을 충족해야 합니다.

::: moniker range="vs-2017"
- [ASP.NET 및 웹 개발](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 워크로드가 있는 최신 버전의 *Visual Studio 2017*
- 별도의 다운로드로 제공되는 [Kubernetes tools for Visual Studio](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes)
::: moniker-end
::: moniker range="vs-2019"
- [ASP.NET 및 웹 개발](https://visualstudio.microsoft.com/downloads) 워크로드가 있는 *Visual Studio 2019*
::: moniker-end
- Docker 이미지를 빌드하거나, 로컬에서 실행 중인 Docker 컨테이너를 디버그하거나, AKS에 게시하려는 경우 Visual Studio를 실행하는 개발 워크스테이션에 설치된 [Docker Desktop](https://store.docker.com/editions/community/docker-ce-desktop-windows). Azure Dev Spaces를 사용하여 AKS에서 Docker 컨테이너를 빌드하고 디버그하는 경우에는 Docker가 필요하지 ‘않습니다’. 
::: moniker range="vs-2017"
- Visual Studio에서 AKS에 게시하려는 경우(Azure Dev Spaces를 사용하여 AKS에서 디버그하는 경우에는 필요하지 ‘않음’): 

    1. 별도의 다운로드로 제공되는 [AKS 게시 도구](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes)

    1. Azure Kubernetes Service 클러스터입니다. 자세한 내용은 [AKS 클러스터 만들기](/azure/aks/kubernetes-walkthrough-portal#create-an-aks-cluster)를 참조하세요. 개발 워크스테이션에서 [클러스터에 연결](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster)해야 합니다.

    1. 개발 워크스테이션에 설치된 Helm CLI. 자세한 내용은 [Helm 설치](https://github.com/helm/helm-www/blob/master/content/en/docs/helm/helm_install.md)를 참조하세요.

    1. `helm init` 명령을 사용하여 AKS 클러스터에 대해 구성된 Helm. 이 작업을 수행하는 방법에 대한 자세한 내용은 [Helm 구성 방법](/azure/aks/kubernetes-helm#configure-helm)을 참조하세요.
::: moniker-end

## <a name="create-a-new-kubernetes-project"></a>새 Kubernetes 프로젝트 만들기

::: moniker range="vs-2017"

적절한 도구가 설치되어 있으면, Visual Studio를 시작하고 새 프로젝트를 만듭니다. **클라우드**에서 **Kubernetes용 컨테이너 애플리케이션** 프로젝트 형식을 선택합니다. 이 프로젝트 형식을 선택하고 **확인**을 선택합니다.

![새 Kubernetes 앱 프로젝트 만들기 스크린샷](media/tutorial-kubernetes-tools/k8s-tools-new-k8s-app.png)

::: moniker-end
::: moniker range=">= vs-2019"

Visual Studio 시작 창에서 *Kubernetes*를 검색하고 **Kubernetes용 컨테이너 애플리케이션**을 선택합니다.

![새 Kubernetes 앱 프로젝트 만들기 스크린샷](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app1.png)

프로젝트 이름을 입력합니다.

![새 Kubernetes 앱 프로젝트 만들기 스크린샷](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app2.png)

::: moniker-end

그런 다음, 만들 ASP.NET Core 웹 애플리케이션 유형을 선택할 수 있습니다. **웹 애플리케이션**을 선택합니다. 이 대화 상자에는 일반적인 **Docker 지원 사용** 옵션이 표시되지 않습니다.  Kubernetes용 컨테이너 애플리케이션에서는 Docker 지원이 기본적으로 사용됩니다.

::: moniker range="vs-2017"

![웹앱 선택 스크린샷](media/tutorial-kubernetes-tools/k8s-tools-web-app-selection-screen.png)

::: moniker-end
::: moniker range=">=vs-2019"

![웹앱 선택 스크린샷](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-web-app-selection-screen-2019.png)

::: moniker-end

## <a name="add-kubernetes-support-to-an-existing-project"></a>기존 프로젝트에 Kubernetes 지원 추가

또는 기존 ASP.NET Core 웹 애플리케이션에 Kubernetes 지원을 추가할 수 있습니다. 이 작업을 수행하려면 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가** > **컨테이너 오케스트레이터 지원**을 선택합니다.

::: moniker range="vs-2017"

![컨테이너 오케스트레이터 추가 메뉴 항목 스크린샷](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator.png)

::: moniker-end
::: moniker range=">=vs-2019"

![컨테이너 오케스트레이터 추가 메뉴 항목 스크린샷](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-add-container-orchestrator-2019.png)

::: moniker-end

대화 상자에서 **Kubernetes/Helm**을 선택하고 **확인**을 선택합니다.

![컨테이너 오케스트레이터 추가 대화 상자 스크린샷](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>Visual Studio에서 자동으로 만드는 항목

**Kubernetes용 컨테이너 애플리케이션** 프로젝트를 새로 만들거나 기존 프로젝트에 Kubernetes 컨테이너 오케스트레이터 지원을 추가하면 Kubernetes에 배포하는 데 도움이 되는 몇 가지 추가 파일이 프로젝트에 표시됩니다.

::: moniker range="vs-2017"

![컨테이너 오케스트레이터 지원을 추가한 후의 솔루션 탐색기 스크린샷](media/tutorial-kubernetes-tools/k8s-tools-solution-explorer.png)

::: moniker-end
::: moniker range="vs-2019"

![컨테이너 오케스트레이터 지원을 추가한 후의 솔루션 탐색기 스크린샷](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-solution-explorer-2019.png)

::: moniker-end

추가된 파일은 다음과 같습니다.

- Dockerfile - 이 웹 애플리케이션을 호스트하는 Docker 컨테이너 이미지를 생성하는 데 사용할 수 있습니다. 나중에 알게 되겠지만, Visual Studio 도구는 디버그하고 Kubernetes에 배포할 때 이 Dockerfile을 활용합니다. Docker 이미지에서 직접 작업하려는 경우, Dockerfile을 마우스 오른쪽 단추로 클릭하고 **Docker 이미지 빌드**를 선택할 수 있습니다.

   ![Docker 이미지 빌드 옵션 스크린샷](media/tutorial-kubernetes-tools/k8s-tools-build-docker-image.png)

- Helm 차트와 *charts* 폴더. 이러한 yaml 파일은 Kubernetes에 배포하는 데 사용할 수 있는 애플리케이션 Helm 차트를 구성합니다. Helm에 대한 자세한 내용은 [https://www.helm.sh](https://www.helm.sh)를 참조하세요.

- *azds.yaml*. 이 파일에는 Azure Kubernetes Service에서 빠르고 반복적인 디버깅 환경을 제공하는 Azure Dev Spaces의 설정이 포함되어 있습니다. 자세한 내용은 [Azure Dev Spaces 설명서](/azure/dev-spaces/azure-dev-spaces)를 참조하세요.

::: moniker range="vs-2017"

## <a name="publish-to-azure-kubernetes-service-aks"></a>AKS(Azure Kubernetes Service)에 게시

이러한 파일이 모두 준비되면, Visual Studio IDE를 사용하여 일반적인 방법으로 애플리케이션 코드를 작성하고 디버그할 수 있습니다. [Azure Dev Spaces](/azure/dev-spaces/)를 사용하여 코드를 빠르게 실행하고, AKS 클러스터에서 라이브로 실행 중인 코드를 디버그할 수도 있습니다. 자세한 내용은 [Azure Dev Spaces 자습서](/azure/dev-spaces/get-started-netcore-visualstudio)를 참조하세요.

코드가 원하는 방식으로 실행되면, Visual Studio에서 AKS 클러스터로 직접 게시할 수 있습니다.

이 작업을 수행하려면 먼저 [필수 조건](#prerequisites) 섹션에서 AKS에 게시하기 위한 항목 아래에 설명된 모든 항목을 설치했는지 다시 확인하고 링크에 제공된 명령줄 단계를 모두 실행해야 합니다. 그런 다음, 컨테이너 이미지를 ACR(Azure Container Registry)에 게시하는 게시 프로필을 설정합니다. 그러면 AKS가 ACR에서 컨테이너 이미지를 풀하여 클러스터에 배포할 수 있습니다.

1. **솔루션 탐색기**에서 *프로젝트*를 마우스 오른쪽 단추로 클릭하고 **게시**를 선택합니다.

   ![게시 메뉴 항목 스크린샷](media/tutorial-kubernetes-tools/k8s-tools-publish-project.png)

2. **게시** 화면에서 **Container Registry**를 게시 대상으로 선택하고 프롬프트에 따라 컨테이너 레지스트리를 선택합니다. 컨테이너 레지스트리가 아직 없는 경우, **새 Azure Container Registry 만들기**를 선택하여 Visual Studio에서 새로 만듭니다. 자세한 내용은 [Azure Container Registry에 컨테이너 게시](hosting-web-apps-in-docker.md)를 참조하세요.

   ![게시 대상 선택 화면 스크린샷](media/tutorial-kubernetes-tools/k8s-tools-publish-to-acr.png)

3. 솔루션 탐색기로 돌아가서 *솔루션*을 마우스 오른쪽 단추로 클릭하고 **Azure AKS에 게시**를 클릭합니다.

   ![Azure AKS에 게시 메뉴 항목 스크린샷](media/tutorial-kubernetes-tools/k8s-tools-publish-solution.png)

4. 방금 만든 ACR 게시 프로필과 함께 해당 구독과 AKS 클러스터를 선택합니다. 그런 후 **OK**를 클릭합니다.

   ![AKS에 게시 화면 스크린샷](media/tutorial-kubernetes-tools/k8s-tools-publish-to-aks.png)

   **Azure AKS에 게시** 화면으로 이동됩니다.

5. **Helm 구성** 링크를 선택하여 서버에 Helm 차트를 설치하는 데 사용되는 명령줄을 업데이트합니다.

   ![Helm 구성 링크 스크린샷](media/tutorial-kubernetes-tools/k8s-tools-configure-helm.png)

   다른 Kubernetes 컨텍스트나 차트 이름과 같은, 지정하려는 사용자 지정 명령줄 인수가 있는 경우 명령줄을 업데이트하는 것이 유용합니다.

   ![Helm 구성 화면 스크린샷](media/tutorial-kubernetes-tools/k8s-tools-helm-configure-screen.png)

6. 배포할 준비가 되면 **게시** 단추를 클릭하여 AKS에 애플리케이션을 게시합니다.

   ![Azure AKS에 게시 화면 스크린샷](media/tutorial-kubernetes-tools/k8s-tools-publish-screen.png)

::: moniker-end

축하합니다! 이제 모든 Kubernetes 앱 개발에서 Visual Studio의 전체 기능을 사용할 수 있습니다.

## <a name="next-steps"></a>다음 단계

[AKS 설명서](/azure/aks)를 참조하여 Azure의 Kubernetes 개발에 대해 자세히 알아봅니다.

[Azure Dev Spaces 설명서](/azure/dev-spaces/)를 참조하여 Azure Dev Spaces에 대해 자세히 알아봅니다.
