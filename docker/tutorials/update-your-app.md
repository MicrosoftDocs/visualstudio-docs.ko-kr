---
title: 'Docker 자습서 - 2부: 앱 업데이트'
description: Docker 앱을 업데이트하는 방법을 설명합니다.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 4a1cba71481608803522336ad5c0f6b6354bca32
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89176843"
---
# <a name="update-the-app"></a>앱 업데이트

작은 기능 요청으로, todo 목록 항목이 없는 경우의 “빈 텍스트”를 변경하라는 요청을 제품 팀에서 받았습니다. 제품 팀은 다음과 같이 전환되기를 바랍니다.

> 아직 todo 항목이 없습니다. 위에서 항목을 하나 추가하세요.

매우 간단하죠? 이제 변경해 봅시다.

## <a name="update-the-source-code"></a>소스 코드 업데이트

1. `src/static/js/app.js` 파일에서 새로운 빈 텍스트를 사용하도록 줄 56을 업데이트합니다.

    ```diff
    -                <p className="text-center">No items yet! Add one above!</p>
    +                <p className="text-center">You have no todo items yet! Add one above!</p>
    ```

1. 이전에 사용한 것과 동일한 명령을 사용하여 업데이트된 이미지 버전을 빌드합니다.

    ```bash
    docker build -t getting-started .
    ```

1. 업데이트된 코드를 사용하여 새 컨테이너를 시작합니다.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

**그런데** 다음과 같은 오류가 표시됩니다(ID는 다름).

```bash
docker: Error response from daemon: driver failed programming external connectivity on endpoint laughing_burnell 
(bb242b2ca4d67eba76e79474fb36bb5125708ebdabd7f45c8eaf16caaabde9dd): Bind for 0.0.0.0:3000 failed: port is already allocated.
```

어떻게 된 것일까요? 이전 컨테이너가 여전히 실행되고 있으므로 새 컨테이너를 시작할 수 없습니다. 이 동작이 문제가 되는 이유는 해당 컨테이너가 호스트의 포트 3000을 사용하고 있으며, 머신(컨테이너 포함)에서 하나의 프로세스만 특정 포트를 수신 대기할 수 있기 때문입니다. 이 문제를 해결하려면 이전 컨테이너를 제거합니다.

## <a name="replace-the-old-container"></a>이전 컨테이너 바꾸기

컨테이너를 제거하려면 먼저 중지해야 합니다. 컨테이너가 중지되면 제거할 수 있습니다. 이전 컨테이너를 제거하는 방법에는 두 가지가 있습니다. 편리한 경로를 자유롭게 선택할 수 있습니다.

### <a name="remove-a-container-using-the-cli"></a>CLI를 사용하여 컨테이너 제거

1. `docker ps` 명령을 사용하여 컨테이너 ID를 가져옵니다.

    ```bash
    docker ps
    ```

1. `docker stop` 명령을 사용하여 컨테이너를 중지합니다.

    ```bash
    # Swap out <the-container-id> with the ID from docker ps
    docker stop <the-container-id>
    ```

1. 컨테이너가 중지되면 `docker rm` 명령을 사용하여 제거할 수 있습니다.

    ```bash
    docker rm <the-container-id>
    ```

> [!TIP]
> `docker rm` 명령에 “force” 플래그를 추가하면 단일 명령으로 컨테이너를 중지하고 제거할 수 있습니다. 예: `docker rm -f <the-container-id>`

### <a name="remove-a-container-using-the-docker-dashboard"></a>Docker 대시보드를 사용하여 컨테이너 제거

VS Code 확장을 여는 경우 두 번만 클릭하면 컨테이너를 제거할 수 있습니다. 컨테이너 ID를 조회하고 제거하는 것보다 훨씬 간편합니다.

1. 확장을 연 후 컨테이너로 이동하여 마우스 오른쪽 단추를 클릭합니다.

1. **제거** 옵션을 클릭합니다.

1. 제거를 확인하면 작업이 완료됩니다.

![Docker 대시보드 - 컨테이너 제거](media/vs-removing-container.png)

### <a name="start-the-updated-app-container"></a>업데이트된 앱 컨테이너 시작

1. 이제 업데이트된 앱을 시작합니다.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

1. 브라우저에서 [http://localhost:3000](http://localhost:3000)을 새로 고치면 업데이트된 도움말 텍스트가 표시됩니다.

![업데이트된 빈 텍스트가 있는 업데이트된 애플리케이션](media/todo-list-updated-empty-text.png)

## <a name="recap"></a>요약

업데이트를 빌드할 수 있었던 동시에 다음 두 가지 사항을 발견했을 수 있습니다.

- todo 목록의 기존 항목이 모두 사라졌습니다. 매우 좋은 앱은 아닙니다. 이 내용은 잠시 후에 살펴보겠습니다.
- 이처럼 사소한 변경에도 ‘많은’ 단계가 필요했습니다. 이후 섹션에서는 변경할 때마다 새 컨테이너를 다시 빌드하고 시작하지 않고도 코드 업데이트를 확인하는 방법을 알아보겠습니다.

지속성에 대해 배우기 전에 해당 이미지를 다른 사용자와 공유하는 방법을 빠르게 살펴보겠습니다.

## <a name="next-steps"></a>다음 단계

자습서를 계속 진행합니다.

> [!div class="nextstepaction"]
> [앱 공유](share-your-app.md)
