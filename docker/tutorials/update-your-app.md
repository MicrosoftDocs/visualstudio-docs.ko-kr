---
title: 'Docker 자습서-2 부: 앱 업데이트'
description: Docker 앱을 업데이트 하는 방법을 설명 합니다.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 4a1cba71481608803522336ad5c0f6b6354bca32
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176843"
---
# <a name="update-the-app"></a>앱 업데이트

작은 기능 요청으로 제품 팀에서 할 일 목록 항목이 없는 경우 "빈 텍스트"를 변경 하 라는 메시지가 표시 됩니다. 다음과 같이 전환 하려고 합니다.

> 아직 todo 항목이 없습니다. 하나를 추가 합니다.

매우 간단 하 고 적합 한가요? 변경 하겠습니다.

## <a name="update-the-source-code"></a>소스 코드 업데이트

1. 파일에서 `src/static/js/app.js` 줄 56을 업데이트 하 여 비어 있는 새 텍스트를 사용 합니다.

    ```diff
    -                <p className="text-center">No items yet! Add one above!</p>
    +                <p className="text-center">You have no todo items yet! Add one above!</p>
    ```

1. 이전에 사용한 것과 동일한 명령을 사용 하 여 이미지의 업데이트 된 버전을 빌드합니다.

    ```bash
    docker build -t getting-started .
    ```

1. 업데이트 된 코드를 사용 하 여 새 컨테이너를 시작 합니다.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

**그런데** 다음과 같은 오류가 표시 될 수도 있습니다 (Id는 다름).

```bash
docker: Error response from daemon: driver failed programming external connectivity on endpoint laughing_burnell 
(bb242b2ca4d67eba76e79474fb36bb5125708ebdabd7f45c8eaf16caaabde9dd): Bind for 0.0.0.0:3000 failed: port is already allocated.
```

무슨 일이 발생 하나요? 이전 컨테이너가 아직 실행 중 이므로 새 컨테이너를 시작할 수 없습니다. 이것이 문제가 되는 이유는 해당 컨테이너가 호스트의 포트 3000을 사용 하 고 컴퓨터에서 한 프로세스만 (포함 된 컨테이너) 특정 포트를 수신할 수 있기 때문입니다. 이 문제를 해결 하려면 이전 컨테이너를 제거 합니다.

## <a name="replace-the-old-container"></a>이전 컨테이너 바꾸기

컨테이너를 제거 하려면 먼저 중지 해야 합니다. 중지 된 후에는 제거할 수 있습니다. 이전 컨테이너를 제거할 수 있는 두 가지 방법이 있습니다. 가장 편안한 경로를 자유롭게 선택할 수 있습니다.

### <a name="remove-a-container-using-the-cli"></a>CLI를 사용 하 여 컨테이너 제거

1. 명령을 사용 하 여 컨테이너의 ID를 가져옵니다 `docker ps` .

    ```bash
    docker ps
    ```

1. 명령을 사용 `docker stop` 하 여 컨테이너를 중지 합니다.

    ```bash
    # Swap out <the-container-id> with the ID from docker ps
    docker stop <the-container-id>
    ```

1. 컨테이너가 중지 된 후에는 명령을 사용 하 여 제거할 수 있습니다 `docker rm` .

    ```bash
    docker rm <the-container-id>
    ```

> [!TIP]
> 명령에 "force" 플래그를 추가 하 여 단일 명령으로 컨테이너를 중지 하 고 제거할 수 있습니다 `docker rm` . 예: `docker rm -f <the-container-id>`

### <a name="remove-a-container-using-the-docker-dashboard"></a>Docker 대시보드를 사용 하 여 컨테이너 제거

VS Code 확장을 여는 경우 두 번의 클릭으로 컨테이너를 제거할 수 있습니다. 컨테이너 ID를 조회 하 고 제거 하는 것 보다 훨씬 쉽습니다.

1. 확장이 열리면 컨테이너로 이동 하 고를 마우스 오른쪽 단추로 클릭 합니다.

1. **제거** 옵션을 클릭 합니다.

1. 제거를 확인 하 고 완료 되었습니다.

![Docker 대시보드-컨테이너 제거](media/vs-removing-container.png)

### <a name="start-the-updated-app-container"></a>업데이트 된 앱 컨테이너 시작

1. 이제 업데이트 된 앱을 시작 합니다.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

1. 에서 브라우저를 새로 고치면 [http://localhost:3000](http://localhost:3000) 업데이트 된 도움말 텍스트가 표시 됩니다.

![업데이트 된 빈 텍스트가 있는 업데이트 된 응용 프로그램](media/todo-list-updated-empty-text.png)

## <a name="recap"></a>요약

업데이트를 빌드할 수 있는 경우 두 가지 사항을 발견할 수 있습니다.

- 할 일 목록에 있는 모든 기존 항목이 사라집니다. 매우 좋은 앱이 아닙니다. 잠시 후에 살펴보겠습니다.
- 이러한 작은 변경에는 *많은* 단계가 포함 되어 있습니다. 이후 섹션에서는 변경할 때마다 새 컨테이너를 다시 빌드하고 시작할 필요 없이 코드 업데이트를 보는 방법에 대해 알아봅니다.

지 속성에 대해 알아보기 전에 이러한 이미지를 다른 사람들과 공유 하는 방법을 빠르게 확인할 수 있습니다.

## <a name="next-steps"></a>다음 단계

자습서를 계속 진행 합니다.

> [!div class="nextstepaction"]
> [앱 공유](share-your-app.md)
