---
title: Visual Studio 컨테이너 도구 빌드 및 디버그 개요
author: ghogen
description: 컨테이너 도구 빌드 및 디버깅 프로세스 개요
ms.author: ghogen
ms.date: 11/20/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 004427ced7d18d9a5af5c863172416fd8637aa69
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85536866"
---
# <a name="how-visual-studio-builds-containerized-apps"></a>Visual Studio에서 컨테이너화된 앱을 빌드하는 방법

Visual Studio IDE에서 빌드하거나 명령줄 빌드를 설정하는 경우, Visual Studio에서 Dockerfile을 사용하여 프로젝트를 빌드하는 방법을 알고 있어야 합니다.  성능상의 이유로, Visual Studio는 컨테이너화된 앱을 위해 특별한 프로세스를 따릅니다. Dockerfile을 수정하여 빌드 프로세스를 사용자 지정하는 경우에는 Visual Studio에서 프로젝트를 빌드하는 방법을 이해하는 것이 특히 중요합니다.

Visual Studio는 Docker 컨테이너를 사용하지 않는 프로젝트를 빌드할 때, 로컬 컴퓨터에서 MSBuild를 호출하고 로컬 솔루션 폴더 아래에 있는 폴더(일반적으로 `bin`)에 출력 파일을 생성합니다. 그러나 컨테이너화된 프로젝트의 경우 빌드 프로세스에서 컨테이너화된 앱 빌드에 대한 Dockerfile의 지침을 고려합니다. Visual Studio에서 사용하는 Dockerfile은 여러 스테이지로 나누어져 있습니다. 이 프로세스는 Docker의 ‘다단계 빌드’ 기능을 사용합니다.

## <a name="multistage-build"></a>다단계 빌드

다단계 빌드 기능을 사용하면 컨테이너 빌드 프로세스를 보다 효율적으로 수행할 수 있으며, 앱이 런타임에 필요로 하는 비트만 포함하여 컨테이너를 더 작게 만들 수 있습니다. 다단계 빌드는 .NET Framework 프로젝트가 아닌 .NET Core 프로젝트에 사용됩니다.

다단계 빌드를 사용하면 중간 이미지를 생성하는 스테이지에서 컨테이너 이미지를 만들 수 있습니다. 예를 들어 Visual Studio에서 생성되는 일반적인 Dockerfile을 생각해 봅시다. 첫 번째 스테이지는 `base`입니다.

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

Dockerfile의 줄은 Microsoft Container Registry(mcr.microsoft.com)의 Debian 이미지로 시작하며 포트 80과 443을 공개하는 중간 이미지 `base`를 만든 다음, 작업 디렉터리를 `/app`으로 설정합니다.

다음 스테이지는 `build`이며 다음과 같이 표시됩니다.

```
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app
```

`build` 스테이지는 base에서 계속되는 것이 아니라 레지스트리의 다른 원본 이미지(`aspnet` 대신 `sdk`)에서 시작되는 것을 확인할 수 있습니다.  `sdk` 이미지에는 모든 빌드 도구가 포함되어 있으므로, 런타임 구성 요소만 포함하는 aspnet 이미지보다 훨씬 더 큽니다. Dockerfile의 나머지 부분을 살펴보면 개별 이미지를 사용해야 하는 이유가 명확해집니다.

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

최종 스테이지는 다시 `base`에서 시작되며, 게시된 출력을 최종 이미지에 복사하는 `COPY --from=publish`를 포함합니다. 이 프로세스를 사용하면 `sdk` 이미지에 있던 모든 빌드 도구를 포함할 필요가 없으므로 최종 이미지가 훨씬 더 작아질 수 있습니다.

## <a name="building-from-the-command-line"></a>명령줄에서 빌드

Visual Studio 외부에서 빌드하려는 경우 `docker build` 또는 `MSBuild`를 사용하여 명령줄에서 빌드할 수 있습니다.

### <a name="docker-build"></a>docker build

명령줄에서 컨테이너화된 솔루션을 빌드하려는 경우, 일반적으로 솔루션의 각 프로젝트에 대해 `docker build <context>` 명령을 사용할 수 있습니다. ‘빌드컨텍스트’ 인수를 제공합니다. Dockerfile의 ‘빌드 컨텍스트’는 이미지를 생성하기 위한 작업 폴더로 사용되는 로컬 컴퓨터의 폴더입니다. 예를 들어 컨테이너에 복사할 때, 복사할 파일이 들어 있는 폴더입니다.  .NET Core 프로젝트에서는 솔루션 파일(.sln)이 포함된 폴더를 사용합니다.  이 인수는 상대 경로로 표시되며, 일반적으로 프로젝트 폴더의 Dockerfile과 부모 폴더의 솔루션 파일은 “..”으로 지정됩니다.  .NET Framework 프로젝트의 빌드 컨텍스트는 솔루션 폴더가 아닌 프로젝트 폴더입니다.

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

Visual Studio에서 만든 .NET Framework 프로젝트용(및 Visual Studio 2017 업데이트 4 이전의 Visual Studio 버전에서 만든 .NET Core 프로젝트용) Dockerfile은 다단계 Dockerfile이 아닙니다.  해당 Dockerfile의 단계에서는 코드를 컴파일하지 않습니다.  대신, Visual Studio에서 .NET Framework Dockerfile을 빌드할 때 먼저 MSBuild를 사용하여 프로젝트를 컴파일합니다.  작업이 성공하면 Visual Studio에서 Dockerfile을 빌드합니다. 이 프로세스에서는 MSBuild의 빌드 출력을 결과 Docker 이미지에 복사하기만 합니다.  코드를 컴파일하는 단계가 Dockerfile에 포함되지 않기 때문에, 명령줄에서 `docker build`를 사용하여 .NET Framework Dockerfile을 빌드할 수 없습니다. 이러한 프로젝트를 빌드하려면 MSBuild를 사용해야 합니다.

단일 Docker 컨테이너 프로젝트용 이미지를 빌드하려는 경우, `/t:ContainerBuild` 명령 옵션과 함께 MSBuild를 사용할 수 있습니다. 예를 들어:

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

Visual Studio IDE에서 솔루션을 빌드할 때 **출력** 창에 표시되는 것과 유사한 출력이 표시됩니다. Visual Studio에서 다단계 빌드 최적화 기능을 사용하는 경우 **디버그** 구성을 빌드할 때 결과가 예상과 다를 수 있으므로 항상 `/p:Configuration=Release`를 사용합니다. [디버깅](#debugging)을 참조하세요.

Docker Compose 프로젝트를 사용하는 경우에는 다음 명령을 사용하여 이미지를 빌드합니다.

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="project-warmup"></a>프로젝트 준비

*프로젝트 준비*는 후속 실행의 성능을 향상하기 위해 프로젝트에 대해 Docker 프로필이 선택될 때(즉 프로젝트가 로드되거나 Docker 지원이 추가될 때) 발생하는 일련의 단계를 의미합니다(**F5** 또는 **Ctrl**+**F5**). 이 옵션은 **도구** > **옵션** > **컨테이너 도구**에서 구성할 수 있습니다. 다음은 백그라운드에서 실행되는 작업입니다.

- Docker Desktop이 설치되어 실행 중인지 확인합니다.
- Docker Desktop이 프로젝트와 동일한 운영 체제로 설정되어 있는지 확인합니다.
- Dockerfile의 첫 번째 스테이지(대부분 Dockerfile의 `base` 스테이지)에서 이미지를 풀합니다.  
- Dockerfile을 빌드하고 컨테이너를 시작합니다.

준비는 **고속** 모드에서만 발생하므로, 실행 중인 컨테이너에는 앱 폴더 볼륨이 탑재됩니다. 즉, 앱에 대한 변경 내용은 컨테이너를 무효화하지 않습니다. 따라서 디버깅 성능이 크게 향상되고 큰 이미지 풀하기처럼 오랫동안 실행되는 작업의 대기 시간이 줄어듭니다.

## <a name="volume-mapping"></a>볼륨 매핑

컨테이너에서 디버깅이 작동하기 위해 Visual Studio에서는 볼륨 매핑을 사용하여 호스트 머신의 디버거 및 NuGet 폴더를 매핑합니다. 볼륨 매핑은 [여기](https://docs.docker.com/storage/volumes/) Docker 설명서에 설명되어 있습니다. 컨테이너에 탑재된 볼륨은 다음과 같습니다.

|볼륨|설명|
|-|-|
| **원격 디버거** | 프로젝트 형식에 따라 컨테이너에서 디버거를 실행하는 데 필요한 비트를 포함합니다. 이 내용은 |[디버깅](#debugging) 섹션에 자세히 설명되어 있습니다.
| **앱 폴더** | Dockerfile이 있는 프로젝트 폴더를 포함합니다.|
| **소스 폴더** | Docker 명령에 전달되는 빌드 컨텍스트를 포함합니다.|
| **NuGet 패키지 폴더** | 프로젝트의 *obj\{project}.csproj.nuget.g.props* 파일에서 읽은 NuGet 패키지 및 대체 폴더를 포함합니다. |

ASP.NET Core 웹앱의 경우, SSL 인증서 및 사용자 비밀에 대한 추가 폴더가 두 개 있을 수 있습니다. 이 내용은 다음 섹션에 자세히 설명되어 있습니다.

## <a name="ssl-enabled-aspnet-core-apps"></a>SSL 사용 ASP.NET Core 앱

Visual Studio의 컨테이너 도구는 컨테이너 없이 작동하는 것과 동일한 방식으로 개발 인증서를 사용하여 SSL 사용 ASP.NET Core 앱의 디버깅을 지원합니다. 이러한 작업을 수행하기 위해 Visual Studio는 인증서를 내보내고 컨테이너에서 사용할 수 있도록 하는 몇 가지 단계를 더 추가합니다. 컨테이너에서 디버깅할 때 Visual Studio에서 처리하는 흐름은 다음과 같습니다.

1. 로컬 개발 인증서가 있고 `dev-certs` 도구를 통해 호스트 머신에서 신뢰할 수 있는지 확인합니다.
2. 이 특정 앱에 대한 사용자 비밀 저장소에 저장되어 있는 보안 암호를 사용하여 %APPDATA%\ASP.NET\Https로 인증서를 내보냅니다.
3. 다음 디렉터리에 볼륨을 탑재합니다.

   - *%APPDATA%\Microsoft\UserSecrets*
   - *%APPDATA%\ASP.NET\Https*

ASP.NET Core는 *Https* 폴더 아래에서 어셈블리 이름과 일치하는 인증서를 찾습니다. 그래서 해당 경로의 컨테이너에 매핑됩니다. 인증서 경로 및 암호는 환경 변수(즉, `ASPNETCORE_Kestrel__Certificates__Default__Path` 및 `ASPNETCORE_Kestrel__Certificates__Default__Password`) 또는 사용자 비밀 json 파일을 사용하여 정의할 수도 있습니다. 예:

```json
{
  "Kestrel": {
    "Certificates": {
      "Default": {
        "Path": "c:\\app\\mycert.pfx",
        "Password": "strongpassword"
      }
    }
  }
}
```

구성에서 컨테이너화된 빌드와 컨테이너화되지 않은 빌드를 모두 지원하는 경우에는 경로가 컨테이너 환경과 관련되므로 환경 변수를 사용해야 합니다.

컨테이너에서 ASP.NET Core 앱과 함께 SSL을 사용하는 방법에 대한 자세한 내용은 [HTTPS를 통해 Docker를 사용하여 ASP.NET Core 이미지 호스팅](/aspnet/core/security/docker-https)을 참조하세요.

## <a name="debugging"></a>디버깅

**디버그** 구성에서 빌드할 때, Visual Studio에서 컨테이너화된 프로젝트에 대한 빌드 프로세스의 성능 향상을 지원하는 여러 가지 최적화 기능이 있습니다. 컨테이너화된 앱의 빌드 프로세스는 Dockerfile에 설명된 단계만큼 간단하게 진행되지 않습니다. 컨테이너에서 빌드하는 경우 로컬 컴퓨터에서 빌드하는 것보다 훨씬 더 느립니다.  따라서 **디버그** 구성으로 빌드하는 경우, Visual Studio는 실제로 로컬 컴퓨터에서 프로젝트를 빌드한 다음, 볼륨 탑재를 사용하여 출력 폴더를 컨테이너에 공유합니다. 이 최적화 기능을 사용하는 빌드를 ‘고속’ 모드 빌드라고 합니다.

**고속** 모드에서 Visual Studio는 `base` 스테이지만 빌드하도록 Docker에 지시하는 인수를 사용하여 `docker build`를 호출합니다.  Visual Studio는 Dockerfile의 내용에 관계없이 프로세스의 나머지 부분을 처리합니다. 따라서 컨테이너 환경을 사용자 지정하거나 추가 종속성을 설치하기 위해 Dockerfile을 수정하는 경우, 수정 내용을 첫 번째 스테이지에 배치해야 합니다.  Dockerfile의 `build`, `publish` 또는 `final` 스테이지에 배치된 사용자 지정 단계는 모두 실행되지 않습니다.

이 성능 최적화 기능은 **디버그** 구성으로 빌드하는 경우에만 수행됩니다. **릴리스** 구성에서는 Dockerfile에 지정된 대로 컨테이너에서 빌드가 수행됩니다.

성능 최적화 기능을 사용하지 않고 Dockerfile에 지정된 대로 빌드하려면, 프로젝트 파일에서 다음과 같이 **ContainerDevelopmentMode** 속성을 **Regular**로 설정합니다.

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

성능 최적화 기능을 복원하려면 프로젝트 파일에서 해당 속성을 제거합니다.

 디버깅을 시작하면(**F5**) 이전에 시작한 컨테이너가 재사용됩니다(가능한 경우). 이전 컨테이너를 재사용하지 않으려는 경우, Visual Studio의 **다시 빌드** 또는 **정리** 명령을 사용하여 Visual Studio에서 새 컨테이너를 사용하도록 강제로 적용할 수 있습니다.

디버거를 실행하는 프로세스는 프로젝트 및 컨테이너 운영 체제의 형식에 따라 달라집니다.

|시나리오|디버거 프로세스|
|-|-|
| **.NET Core 앱(Linux 컨테이너)**| Visual Studio는 `vsdbg`를 다운로드하여 컨테이너에 매핑한 다음, 프로그램 및 인수(`dotnet webapp.dll`)를 사용하여 호출합니다. 그러면 디버거가 프로세스에 연결됩니다. |
| **.NET Core 앱(Windows 컨테이너)**| Visual Studio는 `onecoremsvsmon`을 사용하여 컨테이너에 매핑하고 진입점으로 실행한 다음, Visual Studio에서 연결하여 프로그램에 연결합니다. 이는 일반적으로 다른 컴퓨터 또는 가상 머신에서 원격 디버깅을 설정하는 방법과 비슷합니다.|
| **.NET Framework 앱** | Visual Studio는 `msvsmon`을 사용하여 컨테이너에 매핑하고, Visual Studio가 연결할 수 있는 진입점으로 실행하여 프로그램에 연결합니다.|

`vsdbg.exe`에 대한 자세한 내용은 [Visual Studio의 Linux 및 OSX에서 .NET Core의 오프로드 디버깅](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)을 참조하세요.

## <a name="container-entry-point"></a>컨테이너 진입점

Visual Studio는 프로젝트 형식 및 컨테이너 운영 체제에 따라 사용자 지정 컨테이너 진입점을 사용합니다. 다음과 같은 다양한 조합이 있습니다.

|컨테이너 유형|진입점|
|-|-|
| **Linux 컨테이너** | 진입점은 컨테이너를 계속 실행하기 위해 무한 대기하는 `tail -f /dev/null`입니다. 앱이 디버거를 통해 시작되면 앱 실행은 디버거에서 담당합니다(즉 `dotnet webapp.dll`). 디버그하지 않고 시작하는 경우 도구는 `docker exec -i {containerId} dotnet webapp.dll`을 실행하여 앱을 실행합니다.|
| **Windows 컨테이너**| 진입점은 디버거를 실행하는 `C:\remote_debugger\x64\msvsmon.exe /noauth /anyuser /silent /nostatus`와 비슷하기 때문에 연결을 수신 대기합니다. 디버그하지 않고 시작될 때, 디버거가 앱을 실행하고 `docker exec` 명령을 실행하는 경우도 마찬가지입니다. .NET Framework 웹앱의 경우 진입점은 `ServiceMonitor`가 명령에 추가되는 위치와 약간 다릅니다.|

컨테이너 진입점은 단일 컨테이너 프로젝트가 아닌 docker-compose 프로젝트에서만 수정할 수 있습니다.

## <a name="next-steps"></a>다음 단계

프로젝트 파일에서 추가 MSBuild 속성을 설정하여 빌드를 추가로 사용자 지정하는 방법을 알아봅니다. [컨테이너 프로젝트에 대한 MSBuild 속성](container-msbuild-properties.md)을 참조하세요.

## <a name="see-also"></a>참조

[MSBuild](../msbuild/msbuild.md)
[Windows의 Dockerfile](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
[Windows의 Linux 컨테이너](/virtualization/windowscontainers/deploy-containers/linux-containers)
