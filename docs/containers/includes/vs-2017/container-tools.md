---
title: ASP.NET Core를 포함한 Visual Studio 컨테이너 도구
author: ghogen
description: Visual Studio 2017 도구 및 Windows용 Docker를 사용하는 방법 알아보기
ms.author: ghogen
ms.date: 02/01/2019
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 627b0b1260a3ccdd401dbb170f8e2dfffadea2dc
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389946"
---
Visual Studio를 사용하여 컨테이너화된 ASP.NET Core 앱을 쉽게 빌드, 디버그, 실행하고 ACR(Azure Container Registry), Docker Hub, Azure App Service 또는 사용자 고유 컨테이너 레지스트리에 게시할 수 있습니다. 이 문서에서는 ACR에 게시합니다.

## <a name="prerequisites"></a>사전 요구 사항

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **웹 개발**, **Azure 도구** 워크로드 및/또는 **.NET Core 플랫폼 간 개발** 워크로드가 설치된 [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)
* Azure Container Registry에 게시하려면 Azure 구독이 있어야 합니다. [평가판에 가입](https://azure.microsoft.com/free/dotnet/)합니다.

## <a name="installation-and-setup"></a>설치 및 설정

Docker를 설치하려면 우선 [Windows용 Docker Desktop: 설치하기 전에 알아야 할 사항](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)의 정보를 검토하세요. 다음으로 [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)을 설치합니다.

## <a name="add-a-project-to-a-docker-container"></a>Docker 컨테이너에 프로젝트 추가

1. Visual Studio 메뉴에서 **파일 > 새로 만들기 > 프로젝트**를 선택합니다.
1. **새 프로젝트** 대화 상자의 **템플릿** 섹션에서 **Visual C# > 웹**을 선택합니다.
1. **ASP.NET Core 웹 애플리케이션**을 선택하거나 .NET Core 대신 .NET Framework를 사용하고 싶다면 **ASP.NET 웹 애플리케이션**을 선택합니다.
1. 새 애플리케이션에 이름을 지정(또는 기본값 사용)하고 **확인**을 선택합니다.
1. **웹 애플리케이션**을 선택합니다.
1. **Docker 지원 사용** 확인란을 선택합니다.

   ![Docker 지원 사용 확인란](../../media/container-tools/enable-docker-support.PNG)

   스크린샷은 .NET Core를 보여줍니다. .NET Framework를 사용하는 경우 약간 다르게 보입니다.

1. 원하는 컨테이너 유형(Windows 또는 Linux)을 선택하고, **확인**을 클릭합니다.

## <a name="dockerfile-overview"></a>Dockerfile 개요

최종 Docker 이미지를 만들기 위한 레시피인 *Dockerfile*은 프로젝트에 생성됩니다. 그 안의 명령을 이해하려면 [Dockerfile 참조](https://docs.docker.com/engine/reference/builder/)를 참조하세요.

```
FROM microsoft/dotnet:2.1-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 59518
EXPOSE 44364

FROM microsoft/dotnet:2.1-sdk AS build
WORKDIR /src
COPY HelloDockerTools/HelloDockerTools.csproj HelloDockerTools/
RUN dotnet restore HelloDockerTools/HelloDockerTools.csproj
COPY . .
WORKDIR /src/HelloDockerTools
RUN dotnet build HelloDockerTools.csproj -c Release -o /app

FROM build AS publish
RUN dotnet publish HelloDockerTools.csproj -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "HelloDockerTools.dll"]
```

위의 *Dockerfile*은 [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) 이미지를 기반으로 하며, 프로젝트를 빌드하고 컨테이너에 추가하여 기본 이미지를 수정하는 방법을 포함하고 있습니다. .NET Framework를 사용하는 경우 기본 이미지가 달라집니다.

새 프로젝트 대화 상자의 **HTTPS에 대한 구성** 확인란이 선택되면 *Dockerfile*은 두 개의 포트를 노출합니다. 한 포트는 HTTP 트래픽에 사용되고 다른 포트는 HTTPS에 사용됩니다. 이 확인란을 선택하지 않으면 단일 포트(80)가 HTTP 트래픽에 노출됩니다.

## <a name="debug"></a>디버그

도구 모음의 디버그 드롭다운에서 **Docker**를 선택하고 앱에서 디버깅을 시작합니다. 인증서 신뢰 요청 메시지가 표시될 수 있습니다. 계속하려면 인증서를 신뢰하도록 선택하세요.

**출력** 창에 실행 중인 작업이 표시됩니다.

**도구**> NuGet 패키지 관리자, **패키지 관리자 콘솔** 메뉴에서 **패키지 관리자 콘솔**(PMC)을 엽니다.

앱의 최종 Docker 이미지는 *dev*로 태그가 지정됩니다. 이미지는 *microsoft/dotnet* 기본 이미지의 *2.1-aspnetcore-runtime* 태그를 기반으로 합니다. **패키지 관리자 콘솔**(PMC) 창에서 `docker images` 명령을 실행합니다. 컴퓨터의 이미지가 표시됩니다.

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
hellodockertools  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.1-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> **디버그** 구성은 볼륨 마운트를 사용하여 반복 편집 및 디버그 환경을 제공하므로 **dev** 이미지에는 앱 바이너리 및 다른 콘텐츠가 포함되지 않습니다. 모든 콘텐츠를 포함하는 프로덕션 이미지를 만들려면 **릴리스** 구성을 사용하세요.

PMC에서 `docker ps` 명령을 실행합니다. 앱은 컨테이너를 사용하여 실행됩니다.

```console
CONTAINER ID        IMAGE                  COMMAND                   CREATED             STATUS              PORTS                   NAMES
baf9a678c88d        hellodockertools:dev   "C:\\remote_debugge..."   21 seconds ago      Up 19 seconds       0.0.0.0:37630->80/tcp   dockercompose4642749010770307127_hellodockertools_1
```

## <a name="publish-docker-images"></a>Docker 이미지 게시

앱의 개발 및 디버그 주기가 완료되면 앱의 프로덕션 이미지를 만들 수 있습니다.

1. 구성 드롭다운을 **릴리스**로 변경하고 앱을 빌드합니다.
1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **게시**를 선택합니다.
1. 게시 대상 대화 상자에서 **컨테이너 레지스트리** 탭을 선택합니다.
1. **새 Azure Container Registry 만들기**를 선택하고 **게시**를 클릭합니다.
1. **새 Azure Container Registry 만들기**에 원하는 값을 채웁니다.

    | 설정      | 제안 값  | 설명                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS 접두사** | 전역적으로 고유한 이름 | 컨테이너 레지스트리를 고유하게 식별하는 이름입니다. |
    | **구독** | 구독 선택 | 사용할 Azure 구독입니다. |
    | **[리소스 그룹](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  컨테이너 레지스트리를 만들 리소스 그룹의 이름입니다. **새로 만들기**를 선택하여 새 리소스 그룹을 만듭니다.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | 표준 | 컨테이너 레지스트리의 서비스 계층  |
    | **레지스트리 위치** | 가까운 위치 | 사용자 또는 컨테이너 레지스트리를 사용할 기타 서비스에 가까운 [지역](https://azure.microsoft.com/regions/)의 위치를 선택합니다. |

    ![Visual Studio의 Azure Container Registry 만들기 대화 상자][0]

1. **만들기**

## <a name="next-steps"></a>다음 단계

이제 레지스트리에서 Docker 이미지를 실행할 수 있는 모든 호스트로 컨테이너를 끌어올 수 있습니다(예: [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app)).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png
