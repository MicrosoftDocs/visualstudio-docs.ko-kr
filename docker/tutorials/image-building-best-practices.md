---
title: 'Docker 자습서-8 부: 이미지 계층화'
description: Docker 이미지에서 이미지 계층을 검사 하 고 관리 하는 방법입니다.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: eae21a729f30a0c77fa52e5774a2f5157286dab1
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176821"
---
# <a name="image-layering"></a>이미지 계층화

이미지를 구성 하는 항목을 확인할 수 있다는 것을 알고 계십니까? 명령을 사용 하 여 `docker image history` 이미지 내에서 각 계층을 만드는 데 사용 된 명령을 볼 수 있습니다.

1. 명령을 사용 `docker image history` 하 여 `getting-started` 자습서의 앞부분에서 만든 이미지의 레이어를 확인 합니다.

    ```bash
    docker image history getting-started
    ```

    다음과 같이 표시 되는 출력을 받아야 합니다 (날짜/Id가 다를 수 있음).

    ```plaintext
    IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
    a78a40cbf866        18 seconds ago      /bin/sh -c #(nop)  CMD ["node" "/app/src/ind…   0B                  
    f1d1808565d6        19 seconds ago      /bin/sh -c yarn install --production            85.4MB              
    a2c054d14948        36 seconds ago      /bin/sh -c #(nop) COPY dir:5dc710ad87c789593…   198kB               
    9577ae713121        37 seconds ago      /bin/sh -c #(nop) WORKDIR /app                  0B                  
    b95baba1cfdb        13 days ago         /bin/sh -c #(nop)  CMD ["node"]                 0B                  
    <missing>           13 days ago         /bin/sh -c #(nop)  ENTRYPOINT ["docker-entry…   0B                  
    <missing>           13 days ago         /bin/sh -c #(nop) COPY file:238737301d473041…   116B                
    <missing>           13 days ago         /bin/sh -c apk add --no-cache --virtual .bui…   5.35MB              
    <missing>           13 days ago         /bin/sh -c #(nop)  ENV YARN_VERSION=1.21.1      0B                  
    <missing>           13 days ago         /bin/sh -c addgroup -g 1000 node     && addu…   74.3MB              
    <missing>           13 days ago         /bin/sh -c #(nop)  ENV NODE_VERSION=12.14.1     0B                  
    <missing>           13 days ago         /bin/sh -c #(nop)  CMD ["/bin/sh"]              0B                  
    <missing>           13 days ago         /bin/sh -c #(nop) ADD file:e69d441d729412d24…   5.59MB   
    ```

    각 선은 이미지의 계층을 나타냅니다. 여기에 표시 되는 맨 위에 최신 계층이 있는 밑이 표시 됩니다. 이를 사용 하 여 각 계층의 크기를 신속 하 게 확인 하 여 큰 이미지를 진단할 수도 있습니다.

1. 몇 개의 줄이 잘릴 수 있습니다. 플래그를 추가 하면 `--no-trunc` 전체 출력을 얻게 됩니다. 예, 잘린 플래그를 사용 하 여 잘린 출력을 가져옵니다.

    ```bash
    docker image history --no-trunc getting-started
    ```

## <a name="layer-caching"></a>계층 캐싱

이제 계층화 작업을 살펴보았으므로 컨테이너 이미지의 빌드 시간을 줄이는 데 도움이 되는 중요 한 단원이 있습니다.

> 계층이 변경 된 후에도 모든 다운스트림 계층을 다시 만들어야 합니다.

한 번 더 사용 하 던 Dockerfile을 살펴보겠습니다.

```dockerfile
FROM node:12-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "/app/src/index.js"]
```

이미지 기록 출력으로 돌아가서 Dockerfile의 각 명령이 이미지의 새 계층이 됩니다. 이미지를 변경한 경우 yarn 종속성을 다시 설치 해야 합니다. 이 문제를 해결 하는 방법이 있나요? 빌드할 때마다 동일한 종속성을 제공 하는 것은 그다지 적합 하지 않습니다.

이 문제를 해결 하기 위해 종속성의 캐싱을 지 원하는 데 도움이 되도록 Dockerfile을 재구성할 수 있습니다. 노드 기반 응용 프로그램의 경우 이러한 종속성은 파일에 정의 됩니다 `package.json` . 따라서 먼저 해당 파일을 복사한 경우 종속성을 설치 하 고 다른 모든 항목 *을 복사 합니다* . 그런 다음에 대 한 변경 내용이 있는 경우에만 yarn 종속성을 다시 만듭니다 `package.json` . 적합 한가요?

1. Dockerfile을 업데이트 하 여 첫 번째에 복사 하 `package.json` 고, 종속성을 설치 하 고,에 있는 다른 모든 항목을 복사 합니다.

    ```dockerfile hl_lines="3 4 5"
    FROM node:12-alpine
    WORKDIR /app
    COPY package.json yarn.lock ./
    RUN yarn install --production
    COPY . .
    CMD ["node", "/app/src/index.js"]
    ```

1. 을 사용 하 여 새 이미지를 빌드합니다 `docker build` .

    ```bash
    docker build -t getting-started .
    ```

    다음과 같은 출력이 표시 됩니다.

    ```plaintext
    Sending build context to Docker daemon  219.1kB
    Step 1/6 : FROM node:12-alpine
    ---> b0dc3a5e5e9e
    Step 2/6 : WORKDIR /app
    ---> Using cache
    ---> 9577ae713121
    Step 3/6 : COPY package* yarn.lock ./
    ---> bd5306f49fc8
    Step 4/6 : RUN yarn install --production
    ---> Running in d53a06c9e4c2
    yarn install v1.17.3
    [1/4] Resolving packages...
    [2/4] Fetching packages...
    info fsevents@1.2.9: The platform "linux" is incompatible with this module.
    info "fsevents@1.2.9" is an optional dependency and failed compatibility check. Excluding it from installation.
    [3/4] Linking dependencies...
    [4/4] Building fresh packages...
    Done in 10.89s.
    Removing intermediate container d53a06c9e4c2
    ---> 4e68fbc2d704
    Step 5/6 : COPY . .
    ---> a239a11f68d8
    Step 6/6 : CMD ["node", "/app/src/index.js"]
    ---> Running in 49999f68df8f
    Removing intermediate container 49999f68df8f
    ---> e709c03bc597
    Successfully built e709c03bc597
    Successfully tagged getting-started:latest
    ```

    모든 계층이 다시 작성 된 것을 볼 수 있습니다. Dockerfile을 매우 약간 변경 했으므로 완벽 하 게 사용할 수 있습니다.

1. 이제 파일을 변경 합니다 (예:를 `src/static/index.html` `<title>` "놀라운 Todo 앱"으로 변경).

1. 이제를 사용 하 여 Docker 이미지를 빌드합니다 `docker build` . 이번에는 출력이 약간 다르게 표시 되어야 합니다.

    ```plaintext hl_lines="5 8 11"
    Sending build context to Docker daemon  219.1kB
    Step 1/6 : FROM node:12-alpine
    ---> b0dc3a5e5e9e
    Step 2/6 : WORKDIR /app
    ---> Using cache
    ---> 9577ae713121
    Step 3/6 : COPY package* yarn.lock ./
    ---> Using cache
    ---> bd5306f49fc8
    Step 4/6 : RUN yarn install --production
    ---> Using cache
    ---> 4e68fbc2d704
    Step 5/6 : COPY . .
    ---> cccde25a3d9a
    Step 6/6 : CMD ["node", "/app/src/index.js"]
    ---> Running in 2be75662c150
    Removing intermediate container 2be75662c150
    ---> 458e5c6f080c
    Successfully built 458e5c6f080c
    Successfully tagged getting-started:latest
    ```

    먼저 빌드가 훨씬 더 빠른 것을 알 수 있습니다. 1-4 단계에 모두 포함 되어 있는 것을 볼 수 있습니다 `Using cache` . 만 세! 빌드 캐시를 사용 하 고 있습니다. 이 이미지와 업데이트를 푸시하는 것도 훨씬 더 빠릅니다. 만 세!

## <a name="multi-stage-builds"></a>다단계 빌드

이 자습서에서는 너무 많은 단계를 사용 하는 것은 아니지만 여러 단계를 사용 하 여 이미지를 만드는 데는 매우 강력한 도구를 제공 합니다. 다음과 같은 여러 가지 이점이 있습니다.

- 런타임 종속성의 빌드 시간 종속성 구분
- 앱을 실행 하는 데 필요한 *항목만* 전달 하 여 전체 이미지 크기를 줄입니다.

### <a name="maventomcat-example"></a>Maven/Tomcat 예

Java 기반 응용 프로그램을 빌드하는 경우 소스 코드를 Java 바이트 코드로 컴파일하려면 JDK가 필요 합니다. 그러나 JDK는 프로덕션 환경에서 필요 하지 않습니다. 또한 Maven 또는 Gradle와 같은 도구를 사용 하 여 앱을 빌드할 수 있습니다.
최종 이미지에도 필요 하지 않습니다. 다단계 빌드를 지원 합니다.

```dockerfile
FROM maven AS build
WORKDIR /app
COPY . .
RUN mvn package

FROM tomcat
COPY --from=build /app/target/file.war /usr/local/tomcat/webapps 
```

이 예제에서는 `build` Maven를 사용 하 여 실제 Java 빌드를 수행 하기 위해 하나의 스테이지 (이라고 함)를 사용 합니다. 에서 시작 하는 두 번째 단계는 `FROM tomcat` 단계에서 파일을 복사 합니다 `build` . 최종 이미지는 마지막으로 생성 되는 단계 (플래그를 사용 하 여 재정의할 수 있음 `--target` )입니다.

### <a name="react-example"></a>반응 예

응답 응용 프로그램을 빌드하는 경우 JS 코드 (일반적으로 JSX), SASS 스타일 시트 등을 정적 HTML, JS 및 CSS로 컴파일하기 위한 노드 환경이 필요 합니다. 서버 쪽 렌더링을 수행 하지 않는 경우 프로덕션 빌드에 대 한 노드 환경도 필요 하지 않습니다. 정적 nginx 컨테이너에 정적 리소스를 제공 하지 않는 이유는 무엇 인가요?

```dockerfile
FROM node:12 AS build
WORKDIR /app
COPY package* yarn.lock ./
RUN yarn install
COPY public ./public
COPY src ./src
RUN yarn run build

FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
```

여기서는 이미지를 사용 하 여 `node:12` 빌드를 수행 하 고 (계층 캐싱 최대화) nginx 컨테이너에 출력을 복사 합니다. 멋지지 않나요?

## <a name="recap"></a>요약

이미지를 구성 하는 방법에 대 한 약간의 이해를 통해 이미지를 더 빠르게 빌드하고 더 적은 수의 변경 내용을 제공할 수 있습니다. 또한 다단계 빌드는 런타임 종속성의 빌드 시간 종속성을 분리 하 여 전체 이미지 크기를 줄이고 최종 컨테이너 보안을 향상 시키는 데 도움이 됩니다.

## <a name="next-steps"></a>다음 단계

자습서를 계속 진행 합니다.

> [!div class="nextstepaction"]
> [클라우드에 배포](deploy-to-cloud.md)