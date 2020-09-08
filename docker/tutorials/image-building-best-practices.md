---
title: 'Docker 자습서 - 8부: 이미지 계층화'
description: Docker 이미지의 이미지 계층을 검사하고 관리하는 방법입니다.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: eae21a729f30a0c77fa52e5774a2f5157286dab1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89176821"
---
# <a name="image-layering"></a>이미지 계층화

이미지 구성 요소를 확인할 수 있다는 것을 알고 계신가요? `docker image history` 명령을 통해 이미지 내의 각 계층을 만드는 데 사용된 명령을 확인할 수 있습니다.

1. `docker image history` 명령을 사용하여 자습서의 앞부분에서 만든 `getting-started` 이미지 계층을 확인합니다.

    ```bash
    docker image history getting-started
    ```

    다음과 같은 출력이 표시됩니다(날짜/ID는 다를 수 있음).

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

    각 선은 이미지 계층을 나타냅니다. 여기에 표시된 것은 맨 아래 기준선으로, 맨 위에 최신 계층이 있습니다. 이 출력을 사용하여 각 계층의 크기를 빠르게 확인하고 큰 이미지를 진단할 수도 있습니다.

1. 여러 개의 선이 잘린 것을 확인할 수 있습니다. `--no-trunc` 플래그를 추가하면 전체 출력이 표시됩니다(truncated 플래그를 사용하면 잘리지 않은 출력이 표시됨).

    ```bash
    docker image history --no-trunc getting-started
    ```

## <a name="layer-caching"></a>계층 캐싱

계층화 방식을 실제로 확인했으며, 이제 컨테이너 이미지의 빌드 시간을 줄이는 데 도움이 되는 중요한 단원이 남았습니다.

> 계층이 변경되면 다운스트림 계층도 모두 다시 만들어야 합니다.

사용한 Dockerfile을 다시 한 번 살펴봅니다.

```dockerfile
FROM node:12-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "/app/src/index.js"]
```

이미지 기록 출력으로 돌아가서 Dockerfile의 각 명령이 이미지의 새 계층이 되는 것을 확인합니다. 이미지를 변경한 경우 yarn 종속성을 다시 설치해야 했던 점도 기억나실 것입니다. 이 문제를 해결할 방법이 있을까요? 빌드할 때마다 같은 종속성을 처리해야 하는 것은 효율적이지 않습니다.

이 문제를 해결하기 위해 종속성 캐싱을 지원하도록 Dockerfile을 재구성할 수 있습니다. 노드 기반 애플리케이션의 경우 `package.json` 파일에서 해당 종속성이 정의됩니다. 따라서 이 파일만 먼저 복사해서 종속성을 설치한 ‘후’ 다른 모든 항목을 복사한다면 어떻게 될까요? 그러면 `package.json`이 변경된 경우에만 yarn 종속성을 다시 만들면 됩니다. 효율적인가요?

1. 먼저 `package.json`에서 복사할 Dockerfile을 업데이트하고 종속성을 설치한 후 다른 모든 항목을 복사합니다.

    ```dockerfile hl_lines="3 4 5"
    FROM node:12-alpine
    WORKDIR /app
    COPY package.json yarn.lock ./
    RUN yarn install --production
    COPY . .
    CMD ["node", "/app/src/index.js"]
    ```

1. `docker build`를 사용하여 새 이미지를 빌드합니다.

    ```bash
    docker build -t getting-started .
    ```

    다음과 같은 출력이 표시됩니다.

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

    모든 계층이 다시 빌드된 것을 확인할 수 있습니다. Dockerfile을 많이 변경했으므로 정상적인 동작입니다.

1. 이제 `src/static/index.html` 파일을 변경합니다(예: `<title>`을 “뛰어난 todo 앱”으로 변경).

1. 다시 `docker build`를 사용하여 Docker 이미지를 빌드합니다. 이번에는 출력이 약간 다르게 표시됩니다.

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

    무엇보다 빌드 속도가 훨씬 빨라졌습니다. 또한 1~4단계에 모두 `Using cache`가 있습니다. 축하합니다. 빌드 캐시를 사용하고 있음을 알 수 있습니다. 이미지 푸시/풀/업데이트 속도도 훨씬 빨라집니다. 축하합니다.

## <a name="multi-stage-builds"></a>다단계 빌드

이 자습서에서는 자세히 설명하지 않지만, 다단계 빌드는 여러 단계로 이미지를 만드는 데 도움이 되는 매우 강력한 도구입니다. 다단계 빌드에는 다음과 같은 몇 가지 이점이 있습니다.

- 런타임 종속성과 빌드 시간 종속성 구분
- 앱을 실행하는 데 필요한 ‘항목’만 제공하여 전체 이미지 크기 축소

### <a name="maventomcat-example"></a>Maven/Tomcat 예제

Java 기반 애플리케이션을 빌드하는 경우 소스 코드를 Java 바이트 코드로 컴파일하려면 JDK가 필요합니다. 그러나 프로덕션 환경에서는 JDK가 필요하지 않습니다. 또한 앱 빌드를 위해 Maven 또는 Gradle과 같은 도구를 사용했을 수 있습니다.
해당 도구도 최종 이미지에는 필요하지 않습니다. 이 경우 다단계 빌드가 도움이 됩니다.

```dockerfile
FROM maven AS build
WORKDIR /app
COPY . .
RUN mvn package

FROM tomcat
COPY --from=build /app/target/file.war /usr/local/tomcat/webapps 
```

이 예제에서는 한 단계(`build`라고 함)를 사용하여 Maven으로 실제 Java 빌드를 수행합니다. 두 번째 단계(`FROM tomcat`부터 시작)는 `build` 단계의 파일을 복사합니다. 마지막으로 생성되는 단계만 최종 이미지입니다(`--target` 플래그를 사용하여 재정의할 수 있음).

### <a name="react-example"></a>React 예제

React 애플리케이션을 빌드하는 경우 JS 코드(일반적으로 JSX), SASS 스타일시트 등을 정적 HTML, JS, CSS로 컴파일하려면 노드 환경이 필요합니다. 서버 쪽 렌더링을 수행하지 않는 경우 프로덕션 빌드에도 노드 환경이 필요하지 않습니다. 정적 nginx 컨테이너에 정적 리소스를 제공하지 않는 이유는 무엇일까요?

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

여기서는 `node:12` 이미지를 사용하여 빌드를 수행하고(계층 캐싱 최대화) 출력을 nginx 컨테이너에 복사합니다. 멋지지 않나요?

## <a name="recap"></a>요약

이미지 구성 방식을 이해함으로써 이미지를 더 빠르게 빌드하고 더 적은 변경 내용을 제공할 수 있습니다. 다단계 빌드는 런타임 종속성과 빌드 시간 종속성을 구분하여 전체 이미지 크기를 줄이고 최종 컨테이너 보안을 강화하는 데에도 도움이 됩니다.

## <a name="next-steps"></a>다음 단계

자습서를 계속 진행합니다.

> [!div class="nextstepaction"]
> [클라우드에 배포](deploy-to-cloud.md)