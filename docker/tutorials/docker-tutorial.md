---
title: Docker 자습서-Docker 시작
description: Visual Studio Code에서 Docker를 사용 하는 기본 사항에 대해 설명 하는 다단계 자습서입니다.
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
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176840"
---
# <a name="tutorial-get-started-with-docker"></a>자습서: Docker 시작

이 자습서에서는 데이터베이스에 여러 컨테이너를 사용 하 고 Docker Compose를 사용 하는 등 Docker 앱을 만들고 배포 하는 방법을 알아봅니다. 또한 Azure에 컨테이너 화 된 앱을 배포 합니다.

## <a name="start-the-tutorial"></a>자습서 시작

명령을 이미 실행 하 여 자습서를 시작 했으면 축 하 합니다!  그렇지 않으면 명령 프롬프트 또는 bash 창을 열고 다음 명령을 실행 합니다.

```cli
docker run -d -p 80:80 docker/getting-started
```

몇 개의 플래그를 사용 하는 것을 알 수 있습니다. 이에 대 한 몇 가지 추가 정보는 다음과 같습니다.

- `-d` -컨테이너를 분리 된 모드 (백그라운드)로 실행 합니다.
- `-p 80:80` -호스트의 80 포트를 컨테이너의 포트 80에 매핑합니다.
- `docker/getting-started` -사용할 이미지

> [!TIP]
> 단일 문자 플래그를 결합 하 여 전체 명령을 줄일 수 있습니다.
> 예를 들어 위의 명령은 다음과 같이 작성할 수 있습니다.
>
> ```cli
> docker run -dp 80:80 docker/getting-started
> ```

## <a name="the-vs-code-extension"></a>VS Code 확장

지금까지 진행 하기 전에 컴퓨터에서 실행 되는 컨테이너의 빠른 보기를 제공 하는 Docker VS Code 확장을 강조 합니다. 컨테이너 로그에 신속 하 게 액세스할 수 있도록 하 여 컨테이너 내에서 셸을 가져오고 컨테이너 수명 주기 (중지, 제거 등)를 쉽게 관리할 수 있습니다.

확장에 액세스 하려면 [여기](https://code.visualstudio.com/docs/containers/overview)의 지침을 따르세요. 왼쪽의 Docker 아이콘을 사용 하 여 Docker 뷰를 엽니다. 이제 확장을 열면이 자습서를 실행 하는 것을 볼 수 있습니다. 컨테이너 이름 ( `angry_taussig` 아래)은 무작위로 생성 된 이름입니다. 따라서 이름이 다를 가능성이 높습니다.

![Docker 확장에서 실행 중인 자습서 컨테이너](media/vs-tutorial-in-extension.png)

## <a name="what-is-a-container"></a>컨테이너 란?

컨테이너를 실행 했으므로 이제 컨테이너 *는 무엇 인가요* ? 간단히 말해서 컨테이너는 호스트 컴퓨터의 다른 모든 프로세스에서 격리 된 컴퓨터의 또 다른 프로세스입니다. 이러한 격리는 [커널 네임 스페이스 및 cgroups](https://medium.com/@saschagrunert/demystifying-containers-part-i-kernel-space-2c53d6979504), 오랜 시간 동안 Linux에 있는 기능을 활용 합니다. Docker는 이러한 기능을 하기 쉬우며 하 고 사용 하기 쉽도록 노력 했습니다.

> [!NOTE]
> **처음부터 컨테이너 만들기** 컨테이너를 처음부터 작성 하는 방법을 확인 하려는 경우 바다색 보안의 Liz 밥에는 처음부터 컨테이너를 만드는 비디오가 있습니다.
>
> [!VIDEO https://www.youtube-nocookie.com/embed/8fi7uSYlOdc]

## <a name="what-is-a-container-image"></a>컨테이너 이미지 정의

컨테이너를 실행 하는 경우에는 격리 된 파일 시스템을 사용 합니다. 이 사용자 지정 파일 시스템은 **컨테이너 이미지**에 의해 제공 됩니다. 이미지에는 컨테이너의 filesystem이 포함 되어 있으므로 응용 프로그램을 실행 하는 데 필요한 모든 항목 (모든 종속성, 구성, 스크립트, 이진 파일 등)이 포함 되어야 합니다. 또한 이미지에는 환경 변수, 실행할 기본 명령 및 기타 메타 데이터와 같은 컨테이너에 대 한 기타 구성이 포함 되어 있습니다.

계층, 모범 사례 등의 주제를 비롯 하 여 나중에 이미지를 자세히 살펴보겠습니다.

> [!NOTE]
> 에 익숙한 경우 `chroot` 컨테이너를의 확장 된 버전으로 생각 하면 `chroot` 됩니다. 파일 시스템은 단순히 이미지에서 가져온 것입니다. 그러나 컨테이너는 단순히 chroot를 사용 하는 경우에는 사용할 수 없는 추가 격리를 추가 합니다.

## <a name="next-steps"></a>다음 단계

자습서를 계속 진행 합니다.

> [!div class="nextstepaction"]
> [응용 프로그램](your-application.md)
