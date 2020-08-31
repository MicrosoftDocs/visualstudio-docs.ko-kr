---
title: 'Docker 자습서-7 부: Docker Compose 사용'
description: Docker Compose를 설치 하 고 사용 하는 방법을 설명 합니다.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 81f70612b05920ea58c752a878831f1d6de34098
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176797"
---
# <a name="use-docker-compose"></a>Docker Compose 사용

[Docker Compose](https://docs.docker.com/compose/) 는 다중 컨테이너 응용 프로그램을 정의 하 고 공유할 수 있도록 개발 된 도구입니다. 작성 된를 사용 하 여 서비스를 정의 하는 YAML 파일을 만들고 단일 명령을 사용 하 여 모든 항목을 회전 하거나 모두 종료할 수 있습니다.

작성을 사용 하는 가장 *큰* 장점은 응용 프로그램 스택을 파일에 정의 하 고, 프로젝트 리포지토리의 루트 (현재는 버전 제어)를 유지 하 고, 다른 사용자가 프로젝트에 기여할 수 있도록 하는 것입니다. 사용자는 리포지토리를 복제 하 고 작성 앱을 시작 하기만 하면 됩니다. 사실 GitHub/GitLab에서이 작업을 수행 하는 몇 가지 프로젝트를 볼 수 있습니다.

그렇다면 어떻게 시작 하나요?

## <a name="install-docker-compose"></a>Docker Compose 설치

Windows 또는 Mac 용 Docker Desktop을 설치한 경우 이미 Docker Compose! Docker를 사용한 재생 인스턴스에는 이미 Docker Compose 설치 되어 있습니다. Linux 컴퓨터를 사용 하는 경우 [여기에 있는 지침](https://docs.docker.com/compose/install/)을 사용 하 여 Docker Compose를 설치 해야 합니다.

설치 후 다음을 실행 하 고 버전 정보를 확인할 수 있습니다.

```bash
docker-compose version
```

## <a name="create-the-compose-file"></a>작성 파일 만들기

1. 앱 프로젝트의 루트에서 라는 파일을 만듭니다 `docker-compose.yml` .

1. 작성 파일에서 스키마 버전을 정의 하 여 시작 합니다. 대부분의 경우 지원 되는 최신 버전을 사용 하는 것이 가장 좋습니다. 현재 스키마 버전 및 호환성 매트릭스에 대 한 [파일 작성 참조](https://docs.docker.com/compose/compose-file/) 를 살펴볼 수 있습니다.

    ```yaml
    version: "3.7"
    ```

1. 그런 다음 응용 프로그램의 일부로 실행 하려는 서비스 (또는 컨테이너)의 목록을 정의 합니다.

    ```yaml hl_lines="3"
    version: "3.7"

    services:
    ```

이제 한 번에 서비스를 작성 파일로 마이그레이션하기 시작 합니다.

## <a name="define-the-app-service"></a>App Service 정의

이 명령은 앱 컨테이너를 정의 하는 데 사용한 것 ` \ ` 입니다 (Windows PowerShell에서 문자를로 바꿈 `` ` `` ).

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

1. 먼저 컨테이너의 서비스 항목과 이미지를 정의 합니다. 서비스의 이름을 선택할 수 있습니다. 이름은 자동으로 네트워크 별칭이 되기 때문에 MySQL 서비스를 정의할 때 유용 합니다.

    ```yaml hl_lines="4 5"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
    ```

1. 일반적으로 `image` 정렬에 대 한 요구 사항은 없지만 정의에 근접 한 명령이 표시 됩니다. 그러면 계속 해 서 파일로 이동 합니다.

    ```yaml hl_lines="6"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
    ```

1. `-p 3000:3000`서비스에 대 한을 정의 하 여 명령의 일부를 마이그레이션합니다 `ports` . 여기서는 [간단한 구문을](https://docs.docker.com/compose/compose-file/#short-syntax-1) 사용 하지만 더 자세한 정보를 제공 하는 [긴 구문도](https://docs.docker.com/compose/compose-file/#long-syntax-1) 있습니다.

    ```yaml hl_lines="7 8"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
    ```

1. 그런 다음 `-w /app` `-v ${PWD}:/app` 및 정의를 사용 하 여 작업 디렉터리 ()와 볼륨 매핑 ()을 모두 마이그레이션합니다 `working_dir` `volumes` . 또한 볼륨에는 [짧고](https://docs.docker.com/compose/compose-file/#short-syntax-3) [긴](https://docs.docker.com/compose/compose-file/#long-syntax-3) 구문이 있습니다.

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

1. 마지막으로, 키를 사용 하 여 환경 변수 정의를 마이그레이션합니다 `environment` .

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

이제 MySQL 서비스를 정의할 때입니다. 해당 컨테이너에 사용 되는 명령은 다음과 ` \ ` 같습니다 (Windows PowerShell에서 문자를로 바꿈 `` ` `` ).

```bash
docker run -d \
  --network todo-app --network-alias mysql \
  -v todo-mysql-data:/var/lib/mysql \
  -e MYSQL_ROOT_PASSWORD=secret \
  -e MYSQL_DATABASE=todos \
  mysql:5.7
```

1. 먼저 새 서비스를 정의 하 고 이름을 자동으로 지정 하 여 `mysql` 네트워크 별칭을 가져옵니다. 사용할 이미지도 지정 합니다.

    ```yaml hl_lines="6 7"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
    ```

1. 다음으로 볼륨 매핑을 정의 합니다. 를 사용 하 여 컨테이너를 실행 하면 `docker run` 명명 된 볼륨이 자동으로 생성 됩니다. 그러나를 작성 하 여 실행 하는 경우에는이 문제가 발생 하지 않습니다. 최상위 섹션에서 볼륨을 정의한 `volumes:` 다음 서비스 구성에 탑재 지점을 지정 해야 합니다. 단순히 볼륨 이름만 제공 하면 기본 옵션이 사용 됩니다. 그러나 [더 많은 옵션을 사용할 수](https://docs.docker.com/compose/compose-file/#volume-configuration-reference) 있습니다.

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

1. 마지막으로 환경 변수만 지정 해야 합니다.

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

이 시점에서 완료는 `docker-compose.yml` 다음과 같습니다.

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

## <a name="run-the-application-stack"></a>응용 프로그램 스택 실행

이제 `docker-compose.yml` 파일이 있으므로 시작할 수 있습니다.

1. 먼저, 응용 프로그램 및 데이터베이스의 다른 복사본 (및)이 실행 되 고 있지 않은지 확인 `docker ps` `docker rm -f <ids>` 합니다.

1. 명령을 사용 하 여 응용 프로그램 스택을 시작 `docker-compose up` 합니다. 플래그를 추가 `-d` 하 여 백그라운드에서 모든 항목을 실행 합니다. 또는 작성 파일을 마우스 오른쪽 단추로 클릭 하 고 VS Code 세로 막대에 대 한 **구성** 옵션을 선택할 수 있습니다. 

    ```bash
    docker-compose up -d
    ```

    이를 실행 하면 다음과 같은 출력이 표시 됩니다.

    ```plaintext
    Creating network "app_default" with the default driver
    Creating volume "app_todo-mysql-data" with default driver
    Creating app_app_1   ... done
    Creating app_mysql_1 ... done
    ```

    볼륨이 만들어지고 네트워크와 함께 생성 된 것을 알 수 있습니다. 기본적으로 Docker Compose는 응용 프로그램 스택에 대 한 네트워크를 자동으로 만듭니다 (즉, 작성 파일에서 정의 하지 않은 이유 때문).

1. 명령을 사용 하 여 로그를 확인 합니다 `docker-compose logs -f` . 단일 스트림으로 인터리브 된 각 서비스의 로그가 표시 됩니다. 이 기능은 타이밍 관련 문제를 감시 하려는 경우에 매우 유용 합니다. `-f`플래그는 로그를 "팔 로우" 하므로 생성 될 때 실시간 출력을 제공 합니다.

    아직 표시 되지 않으면 다음과 같은 출력이 표시 됩니다.

    ```plaintext
    mysql_1  | 2019-10-03T03:07:16.083639Z 0 [Note] mysqld: ready for connections.
    mysql_1  | Version: '5.7.27'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server (GPL)
    app_1    | Connected to mysql db at host mysql
    app_1    | Listening on port 3000
    ```

    메시지를 구분 하는 데 도움이 되도록 서비스 이름이 줄의 시작 부분에 표시 됩니다 (종종 색이 지정 됨). 특정 서비스에 대 한 로그를 보려면 로그 명령 (예:)의 끝에 서비스 이름을 추가할 수 있습니다 `docker-compose logs -f app` .

    > [!TIP]
    > **응용 프로그램을 시작 하기 전에 DB를 기다리는 중** 앱을 시작 하는 경우, ker it.Doc에 연결을 시도 하기 전에 MySQL이 시작 되 고 준비 될 때까지 기다린 후 다른 컨테이너를 시작 하기 전에 다른 컨테이너가 완전히 작동, 실행 및 준비 될 때까지 대기 하는 기본 제공 지원이 없습니다. 노드 기반 프로젝트의 경우 [대기 포트](https://github.com/dwmkerr/wait-port) 종속성을 사용할 수 있습니다. 다른 언어/프레임 워크에도 유사한 프로젝트가 있습니다.

1. 이 시점에서 앱을 열고 실행을 확인할 수 있습니다. 그리고 단일 명령으로 다운 되었습니다.

## <a name="see-the-app-stack-in-the-docker-extension"></a>Docker 확장에서 앱 스택 보기

Docker 확장을 살펴보면 ' 코그 ' 및 ' group by '를 사용 하 여 그룹화 옵션을 변경할 수 있습니다. 이 인스턴스에서는 작성 프로젝트 이름별로 그룹화 된 컨테이너를 확인 하려고 합니다.

![VS 확장 및 작성](media/vs-app-project-collapsed.png)

네트워크를 축소 하면 작성 파일에 정의 된 두 개의 컨테이너가 표시 됩니다.

![구성 확장을 사용한 VS 확장](media/vs-app-project-expanded.png)

## <a name="tear-it-all-down"></a>모두 중단

모든 기능을 종료할 준비가 되 면 `docker-compose down` , VS Code Docker 확장의 컨테이너 목록에서 응용 프로그램을 마우스 오른쪽 단추로 클릭 하 고 **구성**을 선택 합니다. 컨테이너가 중지 되 고 네트워크가 제거 됩니다.

> [!WARNING]
> **볼륨 제거** 기본적으로 작성 파일의 명명 된 볼륨은를 실행할 때 제거 되지 않습니다 `docker-compose down` . 볼륨을 제거 하려면 플래그를 추가 해야 `--volumes` 합니다.

해체 되 면 다른 프로젝트로 전환 하 여 실행 하 `docker-compose up` 고 해당 프로젝트에 기여할 준비가 된 것입니다. 정말 간단 하지 않습니다.

## <a name="recap"></a>요약

이 섹션에서는 Docker Compose 및 다중 서비스 응용 프로그램의 정의 및 공유를 크게 간소화 하는 데 도움이 되는 방법에 대해 알아보았습니다. 사용 중인 명령을 적절 한 작성 형식으로 변환 하 여 작성 파일을 만들었습니다.

이 시점에서 자습서를 먼저 래핑합니다. 그러나 사용 하는 Dockerfile에 큰 문제가 있으므로 이미지 작성에 대 한 몇 가지 모범 사례가 있습니다. 따라서 살펴보겠습니다.

## <a name="next-steps"></a>다음 단계

자습서를 계속 진행 합니다.

> [!div class="nextstepaction"]
> [이미지 작성 모범 사례](image-building-best-practices.md)
