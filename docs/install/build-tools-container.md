---
title: Visual Studio Build Tools를 컨테이너에 설치
titleSuffix: ''
description: Visual Studio Build Tools를 Windows 컨테이너에 설치하여 CI/CD(연속 통합/지속적인 업데이트) 워크플로를 지원하는 방법을 알아봅니다.
ms.date: 03/25/2020
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 61ec972bd5e361c4417e49092de5976000a6da5f
ms.sourcegitcommit: dfa9476b69851c28b684ece66980bee735fef8fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80273896"
---
# <a name="install-build-tools-into-a-container"></a>Build Tools를 컨테이너에 설치

Visual Studio Build Tools를 Windows 컨테이너에 설치하여 CI/CD(지속적인 통합/지속적인 업데이트) 워크플로를 지원할 수 있습니다. 이 문서에서는 컨테이너에 설치할 수 있는 [워크로드 및 구성 요소](workload-component-id-vs-build-tools.md)뿐만 아니라 변경할 필요가 있는 Docker 구성을 안내합니다.

[컨테이너](https://www.docker.com/what-container)는 CI/CD 서버 환경뿐만 아니라 개발 환경에서도 사용할 수 있는 일관된 빌드 시스템을 패키지하는 유용한 방법입니다. 예를 들어 Visual Studio 또는 다른 도구를 사용하여 코드를 계속 작성하는 동안 사용자 지정 환경에서 빌드할 컨테이너에 소스 코드를 탑재할 수 있습니다. CI/CD 워크플로에서 동일한 컨테이너 이미지를 사용하면 코드를 일관되게 작성할 수 있습니다. 또한 런타임 일관성을 위해서도 컨테이너를 사용할 수 있습니다. 이 경우 오케스트레이션 시스템에서 여러 컨테이너를 사용하는 마이크로 서비스에는 일반적이지만 이 문서의 범위를 벗어납니다.

Visual Studio Build Tools에 소스 코드를 빌드하는 데 필요한 것이 없는 경우 다른 Visual Studio 제품에 대해 동일한 단계를 사용할 수 있습니다. 그러나 Windows 컨테이너는 대화형 사용자 인터페이스를 지원하지 않으므로 모든 명령을 자동화해야 합니다.

## <a name="before-you-begin"></a>시작하기 전에

아래에서는 [Docker](https://www.docker.com/what-docker)에 어느 정도 익숙한 것으로 간주합니다. Windows에서 Docker 실행에 대해 아직 익숙하지 않은 경우 [Windows에서 Docker 엔진 설치 및 구성](/virtualization/windowscontainers/manage-docker/configure-docker-daemon) 방법을 확인하세요.

아래 기본 이미지는 샘플이며 사용자 시스템에서는 작동하지 않을 수 있습니다. 사용자 환경에서 어떤 기본 이미지를 사용해야 하는지 확인하려면 [Windows 컨테이너 버전 호환성](/virtualization/windowscontainers/deploy-containers/version-compatibility)을 참조하세요.

## <a name="create-and-build-the-dockerfile"></a>Dockerfile 만들기 및 빌드

다음 예제 Dockerfile을 디스크의 새 파일에 저장합니다. 파일 이름이 단순히 "Dockerfile"이면 기본적으로 인식됩니다.

> [!WARNING]
> 이 Dockerfile 예제는 컨테이너에 설치할 수 없는 이전 버전의 Windows SDK만 제외합니다. 이전 릴리스에서는 빌드 명령이 실패하게 됩니다.

1. 명령 프롬프트를 엽니다.

1. 새 디렉터리를 만듭니다(권장).

   ```shell
   mkdir C:\BuildTools
   ```

1. 디렉터리를 이 새 디렉터리로 변경합니다.

   ```shell
   cd C:\BuildTools
   ```

1. 다음 내용을 C:\BuildTools\Dockerfile에 저장합니다.
 
   ::: moniker range="vs-2017"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.7.2.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.7.2-windowsservercore-ltsc2019

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
   RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --add Microsoft.VisualStudio.Workload.AzureBuildTools `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Define the entry point for the Docker container.
   # This entry point starts the developer command prompt and launches the PowerShell shell.
   ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!TIP]
   > 워크로드 및 구성 요소 목록은 [Visual Studio Build Tools 구성 요소 디렉터리](workload-component-id-vs-build-tools.md)를 참조하세요.
   >

   > [!WARNING]
   > 이미지가 직접 microsoft/windowsservercore 또는 mcr.microsoft.com/windows/servercore를 기반으로 하는 경우([Microsoft 신디케이트 컨테이너 카탈로그](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/) 참조) .NET Framework가 올바로 설치되지 않을 수 있으며 설치 오류 표시가 되지 않습니다. 관리 코드는 설치가 완료된 후 실행되지 않을 수 있습니다. 대신, [microsoft/dotnet-framework:4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) 이상에서 이미지를 기반으로 합니다. 또한 버전 4.7.2 이상 태그가 지정된 이미지는 `RUN` 및 `ENTRYPOINT` 지침 실패로 이어지는 기본값 `SHELL`로 PowerShell을 사용할 수 있습니다.
   >
   > Visual Studio 2017 버전 15.8 또는 이전 버전(제품)이 mcr.microsoft.com/windows/servercore:1809 이상에 제대로 설치되지 않습니다. 오류가 표시되지 않습니다.
   >
   > 어떤 호스트 OS 버전에 어떤 컨테이너 OS 버전이 지원되는지 확인하려면 [Windows 컨테이너 버전 호환성](/virtualization/windowscontainers/deploy-containers/version-compatibility)을 참조하고, 알려진 문제의 경우에는 [알려진 컨테이너 관련 문제](build-tools-container-issues.md)를 참조하세요.
   
   ::: moniker-end

   ::: moniker range="vs-2019"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.8.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/16/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
   RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --add Microsoft.VisualStudio.Workload.AzureBuildTools `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Define the entry point for the docker container.
   # This entry point starts the developer command prompt and launches the PowerShell shell.
   ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!TIP]
   > 워크로드 및 구성 요소 목록은 [Visual Studio Build Tools 구성 요소 디렉터리](workload-component-id-vs-build-tools.md)를 참조하세요.
   >

   > [!WARNING]
   > microsoft/windowsservercore에 이미지를 직접 베이스하는 경우 .NET Framework는 제대로 설치되지 않을 수 있으며 설치 오류가 표시되지 않습니다. 관리 코드는 설치가 완료된 후 실행되지 않을 수 있습니다. 대신, [microsoft/dotnet-framework:4.8](https://hub.docker.com/r/microsoft/dotnet-framework) 이상에서 이미지를 베이스합니다. 또한 버전 4.8 이상 태그가 지정된 이미지는 `RUN` 및 `ENTRYPOINT` 지침 실패로 이어지는 기본값 `SHELL`로 PowerShell을 사용할 수 있습니다.
   >
   > 어떤 호스트 OS 버전에 어떤 컨테이너 OS 버전이 지원되는지 확인하려면 [Windows 컨테이너 버전 호환성](/virtualization/windowscontainers/deploy-containers/version-compatibility)을 참조하고, 알려진 문제의 경우에는 [알려진 컨테이너 관련 문제](build-tools-container-issues.md)를 참조하세요.

   ::: moniker-end
   
   > [!NOTE]
   > 오류 코드 `3010`은 재부팅이 성공해야 함을 나타내는 데 사용됩니다. 자세한 내용은 [MsiExec.exe 오류 메시지](/windows/win32/msi/error-codes)를 참조하세요.

1. 해당 디렉터리 내에서 다음 명령을 실행합니다.

   ::: moniker range="vs-2017"

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   이 명령은 현재 디렉터리에서 2GB의 메모리를 사용하여 Dockerfile을 빌드합니다. 일부 작업을 설치하는 경우 기본 1GB가 충분하지 않지만 빌드 요구 사항에 따라 1GB의 메모리만으로도 빌드할 수 있습니다.

   최종 이미지에는 "buildtools2017:latest"라는 태그가 지정됩니다. 태그가 지정되지 않더라도 "latest" 태그가 기본값이므로 컨테이너에서 해당 이미지를 "buildtools2017"로 쉽게 실행할 수 있습니다. 더 많은 [고급 시나리오](advanced-build-tools-container.md)에서 특정 버전의 Visual Studio Build Tools 2017을 사용하려는 경우, 컨테이너에서 특정 버전을 일관되게 사용할 수 있도록 특정 Visual Studio 빌드 번호뿐만 아니라 "latest"도 포함된 태그를 컨테이너에 지정할 수도 있습니다.

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker build -t buildtools2019:latest -m 2GB .
   ```

   이 명령은 현재 디렉터리에서 2GB의 메모리를 사용하여 Dockerfile을 빌드합니다. 일부 작업을 설치하는 경우 기본 1GB가 충분하지 않지만 빌드 요구 사항에 따라 1GB의 메모리만으로도 빌드할 수 있습니다.

   최종 이미지에는 "buildtools2019:latest"라는 태그가 지정됩니다. 태그가 지정되지 않더라도 "latest" 태그가 기본값이므로 컨테이너에서 해당 이미지를 "buildtools2019"로 쉽게 실행할 수 있습니다. 더 많은 [고급 시나리오](advanced-build-tools-container.md)에서 특정 버전의 Visual Studio Build Tools 2019를 사용하려는 경우, 컨테이너에서 특정 버전을 일관되게 사용할 수 있도록 특정 Visual Studio 빌드 번호뿐만 아니라 "latest"도 포함된 태그를 컨테이너에 지정할 수도 있습니다.

   ::: moniker-end

## <a name="using-the-built-image"></a>빌드된 이미지 사용

이제 이미지를 만들었으므로 컨테이너 내에서 해당 이미지를 실행하여 대화형 빌드와 자동화된 빌드를 모두 수행할 수 있습니다. 이 예제에서는 개발자 명령 프롬프트를 사용하므로 PATH 및 기타 환경 변수가 이미 구성되어 있습니다.

1. 명령 프롬프트를 엽니다.

1. 컨테이너를 실행하여 모든 개발자 환경 변수가 설정된 PowerShell 환경을 시작합니다.

   ::: moniker range="vs-2017"

   ```shell
   docker run -it buildtools2017
   ```

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker run -it buildtools2019
   ```

   ::: moniker-end

이 이미지를 CI/CD 워크플로에 사용하려면 자신의 [Azure Container Registry](https://azure.microsoft.com/services/container-registry) 또는 다른 내부 [Docker 레지스트리](https://docs.docker.com/registry/deploying)에 게시하여 서버에서 끌어오기만 하면 됩니다.

   > [!NOTE]
   > Docker 컨테이너가 시작되지 않는다면 Visual Studio 설치 문제가 있는 것일 수 있습니다. Visual Studio 일괄 처리 명령을 호출하는 단계가 제거되도록 Dockerfile을 업데이트해 보세요. 이렇게 하면 Docker 컨테이너를 시작하고 설치 오류 로그를 읽을 수 있습니다.
   >
   > Dockerfile 파일에서 `ENTRYPOINT` 명령의 `C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat` 매개 변수와 `&&` 매개 변수를 제거합니다. 그러면 명령이 `ENTRYPOINT ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]`가 됩니다. 다음으로 Dockerfile을 다시 빌드하고 `run` 명령을 실행하여 컨테이너 파일에 액세스합니다. 설치 오류 로그를 찾으려면 `$env:TEMP` 디렉터리로 이동하여 `dd_setup_<timestamp>_errors.log` 파일을 찾습니다.
   >
   > 설치 문제를 찾아서 해결한 후에는 `ENTRYPOINT` 명령에 `C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat` 매개 변수와 `&&` 매개 변수를 추가하고 Dockerfile을 다시 빌드하면 됩니다.
   >
   > 자세한 내용은 [컨테이너의 알려진 문제](build-tools-container-issues.md)를 참조하세요.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참고 항목

* [고급 컨테이너 예제](advanced-build-tools-container.md)
* [알려진 컨테이너 관련 문제](build-tools-container-issues.md)
* [Visual Studio Build Tools 워크로드 및 구성 요소 ID](workload-component-id-vs-build-tools.md)
