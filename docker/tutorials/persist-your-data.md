---
title: 'Docker 자습서 - 4부: 데이터 유지'
description: 볼륨을 탑재하여 데이터베이스 및 공유 디렉터리의 데이터를 컨테이너에 보관하는 방법을 알아봅니다.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 9a4eb5062f8f1b01e8ad5e5165d7ec9ede636124
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89485588"
---
# <a name="persist-your-data"></a> 데이터 유지

아직 모르셨다면, todo 목록은 컨테이너를 시작할 때마다 초기화되어 정리됩니다. 그 이유는 무엇입니까? 컨테이너가 어떻게 작동하는지 살펴보겠습니다.

## <a name="the-containers-filesystem"></a>컨테이너 파일 시스템

컨테이너는 실행 시 이미지의 다양한 계층을 파일 시스템에 사용합니다. 또한 각 컨테이너에는 파일을 만들거나 업데이트하거나 제거할 수 있는 자체 “스크래치 공간”이 할당됩니다. 같은 이미지를 사용하는 ‘경우에도’ 다른 컨테이너에는 변경 내용이 표시되지 않습니다.

### <a name="see-this-in-practice"></a>체험해 보기

작동 방식을 실제로 확인하려면 컨테이너 2개를 시작하고 각 컨테이너에 파일을 만듭니다. 한 컨테이너에서 만든 파일을 다른 컨테이너에서는 사용할 수 없다는 것을 알게 됩니다.

1. 1에서 10,000 사이의 난수가 포함된 `/data.txt` 파일을 만드는 `ubuntu` 컨테이너를 시작합니다.

    ```bash
    docker run -d ubuntu bash -c "shuf -i 1-10000 -n 1 -o /data.txt && tail -f /dev/null"
    ```

    명령을 알고 싶으면 Bash 셸을 시작하고 명령 2개를 호출합니다(`&&`가 있는 이유). 첫 번째 명령은 난수 1개를 선택하여 `/data.txt`에 씁니다. 두 번째 명령은 단순히 파일을 감시하여 컨테이너가 계속 실행되게 합니다.

1. `exec`로 컨테이너에 액세스하여 출력이 표시되는지 확인합니다. 이렇게 하려면 VS Code 확장을 열고 **셸 연결** 옵션을 클릭합니다. 이 옵션은 `exec`를 사용하여 VS Code 터미널 내에서 컨테이너의 셸을 엽니다.

    ![Ubuntu 컨테이너에 대한 VS Code 열기 CLI](media/attach_shell.png)

    Ubuntu 컨테이너의 셸을 실행하는 터미널이 표시됩니다. 다음 명령을 실행하여 `/data.txt` 파일 내용을 확인합니다. 그런 다음, 이 터미널을 다시 닫습니다.

    ```bash
    cat /data.txt
    ```

    명령줄을 선호하는 경우 `docker exec` 명령을 사용하여 동일한 작업을 수행할 수 있습니다. 컨테이너 ID를 가져온 후(`docker ps` 사용) 다음 명령을 사용해서 파일 내용을 가져와야 합니다.

    ```bash
    docker exec <container-id> cat /data.txt
    ```

    난수가 표시되어야 합니다.

1. 이제 다른 `ubuntu` 컨테이너(같은 이미지)를 시작하면 같은 파일이 없다는 것을 확인할 수 있습니다.

    ```bash
    docker run -it ubuntu ls /
    ```

    컨테이너를 살펴보고 `data.txt` 파일이 없는 것을 확인합니다. 파일이 첫 번째 컨테이너의 스크래치 공간에만 작성되었기 때문입니다.

1. 계속해서 `docker rm -f` 명령을 사용하여 첫 번째 컨테이너를 제거합니다.

## <a name="container-volumes"></a>컨테이너 볼륨

이전 실험에서는 각 컨테이너를 시작할 때마다 이미지 정의에서 시작되는 것을 확인했습니다. 컨테이너는 파일을 만들고, 업데이트하고, 삭제할 수 있지만 컨테이너를 제거하면 변경 내용이 손실되며 모든 변경 내용이 해당 컨테이너에 격리됩니다. 볼륨을 사용하면 이 모든 것을 변경할 수 있습니다.

[볼륨](https://docs.docker.com/storage/volumes/)은 컨테이너의 특정 파일 시스템 경로를 호스트 머신에 다시 연결하는 기능을 제공합니다. 컨테이너의 디렉터리를 탑재하면 해당 디렉터리의 변경 내용이 호스트 머신에도 표시됩니다. 컨테이너를 다시 시작한 후에도 동일한 디렉터리를 탑재하면 같은 파일이 표시됩니다.

볼륨에는 두 가지 기본 유형이 있습니다. 궁극적으로 둘 다 사용하지만, 시작은 **명명된 볼륨**으로 합니다.

## <a name="persist-your-todo-data"></a>todo 데이터 유지

기본적으로 todo 앱은 `/etc/todos/todo.db`에 있는 [SQLite 데이터베이스](https://www.sqlite.org/index.html)에 데이터를 저장합니다. SQLite를 잘 몰라도 됩니다. 모든 데이터가 단일 파일에 저장되는 관계형 데이터베이스일 뿐입니다. 대규모 애플리케이션에 가장 적합한 데이터베이스는 아니지만 작은 데모에는 효과적입니다. 이 데이터베이스를 실제 데이터베이스 엔진으로 전환하는 방법에 대해서는 나중에 설명하겠습니다.

데이터베이스가 단일 파일이므로 해당 파일을 호스트에 보관하고 다음 컨테이너에서 사용할 수 있게 하면, 컨테이너가 마지막으로 중단된 위치부터 다시 이어서 시작할 수 있어야 합니다. 볼륨을 만들어 데이터가 저장된 디렉터리에 연결(“탑재”라고도 함)하면 데이터를 유지할 수 있습니다. 컨테이너가 `todo.db` 파일에 쓰면 볼륨의 호스트에 보관됩니다.

앞서 설명한 것처럼 **명명된 볼륨**을 사용하겠습니다. 명명된 볼륨은 단순히 데이터 버킷으로 생각하면 됩니다. Docker에서 디스크 상의 실제 위치를 유지 관리하므로 볼륨 이름만 기억하면 됩니다. 볼륨을 사용할 때마다 Docker에서 올바른 데이터가 제공되는지 확인합니다.

1. `docker volume create` 명령을 사용하여 볼륨을 만듭니다.

    ```bash
    docker volume create todo-db
    ```

1. 영구적인 볼륨을 사용하지 않고 계속 실행됨에 따라 Docker 뷰(또는 `docker rm -f <id>`)에서 다시 Todo 앱 컨테이너를 중지합니다.

1. todo 앱 컨테이너를 시작하되, `-v` 플래그를 추가하여 볼륨 탑재를 지정합니다. 명명된 볼륨을 사용하고 `/etc/todos`에 탑재하면 경로에 생성된 모든 파일이 캡처됩니다.

    ```bash
    docker run -dp 3000:3000 -v todo-db:/etc/todos getting-started
    ```

1. 컨테이너가 시작되면 앱을 열고 todo 목록에 몇 개의 항목을 추가합니다.

    ![todo 목록에 추가된 항목](media/items-added.png)

1. todo 앱의 컨테이너를 제거합니다. Docker 뷰 또는 `docker ps`을(를) 사용하여 ID를 가져온 다음 `docker rm -f <id>`을(를) 수행하여 제거합니다.

1. 위와 동일한 명령을 사용하여 새 컨테이너를 시작합니다.

1. 앱을 엽니다. 여전히 항목이 목록에 표시되어야 합니다.

1. 목록 확인을 마쳤으면 컨테이너를 제거합니다.

축하합니다. 이제 데이터를 유지하는 방법을 배웠습니다.

> [!TIP]
> 명명된 볼륨과 잠시 후에 설명할 바인드 탑재는 기본 Docker 엔진 설치에서 지원되는 두 가지 기본 볼륨 유형이지만 NFS, SFTP, NetApp 등을 지원하는 데 사용할 수 있는 많은 볼륨 드라이버 플러그 인이 있습니다. Swarm, Kubernetes 등을 사용하여 클러스터형 환경의 여러 호스트에서 컨테이너 실행을 시작한 후에는 이 점이 특히 중요합니다.

## <a name="dive-into-your-volume"></a>볼륨 자세히 살펴보기

“명명된 볼륨을 사용하는 경우 Docker에서 ‘실제로’ 데이터를 저장하는 곳은 어디인가요?”라고 질문하는 사람들이 많습니다. 정답을 알고 싶으면 `docker volume inspect` 명령을 사용합니다.

```bash
docker volume inspect todo-db
[
    {
        "CreatedAt": "2019-09-26T02:18:36Z",
        "Driver": "local",
        "Labels": {},
        "Mountpoint": "/var/lib/docker/volumes/todo-db/_data",
        "Name": "todo-db",
        "Options": {},
        "Scope": "local"
    }
]
```

`Mountpoint`가 디스크에서 데이터가 저장되는 실제 위치입니다. 대부분의 머신에서는 호스트에서 이 디렉터리에 액세스하기 위해 루트 액세스 권한이 있어야 합니다. 하지만 여기가 맞습니다.

> [!NOTE]
> Docker Desktop에서 실행되는 동안 **Docker Desktop의 볼륨 데이터에 직접 액세스**하는 Docker 명령은 실제로 머신의 작은 VM 내에서 실행됩니다. *Mountpoint* 디렉터리의 실제 내용을 확인하려면 먼저 VM 내부에 액세스해야 합니다. WSL 2에서는 WSL 2 배포판 내에 있으며, 파일 탐색기를 통해 액세스할 수 있습니다.

## <a name="recap"></a>요약

이제 다시 시작해도 정상적으로 작동하는 애플리케이션을 만들었습니다. 투자자에 자랑하고 비전을 공유할 수 있습니다.

그러나 앞서 확인했듯이 변경 시마다 이미지를 다시 빌드하려면 시간이 상당히 오래 걸립니다. 더 효율적인 변경 방법이 필요합니다. 앞서 언급한 바인드 탑재를 통해 더 나은 방법을 사용할 수 있습니다. 이제 그 방법을 살펴봅시다.

## <a name="next-steps"></a>다음 단계

자습서를 계속 진행합니다.

> [!div class="nextstepaction"]
> [바인드 탑재 사용](use-bind-mounts.md)
