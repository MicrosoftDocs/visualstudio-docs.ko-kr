---
title: 'Docker 자습서-5 부: 바인드 탑재 사용'
description: 바인드 탑재를 사용 하 여 호스트의 탑재 지점을 제어 하는 방법을 설명 합니다.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 6474179a0714f2407ac37e724b997139206a91fb
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176832"
---
# <a name="use-bind-mounts"></a>바인드 탑재 사용

이전 장에서는 데이터베이스에 데이터를 유지 하기 위해 **명명 된 볼륨** 에 대해 알아보았습니다. 데이터가 저장 되는 *위치* 에 대해 걱정 하지 않아도 되기 때문에 단순히 데이터를 저장 하려는 경우에는 명명 된 볼륨이 매우 유용 합니다.

**바인드 탑재**를 사용 하면 호스트에서 정확한 탑재 지점을 제어할 수 있습니다. 이를 사용 하 여 데이터를 유지할 수 있지만 컨테이너에 추가 데이터를 제공 하는 데 종종 사용 됩니다. 응용 프로그램에서 작업할 때 바인드 탑재를 사용 하 여 소스 코드를 컨테이너에 탑재 하 고 코드 변경 내용을 표시 하 고 응답 하 고 변경 내용을 바로 볼 수 있도록 합니다.

노드 기반 응용 프로그램의 경우 [nodemon](https://npmjs.com/package/nodemon) 는 파일 변경 내용을 확인 하 고 응용 프로그램을 다시 시작 하는 데 유용한 도구입니다. 대부분의 다른 언어 및 프레임 워크에는 동일한 도구가 있습니다.

## <a name="quick-volume-type-comparisons"></a>빠른 볼륨 형식 비교

바인딩 탑재 및 명명 된 볼륨은 Docker 엔진과 함께 제공 되는 두 가지 주요 볼륨 유형입니다. 그러나 다른 사용 사례 ([SFTP](https://github.com/vieux/docker-volume-sshfs), [Ceph](https://ceph.com/geen-categorie/getting-started-with-the-docker-rbd-volume-plugin/), [netapp](https://netappdvp.readthedocs.io/en/stable/), [S3](https://github.com/elementar/docker-s3-volume)등)를 지원 하기 위해 추가 볼륨 드라이버를 사용할 수 있습니다.

| 속성 | 명명된 볼륨 | 바인딩 마운트 |
| -------- | ------------- | ----------- |
| 호스트 위치 | Docker 선택 | 제어할 수 있습니다. |
| 탑재 예제 (사용 `-v` ) | 내 볼륨:/usr/로컬/데이터 | /path/to/data:/usr/local/data |
| 새 볼륨을 컨테이너 내용으로 채웁니다. | 예 | 예 |
| 볼륨 드라이버 지원 | 예 | 예 |

## <a name="start-a-dev-mode-container"></a>개발 모드 컨테이너 시작

컨테이너를 실행 하 여 개발 워크플로를 지원 하려면 다음을 수행 합니다.

- 컨테이너에 소스 코드를 탑재 합니다.
- "Dev" 종속성을 포함 하 여 모든 종속성을 설치 합니다.
- Nodemon를 시작 하 여 파일 시스템 변경 내용 감시

1. 이전 컨테이너를 실행 하 고 있지 않은지 확인 `getting-started` 합니다.

1. 다음 명령을 실행 합니다 ( ` \ ` Windows PowerShell에서 문자를로 바꿈 `` ` `` ). 다음에 대 한 정보를 확인할 수 있습니다.

    ```bash
    docker run -dp 3000:3000 \
        -w /app -v ${PWD}:/app \
        node:12-alpine \
        sh -c "yarn install && yarn run dev"
    ```

    - `-dp 3000:3000` -이전과 동일 합니다. 분리 된 (백그라운드) 모드에서 실행 및 포트 매핑 만들기
    - `-w /app` -"작업 디렉터리" 또는 명령이 실행 될 현재 디렉터리를 설정 합니다.
    - `-v ${PWD}:/app`-bind 컨테이너의 호스트에서 디렉터리로 현재 디렉터리를 탑재 합니다. `/app`
    - `node:12-alpine` -사용할 이미지입니다. Dockerfile의 앱에 대 한 기본 이미지입니다.
    - `sh -c "yarn install && yarn run dev"` -명령입니다. `sh` `bash` `yarn install` *모든* 종속성을 설치 하 고 실행 하기 위해 (알파인가 없는)를 사용 하 여 셸을 시작 하 고 `yarn run dev` 있습니다. 를 살펴보면 `package.json` 스크립트가 시작 되는 것을 볼 수 있습니다 `dev` `nodemon` .

1. 를 사용 하 여 로그를 볼 수 있습니다 `docker logs -f <container-id>` . 다음과 같이 표시 되 면 이동할 준비가 되었다는 것을 알 수 있습니다.

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

    로그를 확인 하 고 나면 종료 하 여 종료 `Ctrl` + `C` 합니다.

1. 이제 앱을 변경 합니다. 파일에서 `src/static/js/app.js` **항목 추가** 단추를 간단히 **추가**로 변경 합니다. 이 변경 내용은 109 줄에 있습니다.

    ```diff
    -                         {submitting ? 'Adding...' : 'Add Item'}
    +                         {submitting ? 'Adding...' : 'Add'}
    ```

1. 페이지를 새로 고치거 나 열면 간단히 브라우저에 변경 내용이 거의 즉시 표시 됩니다. 노드 서버를 다시 시작 하는 데 몇 초 정도 걸릴 수 있으므로 오류가 발생 하면 몇 초 후에 새로 고쳐 보세요.

    ![추가 단추에 대 한 업데이트 된 레이블의 스크린샷](media/updated-add-button.png)

1. 원한다 면 원하는 다른 변경 작업을 수행할 수 있습니다. 완료 되 면 컨테이너를 중지 하 고를 사용 하 여 새 이미지를 빌드합니다 `docker build -t getting-started .` .

Bind 탑재를 사용 하는 것은 로컬 개발을 위한 *매우* 일반적인 방법입니다. 이점은 개발 컴퓨터에 모든 빌드 도구 및 환경을 설치할 필요가 없다는 것입니다. 단일 명령을 사용 하 여 `docker run` 개발 환경을 끌어온 후 사용할 수 있습니다. 이후 단계에서 Docker Compose 하는 방법에 대해 알아봅니다 .이는 명령을 간소화 하는 데 도움이 됩니다 (이미 많은 플래그를 제공 함).

## <a name="recap"></a>요약

이 시점에서 데이터베이스를 유지 하 고 투자자 및 창립자의 요구와 요구에 신속 하 게 대응할 수 있습니다. 만 세! 무엇 인가요? 훌륭한 소식을 받았습니다.

**향후 개발을 위해 프로젝트를 선택 했습니다.**

프로덕션을 준비 하기 위해 데이터베이스를 SQLite에서 작업 하는 것 보다 더 나은 규모를 확장할 수 있는 항목으로 마이그레이션해야 합니다. 간단히 하기 위해 관계형 데이터베이스를 유지 하 고 MySQL을 사용 하도록 응용 프로그램을 전환 합니다. 하지만 MySQL을 실행 하는 방법은 무엇입니까? 컨테이너가 서로 통신할 수 있도록 허용 하려면 어떻게 해야 하나요? 이에 대 한 자세한 내용은 다음을 확인 하세요.

## <a name="next-steps"></a>다음 단계

자습서를 계속 진행 합니다.

> [!div class="nextstepaction"]
> [다중 컨테이너 앱](multi-container-apps.md)