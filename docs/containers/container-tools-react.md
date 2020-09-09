---
title: ASP.NET Core 및 React.js를 포함한 Visual Studio 컨테이너 도구
author: ghogen
description: Visual Studio 컨테이너 도구 및 Windows용 Docker를 사용하는 방법 알아보기
ms.author: ghogen
ms.date: 05/14/2020
ms.technology: vs-azure
ms.topic: quickstart
ms.openlocfilehash: d92d3a22570fb21381f18f2ce353dbc2d999893b
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89485400"
---
# <a name="quickstart-use-docker-with-a-react-single-page-app-in-visual-studio"></a>빠른 시작: Visual Studio에서 React 단일 페이지 앱과 함께 Docker 사용

Visual Studio를 사용하여 React.js 단일 페이지 앱과 같은 클라이언트 쪽 JavaScript를 포함한 앱과 더불어 컨테이너화된 ASP.NET Core 앱을 손쉽게 빌드, 디버그, 실행하고 Azure Container Registry(ACR), Docker Hub, Azure App Service 또는 자체 컨테이너 레지스트리에 게시할 수 있습니다. 이 문서에서는 ACR에 게시합니다.

## <a name="prerequisites"></a>사전 요구 사항

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **웹 개발**, **Azure 도구** 워크로드 및/또는 **.NET Core 플랫폼 간 개발** 워크로드가 설치된 [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)
* Azure Container Registry에 게시하려면 Azure 구독이 있어야 합니다. [평가판에 가입](https://azure.microsoft.com/offers/ms-azr-0044p/)합니다.
* [Node.JS](https://nodejs.org/en/download/)
* Windows 컨테이너의 경우 이 문서에서 참조된 Docker 이미지를 사용하려면 Windows 10 버전 1903 이상이어야 합니다.
::: moniker-end
::: moniker range=">=vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **웹 개발**, **Azure 도구** 워크로드 및/또는 **.NET Core 플랫폼 간 개발** 워크로드가 설치된 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
* .NET Core 2.2를 사용하여 개발하기 위한 [.NET Core 2.2 개발 도구](https://dotnet.microsoft.com/download/dotnet-core/2.2)
* Azure Container Registry에 게시하려면 Azure 구독이 있어야 합니다. [평가판에 가입](https://azure.microsoft.com/offers/ms-azr-0044p/)합니다.
* [Node.JS](https://nodejs.org/en/download/)
* Windows 컨테이너의 경우 이 문서에서 참조된 Docker 이미지를 사용하려면 Windows 10 버전 1903 이상이어야 합니다.
::: moniker-end

## <a name="installation-and-setup"></a>설치 및 설정

Docker를 설치하려면 우선 [Windows용 Docker Desktop: 설치하기 전에 알아야 할 사항](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)의 정보를 검토하세요. 다음으로 [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)을 설치합니다.

## <a name="create-a-project-and-add-docker-support"></a>프로젝트를 만들고 Docker 지원 추가

::: moniker range="vs-2017"
1. **ASP.NET Core 웹 애플리케이션** 템플릿을 사용하여 새 프로젝트를 만듭니다.
1. **React.js**를 선택합니다. **Docker 지원 사용**을 선택할 수 없지만 프로젝트를 만든 후 해당 지원을 추가할 수 있으니 걱정하지 마세요.

   ![새 React.js 프로젝트의 스크린샷](media/container-tools-react/vs2017/new-react-project.png)

1. 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **추가**> **Docker 지원**을 선택하여 프로젝트에 Dockerfile을 추가합니다.

   ![Docker 지원 추가](media/container-tools-react/vs2017/add-docker-support.png)

1. 컨테이너 형식을 선택하고 **확인**을 클릭합니다.
::: moniker-end
::: moniker range=">=vs-2019"
1. **ASP.NET Core 웹 애플리케이션** 템플릿을 사용하여 새 프로젝트를 만듭니다.
1. **React.js**를 선택하고 **만들기**를 클릭합니다. **Docker 지원 사용**을 선택할 수 없지만 나중에 해당 지원을 추가할 수 있으니 걱정하지 마세요.

   ![새 React.js 프로젝트의 스크린샷](media/container-tools-react/vs2019/new-react-project.png)

1. 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **추가**> **Docker 지원**을 선택하여 프로젝트에 Dockerfile을 추가합니다.

   ![Docker 지원 추가](media/container-tools-react/vs2017/add-docker-support.png)

1. 컨테이너 형식을 선택합니다.
::: moniker-end

다음 단계는 Linux 컨테이너를 사용 중인지 Windows 컨테이너를 사용 중인지에 따라 달라집니다.

## <a name="modify-the-dockerfile-linux-containers"></a>Dockerfile 수정(Linux 컨테이너)

최종 Docker 이미지를 만들기 위한 레시피인 *Dockerfile*은 프로젝트에 생성됩니다. 그 안의 명령을 이해하려면 [Dockerfile 참조](https://docs.docker.com/engine/reference/builder/)를 참조하세요.

프로젝트에서 *Dockerfile*을 열고 다음 행을 추가하여 컨테이너에 Node.js 10.x를 설치합니다. 이 행을 둘 다 첫 번째 섹션에 추가하고 노드 패키지 관리자 *npm.exe* 설치를 기본 이미지 및 `build` 섹션에 추가해야 합니다.

```Dockerfile
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
```

이제 *Dockerfile*이 다음과 같이 표시됩니다.

```Dockerfile
FROM microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim AS base
WORKDIR /app
EXPOSE 80 
EXPOSE 443
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs

FROM microsoft/dotnet:2.2-sdk-stretch AS build
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
WORKDIR /src
COPY ["WebApplication37/WebApplication37.csproj", "WebApplication37/"]
RUN dotnet restore "WebApplication37/WebApplication37.csproj"
COPY . .
WORKDIR "/src/WebApplication37"
RUN dotnet build "WebApplication37.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "WebApplication37.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication37.dll"]
```

위의 *Dockerfile*은 [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) 이미지를 기반으로 하며, 프로젝트를 빌드하고 컨테이너에 추가하여 기본 이미지를 수정하는 방법을 포함하고 있습니다.

새 프로젝트 대화 상자의 **HTTPS에 대한 구성** 확인란이 선택되면 *Dockerfile*은 두 개의 포트를 노출합니다. 한 포트는 HTTP 트래픽에 사용되고 다른 포트는 HTTPS에 사용됩니다. 이 확인란을 선택하지 않으면 단일 포트(80)가 HTTP 트래픽에 노출됩니다.

## <a name="modify-the-dockerfile-windows-containers"></a>Dockerfile 수정(Windows 컨테이너)

프로젝트 노드를 두 번 클릭하여 프로젝트 파일을 열고 다음 속성을 `<PropertyGroup>` 요소의 자식으로 추가하여 프로젝트 파일(*.csproj)을 업데이트합니다.

   ```xml
    <DockerfileFastModeStage>base</DockerfileFastModeStage>
   ```

다음 줄을 추가하여 Dockerfile을 업데이트합니다. 그러면 노드 및 npm이 컨테이너에 복사됩니다.

   1. Dockerfile의 첫 번째 줄에 ``# escape=` ``를 추가합니다.
   1. `FROM … base` 앞에 다음 줄을 추가합니다.

      ```Dockerfile
      FROM mcr.microsoft.com/powershell:nanoserver-1903 AS downloadnodejs
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs
      ```

   1. `FROM … build` 앞과 뒤에 다음 줄을 추가합니다.

      ```Dockerfile
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      ```

   1. 이제 완전한 Dockerfile이 다음과 같이 표시됩니다.

      ```Dockerfile
      # escape=`
      #Depending on the operating system of the host machines(s) that will build or run the containers, the image specified in the FROM statement may need to be changed.
      #For more information, please see https://aka.ms/containercompat
      FROM mcr.microsoft.com/powershell:nanoserver-1903 AS downloadnodejs
      RUN mkdir -p C:\nodejsfolder
      WORKDIR C:\nodejsfolder
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs

      FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1903 AS base
      WORKDIR /app
      EXPOSE 80
      EXPOSE 443
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\

      FROM mcr.microsoft.com/dotnet/core/sdk:2.2-nanoserver-1903 AS build
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      WORKDIR /src
      COPY ["WebApplication7/WebApplication37.csproj", "WebApplication37/"]
      RUN dotnet restore "WebApplication7/WebApplication7.csproj"
      COPY . .
      WORKDIR "/src/WebApplication37"
      RUN dotnet build "WebApplication37.csproj" -c Release -o /app/build

      FROM build AS publish
      RUN dotnet publish "WebApplication37.csproj" -c Release -o /app/publish

      FROM base AS final
      WORKDIR /app
      COPY --from=publish /app/publish .
      ENTRYPOINT ["dotnet", "WebApplication37.dll"]
      ```

   1. `**/bin`을 제거하여 .dockerignore 파일을 업데이트합니다.

## <a name="debug"></a>디버그

도구 모음의 디버그 드롭다운에서 **Docker**를 선택하고 앱에서 디버깅을 시작합니다. 인증서 신뢰 요청 메시지가 표시될 수 있습니다. 계속하려면 인증서를 신뢰하도록 선택하세요.  처음 빌드할 때는 docker가 기본 이미지를 다운로드하기 때문에 시간이 조금 더 걸릴 수 있습니다.

**출력** 창의 **컨테이너 도구** 옵션에 실행 중인 작업이 표시됩니다. *npm.exe*와 연관된 설치 단계가 표시됩니다.

브라우저에 앱의 홈페이지가 표시됩니다.

::: moniker range="vs-2017"
   ![실행 중인 앱의 스크린샷](media/container-tools-react/vs2017/running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
   ![실행 중인 앱의 스크린샷](media/container-tools-react/vs2019/running-app.png)
::: moniker-end

*카운터* 페이지로 이동한 후 **증분** 단추를 클릭하여 카운터의 클라이언트 쪽 코드를 테스트합니다.

**도구**> NuGet 패키지 관리자, **패키지 관리자 콘솔** 메뉴에서 **패키지 관리자 콘솔**(PMC)을 엽니다.

앱의 최종 Docker 이미지는 *dev*로 태그가 지정됩니다. 이미지는 *microsoft/dotnet* 기본 이미지의 *2.2-aspnetcore-runtime* 태그를 기반으로 합니다. **패키지 관리자 콘솔**(PMC) 창에서 `docker images` 명령을 실행합니다. 컴퓨터의 이미지가 표시됩니다.

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
webapplication37  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.2-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> **디버그** 구성은 볼륨 마운트를 사용하여 반복 편집 및 디버그 환경을 제공하므로 **dev** 이미지에는 앱 바이너리 및 다른 콘텐츠가 포함되지 않습니다. 모든 콘텐츠를 포함하는 프로덕션 이미지를 만들려면 **릴리스** 구성을 사용하세요.

PMC에서 `docker ps` 명령을 실행합니다. 앱은 컨테이너를 사용하여 실행됩니다.

```console
CONTAINER ID        IMAGE                  COMMAND               CREATED             STATUS              PORTS                                           NAMES
cf5d2ef5f19a        webapplication37:dev   "tail -f /dev/null"   2 minutes ago       Up 2 minutes        0.0.0.0:52036->80/tcp, 0.0.0.0:44342->443/tcp   priceless_cartwright
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

1. **만들기**를 클릭합니다.

   ![성공적인 게시를 보여 주는 스크린샷](media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>다음 단계

이제 레지스트리에서 Docker 이미지를 실행할 수 있는 모든 호스트로 컨테이너를 끌어올 수 있습니다(예: [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app)).

## <a name="additional-resources"></a>추가 자료

* [Visual Studio를 사용한 컨테이너 개발](./index.yml)
* [Docker 관련 Visual Studio 개발 문제 해결](troubleshooting-docker-errors.md)
* [Visual Studio 컨테이너 도구 GitHub 리포지토리](https://github.com/Microsoft/DockerTools)

::: moniker range="vs-2017"
[0]:media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png
::: moniker-end
::: moniker range=">=vs-2019"
[0]:media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
::: moniker-end