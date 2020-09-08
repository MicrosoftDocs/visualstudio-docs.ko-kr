---
title: 'Docker 자습서 - 3부: 앱 공유'
description: Docker Hub 레지스트리를 사용하여 Docker 이미지를 공유하는 방법을 설명합니다.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: d5bd7a2d79bf6da710fd0f5803c2415781160143
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89176839"
---
# <a name="share-your-app"></a>앱 공유

이제 이미지를 빌드했으므로 공유해 봅시다. Docker 이미지를 공유하려면 Docker 레지스트리를 사용해야 합니다. 기본 레지스트리는 Docker Hub이며, 사용한 모든 이미지는 여기서 가져온 것입니다.

## <a name="create-a-repo"></a>리포지토리 만들기

이미지를 푸시하려면 먼저 Docker Hub에 리포지토리를 만들어야 합니다.

1. 필요한 경우 [Docker Hub](https://hub.docker.com)로 이동하여 로그인합니다.

1. **리포지토리 만들기** 단추를 클릭합니다.

1. 리포지토리 이름에 `getting-started`를 사용합니다. 표시 유형이 `Public`인지 확인합니다.

1. **만들기** 단추를 클릭합니다.

페이지 오른쪽을 보면 **Docker 명령** 섹션이 표시됩니다. 이 리포지토리에 푸시하기 위해 실행해야 하는 예제 명령을 여기서 확인할 수 있습니다.

![Docker 명령 및 푸시 예제](media/push-command.png)

## <a name="push-the-image"></a>이미지 푸시

1. Docker Hub에 표시된 푸시 명령을 명령줄에서 실행해 봅니다. 명령에서 “docker”가 아니라 해당 네임스페이스를 사용하는 것을 확인합니다.

    ```plaintext
    $ docker push docker/getting-started
    The push refers to repository [docker.io/docker/getting-started]
    An image does not exist locally with the tag: docker/getting-started
    ```

    명령이 실패한 이유는 무엇일까요? 푸시 명령에서 docker/getting-started라는 이미지를 찾았으나 찾지 못했습니다. `docker image ls`를 실행해도 해당 이미지가 표시되지 않습니다.

    이 문제를 해결하려면 빌드한 기존 이미지에 “태그”를 지정하여 다른 이름을 지정해야 합니다.

1. `docker login -u <username>` 명령을 사용하여 Docker Hub에 로그인합니다.

1. `docker tag` 명령을 사용하여 `getting-started` 이미지에 새 이름을 지정합니다. `<username>`을 Docker ID로 교체해야 합니다.

    ```bash
    docker tag getting-started <username>/getting-started
    ```

1. 이제 푸시 명령을 다시 시도합니다. Docker Hub에서 값을 복사하는 경우에는 이미지 이름에 태그를 추가하지 않았으므로 `tagname` 부분을 삭제할 수 있습니다. 태그를 지정하지 않으면 Docker에서 `latest`라는 태그를 사용합니다.

    ```bash
    docker push <username>/getting-started
    ```

## <a name="run-the-image-on-a-new-instance"></a>새 인스턴스에서 이미지 실행

이제 이미지를 빌드하고 레지스트리에 푸시했으므로 이 컨테이너 이미지가 표시된 적이 없는 새 인스턴스에서 앱을 실행해 봅니다. 이렇게 하려면 Play with Docker를 사용합니다.

1. 브라우저에서 [Play with Docker](http://play-with-docker.com)를 엽니다.

1. Docker Hub 계정으로 로그인합니다.

1. 로그인한 후 왼쪽 사이드바에서 “+ 새 인스턴스 추가” 링크를 클릭합니다. 링크가 표시되지 않으면 브라우저를 좀 더 넓게 만듭니다. 몇 초 후에 브라우저에서 터미널 창이 열립니다.

    ![Play with Docker 새 인스턴스 추가](media/pwd-add-new-instance.png)

1. 터미널에서 새로 푸시된 앱을 시작합니다.

    ```bash
    docker run -dp 3000:3000 <username>/getting-started
    ```

    이미지가 풀다운되어 결국 시작되는 것을 확인할 수 있습니다.

1. 3000 배지가 표시되면 클릭하고 앱에 수정 내용이 반영된 것을 확인합니다. 축하합니다. 3000 배지가 표시되지 않으면 **포트 열기** 단추를 클릭하고 3000을 입력할 수 있습니다.

## <a name="recap"></a>요약

이 섹션에서는 이미지를 레지스트리에 푸시하여 공유하는 방법을 배웠습니다. 그런 다음 새 인스턴스로 이동하여 새로 푸시된 이미지를 실행할 수 있었습니다. 이 동작은 파이프라인이 이미지를 만들어 레지스트리에 푸시한 다음, 프로덕션 환경에서 최신 버전의 이미지를 사용할 수 있는 CI 파이프라인에서는 매우 일반적입니다.

이 동작이 이해가 되면, 지난 섹션의 끝 부분에서 앱을 다시 시작했을 때 todo 목록 항목이 모두 사라진 것을 떠올려 봅니다. 사용자 환경에 좋지 않으므로 다음에는 앱을 다시 시작해도 데이터를 유지할 수 있는 방법을 알아보겠습니다.

## <a name="next-steps"></a>다음 단계

자습서를 계속 진행합니다.

> [!div class="nextstepaction"]
> [데이터베이스 유지](persist-your-data.md)