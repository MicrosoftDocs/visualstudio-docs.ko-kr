---
title: Docker Compose 빌드 설정
author: ghogen
description: 컨테이너 도구 빌드 프로세스 개요
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 08/12/2019
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: a25aca5082d8a55eccff861d542d16095c178a4f
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036303"
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

| 속성 이름 | 위치 | Description | 기본값  |
|---------------|----------|-------------|----------------|
|AdditionalComposeFilePaths|dcproj|모든 명령에 대해 docker-compose.exe로 보낼 세미콜론으로 구분된 목록에 추가 작성 파일을 지정합니다. dcproj(docker-compose project) 파일에서 상대 경로가 허용됩니다.|-|
|DockerComposeBaseFilePath|dcproj|*.yml* 확장명을 사용하지 않고 docker-compose 파일의 파일 이름 중 첫 번째 부분을 지정합니다. 다음은 그 예입니다. <br>1.  DockerComposeBaseFilePath = null/undefined: 기본 파일 경로 *docker-compose*를 사용하면 파일 이름이 *docker-compose.yml* 및 *docker-compose.override.yml*이 됩니다.<br>2.   DockerComposeBaseFilePath = *mydockercompose*: 파일 이름은 *mydockercompose.yml* 및 *mydockercompose.override.yml*이 됩니다.<br> 3.  DockerComposeBaseFilePath = *..\mydockercompose*: 파일이 한 수준 올라갑니다. |docker-compose|
|DockerComposeBuildArguments|dcproj|`docker-compose build` 명령에 전달할 추가 매개 변수를 지정합니다. 예를 들어 `--parallel --pull` |
|DockerComposeDownArguments|dcproj|`docker-compose down` 명령에 전달할 추가 매개 변수를 지정합니다. 예를 들어 `--timeout 500`|-|  
|DockerComposeProjectPath|csproj 또는 vbproj|docker-compose 프로젝트(dcproj) 파일의 상대 경로입니다. 서비스 프로젝트를 게시할 때 이 속성을 설정하여 docker-compose.yml 파일에 저장된 관련 이미지 빌드 설정을 찾습니다.|-|
|DockerComposeUpArguments|dcproj|`docker-compose up` 명령에 전달할 추가 매개 변수를 지정합니다. 예를 들어 `--timeout 500`|-|
|DockerDevelopmentMode|dcproj| “호스트에서 빌드” 최적화(“고속 모드” 디버깅)를 사용할지 여부를 제어합니다.  허용되는 값은 **Fast**와 **Regular**입니다. | 빠름 |
|DockerLaunchAction| dcproj | F5 키나 Ctrl+F5를 누를 때 수행할 시작 작업을 지정합니다.  허용되는 값은 None, LaunchBrowser, LaunchWCFTestClient입니다.|None|
|DockerLaunchBrowser| dcproj | 브라우저를 시작할지 여부를 나타냅니다. DockerLaunchAction을 지정한 경우에는 무시됩니다. | False |
|DockerServiceName| dcproj|DockerLaunchAction 또는 DockerLaunchBrowser를 지정한 경우, DockerServiceName은 시작할 서비스의 이름입니다.  이 속성을 사용하여 docker-compose 파일에서 참조할 수 있는 많은 프로젝트 중 시작할 프로젝트를 확인합니다.|-|
|DockerServiceUrl| dcproj | 브라우저를 시작할 때 사용할 URL입니다.  유효한 대체 토큰은 “{ServiceIPAddress}”, “{ServicePort}”, “{Scheme}”입니다.  예: {Scheme}://{ServiceIPAddress}:{ServicePort}|-|
|DockerTargetOS| dcproj | Docker 이미지를 빌드할 때 사용되는 대상 OS입니다.|-|

## <a name="example"></a>예제

`DockerComposeBaseFilePath`를 상대 경로로 설정하여 Docker Compose 파일의 위치를 변경하는 경우 솔루션 폴더를 참조하도록 빌드 컨텍스트가 변경되었는지도 확인해야 합니다. 예를 들어 Docker Compose 파일이 *DockerComposeFiles*라는 폴더인 경우 Docker Compose 파일은 솔루션 폴더를 기준으로 한 상대 위치에 따라 빌드 컨텍스트를 “..” 또는 “../..”으로 설정해야 합니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0" Sdk="Microsoft.Docker.Sdk">
  <PropertyGroup Label="Globals">
    <ProjectVersion>2.1</ProjectVersion>
    <DockerTargetOS>Windows</DockerTargetOS>
    <ProjectGuid>154022c1-8014-4e9d-bd78-6ff46670ffa4</ProjectGuid>
    <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
    <DockerServiceUrl>{Scheme}://{ServiceIPAddress}{ServicePort}</DockerServiceUrl>
    <DockerServiceName>webapplication1</DockerServiceName>
    <DockerComposeBaseFilePath>DockerComposeFiles\mydockercompose</DockerComposeBaseFilePath>
    <AdditionalComposeFilePaths>AdditionalComposeFiles\myadditionalcompose.yml</AdditionalComposeFilePaths>
  </PropertyGroup>
  <ItemGroup>
    <None Include="DockerComposeFiles\mydockercompose.override.yml">
      <DependentUpon>DockerComposeFiles\mydockercompose.yml</DependentUpon>
    </None>
    <None Include="DockerComposeFiles\mydockercompose.yml" />
    <None Include=".dockerignore" />
  </ItemGroup>
</Project>
```

*mydockercompose.yml* 파일은 다음과 같으며, 빌드 컨텍스트가 솔루션 폴더의 상대 경로(이 경우 `..`)로 설정된 상태입니다.

```yml
version: '3.4'

services:
  webapplication1:
    image: ${DOCKER_REGISTRY-}webapplication1
    build:
      context: ..
      dockerfile: WebApplication1\Dockerfile
```

> [!NOTE]
> DockerComposeBuildArguments, DockerComposeDownArguments 및 DockerComposeUpArguments는 Visual Studio 2019 버전 16.3에 새로 추가되었습니다.

## <a name="docker-compose-file-labels"></a>Docker Compose 파일 레이블

*docker-compose.vs.debug.yml*(**디버그** 구성) 또는 *docker-compose.vs.release.yml*(**릴리스** 구성)을 *docker-compose.yml* 파일과 동일한 디렉터리에 배치하여 특정 설정을 재정의할 수도 있습니다.  이 파일에서 다음과 같이 설정을 지정할 수 있습니다.

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

앞의 예제와 같이 값을 큰따옴표로 묶고, 경로의 백슬래시에 대한 이스케이프 문자로 백슬래시를 사용합니다.

|레이블 이름|Description|
|----------|-----------|
|com.microsoft.visualstudio.debuggee.arguments|디버깅을 시작할 때 프로그램에 전달되는 인수입니다. .NET Core 앱에서 이 인수는 일반적으로 NuGet 패키지의 추가 검색 경로와 프로젝트의 출력 어셈블리 경로입니다.|
|com.microsoft.visualstudio.debuggee.killprogram|이 명령은 필요한 경우 컨테이너 내부에서 실행 중인 디버기 프로그램을 중지하는 데 사용됩니다.|
|com.microsoft.visualstudio.debuggee.program|디버깅을 시작할 때 시작되는 프로그램입니다. .NET Core 앱에서 이 설정은 일반적으로 **dotnet**입니다.|
|com.microsoft.visualstudio.debuggee.workingdirectory|디버깅을 시작할 때 시작 디렉터리로 사용되는 디렉터리입니다. 이 설정은 일반적으로 Linux 컨테이너의 경우 */app*, Windows 컨테이너의 경우 *C:\app*입니다.|

## <a name="customize-the-app-startup-process"></a>앱 시작 프로세스 사용자 지정

`entrypoint` 설정을 사용하여 앱을 시작하고 구성에 종속되도록 만들기 전에 명령 또는 사용자 지정 스크립트를 실행할 수 있습니다. 예를 들어 `update-ca-certificates`를 실행하여 **릴리스** 모드가 아닌 **디버그** 모드에서만 인증서를 설정해야 한다면 *docker-compose.ci.build.yml*에만 다음 코드를 추가할 수 있습니다.

```yml
services:
  webapplication1:
    entrypoint: "sh -c 'update-ca-certificates && tail -f /dev/null'"
    labels:
      ...
```

*docker-compose.vs.release.yml* 또는 *docker-compose.vs.debug.yml*을 생략하는 경우 Visual Studio가 기본 설정에 따라 하나를 생성합니다.

## <a name="next-steps"></a>다음 단계

MSBuild 속성에 대한 일반적인 내용은 [MSBuild 속성](../msbuild/msbuild-properties.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[컨테이너 도구 빌드 속성](container-msbuild-properties.md)

[컨테이너 도구 시작 설정](container-launch-settings.md)

[MSBuild의 예약된 속성 및 잘 알려진 속성](../msbuild/msbuild-reserved-and-well-known-properties.md)
