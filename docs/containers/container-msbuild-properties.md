---
title: Visual Studio Container Tools 빌드 속성
author: ghogen
description: 컨테이너 도구 빌드 프로세스 개요
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 987d358abcccadf36d15593722ff55ba4b879d03
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "71950693"
---
# <a name="container-tools-build-properties"></a>컨테이너 도구 빌드 속성

MSBuild에서 프로젝트를 빌드하는 데 사용하는 속성을 설정하여 Visual Studio에서 컨테이너 프로젝트를 빌드하는 방식을 사용자 지정할 수 있습니다. 예를 들어 Dockerfile의 이름을 변경하고, 이미지의 태그 및 레이블을 지정하고, Docker 명령에 전달되는 추가 인수를 제공하고, Visual Studio에서 컨테이너 환경 외부 빌드와 같은 특정 성능 최적화를 수행할지 여부를 제어할 수 있습니다. 시작할 실행 파일의 이름, 제공할 명령줄 인수와 같은 디버깅 속성을 설정할 수도 있습니다.

속성의 값을 설정하려면 프로젝트 파일을 편집합니다. 예를 들어 Dockerfile의 이름이 *MyDockerfile*이라고 가정해 봅시다. 프로젝트 파일에서 `DockerfileFile` 속성을 다음과 같이 설정할 수 있습니다.

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

기존 `PropertyGroup` 요소에 속성 설정을 추가하거나, 기존 요소가 없는 경우 새 `PropertyGroup` 요소를 만들 수 있습니다.

다음 표에서는 컨테이너 프로젝트에 사용할 수 있는 MSBuild 속성을 보여 줍니다. NuGet 패키지 버전은 [Microsoft.VisualStudio.Azure.Containers.Tools.Targets](https://www.nuget.org/packages/Microsoft.VisualStudio.Azure.Containers.Tools.Targets/)에 적용됩니다.

| 속성 이름 | 설명 | 기본값  | NuGet 패키지 버전|
|---------------|-------------|----------------|----------------------|
| ContainerDevelopmentMode | “호스트에서 빌드” 최적화(“고속 모드” 디버깅)를 사용할지 여부를 제어합니다.  허용되는 값은 **Fast**와 **Regular**입니다. | Fast |1.0.1872750 이상|
| ContainerVsDbgPath | VSDBG 디버거의 경로입니다. | `%USERPROFILE%\vsdbg\vs2017u5` |1.0.1985401 이상|
| DockerDebuggeeArguments | 디버그 시, 이 인수를 시작된 실행 파일에 전달하도록 디버거에 지시합니다. | ASP.NET .NET Framework 프로젝트에는 사용할 수 없습니다. |1.7.8 이상|
| DockerDebuggeeProgram | 디버그 시, 실행 파일을 시작하도록 디버거에 지시합니다. | .NET Core 프로젝트의 경우: dotnet, ASP.NET .NET Framework 프로젝트의 경우: 사용할 수 없습니다(IIS는 항상 사용됨). |1.7.8 이상|
| DockerDebuggeeKillProgram | 이 명령은 컨테이너에서 실행 중인 프로세스를 종료하는 데 사용됩니다. | ASP.NET .NET Framework 프로젝트에는 사용할 수 없습니다. |1.7.8 이상|
| DockerDebuggeeWorkingDirectory | 디버그 시, 이 경로를 작업 디렉터리로 사용하도록 디버거에 지시합니다. | C:\app(Windows) 또는 /app(Linux) |1.7.8 이상|
| DockerDefaultTargetOS | Docker 이미지를 빌드할 때 사용되는 기본 대상 운영 체제입니다. | Visual Studio에서 설정됩니다. |1.0.1985401 이상|
| DockerImageLabels | Docker 이미지에 적용되는 기본 레이블 집합입니다. | com.microsoft.created-by=visual-studio;com.microsoft.visual-studio.project-name=$(MSBuildProjectName) |1.5.4 이상|
| DockerFastModeProjectMountDirectory|**고속 모드**에서 이 속성은 프로젝트 출력 디렉터리가 실행 중인 컨테이너에 대량 탑재되는 위치를 제어합니다.|C:\app(Windows) 또는 /app(Linux)|1.9.2 이상|
| DockerfileBuildArguments | Docker build 명령에 전달되는 추가 인수입니다. | 해당 사항 없음. |1.0.1872750 이상|
| DockerfileContext | Docker 이미지를 빌드할 때 사용되는 기본 컨텍스트입니다. | Visual Studio에서 설정됩니다. |1.0.1872750 이상|
| DockerfileFastModeStage | 디버그 모드로 이미지를 빌드할 때 사용되는 Dockerfile 스테이지(즉, 대상)입니다. | Dockerfile에 있는 첫 번째 스테이지(base) |
| DockerfileFile | 프로젝트의 컨테이너를 빌드/실행하는 데 사용되는 기본 Dockerfile에 대해 설명합니다. 경로일 수도 있습니다. | Dockerfile |1.0.1872750 이상|
| DockerfileRunArguments | Docker run 명령에 전달되는 추가 인수입니다. | 해당 사항 없음. |1.0.1872750 이상|
| DockerfileRunEnvironmentFiles | Docker 실행 중에 적용되는 환경 파일의 세미콜론으로 구분된 목록입니다. | 해당 사항 없음. |1.0.1872750 이상|
| DockerfileTag | Docker 이미지를 빌드할 때 사용되는 태그입니다. 디버그 시, “:dev”가 태그에 추가됩니다. | 다음 규칙을 사용하여 영숫자가 아닌 문자를 제거한 후의 어셈블리 이름 <br/> 결과 태그가 모두 숫자이면 “image”가 접두사로 삽입됩니다(예: image2314). <br/> 결과 태그가 빈 문자열이면 “image”가 태그로 사용됩니다. |1.0.1872750 이상|

## <a name="next-steps"></a>다음 단계

MSBuild 속성에 대한 일반적인 내용은 [MSBuild 속성](../msbuild/msbuild-properties.md)을 참조하세요.

## <a name="see-also"></a>참조

[Docker Compose 빌드 속성](docker-compose-properties.md)

[컨테이너 도구 시작 설정](container-launch-settings.md)

[MSBuild의 예약된 속성 및 잘 알려진 속성](../msbuild/msbuild-reserved-and-well-known-properties.md)
