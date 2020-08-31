---
title: 'Docker 자습서-6 부: 다중 컨테이너 앱'
description: 컨테이너 간에 네트워킹을 설정 하 고 MySQL 데이터베이스용 컨테이너를 추가 하는 방법입니다.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 9513a3414a38aa02f6a4607a8c95bbf02c0e1cf6
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176803"
---
# <a name="multi-container-apps"></a>다중 컨테이너 앱

이 시점까지 단일 컨테이너 앱을 사용 했습니다. 그러나 이제 응용 프로그램 스택에 MySQL을 추가 합니다. 다음 질문은 종종 MySQL이 실행 되나요? 동일한 컨테이너에 설치 하거나 별도로 실행 하 시겠습니까? " 일반적으로 **각 컨테이너는 한 가지 작업을 수행 해야 합니다.** 몇 가지 이유는 다음과 같습니다.

- Api와 프런트 엔드를 데이터베이스와 다르게 조정 해야 할 가능성이 있습니다.
- 별도의 컨테이너를 사용 하 여 버전 및 업데이트 버전 격리
- 데이터베이스에 대 한 컨테이너를 로컬로 사용할 수 있지만 프로덕션 환경에서는 데이터베이스에 대해 관리 서비스를 사용 하는 것이 좋습니다. 응용 프로그램을 사용 하 여 데이터베이스 엔진을 제공 하지 않으려는 경우
- 여러 프로세스를 실행 하려면 프로세스 관리자가 필요 합니다 (컨테이너는 한 프로세스만 시작 함) .이는 컨테이너 시작/종료에 복잡성을 추가 합니다.

더 많은 이유가 있습니다. 따라서 다음과 같이 작동 하도록 응용 프로그램을 업데이트 합니다.

![MySQL 컨테이너에 연결 된 Todo 앱](media/multi-app-architecture.png)

## <a name="container-networking"></a>컨테이너 네트워킹

컨테이너는 기본적으로 격리에서 실행 되며 동일한 컴퓨터의 다른 프로세스나 컨테이너에 대해 알지 못합니다. 따라서 하나의 컨테이너가 다른 컨테이너와 통신 하도록 허용 하려면 어떻게 해야 하나요? **네트워킹**에 대 한 대답입니다. 이제 네트워크 엔지니어 (만 세!)가 될 필요는 없습니다. 이 규칙을 잊지 말고

> [!NOTE]
> 두 컨테이너가 동일한 네트워크에 있는 경우 서로 통신할 수 있습니다. 그렇지 않은 경우에는 사용할 수 없습니다.

## <a name="start-mysql"></a>MySQL을 시작합니다.

네트워크에 컨테이너를 배치 하는 방법에는 두 가지가 있습니다. 즉, 시작 부분에 할당 하거나 기존 컨테이너에 연결 합니다. 지금은 네트워크를 먼저 만들고 시작 시 MySQL 컨테이너를 연결 합니다.

1. 네트워크를 만듭니다.

    ```bash
    docker network create todo-app
    ```

1. MySQL 컨테이너를 시작 하 고 네트워크에 연결 합니다. 또한 데이터베이스를 초기화 하는 데 사용할 몇 가지 환경 변수 ( [MySQL Docker 허브 목록의](https://hub.docker.com/_/mysql/)"환경 변수" 섹션 참조)를 정의 ` \ ` 합니다 ( `` ` `` Windows PowerShell에서 문자 대체).

    ```bash
    docker run -d \
        --network todo-app --network-alias mysql \
        -v todo-mysql-data:/var/lib/mysql \
        -e MYSQL_ROOT_PASSWORD=secret \
        -e MYSQL_DATABASE=todos \
        mysql:5.7
    ```

    플래그를 지정 하는 것도 표시 됩니다 `--network-alias` . 잠시 후에 다시 살펴보겠습니다.

    > [!TIP]
    > 여기에서 볼륨 이름을 사용 하 고에 탑재 하는 것을 알 수 있습니다 `todo-mysql-data` `/var/lib/mysql` . 여기에서 MySQL은 데이터를 저장 합니다. 그러나 명령을 실행 한 적이 없습니다 `docker volume create` . Docker에서는 명명 된 볼륨을 사용 하 고 자동으로 만드는 것을 인식 합니다.

1. 데이터베이스가 실행 중인지 확인 하려면 데이터베이스에 연결 하 고 연결을 확인 합니다.

    ```bash
    docker exec -it <mysql-container-id> mysql -p
    ```

    암호 프롬프트가 표시 되 면 암호 입력을 입력 **합니다.** MySQL 셸에서 데이터베이스를 나열 하 고 데이터베이스가 표시 되는지 확인 합니다 `todos` .

    ```cli
    mysql> SHOW DATABASES;
    ```

    결과는 다음과 같습니다.

    ```plaintext
    +--------------------+
    | Database           |
    +--------------------+
    | information_schema |
    | mysql              |
    | performance_schema |
    | sys                |
    | todos              |
    +--------------------+
    5 rows in set (0.00 sec)
    ```

    만 세! `todos`데이터베이스를 사용할 준비가 되었습니다.

## <a name="connect-to-mysql"></a>MySQL에 연결

MySQL이 실행 중임을 확인 했으므로 사용해 보세요! 하지만 질문은 ... 얼마나? 동일한 네트워크에서 다른 컨테이너를 실행 하는 경우 컨테이너를 어떻게 찾을 수 있나요 (각 컨테이너에는 고유한 IP 주소가 있음을 명심)?

이를 파악 하기 위해 [nicolaka/netscontainer](https://github.com/nicolaka/netshoot) 를 사용 하 여 네트워킹 문제를 해결 하거나 문제를 디버그 하는 데 유용한 *많은* 도구를 제공 하 고 있습니다.

1. 이미지를 사용 하 여 새 컨테이너를 시작 `nicolaka/netshoot` 합니다. 동일한 네트워크에 연결 해야 합니다.

    ```bash
    docker run -it --network todo-app nicolaka/netshoot
    ```

1. 컨테이너 내에서 `dig` 유용한 DNS 도구인 명령을 사용 합니다. 호스트 이름에 대 한 IP 주소를 조회 `mysql` 합니다.

    ```bash
    dig mysql
    ```

    그리고 다음과 같은 출력을 얻게 됩니다.

    ```text
    ; <<>> DiG 9.14.1 <<>> mysql
    ;; global options: +cmd
    ;; Got answer:
    ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 32162
    ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

    ;; QUESTION SECTION:
    ;mysql.             IN  A

    ;; ANSWER SECTION:
    mysql.          600 IN  A   172.23.0.2

    ;; Query time: 0 msec
    ;; SERVER: 127.0.0.11#53(127.0.0.11)
    ;; WHEN: Tue Oct 01 23:47:24 UTC 2019
    ;; MSG SIZE  rcvd: 44
    ```

    "응답 섹션"에서 `A` 로 확인 되는에 대 한 레코드가 표시 됩니다 `mysql` `172.23.0.2` . IP 주소는 다른 값을 가질 가능성이 높습니다. `mysql`일반적으로 유효한 호스트 이름이 아니지만 Docker는 해당 네트워크 별칭이 있는 컨테이너의 IP 주소를 확인할 수 있었습니다 ( `--network-alias` 이전에 사용한 플래그는?).

    이 의미는 다음과 같습니다. 앱은 라는 호스트에만 연결 하면 `mysql` 되며 데이터베이스와 통신 합니다. 훨씬 더 간단 하지 않습니다.

## <a name="run-your-app-with-mysql"></a>MySQL을 사용 하 여 앱 실행

Todo 앱은 몇 가지 환경 변수 설정을 지원 하 여 MySQL 연결 설정을 지정 합니다. 해당 항목은 다음과 같습니다.

- `MYSQL_HOST` -실행 중인 MySQL server에 대 한 호스트 이름
- `MYSQL_USER` -연결에 사용할 사용자 이름
- `MYSQL_PASSWORD` -연결에 사용할 암호
- `MYSQL_DB` -연결 된 후 사용할 데이터베이스

> [!WARNING]
> **환경 변수를 통해 연결 설정 설정** 환경 변수를 사용 하 여 연결 설정을 설정 하는 것은 일반적으로 개발에 사용할 수 있지만 프로덕션 환경에서 응용 프로그램을 실행할 때는 권장 되지 않습니다. 이유를 이해 하려면 [비밀 데이터에 환경 변수를 사용 하지 않는 이유](https://diogomonica.com/2017/03/27/why-you-shouldnt-use-env-variables-for-secret-data/)를 참조 하세요.
> 보다 안전한 메커니즘은 컨테이너 오케스트레이션 프레임 워크에서 제공 하는 비밀 지원을 사용 하는 것입니다. 대부분의 경우 이러한 암호는 실행 중인 컨테이너에 파일로 탑재 됩니다. 많은 앱 (MySQL 이미지 및 todo 앱 포함)이 파일을 포함 하는 파일을 가리키는 접미사를 사용 하 여 env 변수도 지원 `_FILE` 합니다.
> 예를 들어 var을 설정 하면 `MYSQL_PASSWORD_FILE` 앱이 참조 된 파일의 내용을 연결 암호로 사용 하 게 됩니다. Docker는 이러한 env 변수을 지원 하기 위해 어떤 작업도 수행 하지 않습니다. 앱은 변수를 찾고 파일 콘텐츠를 가져오기 위해 알고 있어야 합니다.

설명 된 모든 기능을 사용 하 여 개발 준비 컨테이너를 시작 합니다.

1. 위의 각 환경 변수를 지정 하 고 컨테이너를 앱 네트워크에 연결 ` \ ` `` ` `` 합니다 (Windows PowerShell에서 문자 대체).

    ```bash hl_lines="3 4 5 6 7"
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

1. 컨테이너 ()에 대 한 로그 `docker logs <container-id>` 를 살펴보면 MySQL 데이터베이스를 사용 중임을 나타내는 메시지가 표시 됩니다.

    ```plaintext hl_lines="7"
    # Previous log messages omitted
    $ nodemon src/index.js
    [nodemon] 1.19.2
    [nodemon] to restart at any time, enter `rs`
    [nodemon] watching dir(s): *.*
    [nodemon] starting `node src/index.js`
    Connected to mysql db at host mysql
    Listening on port 3000
    ```

1. 브라우저에서 앱을 열고 할 일 목록에 몇 가지 항목을 추가 합니다.

1. MySQL 데이터베이스에 연결 하 여 해당 항목이 데이터베이스에 기록 되 고 있음을 증명 합니다. 암호 **는 암호입니다.**

    ```bash
    docker exec -ti <mysql-container-id> mysql -p todos
    ```

    MySQL 셸에서 다음을 실행 합니다.

    ```plaintext
    mysql> select * from todo_items;
    +--------------------------------------+--------------------+-----------+
    | id                                   | name               | completed |
    +--------------------------------------+--------------------+-----------+
    | c906ff08-60e6-44e6-8f49-ed56a0853e85 | Do amazing things! |         0 |
    | 2912a79e-8486-4bc3-a4c5-460793a575ab | Be awesome!        |         0 |
    +--------------------------------------+--------------------+-----------+
    ```

    테이블에는 항목이 있으므로 테이블이 다르게 보입니다. 그러나 거기에 저장 된 것을 볼 수 있습니다.

Docker 확장을 신속 하 게 확인 하는 경우 두 개의 앱 컨테이너가 실행 되는 것을 볼 수 있습니다. 그러나 단일 앱에서 함께 그룹화 되는 실제 표시는 없습니다. 이러한 작업을 더 쉽게 수행 하는 방법을 확인할 수 있습니다.

![두 개의 그룹화 되지 않은 앱 컨테이너를 보여 주는 Docker 확장](media/vs-multi-container-app.png)

## <a name="recap"></a>요약

이제 응용 프로그램이 별도의 컨테이너에서 실행 되는 외부 데이터베이스에 데이터를 저장 하 게 됩니다. 컨테이너 네트워킹에 대해 약간 배우고 DNS를 사용 하 여 서비스 검색을 수행 하는 방법을 살펴보았습니다.

그러나이 응용 프로그램을 시작 하기 위해 수행 해야 하는 모든 작업에 대해 약간의 부담을 주는 것이 좋습니다. 네트워크를 만들고, 컨테이너를 시작 하 고, 모든 환경 변수를 지정 하 고, 포트를 노출 해야 합니다. 이것은 기억할 만한 것 이며, 다른 사람에 게 전달 하기가 더 어려워집니다.

다음 섹션에서는 Docker Compose에 대해 설명 합니다. Docker Compose를 사용 하면 응용 프로그램 스택을 훨씬 더 쉽게 공유할 수 있으며, 다른 사용자가 단일 (및 단순) 명령을 사용 하 여 응용 프로그램 스택을 스핀 할 수 있습니다.

## <a name="next-steps"></a>다음 단계

자습서를 계속 진행 합니다.

> [!div class="nextstepaction"]
> [Docker Compose 사용](use-docker-compose.md)
