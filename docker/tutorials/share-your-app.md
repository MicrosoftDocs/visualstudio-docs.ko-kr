---
title: 'Docker 자습서-3 부: 앱 공유'
description: Docker 허브 레지스트리를 사용 하 여 Docker 이미지를 공유 하는 방법을 설명 합니다.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: d5bd7a2d79bf6da710fd0f5803c2415781160143
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176839"
---
# <a name="share-your-app"></a>앱 공유

이제 이미지를 빌드 했으므로 공유 해 보겠습니다! Docker 이미지를 공유 하려면 Docker 레지스트리를 사용 해야 합니다. 기본 레지스트리는 Docker 허브 이며, 사용한 모든 이미지는에서 가져온 것입니다.

## <a name="create-a-repo"></a>리포지토리 만들기

이미지를 푸시 하려면 먼저 Docker 허브에서 리포지토리를 만들어야 합니다.

1. [Docker Hub](https://hub.docker.com) 로 이동 하 여 필요한 경우 로그인 합니다.

1. **리포지토리 만들기** 단추를 클릭 합니다.

1. 리포지토리 이름으로를 사용 `getting-started` 합니다. 표시 유형이 인지 확인 합니다 `Public` .

1. **만들기** 단추를 클릭 합니다.

페이지의 오른쪽을 살펴보면 **Docker commands**라는 섹션이 표시 됩니다. 이 리포지토리에 푸시 하기 위해 실행 해야 하는 예제 명령이 제공 됩니다.

![Push 예제가 포함 된 Docker 명령](media/push-command.png)

## <a name="push-the-image"></a>이미지 푸시

1. 명령줄에서 Docker 허브에 표시 되는 푸시 명령을 실행 해 봅니다. 명령은 "docker"가 아니라 네임 스페이스를 사용 합니다.

    ```plaintext
    $ docker push docker/getting-started
    The push refers to repository [docker.io/docker/getting-started]
    An image does not exist locally with the tag: docker/getting-started
    ```

    실패 한 이유는 무엇 인가요? Push 명령이 docker/시작 이라는 이미지를 찾으십니까 하나를 찾지 못했습니다. 를 실행 하면 `docker image ls` 하나가 표시 되지 않습니다.

    이 문제를 해결 하려면 다른 이름을 지정 하기 위해 작성 한 기존 이미지를 "태그" 해야 합니다.

1. 명령을 사용 하 여 Docker 허브에 로그인 `docker login -u <username>` 합니다.

1. 명령을 사용 `docker tag` 하 여 이미지에 `getting-started` 새 이름을 지정 합니다. `<username>`DOCKER ID로 교체 해야 합니다.

    ```bash
    docker tag getting-started <username>/getting-started
    ```

1. 이제 push 명령을 다시 시도 합니다. Docker 허브에서 값을 복사 하는 경우 `tagname` 이미지 이름에 태그를 추가 하지 않았으므로 부분을 삭제할 수 있습니다. 태그를 지정 하지 않으면 Docker는 이라는 태그를 사용 `latest` 합니다.

    ```bash
    docker push <username>/getting-started
    ```

## <a name="run-the-image-on-a-new-instance"></a>새 인스턴스에서 이미지를 실행 합니다.

이제 이미지를 빌드하여 레지스트리에 푸시 했으므로이 컨테이너 이미지가 표시 되지 않은 새 인스턴스에서 앱을 실행 해 봅니다. 이 작업을 수행 하려면 Docker에서 재생을 사용 합니다.

1. [Docker를 사용](http://play-with-docker.com)하 여 재생 하려면 브라우저를 엽니다.

1. Docker 허브 계정으로 로그인 합니다.

1. 로그인 하면 왼쪽 막대에서 "+ 새 인스턴스 추가" 링크를 클릭 합니다. (표시 되지 않는 경우 브라우저를 조금 더 넓게 만듭니다.) 몇 초 후에 브라우저에서 터미널 창이 열립니다.

    ![Docker를 사용 하 여 재생 새 인스턴스 추가](media/pwd-add-new-instance.png)

1. 터미널에서 새로 푸시된 앱을 시작 합니다.

    ```bash
    docker run -dp 3000:3000 <username>/getting-started
    ```

    이미지를 끌어온 후 결국 시작 되는 것을 볼 수 있습니다.

1. 표시 되 면 3000 배지를 클릭 하면 앱이 수정 된 상태로 표시 됩니다. 만 세! 3000 배지가 표시 되지 않으면 **포트 열기** 단추를 클릭 하 고 3000에를 입력 하면 됩니다.

## <a name="recap"></a>요약

이 섹션에서는 레지스트리에 푸시하여 이미지를 공유 하는 방법을 배웠습니다. 그런 다음 새 인스턴스로 이동 하 여 새로 푸시된 이미지를 실행할 수 있었습니다. 이는 파이프라인에서 이미지를 만들어 레지스트리에 푸시하는 CI 파이프라인에서 매우 일반적입니다. 그러면 프로덕션 환경에서 최신 버전의 이미지를 사용할 수 있습니다.

이제 마지막 섹션의 끝 부분에서 앱을 다시 시작할 때 모든 할 일 목록 항목을 모두 잃어 버렸습니다. 훌륭한 사용자 환경이 아닙니다. 다음에 다시 시작할 때마다 데이터를 유지할 수 있는 방법에 대해 알아봅니다.

## <a name="next-steps"></a>다음 단계

자습서를 계속 진행 합니다.

> [!div class="nextstepaction"]
> [데이터베이스 유지](persist-your-data.md)