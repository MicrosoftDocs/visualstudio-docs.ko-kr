---
title: Docker 시작
description: Mac용 Visual Studio에서 프로젝트에 Docker를 추가하는 방법을 알아봅니다.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 06/17/2019
ms.topic: how-to
ms.openlocfilehash: 5f21d55568328a9aeb9b7982e5978500f7ef715b
ms.sourcegitcommit: 2ce59c2ffeba5ba7f628c2e6c75cba4731deef8a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85939053"
---
# <a name="get-started-with-docker-in-visual-studio-for-mac"></a>Mac용 Visual Studio에서 Docker 시작

Mac용 Visual Studio를 사용하면 컨테이너화된 ASP.NET Core 앱을 간편하게 빌드, 디버그, 실행하고 Azure에 게시할 수 있습니다.

## <a name="prerequisites"></a>사전 요구 사항

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Mac용 Visual Studio 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="installation-and-setup"></a>설치 및 설정

Docker를 설치하려면 [Mac용 Docker Desktop 설치](https://docs.docker.com/docker-for-mac/install/)의 정보를 검토하고 따릅니다.

## <a name="creating-an-aspnet-core-web-application-and-adding-docker-support"></a>ASP.NET Core 웹 애플리케이션을 만들고 Docker 지원 추가

1. **파일 > 새 솔루션**으로 이동하여 새 솔루션을 만듭니다.
1. **.NET Core > 앱**에서 **웹 애플리케이션** 템플릿을 선택합니다. ![새 ASP.NET 애플리케이션 만들기](media/docker-quickstart-1.png)
1. 대상 프레임워크를 선택합니다. 이 예제에서는 .NET Core 2.2를 사용합니다. ![대상 프레임워크 설정](media/docker-quickstart-2.png)
1. 이름(이 예제에서는 _DockerDemo_) 등의 프로젝트 정보를 입력합니다. 생성된 프로젝트에는 ASP.NET Core 웹 사이트를 빌드 및 실행하는 데 필요한 모든 기본 사항이 포함되어 있습니다.
1. Solution Pad에서 DockerDemo 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가 > Docker 지원 추가**를 선택합니다. ![Docker 지원 추가](media/docker-quickstart-3.png)

Mac용 Visual Studio에서 **docker-compose**라는 새 프로젝트를 솔루션에 자동으로 추가하고, 기존 프로젝트에 **Dockerfile**을 추가합니다.

![생성된 docker 지원 파일](media/docker-quickstart-4.png)

## <a name="dockerfile-overview"></a>Dockerfile 개요

Dockerfile은 최종 Docker 이미지를 만들기 위한 레시피입니다. 그 안의 명령을 이해하려면 [Dockerfile 참조](https://docs.docker.com/engine/reference/builder/)를 참조하세요.

```
FROM microsoft/dotnet:2.2-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 80

FROM microsoft/dotnet:2.2-sdk AS build
WORKDIR /src
COPY DockerDemo/DockerDemo.csproj DockerDemo/
RUN dotnet restore DockerDemo/DockerDemo.csproj
COPY . .
WORKDIR /src/DockerDemo
RUN dotnet build DockerDemo.csproj -c Release -o /app

FROM build AS publish
RUN dotnet publish DockerDemo.csproj -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "DockerDemo.dll"]
```

위의 *Dockerfile*은 [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) 이미지를 기반으로 하며, 프로젝트를 빌드하고 컨테이너에 추가하여 기본 이미지를 수정하는 방법을 포함하고 있습니다.

> [!NOTE]
> Mac용 Visual Studio에서 생성된 기본 Dockerfile은 HTTP 트래픽용 포트 80을 공개합니다. HTTPS 트래픽을 사용하려면 Dockerfile에 `Expose 443`을 추가합니다.

## <a name="debugging"></a>디버깅

`docker-compose` 프로젝트를 시작 프로젝트로 선택하고 디버깅을 시작합니다(**실행 > 디버깅 시작**). 컨테이너에서 ASP.NET 프로젝트가 빌드, 배포 및 시작됩니다.

> [!TIP]
> Docker 데스크톱을 설치한 후 첫 번째 실행에서 디버그할 때 다음 오류가 나타날 수 있습니다. `Cannot start service dockerdemo: Mounts denied`
>
> Docker Desktop의 파일 공유 탭에 `/usr/local/share/dotnet/sdk/NuGetFallbackFolder`를 추가합니다.
>
> ![파일 공유에 NuGetFallbackFolder 폴더 추가](media/docker-quickstart-5.png)

빌드가 완료되면 Safari에서 애플리케이션이 시작됩니다.

![Safari에서 실행되는 기본 Docker 프로젝트](media/docker-quickstart-6.png)

컨테이너가 포트(예: `http://localhost:32768`)에서 수신 대기합니다. 이 포트는 달라질 수 있습니다.

실행 중인 컨테이너 목록을 보려면 터미널에서 `docker ps` 명령을 사용합니다.

아래 스크린샷에서 포트 릴레이를 확인합니다(**PORTS** 아래). 이 스크린샷에서 컨테이너는 위의 Safari에서 확인한 포트에서 수신 대기하고, Dockerfile에 정의된 대로 포트 80의 내부 웹 서버에 요청을 릴레이합니다. 애플리케이션 관점에서는 포트 80에서 수신 대기 중입니다.

![Docker 컨테이너 목록](media/docker-quickstart-7.png)
