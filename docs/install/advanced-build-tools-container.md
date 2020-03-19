---
title: 컨테이너에 대한 고급 예제
description: ''
ms.date: 07/03/2019
ms.topic: conceptual
ms.assetid: e03835db-a616-41e6-b339-92b41d0cfc70
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: b0a88815c4a2853270b539a3e012297b681af62e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114948"
---
# <a name="advanced-example-for-containers"></a>컨테이너에 대한 고급 예제

::: moniker range="vs-2017"

[컨테이너에 빌드 도구 설치](build-tools-container.md)에서 샘플 Dockerfile은 항상 최신 microsoft/windowsservercore 이미지와 최신 Visual Studio Build Tools 설치 관리자를 기반으로 하는 [microsoft/dotnet-framework:4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) 이미지를 사용합니다. 이 이미지를 다른 사용자가 풀할 수 있는 [Docker 레지스트리](https://azure.microsoft.com/services/container-registry)에 게시할 경우 많은 시나리오에 괜찮을 수 있습니다. 그러나 실제로 사용하는 기본 이미지, 다운로드하는 바이너리, 그리고 설치하는 도구 버전에 대해 더 구체적인 것이 일반적입니다.

::: moniker-end

::: moniker range="vs-2019"

[컨테이너에 빌드 도구 설치](build-tools-container.md)에서 샘플 Dockerfile은 항상 최신 microsoft/windowsservercore 이미지와 최신 Visual Studio Build Tools 설치 관리자를 기반으로 하는 [microsoft/dotnet-framework:4.8](https://hub.docker.com/r/microsoft/dotnet-framework) 이미지를 사용합니다. 이 이미지를 다른 사용자가 풀할 수 있는 [Docker 레지스트리](https://azure.microsoft.com/services/container-registry)에 게시할 경우 많은 시나리오에 괜찮을 수 있습니다. 그러나 실제로 사용하는 기본 이미지, 다운로드하는 바이너리, 그리고 설치하는 도구 버전에 대해 더 구체적인 것이 일반적입니다.

::: moniker-end

다음 예제의 Dockerfile은 microsoft/dotnet-framework 이미지의 특정 버전 태그를 사용합니다. 기본 이미지에 특정 태그를 사용하는 것이 일반적이며 이미지를 빌드 또는 다시 빌드할 때 항상 동일한 근거가 있다는 점을 기억하는 것이 쉽습니다.

> [!NOTE]
> 컨테이너에서 설치 관리자 실행 시 알려진 문제가 있는 microsoft/windowsservercore:10.0.14393.1593 또는 이를 기반으로 하는 이미지에는 Visual Studio를 설치할 수 없습니다. 자세한 내용은 [컨테이너의 알려진 문제](build-tools-container-issues.md)를 참조하세요.

다음 예제에서는 최신 릴리스의 Build Tools를 다운로드합니다. 나중에 컨테이너에 설치할 수 있는 이전 버전의 Build Tools를 사용하려면 먼저 레이아웃을 [만들고](create-an-offline-installation-of-visual-studio.md)[유지](update-a-network-installation-of-visual-studio.md)해야 합니다.

## <a name="install-script"></a>스크립트 설치

설치 오류가 발생할 때 로그를 수집하려면 다음 콘텐츠를 포함하는 작업 디렉터리에서 "Install.cmd"라는 일괄 처리 스크립트를 만듭니다.

```shell
@if not defined _echo echo off
setlocal enabledelayedexpansion

call %*
if "%ERRORLEVEL%"=="3010" (
    exit /b 0
) else (
    if not "%ERRORLEVEL%"=="0" (
        set ERR=%ERRORLEVEL%
        call C:\TEMP\collect.exe -zip:C:\vslogs.zip

        exit /b !ERR!
    )
)
```

## <a name="dockerfile"></a>Dockerfile

작업 디렉터리에서 다음 콘텐츠로 "Dockerfile"을 만듭니다.

::: moniker range="vs-2017"

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:3eaa3ba18f45e6561f32d8dd927045413f1dd043d7d29fb581f5cb3c6f7d7481
ARG FROM_IMAGE=mcr.microsoft.com/dotnet/framework/sdk:4.7.2-windowsservercore-ltsc2019
FROM ${FROM_IMAGE}

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/15/release/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Download and install Build Tools excluding workloads and components with known issues.
ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --all `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Start developer command prompt with any other commands specified.
ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

# Default to PowerShell if no other command specified.
CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

   > [!WARNING]
   > Visual Studio 2017 버전 15.8 또는 이전 버전(제품)이 mcr\.microsoft\.com\/windows\/servercore:1809 이상에 제대로 설치되지 않습니다. 오류가 표시되지 않습니다.
   >
   > 자세한 내용은 [컨테이너의 알려진 문제](build-tools-container-issues.md)를 참조하세요.

::: moniker-end

::: moniker range="vs-2019"

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:324e9ab7262331ebb16a4100d0fb1cfb804395a766e3bb1806c62989d1fc1326
ARG FROM_IMAGE=mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019
FROM ${FROM_IMAGE}

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/16/release/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Download and install Build Tools excluding workloads and components with known issues.
ADD https://aka.ms/vs/16/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --all `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Start developer command prompt with any other commands specified.
ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

# Default to PowerShell if no other command specified.
CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

::: moniker-end

다음 명령을 실행하여 현재 작업 디렉터리에 이미지를 빌드합니다.

::: moniker range="vs-2017"

```shell
docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
```

::: moniker-end

::: moniker range="vs-2019"

```shell
docker build -t buildtools2019:16.0.28714.193 -t buildtools2019:latest -m 2GB .
```

::: moniker-end

필요에 따라 `FROM_IMAGE` 명령줄 스위치를 사용하여 `CHANNEL_URL` 또는 `--build-arg` 인수 중 하나 또는 모두를 전달하여 고정된 이미지를 유지하도록 다른 기본 이미지 또는 내부 레이아웃의 위치를 지정합니다.

## <a name="diagnosing-install-failures"></a>설치 오류 진단

이 예제에서는 특정 도구를 다운로드하고 해시가 일치하는지 검증합니다. 또한 설치 실패가 발생할 경우 호스트 시스템으로 로그를 복사하여 실패를 분석할 수 있도록 최신 Visual Studio 및 .NET 로컬 컬렉션을 다운로드합니다.

::: moniker range="vs-2017"

```shell
> docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
Sending build context to Docker daemon

...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

::: moniker-end

::: moniker range="vs-2019"

```shell
> docker build -t buildtools2019:16.0.28714.193 -t buildtools2019:latest -m 2GB .
Sending build context to Docker daemon

...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

::: moniker-end

마지막 줄의 실행이 끝나면 머신에서 "%TEMP%\vslogs.zip"을 열거나 [개발자 커뮤니티](https://developercommunity.visualstudio.com) 웹 사이트에서 문제를 제출합니다.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참고 항목

* [Build Tools를 컨테이너에 설치](build-tools-container.md)
* [컨테이너에 대한 알려진 문제](build-tools-container-issues.md)
* [Visual Studio Build Tools 워크로드 및 구성 요소 ID](workload-component-id-vs-build-tools.md)
