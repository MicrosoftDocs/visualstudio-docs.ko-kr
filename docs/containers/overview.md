---
title: Windows의 Visual Studio 컨테이너 도구
description: Docker로 작업하기 위해 Visual Studio에서 사용할 수 있는 도구 알아보기
author: ghogen
ms.author: ghogen
ms.topic: overview
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: 0d5859016a02de259c24c213c6cfef8cb5fce005
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916559"
---
# <a name="container-tools-in-visual-studio"></a>Visual Studio의 컨테이너 도구

Visual Studio에 컨테이너 개발용으로 포함된 도구는 쉽게 사용할 수 있으며 컨테이너화된 애플리케이션의 빌드, 디버깅 및 배포를 크게 단순화합니다. 단일 프로젝트용 컨테이너를 사용해 작업하거나 Docker Compose, Service Fabric 또는 Kubernetes를 통한 컨테이너 오케스트레이션을 사용하여 여러 컨테이너의 여러 서비스를 작업할 수 있습니다.

::: moniker range="vs-2017"

## <a name="prerequisites"></a>사전 요구 사항

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **웹 개발**, **Azure 도구** 워크로드 및/또는 **.NET Core 플랫폼 간 개발** 워크로드가 설치된 [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)
* Azure Container Registry에 게시하려면 Azure 구독이 있어야 합니다. [평가판에 가입](https://azure.microsoft.com/offers/ms-azr-0044p/)합니다.

## <a name="docker-support-in-visual-studio"></a>Visual Studio의 Docker 지원

Docker 지원은 ASP.NET 프로젝트, ASP.NET Core, .NET Core 및 .NET Framework 콘솔 프로젝트에서 사용할 수 있습니다.

Visual Studio의 Docker에 대한 지원은 고객 요구에 대응하여 여러 릴리스에 걸쳐 변경되었습니다. 프로젝트에 추가할 수 있는 Docker 지원에는 두 가지 수준이 있으며, 지원되는 옵션은 프로젝트의 유형 및 Visual Studio 버전에 따라 다릅니다. 일부 지원되는 프로젝트 유형에서 오케스트레이션을 사용하지 않고 단일 프로젝트용 컨테이너만 원하는 경우 Docker 지원을 추가하면 됩니다.  다음 수준은 컨테이너 오케스트레이션 지원으로, 선택한 특정 오케스트레이터용으로 적절한 지원 파일을 추가합니다.  

Visual Studio 2017을 사용하면 Docker Compose 및 Service Fabric을 컨테이너 오케스트레이션 서비스로 사용할 수 있습니다.  [Visual Studio Tools for Kubernetes](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes)를 설치하는 경우 Kubernetes를 사용할 수도 있습니다.

> [!NOTE]
> 15.8 이전 버전의 Visual Studio 2017을 사용하는 중이거나 .NET Framework 프로젝트 템플릿(.NET Core 아님)을 사용하는 중인 경우 Docker Compose를 사용하는 오케스트레이션 지원이 자동으로 추가됩니다. Docker Compose를 통한 컨테이너 오케스트레이션 지원은 Visual Studio 2017 버전 15.0~15.7에서 자동 추가되고 .NET Framework 프로젝트용으로 자동 추가됩니다.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="prerequisites"></a>사전 요구 사항

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **웹 개발**, **Azure 도구** 워크로드 및/또는 **.NET Core 플랫폼 간 개발** 워크로드가 설치된 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
* .NET Core를 사용하여 개발하기 위한 [.NET Core 개발 도구](https://dotnet.microsoft.com/download/dotnet-core/)입니다.
* Azure Container Registry에 게시하려면 Azure 구독이 있어야 합니다. [평가판에 가입](https://azure.microsoft.com/offers/ms-azr-0044p/)합니다.

## <a name="docker-support-in-visual-studio"></a>Visual Studio의 Docker 지원

Docker 지원은 ASP.NET 프로젝트, ASP.NET Core, .NET Core 및 .NET Framework 콘솔 프로젝트에서 사용할 수 있습니다.

Visual Studio의 Docker에 대한 지원은 고객 요구에 대응하여 여러 릴리스에 걸쳐 변경되었습니다. 프로젝트에 추가할 수 있는 Docker 지원에는 두 가지 수준이 있으며, 지원되는 옵션은 프로젝트의 유형 및 Visual Studio 버전에 따라 다릅니다. 일부 지원되는 프로젝트 유형에서 오케스트레이션을 사용하지 않고 단일 프로젝트용 컨테이너만 원하는 경우 Docker 지원을 추가하면 됩니다.  다음 수준은 컨테이너 오케스트레이션 지원으로, 선택한 특정 오케스트레이터용으로 적절한 지원 파일을 추가합니다.  

Visual Studio 2019를 사용하면 Docker Compose, Kubernetes 및 Service Fabric을 컨테이너 오케스트레이션 서비스로 사용할 수 있습니다.

> [!NOTE]
> 전체 .NET Framework 콘솔 프로젝트 템플릿을 사용하는 경우 프로젝트 작성 후 지원되는 옵션은 Service Fabric 또는 Docker Compose를 사용하는 옵션과 함께 **컨테이너 오케스트레이터 지원 추가**입니다. 프로젝트 작성 시 지원 추가와 오케스트레이션이 없는 단일 프로젝트에 대한 **Docker 지원 추가**는 사용 가능한 옵션이 아닙니다.

Visual Studio 2019 버전 16.4 이상에서는 실행 중인 컨테이너를 보고, 사용할 수 있는 이미지를 찾아보고, 환경 변수, 로그 및 포트 매핑을 보고, 파일 시스템을 검사하고, 디버거를 연결하거나, 컨테이너 환경 내에서 터미널 창을 열 수 있는 **컨테이너** 창을 사용할 수 있습니다. [Visual Studio에서 컨테이너와 이미지를 보고 진단](view-and-diagnose-containers.md)을 참조하세요.

::: moniker-end

### <a name="adding-docker-support"></a>Docker 지원 추가

다음 스크린샷에 표시된 것처럼 새 프로젝트를 만들 때 **Docker 지원 사용**을 선택하여 프로젝트 생성 중에 Docker 지원을 사용하도록 설정할 수 있습니다.

::: moniker range="vs-2017"
![Visual Studio에서 새 ASP.NET Core 웹앱에 Docker 지원 사용](./media/overview/enable-docker-support-visual-studio.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Visual Studio에서 새 ASP.NET Core 웹앱에 Docker 지원 사용](./media/overview/vs-2019/enable-docker-support-visual-studio.png)
::: moniker-end

> [!NOTE]
> .NET Framework 프로젝트(.NET Core 아님)의 경우 Windows 컨테이너만 사용할 수 있습니다.

**솔루션 탐색기**에서 **추가** > **Docker 지원**을 선택하여 기존 프로젝트에 Docker 지원을 추가할 수 있습니다. **추가 > Docker 지원** 및 **추가 > 컨테이너 오케스트레이터 지원** 명령은 다음 스크린샷에 나온 것처럼 **솔루션 탐색기**에서 ASP.NET Core 프로젝트에 해당하는 프로젝트 노드의 오른쪽 클릭 메뉴(또는 상황에 맞는 메뉴)에 있습니다.

![Visual Studio에서 Docker 지원 메뉴 옵션 추가](./media/overview/add-docker-support-menu.png)

Docker 지원을 추가하거나 사용 설정하면 Visual Studio에서 프로젝트에 다음을 추가합니다.

- *Dockerfile* 파일
- .dockerignore 파일
- Microsoft.VisualStudio.Azure.Containers.Tools.Targets에 대한 NuGet 패키지 참조

::: moniker range=">=vs-2019"
Docker 지원을 추가하면 솔루션은 다음과 같이 됩니다.

![Dockerfile 및 .dockerignore 파일이 있는 솔루션 탐색기 스크린샷](media/overview/vs-2019/dockerfile-dockerignore.png)
::: moniker-end

::: moniker range="vs-2017"
> [!NOTE]
> 다음 스크린샷에 나온 것처럼 ASP.NET 프로젝트(.NET Framework 프로젝트임, .NET Core 프로젝트 아님)를 위해 프로젝트를 생성하는 동안 Docker 지원을 사용하도록 설정하면 컨테이너 오케스트레이션 지원도 추가됩니다.

![ASP.NET 프로젝트에 Docker Compose 지원 사용](media/overview/enable-docker-compose-support.png)
::: moniker-end

## <a name="docker-compose-support"></a>Docker Compose 지원

Docker Compose를 사용하여 다중 컨테이너 솔루션을 작성하려면 프로젝트에 컨테이너 오케스트레이션 지원을 추가합니다. 이렇게 하면 동일한 *docker-compose.yml* 파일에 정의된 경우 일련의 컨테이너(전체 솔루션 또는 프로젝트 그룹)를 동시에 실행 및 디버그할 수 있습니다.

Docker Compose를 사용하여 컨테이너 오케스트레이션 지원을 추가하려면 **솔루션 탐색기**에서 솔루션 또는 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **추가 > Container Orchestration Support**(컨테이너 오케스트레이션 지원)를 선택합니다. 그런 다음, 컨테이너를 관리할 **Docker Compose**를 선택합니다.

프로젝트에 컨테이너 오케스트레이션 지원을 추가한 후에는 다음에서 보이는 것처럼 **솔루션 탐색기**에서 *Dockerfile*이 프로젝트에 추가(기존에 없었던 경우)되고 **docker-compose** 폴더가 솔루션에 추가된 것이 표시됩니다.

![Visual Studio의 솔루션 탐색기 내의 Docker 파일](media/overview/docker-support-solution-explorer.png)

*docker-compose.yml*이 이미 있는 경우에는 Visual Studio에서 이 파일에 필수 구성 코드 줄을 추가합니다.

Docker Compose를 사용하여 제어할 다른 프로젝트에 이 프로세스를 반복합니다.

## <a name="kubernetes-support"></a>Kubernetes 지원

::: moniker range="vs-2017"
Kubernetes 지원을 추가하려면 [Visual Studio Tools for Kubernetes](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes)를 설치하세요.
::: moniker-end

Kubernetes 지원을 사용하면 로컬 프로젝트와 [AKS(Azure Kubernetes Service)](/azure/aks)에서 실행되는 Kubernetes 클러스터 간에 연결을 사용하도록 설정할 수 있으며 이에 따라 Visual Studio를 사용하여 AKS에서 실행되는 서비스를 수정 및 디버그할 수 있습니다.  이 서비스는 [Azure Dev Spaces](/azure/dev-spaces/quickstart-netcore-visualstudio)에서 제공됩니다. Azure Dev Spaces를 사용하면 개발 목적으로 *dev spaces*라는 별도의 Kubernetes 서비스 분기를 설정할 수도 있으므로 개발 중인 작업 버전에서 프로덕션 서비스를 효율적으로 분리하고 서로 명확히 분리하여 수정 사항을 별개로 유지할 수 있습니다.

프로젝트에 Kubernetes 지원을 추가하려면 컨테이너 오케스트레이션 지원을 추가할 때 **Kubernetes/Helm**을 선택합니다. Azure Dev Spaces를 구성하는 *azds.yaml*을 포함한 다수의 파일과 Kubernetes 서비스의 구조를 설명하는 Helm 차트가 프로젝트에 추가됩니다.

## <a name="service-fabric-support"></a>Service Fabric 지원

Visual Studio에서 Service Fabric 도구를 사용하면 Azure Service Fabric용으로 개발 및 디버그하고, 로컬에서 실행하고, Azure에 배포할 수 있습니다.

::: moniker range="vs-2017"
Azure 개발 워크로드가 설치된 Visual Studio 2017 버전 15.9 이상에서는 Windows 컨테이너 및 Service Fabric 오케스트레이션을 사용하여 컨테이너화된 마이크로 서비스 개발을 지원합니다.
::: moniker-end
::: moniker range=">=vs-2019"
Visual Studio 2019는 Windows 컨테이너 및 Service Fabric 오케스트레이션을 사용하여 컨테이너화된 마이크로 서비스 개발을 지원합니다.
::: moniker-end

자세한 자습서는 [자습서: Azure Service Fabric에 Windows 컨테이너의 .NET 애플리케이션 배포](/azure/service-fabric/service-fabric-host-app-in-a-container)를 참조하세요.

Azure Service Fabric에 대한 자세한 내용은 [Service Fabric](/azure/service-fabric)을 참조하세요.

## <a name="continuous-delivery-and-continuous-integration-cicd"></a>지속적인 업데이트 및 연속 통합(CI/CD)

Visual Studio는 Azure Pipelines와 원활하게 통합되어 서비스 코드 및 구성의 변경 사항에 대해 자동화된 연속 통합 및 지속적인 업데이트를 제공합니다. 시작하려면 [첫 번째 파이프라인 만들기](/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=tfs-2018-2)를 참조하세요.

Service Fabric에 대해서는 [자습서: Deploy your ASP.NET Core app to Azure Service Fabric by using Azure DevOps Projects](/azure/devops-project/azure-devops-project-service-fabric)(Azure DevOps Projects를 사용하여 Azure Service Fabric에 ASP.NET Core 앱 배포)를 참조하세요.

Kubernetes에 대해서는 [Deploy a Docker container app to Azure Kubernetes Service](/azure/devops/pipelines/apps/cd/deploy-aks?view=azure-devops)(Azure Kubernetes Service에 Docker 컨테이너 앱 배포)를 참조하세요.

## <a name="next-steps"></a>다음 단계

서비스 구현 및 컨테이너 작업에서 Visual Studio 도구 사용에 대한 자세한 내용을 보려면 다음 문서를 참조하세요.

[로컬 Docker 컨테이너에서 앱 디버그](edit-and-refresh.md)

[Visual Studio를 사용하여 컨테이너 레지스트리에 ASP.NET 컨테이너 배포](hosting-web-apps-in-docker.md)
