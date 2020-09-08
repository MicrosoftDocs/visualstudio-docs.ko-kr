---
title: 'Docker 자습서 - 7부: Docker Compose 사용'
description: Docker Compose를 설치하고 사용하는 방법을 설명합니다.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 81f70612b05920ea58c752a878831f1d6de34098
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89176797"
---
# <a name="use-docker-compose"></a>Docker Compose 사용

[Docker Compose](https://docs.docker.com/compose/)는 다중 컨테이너 애플리케이션을 정의하고 공유할 수 있도록 개발된 도구입니다. Compose에서 서비스를 정의하는 YAML 파일을 만들고, 단일 명령을 사용하여 모두 실행하거나 모두 종료할 수 있습니다.

Compose를 사용할 경우의 ‘중요한’ 이점은 파일에서 애플리케이션 스택을 정의하고 프로젝트 리포지토리 루트에 파일을 저장하여(이제 버전 제어 사용) 다른 사용자가 프로젝트에 참여하기 쉽게 만들 수 있다는 것입니다. 사용자가 리포지토리를 복제하고 Compose 앱을 시작하기만 하면 됩니다. 사실상, GitHub/GitLab에서 정확히 이 작업을 수행하는 많은 프로젝트를 볼 수 있습니다.

그렇다면 어떻게 시작할까요?

## <a name="install-docker-compose"></a>Docker Compose 설치

Windows 또는 Mac용 Docker Desktop을 설치한 경우 Docker Compose가 이미 있습니다. Play with Docker 인스턴스에도 Docker Compose가 이미 설치되어 있습니다. Linux 머신을 사용하는 경우 [여기에 제공된 지침](https://docs.docker.com/compose/install/)을 따라 Docker Compose를 설치해야 합니다.

설치 후에 다음을 실행하면 버전 정보가 표시되어야 합니다.

```bash
docker-compose version
```

## <a name="create-the-compose-file"></a>Compose 파일 만들기

1. 앱 프로젝트 루트에 `docker-compose.yml`이라는 파일을 만듭니다.

1. Compose 파일에서 먼저 스키마 버전을 정의합니다. 대부분의 경우 지원되는 최신 버전을 사용하는 것이 가장 좋습니다. [Compose 파일 참조](https://docs.docker.com/compose/compose-file/)에서 현재 스키마 버전과 호환성 매트릭스를 확인할 수 있습니다.

    ```yaml
    version: "3.7"
    ```

1. 다음에는 애플리케이션 일부로 실행하려는 서비스(또는 컨테이너) 목록을 정의합니다.

    ```yaml hl_lines="3"
    version: "3.7"

    services:
    ```

이제 한 번에 하나씩, 서비스를 Compose 파일로 마이그레이션하기 시작합니다.

## <a name="define-the-app-service"></a>App Service 정의

이 명령은 앱 컨테이너를 정의하는 데 사용한 명령입니다(Windows PowerShell에서 ` \ ` 문자를 `` ` ``로 바꿈).

```bash
docker run -dp 3000:3000 \
  -w /app -v ${PWD}:/app \
  --network todo-app \
  -e MYSQL_HOST=mysql \
  -e MYSQL_USER=root \
  -e MYSQL_PASSWORD=secret \
  -e MYSQL_DB=todos \
  node:12-alpine \
  sh -c "yarn install && yarn run dev"
```

1. 먼저 서비스 항목과 컨테이너 이미지를 정의합니다. 서비스 이름은 임의로 선택할 수 있습니다. 이름은 자동으로 네트워크 별칭이 되므로 MySQL 서비스를 정의할 때 유용합니다.

    ```yaml hl_lines="4 5"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
    ```

1. 순서 지정에 대한 요구 사항은 없지만 일반적으로 `image` 정의와 가까운 곳에 명령이 표시됩니다. 해당 명령을 파일로 이동합니다.

    ```yaml hl_lines="6"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
    ```

1. 서비스의 `ports`를 정의하여 명령의 `-p 3000:3000` 부분을 마이그레이션합니다. 여기서는 [짧은 구문](https://docs.docker.com/compose/compose-file/#short-syntax-1)을 사용하지만, 더 자세한 [긴 구문](https://docs.docker.com/compose/compose-file/#long-syntax-1)을 사용할 수도 있습니다.

    ```yaml hl_lines="7 8"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
    ```

1. 다음에는 `working_dir` 및 `volumes` 정의를 사용하여 작업 디렉터리(`-w /app`)와 볼륨 매핑(`-v ${PWD}:/app`)을 둘 다 마이그레이션합니다. 볼륨에도 [짧은](https://docs.docker.com/compose/compose-file/#short-syntax-3) 구문과 [긴](https://docs.docker.com/compose/compose-file/#long-syntax-3) 구문이 있습니다.

   Docker Compose 볼륨 정의의 이점 중 하나는 현재 디렉터리의 상대 경로를 사용할 수 있다는 것입니다.

    ```yaml hl_lines="9 10 11"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
        working_dir: /app
        volumes:
          - ./:/app
    ```

1. 마지막으로, `environment` 키를 사용하여 환경 변수 정의를 마이그레이션합니다.

    ```yaml hl_lines="12 13 14 15 16"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
        working_dir: /app
        volumes:
          - ./:/app
        environment:
          MYSQL_HOST: mysql
          MYSQL_USER: root
          MYSQL_PASSWORD: secret
          MYSQL_DB: todos
    ```

### <a name="define-the-mysql-service"></a>MySQL 서비스 정의

이제 MySQL 서비스를 정의할 차례입니다. 해당 컨테이너에 사용한 명령은 다음과 같습니다(Windows PowerShell에서 ` \ ` 문자를 `` ` ``로 바꿈).

```bash
docker run -d \
  --network todo-app --network-alias mysql \
  -v todo-mysql-data:/var/lib/mysql \
  -e MYSQL_ROOT_PASSWORD=secret \
  -e MYSQL_DATABASE=todos \
  mysql:5.7
```

1. 먼저 새 서비스를 정의하고 이름을 `mysql`로 지정하여 네트워크 별칭을 자동으로 가져옵니다. 사용할 이미지도 지정합니다.

    ```yaml hl_lines="6 7"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
    ```

1. 다음에는 볼륨 매핑을 정의합니다. `docker run`을 사용하여 컨테이너를 실행한 경우 명명된 볼륨이 자동으로 생성되었습니다. 그러나 Compose로 실행하는 경우에는 자동으로 생성되지 않습니다. 최상위 `volumes:` 섹션에 볼륨을 정의한 다음, 서비스 구성에서 탑재 지점을 지정해야 합니다. 단순히 볼륨 이름만 지정하면 기본 옵션이 사용됩니다. 하지만 [훨씬 더 많은 옵션을 사용할 수 있습니다](https://docs.docker.com/compose/compose-file/#volume-configuration-reference).

    ```yaml hl_lines="8 9 10 11 12"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
        volumes:
          - todo-mysql-data:/var/lib/mysql
    
    volumes:
      todo-mysql-data:
    ```

1. 마지막으로, 환경 변수만 지정하면 됩니다.

    ```yaml hl_lines="10 11 12"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
        volumes:
          - todo-mysql-data:/var/lib/mysql
        environment: 
          MYSQL_ROOT_PASSWORD: secret
          MYSQL_DATABASE: todos
    
    volumes:
      todo-mysql-data:
    ```

이 시점에서 전체 `docker-compose.yml`은 다음과 같이 표시되어야 합니다.

```yaml
version: "3.7"

services:
  app:
    image: node:12-alpine
    command: sh -c "yarn install && yarn run dev"
    ports:
      - 3000:3000
    working_dir: /app
    volumes:
      - ./:/app
    environment:
      MYSQL_HOST: mysql
      MYSQL_USER: root
      MYSQL_PASSWORD: secret
      MYSQL_DB: todos

  mysql:
    image: mysql:5.7
    volumes:
      - todo-mysql-data:/var/lib/mysql
    environment: 
      MYSQL_ROOT_PASSWORD: secret
      MYSQL_DATABASE: todos

volumes:
  todo-mysql-data:
```

## <a name="run-the-application-stack"></a>애플리케이션 스택 실행

이제 `docker-compose.yml` 파일이 준비되었으므로 시작할 수 있습니다.

1. 먼저 앱과 데이터베이스의 다른 복사본이 실행되고 있지는 않은지 확인합니다(`docker ps` 및 `docker rm -f <ids>`).

1. `docker-compose up` 명령을 사용하여 애플리케이션 스택을 시작합니다. 모든 명령을 백그라운드에서 실행하려면 `-d` 플래그를 추가합니다. 또는 Compose 파일을 마우스 오른쪽 단추로 클릭하고 VS Code 사이드바에 대해 **Compose 시작** 옵션을 선택할 수 있습니다. 

    ```bash
    docker-compose up -d
    ```

    이 명령을 실행하면 다음과 같은 출력이 표시됩니다.

    ```plaintext
    Creating network "app_default" with the default driver
    Creating volume "app_todo-mysql-data" with default driver
    Creating app_app_1   ... done
    Creating app_mysql_1 ... done
    ```

    볼륨과 네트워크가 생성된 것을 확인할 수 있습니다. 기본적으로 Docker Compose에서 애플리케이션 스택 전용 네트워크를 자동으로 만들기 때문에 Compose 파일에서는 정의하지 않았습니다.

1. `docker-compose logs -f` 명령을 사용하여 로그를 확인합니다. 각 서비스의 로그가 단일 스트림으로 인터리브되어 표시됩니다. 이 기능은 타이밍 관련 문제를 감시하려는 경우에 매우 유용합니다. `-f` 플래그가 로그 “뒤에 추가”되었기 때문에 실시간 출력이 생성되는 즉시 표시됩니다.

    아직 표시되지 않은 경우 다음과 같은 출력이 표시됩니다.

    ```plaintext
    mysql_1  | 2019-10-03T03:07:16.083639Z 0 [Note] mysqld: ready for connections.
    mysql_1  | Version: '5.7.27'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server (GPL)
    app_1    | Connected to mysql db at host mysql
    app_1    | Listening on port 3000
    ```

    메시지를 구분하기 쉽도록 서비스 이름이 줄 시작 부분에 표시됩니다(색으로 구분된 경우가 많음). 특정 서비스에 대한 로그를 보려면 로그 명령의 끝에 서비스 이름을 추가합니다(예: `docker-compose logs -f app`).

    > [!TIP]
    > **앱을 시작하기 전에 DB 대기** 앱이 시작되면 실제로 MySQL이 시작되어 준비될 때까지 기다린 후에 연결을 시도합니다. Docker에는 다른 컨테이너가 완전히 시작하고 실행되어 준비될 때까지 기다렸다가 다른 컨테이너를 시작하기 위한 기본 제공 지원이 없습니다. 노드 기반 프로젝트의 경우 [wait-port](https://github.com/dwmkerr/wait-port) 종속성을 사용할 수 있습니다. 다른 언어/프레임워크에 대해서도 유사한 프로젝트가 있습니다.

1. 이제 앱을 열고 실행되는 것을 확인할 수 있습니다. 마지막으로 명령 한 개가 남았습니다.

## <a name="see-the-app-stack-in-the-docker-extension"></a>Docker 확장에서 앱 스택 확인

Docker 확장을 살펴보는 경우 ‘톱니바퀴’ 및 ‘그룹화 방법’을 사용하여 그룹화 옵션을 변경할 수 있습니다. 이 인스턴스에서는 Compose 프로젝트 이름별로 그룹화하여 컨테이너를 확인하려고 합니다.

![Compose가 있는 VS 확장](media/vs-app-project-collapsed.png)

네트워크를 휘감아 내리면 Compose 파일에서 정의한 컨테이너 2개가 표시됩니다.

![Compose가 펼쳐진 VS 확장](media/vs-app-project-expanded.png)

## <a name="tear-it-all-down"></a>모두 종료

모두 종료할 준비가 되었으면 `docker-compose down`을 실행하거나 VS Code Docker 확장의 컨테이너 목록에서 애플리케이션을 마우스 오른쪽 단추로 클릭하고 **Compose 종료**를 선택합니다. 컨테이너가 중지되고 네트워크가 제거됩니다.

> [!WARNING]
> **볼륨 제거** 기본적으로 Compose 파일에서 명명된 볼륨은 `docker-compose down`을 실행해도 제거되지 않습니다. 볼륨을 제거하려면 `--volumes` 플래그를 추가해야 합니다.

종료되고 나면 다른 프로젝트로 전환하고 `docker-compose up`을 실행하여 해당 프로젝트에 참여할 수 있습니다. 매우 간단합니다.

## <a name="recap"></a>요약

이 섹션에서는 Docker Compose에 대해 알아보고, Compose를 통해 다중 서비스 애플리케이션 정의 및 공유를 훨씬 더 간소화할 방법을 살펴보았습니다. 사용하는 명령을 적절한 Compose 형식으로 변환하여 Compose 파일을 만들었습니다.

이제 자습서를 마무리해야 합니다. 하지만 사용한 Dockerfile에 큰 문제가 있으므로 이미지 빌드와 관련해서 확인할 몇 가지 모범 사례가 있습니다. 함께 살펴봅시다.

## <a name="next-steps"></a>다음 단계

자습서를 계속 진행합니다.

> [!div class="nextstepaction"]
> [이미지 빌드 모범 사례](image-building-best-practices.md)
