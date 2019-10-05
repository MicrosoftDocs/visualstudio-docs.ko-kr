---
title: Visual Studio Container Tools Docker Compose 빌드 설정
author: ghogen
description: 컨테이너 도구 빌드 프로세스 개요
ms.author: ghogen
ms.date: 08/12/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 06a1c5b637ca2ed9306162ee1960c60d103e5843
ms.sourcegitcommit: 88f576ac32af31613c1a10c1548275e1ce029f4f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71185975"
---
# <a name="docker-compose-build-properties"></a>Docker Compose 빌드 속성

[컨테이너 도구 빌드 속성](container-msbuild-properties.md)에 설명된 개별 Docker 프로젝트 제어 속성 외에도, MSBuild에서 솔루션을 빌드하는 데 사용하는 Docker Compose 속성을 설정하여 Visual Studio에서 Docker Compose 프로젝트를 빌드하는 방식을 사용자 지정할 수 있습니다. Docker Compose 구성 파일에서 파일 레이블을 설정하여 Visual Studio 디버거가 Docker Compose 앱을 실행하는 방식을 제어할 수도 있습니다.

## <a name="how-to-set-the-msbuild-properties"></a>MSBuild 속성을 설정하는 방법

속성의 값을 설정하려면 프로젝트 파일을 편집합니다. 다음 섹션의 표에 달리 표시되지 않은 경우, Docker Compose 속성에 대한 이 프로젝트 파일은 .dcproj 확장명을 사용합니다. 예를 들어 디버깅을 시작할 때 브라우저를 시작하도록 지정한다고 가정해 봅시다. .dcproj 프로젝트 파일의 `DockerLaunchAction` 속성을 다음과 같이 설정할 수 있습니다.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

기존 `PropertyGroup` 요소에 속성 설정을 추가하거나, 기존 요소가 없는 경우 새 `PropertyGroup` 요소를 만들 수 있습니다.

## <a name="docker-compose-msbuild-properties"></a>Docker Compose MSBuild 속성

다음 표에서는 Docker Compose 프로젝트에 사용할 수 있는 MSBuild 속성을 보여 줍니다.

| 속성 이름 | 위치 | 설명 | 기본값  |
|---------------|----------|-------------|----------------|
|DockerComposeBuildArguments|dcproj|`docker-compose build` 명령에 전달할 추가 매개 변수를 지정합니다. 예를 들어 `--parallel --pull` |
|DockerComposeDownArguments|dcproj|`docker-compose down` 명령에 전달할 추가 매개 변수를 지정합니다. 예를 들어 `--timeout 500`|-|  
|DockerComposeProjectPath|csproj 또는 vbproj|docker-compose 프로젝트(dcproj) 파일의 상대 경로입니다. 서비스 프로젝트를 게시할 때 이 속성을 설정하여 docker-compose.yml 파일에 저장된 관련 이미지 빌드 설정을 찾습니다.|-|
|DockerComposeUpArguments|dcproj|`docker-compose up` 명령에 전달할 추가 매개 변수를 지정합니다. 예를 들어 `--timeout 500`|-|
|DockerLaunchAction| dcproj | F5 키나 Ctrl+F5를 누를 때 수행할 시작 작업을 지정합니다.  허용되는 값은 None, LaunchBrowser, LaunchWCFTestClient입니다.|없음|
|DockerLaunchBrowser| dcproj | 브라우저를 시작할지 여부를 나타냅니다. DockerLaunchAction을 지정한 경우에는 무시됩니다. | False |
|DockerServiceName| dcproj|DockerLaunchAction 또는 DockerLaunchBrowser를 지정한 경우, DockerServiceName은 시작할 서비스의 이름입니다.  이 속성을 사용하여 docker-compose 파일에서 참조할 수 있는 많은 프로젝트 중 시작할 프로젝트를 확인합니다.|-|
|DockerServiceUrl| dcproj | 브라우저를 시작할 때 사용할 URL입니다.  유효한 대체 토큰은 “{ServiceIPAddress}”, “{ServicePort}”, “{Scheme}”입니다.  예: {Scheme}://{ServiceIPAddress}:{ServicePort}|-|
|DockerTargetOS| dcproj | Docker 이미지를 빌드할 때 사용되는 대상 OS입니다.|-|

> [!NOTE]
> DockerComposeBuildArguments, DockerComposeDownArguments 및 DockerComposeUpArguments는 Visual Studio 2019 버전 16.3 미리 보기 3에서 새로 추가되었습니다.

## <a name="docker-compose-file-labels"></a>Docker Compose 파일 레이블

*docker-compose.vs.debug.yml*(**디버그** 구성) 또는 *docker-compose.vs.release.yml*(**릴리스** 구성)을 *docker-compose.yml* 파일과 동일한 디렉터리에 배치하여 특정 설정을 재정의할 수도 있습니다.  이 파일에서 다음과 같이 설정을 지정할 수 있습니다.

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

앞의 예제와 같이 값을 큰따옴표로 묶고, 경로의 백슬래시에 대한 이스케이프 문자로 백슬래시를 사용합니다.

|레이블 이름|설명|
|----------|-----------|
|com.microsoft.visualstudio.debuggee.arguments|디버깅을 시작할 때 프로그램에 전달되는 인수입니다. .NET Core 앱에서 이 인수는 일반적으로 NuGet 패키지의 추가 검색 경로와 프로젝트의 출력 어셈블리 경로입니다.|
|com.microsoft.visualstudio.debuggee.killprogram|이 명령은 필요한 경우 컨테이너 내부에서 실행 중인 디버기 프로그램을 중지하는 데 사용됩니다.|
|com.microsoft.visualstudio.debuggee.program|디버깅을 시작할 때 시작되는 프로그램입니다. .NET Core 앱에서 이 설정은 일반적으로 **dotnet**입니다.|
|com.microsoft.visualstudio.debuggee.workingdirectory|디버깅을 시작할 때 시작 디렉터리로 사용되는 디렉터리입니다. 이 설정은 일반적으로 Linux 컨테이너의 경우 */app*, Windows 컨테이너의 경우 *C:\app*입니다.|

## <a name="next-steps"></a>다음 단계

MSBuild 속성에 대한 일반적인 내용은 [MSBuild 속성](../msbuild/msbuild-properties.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[컨테이너 도구 빌드 속성](container-msbuild-properties.md)

[컨테이너 도구 시작 설정](container-launch-settings.md)

[MSBuild의 예약된 속성 및 잘 알려진 속성](../msbuild/msbuild-reserved-and-well-known-properties.md)