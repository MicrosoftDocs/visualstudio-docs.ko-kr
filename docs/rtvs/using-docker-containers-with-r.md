---
title: R 및 Docker 컨테이너
description: R에 맞게 Docker 컨테이너를 설정하고 Visual Studio를 사용하여 컨테이너에 연결하는 방법입니다.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 8c5b4278ab50aac96703f03e74c014d29831f22e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62810210"
---
# <a name="use-docker-containers-with-r-tools-for-visual-studio"></a>Visual Studio용 R 도구와 함께 Docker 컨테이너 사용

RTVS(Visual Studio용 R 도구) 버전 1.3 이상은 설치된 [Windows용 Docker](https://www.docker.com/docker-windows)와 함께 Docker 컨테이너 작업을 지원합니다.

## <a name="create-a-container"></a>컨테이너 만들기

1. **작업 영역** 창의 오른쪽 모서리에서 **컨테이너** 단추를 선택합니다(**R 도구** > **Windows** > **작업 영역**). Windows용 Docker가 설치되지 않은 경우 창에 표시되고 다운로드에 대한 링크를 제공합니다. Docker를 설치하면 컴퓨터를 다시 시작해야 합니다.

    ![컨테이너 명령을 사용하는 Visual Studio용 R 도구(VS2017)의 작업 영역 창](media/container-workspaces-window.png)

1. **컨테이너** 창에서 **만들기**를 선택합니다.

    ![컨테이너 창에서 명령 만들기](media/containers-window-create.png)

1. 대화 상자에서 필수 정보를 채우고 **만들기**를 선택합니다. 입력한 자격 증명은 나중에 로그인할 때 사용할 Linux 계정을 만드는 데 사용됩니다.

    ![컨테이너를 만들 때 컨테이너 이름 및 자격 증명 입력](media/containers-window-create-fill.png)

1. RTVS에서 이미지를 빌드하는 데 약간의 시간이 걸릴 수 있습니다. Visual Studio에서 **출력** 창은 진행률을 표시하지만 긴 이미지를 다운로드하는 중에는 많은 작업을 수행하지 않는 것처럼 표시될 수 있습니다. 잠시 기다려주십시오. 이미지가 빌드되면 RTVS는 컨테이너를 시작하고 **컨테이너** 창에 표시됩니다. 오른쪽의 컨트롤은 컨테이너를 중지, 제거 또는 다시 시작합니다.

    ![완료된 컨테이너를 표시하는 컨테이너 창](media/containers-window-created.png)

## <a name="connect-to-a-container"></a>컨테이너에 연결

1. **작업 영역** 창의 **로컬 실행 중인 컨테이너** 섹션은 5444 포트에서 RTVS 디먼을 실행하는 컨테이너를 표시합니다. (디먼을 구성하는 방법에 대한 자세한 내용은 [Linux용 원격 R Server](setting-up-remote-r-service-on-linux.md)를 참조하세요.)

    ![사용 가능한 컨테이너를 보여주는 작업 영역 창](media/workspaces-window-running-containers.png)

1. 컨테이너에 연결하려면 컨테이너 이름을 두 번 클릭하거나 오른쪽에 있는 앞쪽 화살표 단추를 선택합니다. 연결되면 **R 대화형** 창이 표시됩니다([R 대화형 창 사용](interactive-repl-for-r-in-visual-studio.md) 참조).

    ![작업 영역 창 및 컨테이너에 열린 REPL 창](media/workspaces-window-container-connected.png)

## <a name="use-custom-built-images"></a>사용자 빌드 이미지 사용

RTVS는 아래 Docker 파일에서 설명한 microsoft/rtvs 이미지와 같은 사용자 빌드 이미지를 사용하여 만든 컨테이너의 관리를 감지하고 허용합니다. 여기에서 사용된 기본 이미지에는 rtvs-daemon, R 3.4.2 및 공통 R 패키지가 미리 설치되어 있습니다. **참고**: 필요에 따라 여기에 표시된 사용자 이름 및 암호를 변경합니다.

```docker
FROM microsoft/rtvs:1.3-ub1604-r3.4.2
RUN useradd --create-home ruser1
RUN echo "ruser1:foobar" | chpasswd

#Install additional R packages. You may have to install OS dependencies, see package info or error messages during build.
#RUN Rscript --vanilla -e "install.packages(c('AzureML','wordcloud'), repos = 'http://cran.us.r-project.org');"
```

다음 명령을 사용하여 이미지를 빌드하면 원하는 대로 컨테이너 이름(`--name` 인수)을 변경합니다.

```bash
docker build -t my-rtvs-image:latest .
docker run -p 6056:5444 --name my-rtvs-container my-rtvs-image:latest rtvsd
```

`-p 6056:5444` 인수는 포트 6056을 포트 5444에 매핑합니다. 여기서 RTVS는 rtvs-daemon을 감지하기 위해 사용합니다. 컨테이너 포트 5444를 노출하는 모든 컨테이너는 **작업 영역** 창에 나열됩니다. Docker 파일에서 다른 자격 증명을 지정하지 않으면 **작업 영역** 창을 사용하여 `<<unix>>\ruser1`을 사용자 이름으로 사용하고 "foobar"를 암호로 사용하는 컨테이너에 연결할 수 있습니다.
