---
title: 'Docker 자습서 - 5부: 바인드 탑재 사용'
description: 바인드 탑재를 사용하여 호스트의 탑재 지점을 제어하는 방법을 설명합니다.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 6474179a0714f2407ac37e724b997139206a91fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89176832"
---
# <a name="use-bind-mounts"></a>바인드 탑재 사용

이전 챕터에서는 **명명된 볼륨**에 대해 설명하고 데이터베이스의 데이터를 유지하는 데 사용했습니다. 명명된 볼륨을 사용하면 데이터 저장 ‘위치’에 대해 걱정하지 않아도 되므로 단순히 데이터를 저장하려는 경우에 유용합니다.

**바인드 탑재**를 사용하면 호스트의 탑재 지점을 정확하게 제어할 수 있습니다. 이 유형은 데이터 유지뿐 아니라 컨테이너에 추가 데이터를 제공하는 데에도 사용됩니다. 애플리케이션 작업 시 바인드 탑재를 사용하여 소스 코드를 컨테이너에 탑재하면 변경 내용을 즉시 확인할 수 있으며, 컨테이너가 코드 변경을 확인하고 응답하게 할 수 있습니다.

노드 기반 애플리케이션에서 [nodemon](https://npmjs.com/package/nodemon)은 파일 변경을 감시하고 애플리케이션을 다시 시작하는 유용한 도구입니다. 대부분의 다른 언어와 프레임워크에도 동등한 도구가 있습니다.

## <a name="quick-volume-type-comparisons"></a>볼륨 유형 빠른 비교

바인드 탑재와 명명된 볼륨은 Docker 엔진과 함께 제공되는 두 가지 기본 볼륨 유형입니다. 그러나 다른 사용 사례([SFTP](https://github.com/vieux/docker-volume-sshfs), [Ceph](https://ceph.com/geen-categorie/getting-started-with-the-docker-rbd-volume-plugin/), [NetApp](https://netappdvp.readthedocs.io/en/stable/), [S3](https://github.com/elementar/docker-s3-volume) 등)를 지원하기 위해 추가 볼륨 드라이버도 사용할 수 있습니다.

| 속성 | 명명된 볼륨 | 바인딩 마운트 |
| -------- | ------------- | ----------- |
| 호스트 위치 | Docker 선택 | 사용자 제어 |
| 탑재 예(`-v` 사용) | my-volume:/usr/local/data | /path/to/data:/usr/local/data |
| 새 볼륨에 컨테이너 내용을 채웁니다. | 예 | 아니요 |
| 볼륨 드라이버 지원 | 예 | 아니요 |

## <a name="start-a-dev-mode-container"></a>개발 모드 컨테이너 시작

컨테이너를 실행하여 개발 워크플로를 지원하려면 다음을 수행합니다.

- 컨테이너에 소스 코드 탑재
- “dev” 종속성을 포함하여 모든 종속성 설치
- nodemon을 시작하여 파일시스템 변경 감시

1. 이전 `getting-started` 컨테이너가 실행되고 있지는 않은지 확인합니다.

1. 다음 명령을 실행합니다(Windows PowerShell에서 ` \ ` 문자를 `` ` ``로 바꿈). 코드에서 수행하는 작업은 나중에 알아보겠습니다.

    ```bash
    docker run -dp 3000:3000 \
        -w /app -v ${PWD}:/app \
        node:12-alpine \
        sh -c "yarn install && yarn run dev"
    ```

    - `-dp 3000:3000` - 이전과 같습니다. 백그라운드에서 분리 모드로 실행되며 포트 매핑을 만듭니다.
    - `-w /app` - 명령이 실행되는 현재 디렉터리 또는 “작업 디렉터리”를 설정합니다.
    - `-v ${PWD}:/app` - 컨테이너에 있는 호스트의 현재 디렉터리를 `/app` 디렉터리로 바인드 탑재합니다.
    - `node:12-alpine` - 사용할 이미지입니다. Dockerfile에 있는 앱의 기본 이미지입니다.
    - `sh -c "yarn install && yarn run dev"` - 명령입니다. `sh`를 사용하여 셸을 시작하고(alpine에는 `bash`가 없음) `yarn install`을 실행하여 ‘모든’ 종속성을 설치한 다음, `yarn run dev`를 실행합니다. `package.json`을 살펴보면 `dev` 스크립트에서 `nodemon`을 시작하는 것을 확인할 수 있습니다.

1. `docker logs -f <container-id>`를 사용하여 로그를 확인할 수 있습니다. 다음과 같이 표시되면 사용할 준비가 된 것입니다.

    ```bash
    docker logs -f <container-id>
    $ nodemon src/index.js
    [nodemon] 1.19.2
    [nodemon] to restart at any time, enter `rs`
    [nodemon] watching dir(s): *.*
    [nodemon] starting `node src/index.js`
    Using sqlite database at /etc/todos/todo.db
    Listening on port 3000
    ```

    로그 확인을 마쳤으면 `Ctrl`+`C`를 눌러 종료합니다.

1. 이제 앱을 변경합니다. `src/static/js/app.js` 파일에서 단추를 로 표시되도록 변경합니다. 이 변경 내용은 109줄에 있습니다.

    ```diff
    -                         {submitting ? 'Adding...' : 'Add Item'}
    +                         {submitting ? 'Adding...' : 'Add'}
    ```

1. 페이지를 새로 고치거나 열면, 거의 즉시 브라우저에 변경 내용이 표시됩니다. 노드 서버를 다시 시작하는 데 몇 초 정도 걸릴 수 있으므로, 오류가 표시되면 몇 초 후에 새로 고쳐 보세요.

    ![업데이트된 Add 단추 레이블 스크린샷](media/updated-add-button.png)

1. 필요에 따라 다른 내용을 변경합니다. 완료되면 컨테이너를 중지하고, `docker build -t getting-started .`를 사용하여 새 이미지를 빌드합니다.

바인드 탑재 사용은 로컬 개발 설정에서 ‘매우’ 일반적입니다. 개발 머신에 모든 빌드 도구와 환경을 설치할 필요가 없다는 이점이 있기 때문입니다. 단일 `docker run` 명령을 사용하면 개발 환경이 풀되어 바로 사용할 수 있습니다. 명령 간소화에 도움이 되는 Docker Compose도 이후 단계에서 알아보겠습니다(이미 많은 플래그가 제공됨).

## <a name="recap"></a>요약

이제 데이터베이스를 유지하고 투자자와 경영진의 다양한 요구 사항에 신속하게 대응할 수 있습니다. 이에 따라 좋은 결과를 얻게 됩니다.

**진행 중인 프로젝트가 향후 개발 프로젝트로 선정된 것입니다!**

프로덕션을 준비하기 위해 데이터베이스를 SQLite 작동 환경에서 좀 더 효과적으로 스케일링되는 환경으로 마이그레이션해야 합니다. 편의상, 관계형 데이터베이스를 유지하고 MySQL을 사용하도록 애플리케이션을 전환하겠습니다. 하지만 MySQL을 실행하려면 어떻게 해야 할까요? 컨테이너 간 통신을 어떻게 허용할 수 있을까요? 다음에는 이 내용에 대해 알아보겠습니다.

## <a name="next-steps"></a>다음 단계

자습서를 계속 진행합니다.

> [!div class="nextstepaction"]
> [다중 컨테이너 앱](multi-container-apps.md)