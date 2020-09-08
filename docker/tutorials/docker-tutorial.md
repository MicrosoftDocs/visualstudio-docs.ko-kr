---
title: Docker 자습서 - Docker 시작
description: Visual Studio Code에서 Docker를 사용하는 방법의 기본 사항에 대해 설명하는 다단계 자습서입니다.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
next_page: app.md
ms.openlocfilehash: 9961810ad408a384db46439235b0b7acab325062
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89176840"
---
# <a name="tutorial-get-started-with-docker"></a>자습서: Docker 시작

이 자습서에서는 데이터베이스와 함께 여러 컨테이너 사용, Docker Compose 사용 등을 포함하여 Docker 앱을 만들고 배포하는 방법을 알아보겠습니다. 또한 컨테이너화된 앱을 Azure에 배포합니다.

## <a name="start-the-tutorial"></a>자습서 시작

이미 명령을 실행하여 자습서를 시작했으면 잘했습니다.  자습서를 시작하지 않았으면 명령 프롬프트 또는 bash 창을 열고 다음 명령을 실행합니다.

```cli
docker run -d -p 80:80 docker/getting-started
```

몇 개의 플래그가 사용되는 것을 확인할 수 있습니다. 플래그에 대한 자세한 정보는 다음과 같습니다.

- `-d` - 백그라운드에서 분리 모드로 컨테이너를 실행합니다.
- `-p 80:80` - 호스트의 포트 80을 컨테이너의 포트 80에 매핑합니다.
- `docker/getting-started` - 사용할 이미지입니다.

> [!TIP]
> 단일 문자 플래그를 결합하여 전체 명령을 줄일 수 있습니다.
> 예를 들어 위의 명령을 다음과 같이 작성할 수 있습니다.
>
> ```cli
> docker run -dp 80:80 docker/getting-started
> ```

## <a name="the-vs-code-extension"></a>VS Code 확장

더 진행하기 전에 머신에서 실행되는 컨테이너의 빠른 보기를 제공하는 Docker VS Code 확장의 주요 기능을 살펴보겠습니다. 이 확장을 통해 컨테이너 로그에 신속하게 액세스하고, 컨테이너 내부로 셸을 가져오고, 컨테이너 수명 주기를 쉽게 관리(중지, 제거 등)할 수 있습니다.

확장에 액세스하려면 [여기](https://code.visualstudio.com/docs/containers/overview)에 제공된 지침을 따르세요. 왼쪽에 있는 Docker 아이콘을 사용하여 Docker 뷰를 엽니다. 이제 확장을 열면 이 자습서가 실행되는 것을 확인할 수 있습니다. 컨테이너 이름(아래에서는 `angry_taussig`)은 무작위로 생성된 이름입니다. 따라서 사용자에게 표시되는 이름은 다를 가능성이 큽니다.

![Docker 확장에서 실행되는 자습서 컨테이너](media/vs-tutorial-in-extension.png)

## <a name="what-is-a-container"></a>컨테이너란?

이제 컨테이너를 실행했는데, ‘컨테이너란’ 무엇일까요? 간단히 말해서 컨테이너는 호스트 머신의 다른 모든 프로세스로부터 격리된, 사용자 머신의 또 다른 프로세스입니다. 격리는 오랫동안 Linux에서 제공된 기능인 [커널 네임스페이스와 cgroups](https://medium.com/@saschagrunert/demystifying-containers-part-i-kernel-space-2c53d6979504)를 활용합니다. Docker를 통해 두 기능에 쉽게 접근하고 사용할 수 있습니다.

> [!NOTE]
> **처음부터 컨테이너 만들기** 컨테이너를 처음부터 새로 만드는 방법을 알아보려면 Aqua Security의 Liz Rice가 Go에서 컨테이너를 처음부터 만드는 비디오를 시청하세요.
>
> [!VIDEO https://www.youtube-nocookie.com/embed/8fi7uSYlOdc]

## <a name="what-is-a-container-image"></a>컨테이너 이미지란?

컨테이너를 실행하는 경우 컨테이너는 격리된 파일시스템을 사용합니다. 이 사용자 지정 파일시스템은 **컨테이너 이미지**에서 제공됩니다. 이미지에는 컨테이너 파일 시스템이 포함되어 있으므로 애플리케이션을 실행하는 데 필요한 모든 것(모든 종속성, 구성, 스크립트, 이진 파일 등)이 있어야 합니다. 또한 이미지에는 환경 변수, 실행할 기본 명령, 기타 메타데이터와 같은 컨테이너의 다른 구성도 포함되어 있습니다.

나중에 이미지를 자세히 살펴보면서 계층화, 모범 사례 등의 주제를 설명하겠습니다.

> [!NOTE]
> `chroot`에 대해 잘 알고 있다면 컨테이너를 `chroot`의 확장 버전으로 생각해도 됩니다. 파일시스템은 단순히 이미지에서 가져온 것입니다. 그러나 컨테이너는 chroot만 사용할 때는 제공되지 않는 추가 격리 기능을 제공합니다.

## <a name="next-steps"></a>다음 단계

자습서를 계속 진행합니다.

> [!div class="nextstepaction"]
> [애플리케이션](your-application.md)
