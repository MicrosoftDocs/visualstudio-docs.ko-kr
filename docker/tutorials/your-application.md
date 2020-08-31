---
title: 'Docker 자습서-1 부: 할 일 목록 샘플 앱 빌드 및 실행'
description: Node.js에서 실행 되는 할 일 목록 샘플 앱에 대 한 개요입니다.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: b8470c8d7708bc51916a6f57f5aa135c3267e355
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176835"
---
# <a name="build-and-run-the-todo-sample-app"></a>Todo 샘플 앱 빌드 및 실행

이 자습서의 나머지 부분에서는 Node.js에서 실행 되는 간단한 할 일 목록 관리자로 작업 합니다. Node.js 잘 모르는 경우 걱정할 필요가 없습니다. 실제 JavaScript 환경이 필요 하지 않습니다.

이 시점에서 개발 팀은 매우 작고 MVP (최소 실행 가능 제품)를 입증 하는 앱을 빌드 하기만 하면 됩니다. 어떻게 작동 하는지, 그리고 규모가 많은 팀, 여러 개발자 등에 게 어떻게 작동 하는지 고려 하지 않고도 수행할 수 있는 작업을 표시 하려고 합니다.

![할 일 목록 관리자 스크린샷](media/todo-list-sample.png)

## <a name="get-the-app"></a>앱 다운로드

응용 프로그램을 실행 하려면 먼저 컴퓨터에 응용 프로그램 소스 코드를 가져와야 합니다. 실제 프로젝트의 경우 일반적으로 리포지토리를 복제 합니다. 그러나이 자습서에서는 응용 프로그램을 포함 하는 ZIP 파일을 만들었습니다.

1. [ZIP을 다운로드](/assets/app.zip)합니다. ZIP 파일을 열고 콘텐츠를 추출 했는지 확인 합니다.

1. 압축을 푼 후에는 자주 사용 하는 코드 편집기를 사용 하 여 프로젝트를 엽니다. 편집기가 필요한 경우 [Visual Studio Code](https://code.visualstudio.com/)를 사용할 수 있습니다. `package.json`및 두 개의 하위 디렉터리 (및)가 표시 되어야 합니다 `src` `spec` .

    ![앱을 로드 하 여 연 Visual Studio Code의 스크린샷](media/ide-screenshot.png)

## <a name="building-the-apps-container-image"></a>앱의 컨테이너 이미지 빌드

응용 프로그램을 빌드하기 위해를 사용 해야 `Dockerfile` 합니다. Dockerfile은 단순히 컨테이너 이미지를 만드는 데 사용 되는 명령의 텍스트 기반 스크립트입니다. 이전에 Dockerfiles를 만든 경우 아래 Dockerfiles에 몇 가지 결함이 나타날 수 있습니다. 하지만 걱정 하지 마세요. 이에 대해 자세히 살펴보겠습니다.

1. `Dockerfile`다음 내용이 포함 된 파일과 동일한 폴더에 이라는 파일을 만듭니다 `package.json` .

    ```dockerfile
    FROM node:12-alpine
    WORKDIR /app
    COPY . .
    RUN yarn install --production
    CMD ["node", "/app/src/index.js"]
    ```

    파일에 `Dockerfile` 와 같은 파일 확장명이 없는지 확인 하세요 `.txt` . 일부 편집기는이 파일 확장명을 자동으로 추가할 수 있으며이로 인해 다음 단계에서 오류가 발생 합니다.

1. 아직 수행 하지 않은 경우 터미널을 열고를 사용 하 여 디렉터리로 이동 `app` `Dockerfile` 합니다. 이제 명령을 사용 하 여 컨테이너 이미지를 빌드합니다 `docker build` .

    ```bash
    docker build -t getting-started .
    ```

    이 명령은 Dockerfile을 사용 하 여 새 컨테이너 이미지를 빌드 했습니다. 많은 "계층"이 다운로드 되었음을 알 수 있습니다. 이는 이미지에서 시작 하는 작성기를 지시 했기 때문입니다 `node:12-alpine` . 그러나 컴퓨터에서 해당 이미지를 다운로드 하는 데 필요한 것은 아닙니다.

    이미지를 다운로드 한 후 응용 프로그램에서 복사 하 고 `yarn` 응용 프로그램의 종속성을 설치 하는 데 사용 합니다. `CMD`지시문은이 이미지에서 컨테이너를 시작할 때 실행할 기본 명령을 지정 합니다.

    마지막으로 `-t` 플래그는 이미지에 태그를 지정 합니다. 이를 최종 이미지에 대 한 사람이 읽을 수 있는 이름으로 생각 하면 됩니다. 이미지의 이름을 지정 했으므로 `getting-started` 컨테이너를 실행할 때 해당 이미지를 참조할 수 있습니다.

    명령의 끝에 있는는 `.` `docker build` Docker가 현재 디렉터리에서를 찾도록 지시 합니다 `Dockerfile` .

## <a name="starting-an-app-container"></a>앱 컨테이너 시작

이제 이미지가 있으므로 응용 프로그램을 실행 합니다. 이렇게 하려면 `docker run` 명령을 사용 합니다 (이전에는?).

1. 명령을 사용 하 여 컨테이너를 시작 `docker run` 하 고 방금 만든 이미지의 이름을 지정 합니다.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

    `-d`및 플래그를 기억할 `-p` 까 요? "분리 됨" 모드로 새 컨테이너를 실행 하 고 (백그라운드에서) 호스트의 포트 3000 간 매핑을 컨테이너의 포트 3000로 만듭니다. 포트 매핑이 없으면 응용 프로그램에 액세스할 수 없습니다.

1. 몇 초 후에 웹 브라우저를 엽니다 [http://localhost:3000](http://localhost:3000) .
    앱이 표시 됩니다.

    ![빈 Todo 목록](media/todo-list-empty.png)

1. 계속 해 서 항목을 추가 하 고 원하는 대로 작동 하는지 확인 합니다. 항목을 완료로 표시 하 고 항목을 제거할 수 있습니다. 프런트 엔드가 백 엔드에 항목을 저장 하는 데 성공 했습니다. 매우 빠르고 쉬우며,

이 시점에서 몇 가지 항목을 포함 하는 todo 목록 관리자를 실행 하 고 모든 항목을 작성 해야 합니다. 이제 몇 가지 사항을 변경 하 고 컨테이너를 관리 하는 방법을 알아보겠습니다.

VS Code 확장을 빠르게 확인 하는 경우 현재 실행 중인 두 개의 컨테이너 (이 자습서와 새로 시작한 앱 컨테이너)가 표시 되어야 합니다.

![자습서 및 앱 컨테이너를 실행 하는 Docker 확장](media/vs-two-containers.png)

## <a name="recap"></a>요약

이 짧은 섹션에서는 컨테이너 이미지를 빌드하고이를 위해 Dockerfile을 만드는 방법에 대 한 기본 사항을 배웠습니다. 이미지를 작성 한 후에는 컨테이너를 시작 하 고 실행 중인 앱을 살펴보았습니다.

다음으로 앱을 수정 하 고 실행 중인 응용 프로그램을 새 이미지로 업데이트 하는 방법을 알아봅니다. 이 방법에 따라 몇 가지 다른 유용한 명령을 배울 수 있습니다.

## <a name="next-steps"></a>다음 단계

자습서를 계속 진행 합니다.

> [!div class="nextstepaction"]
> [앱 업데이트](update-your-app.md)