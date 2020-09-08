---
title: 'Docker 자습서 - 6부: 다중 컨테이너 앱'
description: 컨테이너 간에 네트워킹을 설정하고 MySQL 데이터베이스용 컨테이너를 추가하는 방법입니다.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 9513a3414a38aa02f6a4607a8c95bbf02c0e1cf6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89176803"
---
# <a name="multi-container-apps"></a>다중 컨테이너 앱

지금까지는 단일 컨테이너 앱을 사용했습니다. 이제 애플리케이션 스택에 MySQL을 추가하겠습니다. “MySQL은 어디서 실행되나요? 같은 컨테이너에 설치하나요, 아니면 별도로 실행하나요?”라는 질문을 받는 경우가 많습니다. 일반적으로 **각 컨테이너에서 한 가지 작업을 잘 수행하는 것이 좋습니다.** 다음과 같은 몇 가지 이유가 있습니다.

- API와 프런트 엔드의 크기를 데이터베이스와 다르게 스케일링해야 할 가능성이 있습니다.
- 개별 컨테이너를 사용하면 격리된 상태로 버전을 관리하고 업데이트할 수 있습니다.
- 로컬에서는 데이터베이스에 컨테이너를 사용할 수 있지만, 프로덕션 환경에서는 데이터베이스에 관리형 서비스를 사용하는 것이 좋습니다. 그러면 앱과 함께 데이터베이스 엔진을 제공하지 않아도 됩니다.
- 여러 프로세스를 실행하는 경우 프로세스 관리자가 필요하며(컨테이너는 하나의 프로세스만 시작함), 컨테이너 시작/종료가 복잡해집니다.

그 밖의 다른 이유도 있습니다. 따라서 애플리케이션을 다음과 같이 업데이트하겠습니다.

![MySQL 컨테이너에 연결된 todo 앱](media/multi-app-architecture.png)

## <a name="container-networking"></a>컨테이너 네트워킹

기본적으로 컨테이너는 격리된 상태로 실행되며, 같은 머신의 다른 프로세스나 컨테이너에 대해 아무것도 모릅니다. 컨테이너 간 통신을 허용하려면 어떻게 해야 할까요? 정답은 **네트워킹**입니다. 네트워크 엔지니어가 아니어도 괜찮습니다. 다음 규칙만 기억하면 됩니다

> [!NOTE]
> 두 컨테이너가 같은 네트워크에 있으면 서로 통신할 수 있습니다. 그러지 않으면 통신할 수 없습니다.

## <a name="start-mysql"></a>MySQL을 시작합니다.

네트워크에 컨테이너를 배치하는 방법에는 두 가지가 있습니다. 시작할 때 할당하거나 기존 컨테이너를 연결하는 것입니다. 지금은 먼저 네트워크를 만든 다음, 시작 시 MySQL 컨테이너를 연결하겠습니다.

1. 네트워크를 만듭니다.

    ```bash
    docker network create todo-app
    ```

1. MySQL 컨테이너를 시작하고 네트워크에 연결합니다. 또한 데이터베이스를 초기화하는 데 사용할 몇 개의 환경 변수를 정의해 보겠습니다([MySQL Docker Hub 목록](https://hub.docker.com/_/mysql/)에서 “환경 변수” 섹션 참조)(Windows PowerShell에서 ` \ ` 문자를 `` ` ``로 바꿈).

    ```bash
    docker run -d \
        --network todo-app --network-alias mysql \
        -v todo-mysql-data:/var/lib/mysql \
        -e MYSQL_ROOT_PASSWORD=secret \
        -e MYSQL_DATABASE=todos \
        mysql:5.7
    ```

    `--network-alias` 플래그도 지정했습니다. 잠시 후에 살펴보겠습니다.

    > [!TIP]
    > 여기서는 `todo-mysql-data`라는 볼륨 이름을 사용하고, MySQL에서 데이터를 저장하는 위치인 `/var/lib/mysql`에 볼륨을 탑재합니다. 그러나 `docker volume create` 명령을 실행한 적은 없습니다. Docker에서 명명된 볼륨을 사용하려는 의도를 인식하고 자동으로 볼륨을 만듭니다.

1. 데이터베이스가 시작되어 실행되고 있는지 확인하려면 데이터베이스에 연결하여 연결 상태를 확인합니다.

    ```bash
    docker exec -it <mysql-container-id> mysql -p
    ```

    암호 프롬프트가 표시되면 **secret**을 입력합니다. MySQL 셸에서 데이터베이스 목록을 표시하고 `todos` 데이터베이스가 표시되는지 확인합니다.

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

    축하합니다. `todos` 데이터베이스가 있으며 사용할 준비가 되었습니다.

## <a name="connect-to-mysql"></a>MySQL에 연결

MySQL이 시작되어 실행되고 있음을 확인했으므로 사용해 봅시다. 그런데 사용하려면 어떻게 해야 할까요? 같은 네트워크에서 다른 컨테이너를 실행하는 경우 컨테이너를 어떻게 찾을 수 있을까요(각 컨테이너에 고유한 IP 주소가 있음)?

방법을 파악하기 위해, 네트워킹 문제 해결 또는 디버그에 유용한 ‘많은’ 도구가 포함된 [nicolaka/netshoot](https://github.com/nicolaka/netshoot) 컨테이너를 사용하겠습니다.

1. `nicolaka/netshoot` 이미지를 사용하여 새 컨테이너를 시작합니다. 같은 네트워크에 컨테이너를 연결해야 합니다.

    ```bash
    docker run -it --network todo-app nicolaka/netshoot
    ```

1. 컨테이너 내에서 유용한 DNS 도구인 `dig` 명령을 사용합니다. 호스트 이름 `mysql`의 IP 주소를 조회합니다.

    ```bash
    dig mysql
    ```

    다음과 같은 출력이 표시됩니다.

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

    “ANSWER SECTION”에서 `mysql`에 대해 `A` 레코드가 표시되며, `172.23.0.2`로 확인됩니다(사용자 IP 주소는 다른 값일 가능성이 높음). `mysql`는 일반적으로 유효한 호스트 이름이 아니지만, Docker에서 해당 네트워크 별칭을 가진 컨테이너의 IP 주소로 확인할 수 있었습니다(앞에서 사용한 `--network-alias` 플래그 참조).

    따라서 앱이 `mysql`이라는 호스트에 연결하기만 하면 데이터베이스와 통신할 수 있습니다. 매우 간단합니다.

## <a name="run-your-app-with-mysql"></a>MySQL을 사용하여 앱 실행

todo 앱에서 몇 개의 환경 변수를 설정하여 MySQL 연결 설정을 지정할 수 있습니다. 관련 토폴로지는 다음과 같습니다.

- `MYSQL_HOST` - 실행 중인 MySQL 서버의 호스트 이름
- `MYSQL_USER` - 연결에 사용할 사용자 이름
- `MYSQL_PASSWORD` - 연결에 사용할 암호
- `MYSQL_DB` - 연결된 후 사용할 데이터베이스

> [!WARNING]
> **환경 변수를 통해 연결 설정 지정** 일반적으로 개발 환경에서는 환경 변수로 연결 설정을 지정해도 되지만, 프로덕션 환경에서 애플리케이션을 실행할 때는 이 방법을 사용하지 않는 것이 좋습니다. 이유를 파악하려면 [비밀 데이터에 환경 변수를 사용할 수 없는 이유](https://diogomonica.com/2017/03/27/why-you-shouldnt-use-env-variables-for-secret-data/)를 참조하세요.
> 더 안전한 메커니즘은 컨테이너 오케스트레이션 프레임워크에서 제공하는 비밀 지원을 사용하는 것입니다. 해당 비밀은 대부분의 경우 실행 중인 컨테이너에 파일로 탑재됩니다. 파일이 포함된 파일을 가리키는 `_FILE` 접미사가 있는 환경 변수를 지원하는 앱도 많습니다(MySQL 이미지, todo 앱 포함).
> 예를 들어 `MYSQL_PASSWORD_FILE` 변수를 설정하면 앱이 참조된 파일 내용을 연결 암호로 사용합니다. Docker에서는 해당 환경 변수를 지원하는 작업을 수행하지 않습니다. 앱이 변수를 찾고 파일 내용을 가져와야 합니다.

설명한 모든 사항에 유의하여, 개발 환경용 컨테이너를 시작합니다.

1. 위에서 언급한 각 환경 변수를 지정하고 컨테이너를 앱 네트워크에 연결합니다(Windows PowerShell에서 ` \ ` 문자를 `` ` ``로 바꿈).

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

1. 컨테이너에 대한 로그(`docker logs <container-id>`)를 살펴보면 MySQL 데이터베이스를 사용하고 있음을 나타내는 메시지를 볼 수 있습니다.

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

1. 브라우저에서 앱을 열고 todo 목록에 몇 개의 항목을 추가합니다.

1. MySQL 데이터베이스에 연결하여 데이터베이스에 항목이 기록되고 있음을 증명합니다. 암호는 **secret**입니다.

    ```bash
    docker exec -ti <mysql-container-id> mysql -p todos
    ```

    MySQL 셸에서 다음을 실행합니다.

    ```plaintext
    mysql> select * from todo_items;
    +--------------------------------------+--------------------+-----------+
    | id                                   | name               | completed |
    +--------------------------------------+--------------------+-----------+
    | c906ff08-60e6-44e6-8f49-ed56a0853e85 | Do amazing things! |         0 |
    | 2912a79e-8486-4bc3-a4c5-460793a575ab | Be awesome!        |         0 |
    +--------------------------------------+--------------------+-----------+
    ```

    사용자 테이블은 해당 항목을 포함하므로 다르게 표시될 것입니다. 그러나 항목이 테이블에 저장된 것은 확인할 수 있습니다.

Docker 확장을 잠시 살펴보면 앱 컨테이너 2가 실행되고 있음을 확인할 수 있습니다. 그러나 단일 앱으로 그룹화되었음을 나타내는 실제 표시는 없습니다. 해당 작업을 더 효율적으로 수행하는 방법은 잠시 후에 살펴보겠습니다.

![그룹화되지 않은 앱 컨테이너 2개를 보여 주는 Docker 확장](media/vs-multi-container-app.png)

## <a name="recap"></a>요약

이제 별도의 컨테이너에서 실행되는 외부 데이터베이스에 데이터를 저장하는 애플리케이션을 만들었습니다. 컨테이너 네트워킹에 대해 간략하게 배웠으며, DNS를 사용하여 서비스를 검색하는 방법을 살펴보았습니다.

그러나 애플리케이션을 시작하기 위해 수행해야 하는 모든 작업이 약간 부담스러울 수도 있습니다. 네트워크를 만들고, 컨테이너를 시작하고, 모든 환경 변수를 지정하고, 포트를 노출하고, 그 밖의 다른 작업도 수행해야 합니다. 기억해야 할 사항도 많고, 다른 사용자에게 전달하려면 작업은 더욱 어려워질 것입니다.

다음 섹션에서는 Docker Compose에 관해 설명합니다. Docker Compose를 사용하면 애플리케이션 스택을 훨씬 간편하게 공유할 수 있으며, 다른 사용자가 간단한 단일 명령으로 애플리케이션 스택을 실행하게 할 수 있습니다.

## <a name="next-steps"></a>다음 단계

자습서를 계속 진행합니다.

> [!div class="nextstepaction"]
> [Docker Compose 사용](use-docker-compose.md)
