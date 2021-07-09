---
title: Docker Compose 프로젝트의 시작 프로필 관리
description: Docker Compose 시작 프로필을 사용하고 Visual Studio에서 Docker Compose를 사용할 때 시작되는 서비스를 제어하는 방법을 알아봅니다.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: how-to
ms.date: 05/10/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: e740ea3b7950c14bf11522c4e438a105b09eb7f6
ms.sourcegitcommit: ab5735d64a6ad7aecabf5d6df159888e3246bff5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2021
ms.locfileid: "111433703"
---
# <a name="manage-launch-profiles-for-docker-compose"></a>Docker Compose의 시작 프로필 관리

여러 서비스로 구성되고 Docker Compose를 사용하는 애플리케이션이 있는 경우 Docker Compose 시작 설정에서 기존 시작 프로필을 만들거나 편집하여 실행하고 디버그할 서비스를 구성할 수 있습니다. 시작 프로필을 사용하면 현재 시나리오에 중요한 서비스만 동적으로 실행할 수 있습니다. 디버깅 환경을 사용자 지정하고 `Browser Launch URL` 같은 특정 시작 작업을 설정하려면 시작 프로필에서 만들고 선택하세요. 또한 각 서비스를 개별적으로 선택하거나 Docker Compose 프로필을 선택할 수 있으며, Compose 파일을 확인하여 실행할 서비스 그룹을 결정할 수도 있습니다.

Docker Compose 프로필에 대한 자세한 내용은 [Using profiles with Compose](https://docs.docker.com/compose/profiles/)(Compose에서 프로필 사용)를 참조하세요.
 
## <a name="prerequisites"></a>필수 조건

- [Visual Studio 2019 버전 16.10](https://visualstudio.microsoft.com/vs/) 이상
- [Docker Compose를 사용하는 컨테이너 오케스트레이션](tutorial-multicontainer.md)이 포함된 솔루션

## <a name="manage-launch-settings"></a>시작 설정 관리

*docker-compose.yml* 에 5개의 서비스와 3개의 Compose 프로필(web, web1, web2)이 있는 다음과 같은 Docker Compose 프로젝트를 고려해 보세요.

```yml
version: '3.9'

services:
  webapplication1:
    image: ${DOCKER_REGISTRY-}webapplication1
    profiles: [web, web1]
    build:
      context: .
      dockerfile: WebApplication1/Dockerfile

  webapplication2:
    image: ${DOCKER_REGISTRY-}webapplication2
    profiles: [web, web2]
    build:
      context: .
      dockerfile: WebApplication2/Dockerfile

  webapplication3:
    image: ${DOCKER_REGISTRY-}webapplication3
    profiles: [web]
    build:
      context: .
      dockerfile: WebApplication3/Dockerfile

  external1:
    image: redis

  external2:
    image: redis

```

Docker Compose 시작 설정 대화 상자를 여는 몇 가지 옵션이 있습니다.
- Visual Studio에서 **디버그** > **Docker Compose 시작 설정 관리** 를 선택합니다.

    ![디버그 관리 Compose 설정 메뉴 항목의 스크린샷](media/launch-settings/debug-dropdown-manage-compose.png)

- Visual Studio `docker-compose` 프로젝트를 마우스 오른쪽 단추로 클릭하고 **Docker Compose 시작 설정 관리** 를 선택합니다.

    ![상황에 맞는 메뉴 항목의 스크린샷](media/launch-settings/launch-settings-context-menu.png)

- 빠른 실행(**Ctrl**+**Q**)을 사용하고 **Docker Compose** 를 검색하여 앞에서 언급한 명령을 찾습니다.

아래 예제에서는 `web1` Compose 프로필을 선택하고 5개 중 3개만 해당 프로필에 포함되도록 **서비스** 목록을 필터링합니다.

![“시작 설정 대화 상자의 스크린샷”](media/launch-settings/launch-settings-create-profile.png)

Docker Compose 프로필 섹션은 *docker-compose.yml* 파일에 정의된 프로필이 있는 경우에만 표시됩니다.

다음 예제에서는 Compose 프로필의 서비스로 필터링하는 대신 개별 서비스 중에서 선택하는 방법을 보여 줍니다. 여기서는 5개 중 2개 서비스(디버깅한 `webapplication1` 및 디버깅하지 않은 `webapplication2`)만 시작하는 `test2`라는 새로운 시작 프로필을 만든 경우 대화 상자가 어떻게 표시되는지를 보여 줍니다.  이 시작 프로필은 애플리케이션이 시작되고 `webapplication1`의 홈페이지로 열리는 경우 브라우저도 시작합니다. 

![일부 서비스가 선택 취소된 시작 설정 대화 상자의 스크린샷](media/launch-settings/launch-settings-selected.png)

이 정보는 아래에 표시된 대로 *launchSettings.json* 에 저장됩니다.

```json
{
    "profiles": {
      "test2": {
        "commandName": "DockerCompose",
        "composeLaunchServiceName": "webapplication1",
        "serviceActions": {
          "external1": "DoNotStart",
          "external2": "DoNotStart",
          "webapplication1": "StartDebugging",
          "webapplication2": "StartWithoutDebugging",
          "webapplication3": "DoNotStart"
        },
        "composeLaunchAction": "LaunchBrowser",
        "commandVersion": "1.0",
        "composeLaunchUrl": "{Scheme}://localhost:{ServicePort}"
      }
   }
}
```

## <a name="create-a-launch-profile-that-uses-a-docker-compose-profile"></a>Docker Compose 프로필을 사용하는 시작 프로필 만들기

Compose 프로필을 사용하는 Visual Studio 시작 프로필을 만들어 시작 동작을 추가로 사용자 지정할 수도 있습니다.

Compose 프로필을 사용하는 다른 프로필을 만들려면 **Docker Compose 프로필 사용** 을 선택하고 `web1`을 선택합니다. 이제 시작 프로필에는 3개의 서비스 `webapplication1`(`web`과 `web1` Compose 프로필 모두에 속함), `external1`, `external2`가 포함됩니다. 기본적으로 `external1` 및 `external2`와 같이 소스 코드가 없는 서비스에는 **디버깅하지 않고 시작** 이라는 기본 작업이 있습니다. 소스 코드가 있는 .NET 애플리케이션은 기본적으로 **디버깅 시작** 으로 설정됩니다.

> [!IMPORTANT]
> 서비스에서 Compose 프로필을 지정하지 않으면 모든 Compose 프로필에 암시적으로 포함됩니다.

![다른 프로필이 생성된 시작 설정 대화 상자의 스크린샷](media/launch-settings/launch-settings-create-profile.png)

이 정보는 다음 코드에 표시된 대로 저장됩니다. 서비스 및 기본 작업에 대한 구성은 기본 작업을 변경하지 않는 한 저장되지 않습니다.

```json
{
  "profiles": {
    "test1": {
      "commandName": "DockerCompose",
      "composeProfile": {
         "includes": [
            "web1"
         ]
      },
      "commandVersion": "1.0"
    }
  }
}
```

webapplication1의 작업을 **디버깅하지 않고 시작** 으로 변경할 수도 있습니다. 그러면 *launchSettings.json* 의 설정이 다음 코드와 같이 표시됩니다.

```json
{
  "profiles": {
    "test1": {
        "commandName": "DockerCompose",
        "composeProfile": {
          "includes": [
              "web1"
              ],
          "serviceActions": {
              "webapplication1": "StartWithoutDebugging"
          }
        },
    "commandVersion": "1.0"
    }
  }
}
```

## <a name="properties"></a>속성

다음은 *launchSettings.json* 에 있는 각 속성에 대한 설명입니다.

|속성| 설명|
| - | - |
|commandName| 명령의 이름입니다. 기본값은 “DockerCompose”입니다.|
|commandVersion| DockerCompose 시작 프로필의 스키마를 관리하는 데 사용되는 버전 번호입니다.|
|composeProfile| 시작 프로필 정의를 정의하는 부모 속성입니다. 자식 속성은 `includes` 및 `serviceActions`입니다.|
|composeProfile - includes | 시작 프로필을 구성하는 Compose 프로필 이름의 목록입니다.|
|composeProfile - serviceActions | 선택한 Compose 프로필, 서비스, 각 서비스의 시작 작업을 나열합니다.|
|serviceActions | 선택한 서비스 및 시작 작업을 나열합니다.|
|composeLaunchServiceName| DockerLaunchAction 또는 DockerLaunchBrowser가 지정된 경우 DockerServiceName은 시작할 서비스의 이름입니다. 이 속성을 사용하여 Docker Compose 파일 내에서 시작할 서비스를 결정합니다.|
|composeLaunchAction| **F5** 키나 **Ctrl**+**F5** 를 누르면 수행할 시작 작업을 지정합니다. 허용되는 값은 None, LaunchBrowser, LaunchWCFTestClient입니다.|
|composeLaunchUrl| 브라우저를 시작할 때 사용할 URL입니다. 유효한 대체 토큰은 “{ServiceIPAddress}”, “{ServicePort}”, “{Scheme}”입니다. 예: {Scheme}://{ServiceIPAddress}:{ServicePort}|

## <a name="next-steps"></a>다음 단계

[Visual Studio 컨테이너 도구 빌드 및 디버그 개요](container-build.md)를 참조하여 컨테이너 도구의 작동 방식에 대해 자세히 알아봅니다.

## <a name="see-also"></a>참조

- [Visual Studio Container Tools 시작 설정](container-launch-settings.md)

- [Docker Compose 빌드 설정](docker-compose-properties.md)
