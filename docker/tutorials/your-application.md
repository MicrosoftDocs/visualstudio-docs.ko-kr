---
title: 'Docker 자습서 - 1부: todo 목록 샘플 앱 빌드 및 실행'
description: Node.js에서 실행되는 todo 목록 샘플 앱에 대한 개요입니다.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: d4538becdf7627cc63ac94f65ac456123c5d9c47
ms.sourcegitcommit: 7a46232242783ebe23f2527f91eac8eb84b3ae05
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90739982"
---
# <a name="build-and-run-the-todo-sample-app"></a>todo 샘플 앱 빌드 및 실행

이 자습서의 나머지 부분에서는 Node.js에서 실행되는 간단한 todo 목록 관리자를 사용합니다. Node.js에 대해 잘 몰라도 걱정할 필요가 없습니다. 실제 JavaScript 환경은 필요하지 않습니다.

이 시점의 개발 팀은 매우 소규모이고 MVP(최소 실행 가능 제품)를 입증하는 앱을 빌드하기만 하면 됩니다. 대규모 팀, 여러 개발자 등에서 어떻게 작동하는지는 고려하지 않고 앱의 작동 방식과 앱에서 수행할 수 있는 기능만 보여 주려고 합니다.

![todo 목록 관리자 스크린샷](media/todo-list-sample.png)

## <a name="get-the-app"></a>앱 다운로드

애플리케이션을 실행하려면 먼저 애플리케이션 소스 코드를 머신으로 가져와야 합니다. 실제 프로젝트의 경우, 일반적으로 리포지토리를 복제합니다. 그러나 이 자습서에서는 애플리케이션이 포함된 ZIP 파일을 만들었습니다.

1. [ZIP을 다운로드](http://localhost/assets/app.zip)합니다. ZIP 파일을 열고 내용을 추출합니다.

1. 추출이 완료되면 선호하는 코드 편집기를 사용하여 프로젝트를 엽니다. 편집기가 필요한 경우 [Visual Studio Code](https://code.visualstudio.com/)를 사용할 수 있습니다. `package.json`과 하위 디렉터리 2개(`src` 및 `spec`)가 표시됩니다.

    ![앱을 로드하여 열린 Visual Studio Code 스크린샷](media/ide-screenshot.png)

## <a name="building-the-apps-container-image"></a>앱 컨테이너 이미지 빌드

애플리케이션을 빌드하려면 `Dockerfile`을 사용해야 합니다. Dockerfile은 컨테이너 이미지를 만드는 데 사용되는 텍스트 기반 명령 스크립트입니다. 이전에 Dockerfile을 만든 적이 있다면 아래 Dockerfile에서 몇 가지 결함을 발견했을 수 있습니다. 하지만 염려하지 않아도 됩니다. 결함은 나중에 살펴보고 수정하겠습니다.

1. `package.json` 파일과 동일한 폴더에 다음 내용으로 `Dockerfile`이라는 파일을 만듭니다.

    ```dockerfile
    FROM node:12-alpine
    WORKDIR /app
    COPY . .
    RUN yarn install --production
    CMD ["node", "/app/src/index.js"]
    ```

    `Dockerfile` 파일에 `.txt` 등의 파일 확장명이 없는지 확인합니다. 일부 편집기에서는 이 파일 확장명이 자동으로 추가되어 다음 단계에서 오류가 발생할 수도 있습니다.

1. 아직 수행하지 않은 경우 터미널을 열고 `Dockerfile`이 있는 `app` 디렉터리로 이동합니다. 이제 `docker build` 명령을 사용하여 컨테이너 이미지를 빌드합니다.

    ```bash
    docker build -t getting-started .
    ```

    또는, Dockerfile을 마우스 오른쪽 단추로 클릭하고 **이미지 빌드...** 를 선택한 다음 프롬프트에서 태그를 지정할 수도 있습니다.

    이 명령은 Dockerfile을 사용하여 새 컨테이너 이미지를 빌드했습니다. 많은 “계층”이 다운로드된 것을 발견했을 수 있습니다. 이는 `node:12-alpine` 이미지에서 시작하도록 작성기에 명령했기 때문입니다. 하지만 머신에 해당 이미지가 없어 이미지를 다운로드해야 했습니다.

    이미지가 다운로드된 후 애플리케이션에서 `yarn`을 복사하고 사용하여 애플리케이션 종속성을 설치했습니다. `CMD` 지시문은 해당 이미지에서 컨테이너를 시작할 때 실행할 기본 명령을 지정합니다.

    마지막으로, `-t` 플래그가 이미지에 태그를 지정합니다. 사람이 읽을 수 있는 최종 이미지 이름으로 생각하면 됩니다. 이미지 이름을 `getting-started`로 지정했기 때문에 컨테이너를 실행할 때 해당 이미지를 가리킬 수 있습니다.

    `docker build` 명령의 끝에 있는 `.`는 현재 디렉터리에서 `Dockerfile`을 찾도록 Docker에 지시합니다.

## <a name="starting-an-app-container"></a>앱 컨테이너 시작

이제 이미지가 준비되었으므로 애플리케이션을 실행합니다. 이렇게 하려면 `docker run` 명령을 사용합니다(앞에서 설명한 내용 참조).

1. `docker run` 명령을 사용하여 컨테이너를 시작하고 방금 만든 이미지의 이름을 지정합니다.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

    `-d` 및 `-p` 플래그를 기억하시나요? 백그라운드에서 “분리” 모드로 새 컨테이너를 실행하고 있으며 호스트의 포트 3000과 컨테이너의 포트 3000 간에 매핑을 만듭니다. 포트 매핑이 없으면 애플리케이션에 액세스할 수 없습니다.

1. 몇 초 후에 웹 브라우저에서 [http://localhost:3000](http://localhost:3000)을 엽니다.
    앱이 표시됩니다.

    ![빈 todo 목록](media/todo-list-empty.png)

1. 계속해서 항목을 한두 개 추가하고 예상대로 작동하는지 확인합니다. 항목을 완료로 표시하고 제거할 수 있습니다. 프런트 엔드가 백 엔드에 항목을 저장하는 데 성공합니다. 매우 빠르고 쉽지 않은가요?

이제 몇 개의 항목이 포함된 todo 목록 관리자가 실행되고 있고, 모두 직접 빌드한 것입니다. 다음에는 몇 가지 사항을 변경하고 컨테이너 관리 방법을 알아보겠습니다.

VS Code 확장을 잠시 살펴보면 현재 컨테이너 2개(이 자습서와 새로 시작한 앱 컨테이너)가 실행되는 것을 확인할 수 있습니다.

![자습서와 앱 컨테이너가 실행되고 있는 Docker 확장](media/vs-two-containers.png)

## <a name="recap"></a>요약

이 짧은 섹션에서는 컨테이너 이미지 빌드의 기본 사항에 대해 배웠으며, 이미지 빌드를 위해 Dockerfile을 만들었습니다. 이미지를 빌드한 후 컨테이너를 시작하고 실행 중인 앱을 살펴보았습니다.

다음에는 앱을 수정하고 실행 중인 애플리케이션을 새 이미지로 업데이트하는 방법을 알아보겠습니다. 그 과정에서 다른 몇 가지 유용한 명령을 배울 수 있습니다.

## <a name="next-steps"></a>다음 단계

자습서를 계속 진행합니다.

> [!div class="nextstepaction"]
> [앱 업데이트](update-your-app.md)
