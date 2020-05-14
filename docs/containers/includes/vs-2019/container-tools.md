---
title: Visual Studio Tools for Docker 및 ASP.NET
author: ghogen
description: Visual Studio 2019 도구 및 Windows용 Docker를 사용하는 방법을 알아봅니다.
ms.author: ghogen
ms.date: 02/01/2019
ms.prod: visual-studio-dev16
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: d6d519483b350f2c1086c76bc17522b71a435fe9
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389982"
---
Visual Studio를 사용하여 컨테이너화된 NET, ASP.NET 및 ASP.NET Core 앱을 쉽게 빌드, 디버그, 실행하고 ACR(Azure Container Registry), Docker Hub, Azure App Service 또는 사용자 고유 컨테이너 레지스트리에 게시할 수 있습니다. 이 문서에서는 ASP.NET Core 앱을 ACR에 게시합니다.

## <a name="prerequisites"></a>사전 요구 사항

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **웹 개발**, **Azure 도구** 워크로드 및/또는 **.NET Core 플랫폼 간 개발** 워크로드가 설치된 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
* .NET Core를 사용하여 개발하기 위한 [.NET Core 개발 도구](https://dotnet.microsoft.com/download/dotnet-core/)
* Azure Container Registry에 게시하려면 Azure 구독이 있어야 합니다. [평가판에 가입](https://azure.microsoft.com/free/dotnet/)합니다.

## <a name="installation-and-setup"></a>설치 및 설정

Docker를 설치하려면 우선 [Windows용 Docker Desktop: 설치하기 전에 알아야 할 사항](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)의 정보를 검토하세요. 다음으로 [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)을 설치합니다.

## <a name="add-a-project-to-a-docker-container"></a>Docker 컨테이너에 프로젝트 추가

1. **ASP.NET Core 웹 애플리케이션** 템플릿을 사용하여 새 프로젝트를 만들거나 .NET Core 대신 .NET Framework를 사용하려는 경우 **ASP.NET 웹 애플리케이션(.NET Framework)** 을 선택합니다.
1. **웹 애플리케이션**을 선택하고, **Docker 지원 사용** 확인란이 선택되어 있는지 확인합니다.

   ![Docker 지원 사용 확인란](../../media/container-tools/vs-2019/create-new-web-application.PNG)

   스크린샷은 .NET Core를 보여줍니다. .NET Framework를 사용하는 경우 약간 다르게 보입니다.

1. 원하는 컨테이너 유형(Windows 또는 Linux)을 선택하고, **만들기**를 클릭합니다.

## <a name="dockerfile-overview"></a>Dockerfile 개요

최종 Docker 이미지를 만들기 위한 레시피인 *Dockerfile*은 프로젝트에 생성됩니다. 그 안의 명령을 이해하려면 [Dockerfile 참조](https://docs.docker.com/engine/reference/builder/)를 참조하세요.

```
FROM microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM microsoft/dotnet:2.2-sdk-stretch AS build
WORKDIR /src
COPY ["HelloDockerTools/HelloDockerTools.csproj", "HelloDockerTools/"]
RUN dotnet restore "HelloDockerTools/HelloDockerTools.csproj"
COPY . .
WORKDIR "/src/HelloDockerTools"
RUN dotnet build "HelloDockerTools.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "HelloDockerTools.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "HelloDockerTools.dll"]
```

위의 *Dockerfile*은 [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) 이미지를 기반으로 하며, 프로젝트를 빌드하고 컨테이너에 추가하여 기본 이미지를 수정하는 방법을 포함하고 있습니다. .NET Framework를 사용하는 경우 기본 이미지가 달라집니다.

새 프로젝트 대화 상자의 **HTTPS에 대한 구성** 확인란이 선택되면 *Dockerfile*은 두 개의 포트를 노출합니다. 한 포트는 HTTP 트래픽에 사용되고 다른 포트는 HTTPS에 사용됩니다. 이 확인란을 선택하지 않으면 단일 포트(80)가 HTTP 트래픽에 노출됩니다.

## <a name="debug"></a>디버그

도구 모음의 디버그 드롭다운에서 **Docker**를 선택하고 앱에서 디버깅을 시작합니다. 인증서 신뢰 요청 메시지가 표시될 수 있습니다. 계속하려면 인증서를 신뢰하도록 선택하세요.

**출력** 창의 **컨테이너 도구** 옵션에 실행 중인 작업이 표시됩니다. 처음에는 기본 이미지를 다운로드하는 데 시간이 걸릴 수 있지만 이후 실행은 훨씬 더 빠릅니다.

>[!NOTE]
> 디버깅을 위해 포트를 변경해야 하는 경우 *launchSettings. json* 파일에서 변경하면 됩니다. [컨테이너 시작 설정](../../container-launch-settings.md)을 참조하세요.

## <a name="containers-window"></a>컨테이너 창

Visual Studio 2019 버전 16.4 이상을 사용하는 경우 **컨테이너** 창을 사용하여 머신에서 실행 중인 컨테이너와 사용할 수 있는 이미지를 확인할 수 있습니다.

IDE에서 검색 상자를 사용하여(사용하려면 **Ctrl**+**Q**를 누름) **컨테이너** 창을 열고 `container`를 입력한 후 목록에서 **컨테이너** 창을 선택합니다.

**컨테이너** 창을 움직여서 창 배치 안내선에 따라 편집기 아래 등 편리한 위치에 탑재할 수 있습니다.

창에서 컨테이너를 찾고 각 탭을 단계별로 진행하여 환경 변수, 포트 매핑, 로그 및 파일 시스템을 확인합니다.

![컨테이너 창의 스크린샷](../../media/overview/vs-2019/container-tools-window.png)

자세한 내용은 [Visual Studio에서 컨테이너와 이미지를 보고 진단](../../view-and-diagnose-containers.md)을 참조하세요.

## <a name="publish-docker-images"></a>Docker 이미지 게시

앱의 개발 및 디버그 주기가 완료되면 앱의 프로덕션 이미지를 만들 수 있습니다.

1. 구성 드롭다운을 **릴리스**로 변경하고 앱을 빌드합니다.
1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **게시**를 선택합니다.
1. 게시 대상 대화 상자에서 **컨테이너 레지스트리** 탭을 선택합니다.
1. **새 Azure Container Registry 만들기**를 선택하고 **게시**를 클릭합니다.
1. **새 Azure Container Registry 만들기**에 원하는 값을 채웁니다.

    | 설정      | 제안 값  | Description                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS 접두사** | 전역적으로 고유한 이름 | 컨테이너 레지스트리를 고유하게 식별하는 이름입니다. |
    | **구독** | 구독 선택 | 사용할 Azure 구독입니다. |
    | **[리소스 그룹](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  컨테이너 레지스트리를 만들 리소스 그룹의 이름입니다. **새로 만들기**를 선택하여 새 리소스 그룹을 만듭니다.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | 표준 | 컨테이너 레지스트리의 서비스 계층  |
    | **레지스트리 위치** | 가까운 위치 | 사용자 또는 컨테이너 레지스트리를 사용할 기타 서비스에 가까운 [지역](https://azure.microsoft.com/regions/)의 위치를 선택합니다. |

    ![Visual Studio의 Azure Container Registry 만들기 대화 상자][0]

1. **만들기**

   ![성공적인 게시를 보여 주는 스크린샷](../../media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>다음 단계

이제 레지스트리에서 Docker 이미지를 실행할 수 있는 모든 호스트로 컨테이너를 끌어올 수 있습니다(예: [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app)).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
