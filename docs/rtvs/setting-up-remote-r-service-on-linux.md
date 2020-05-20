---
title: Linux에서 원격 R 서비스 설정
description: Ubuntu 및 Linux용 Windows 하위 시스템에서 원격 R 서비스를 설정하는 방법입니다.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: c4d65388db0ef90f807ec85b8c9216d717c2b571
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62809559"
---
# <a name="remote-r-service-for-linux"></a>Linux용 원격 R 서비스

Linux용 원격 R 서비스는 현재 rtvs-daemon으로 패키지됩니다. Ubuntu를 실행하는 Linux의 Ubuntu 16.04, 16.10 LTS 데스크톱, 서버 및 Windows 하위 시스템에서 디먼을 지원하고 테스트합니다. 이 문서에서는 이러한 다양한 시스템에서 원격 R 서비스를 설정하는 방법에 대한 지침을 제공합니다.

원격 컴퓨터를 구성하면 다음 단계에서는 RTVS(Visual Studio용 R 도구)를 해당 서비스에 연결합니다.

1. **R 도구** > **Windows** > **작업 영역**을 선택하여 **작업 영역** 창을 엽니다.
1. **연결 추가**를 선택합니다.
1. 연결에 이름을 지정하고, `https://localhost:5444`(Linux용 Windows 하위 시스템) 또는 `https://public-ip:5444`(Azure 컨테이너)와 같이 해당 URL을 제공합니다. 완료된 경우 **저장**을 선택합니다.
1. 연결 아이콘을 선택하거나 연결 항목을 두 번 클릭합니다.
1. 로그인 자격 증명을 입력합니다. 사용자 이름은 `<<unix>>\ruser1`에서 `<<unix>>\`를 접두사로 사용해야 합니다(Linux 원격 컴퓨터에 대한 모든 연결의 필요에 따라).
1. 자체 서명된 인증서를 사용하는 경우 경고 메시지가 표시될 수 있습니다. 메시지는 경고를 수정하기 위한 지침을 제공합니다.

## <a name="set-up-remote-r-service"></a>원격 R 서비스 설정

이 단원에서는 다음과 같은 옵션에 대해 설명합니다.

- [물리적 Ubuntu 컴퓨터](#physical-ubuntu-computer)
- [Ubuntu Server VM 또는 Azure의 데이터 과학 VM](#ubuntu-server-vm-or-data-science-vm-on-azure)
- [로컬 또는 원격 Docker 컨테이너(빌드 정리)](#local-or-remote-docker-container-clean-build)
- [Azure Container Instances에서 실행하는 컨테이너](#container-running-on-azure-container-instances)

각각의 경우 원격 컴퓨터는 다음 중 하나의 R 인터프리터가 설치되어야 합니다.

- [Microsoft R Open](https://mran.microsoft.com/open/)
- [CRAN R for Windows](https://cran.r-project.org/bin/linux/ubuntu/)

### <a name="physical-ubuntu-computer"></a>물리적 Ubuntu 컴퓨터

1. 컴퓨터에 로그인하면 rtvs-daemon tarball을 다운로드합니다.

    ```bash
    wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current
    tar -xvzf rtvs-daemon.tar.gz
    ```

1. 설치 스크립트를 실행합니다.

    ```bash
    sudo ./rtvs-install
    ```

    자동 자동화에서 `sudo ./rtvs-install -s`를 사용합니다.

1. 서비스를 사용하도록 설정하고 시작합니다.

    ```bash
    sudo systemctl enable rtvsd
    sudo systemctl start rtvsd
    ```

1. SSL 인증서를 구성합니다(프로덕션에 필요). 기본적으로 rtvs-daemon은 `ssl-cert` 패키지에서 생성된 `ssl-cert-snakeoil.pem` 및 `ssl-cert-snakeoil.pem`을 사용합니다. 설치 중에 `ssl-cert-snakeoil.pfx`로 결합됩니다. 프로덕션용으로 관리자가 제공한 SSL 인증서를 사용합니다. SSL 인증서는 */etc/rtvs/rtvsd.config.json*에서 *.pfx* 파일 및 선택적 가져오기 암호를 제공하여 구성할 수 있습니다.

1. (선택 사항)서비스가 실행되고 있는지 확인합니다.

    ```bash
    ps -A -f | grep rtvsd
    ```

    사용자 이름 `rtvssvc` 하에서 실행되는 프로세스가 표시되지 않는 경우 다음 명령을 사용하여 시작합니다.

    ```bash
    sudo systemctl start rtvsd
    ```

1. rtvs-daemon을 추가로 구성하려면 `man rtvsd`를 참조하세요.

### <a name="ubuntu-server-vm-or-data-science-vm-on-azure"></a>Ubuntu Server VM 또는 Azure의 데이터 과학 VM

#### <a name="create-a-vm"></a>VM 만들기

1. [Azure Portal](https://portal.azure.com)에 로그인합니다.
1. Virtual Machines로 이동한 다음 **추가**를 선택합니다.
1. 사용 가능한 VM 이미지의 목록에서 다음 중 하나를 검색하고 선택합니다.
    - Ubuntu Server: `Ubuntu Server 16.04 LTS`
    - 데이터 과학 VM: `Linux Data Science`(자세한 내용은 [데이터 과학 Virtual Machines](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) 참조)
1. 배포 모델을 `Resource manager`로 설정하고 **만들기**를 선택합니다.
1. VM의 이름을 선택하고, 사용자 이름 및 암호를 제공합니다(SSH 공개 키 로그인이 지원되지 않으므로 암호는 필수임).
1. VM 구성에 다른 내용을 원하는 대로 변경합니다.
1. VM 크기를 선택하고, 구성을 확인하고, **만들기**를 선택합니다. VM을 만든 후에 다음 섹션을 진행합니다.

#### <a name="configure-the-vm"></a>VM 구성

1. VM의 **네트워킹** 섹션에서 5444 포트를 허용되는 인바운드 포트로 추가합니다. 다른 포트를 사용하려면 RTVS 디먼 구성 파일( */etc/rtvs/rtvsd.config.json*)에서 설정을 변경합니다.
1. (선택 사항)DNS 이름을; 설정합니다. IP 주소를 사용할 수 있습니다.
1. WIndows용 PuTTY와 같은 SSH 클라이언트를 사용하여 VM에 연결합니다.
1. 위의 [물리적 Ubuntu 컴퓨터](#physical-ubuntu-computer)에 대한 지침을 따릅니다.

### <a name="windows-subsystem-for-linux-wsl"></a>WSL(Linux용 Windows 하위 시스템)

1. [Windows 10](/windows/wsl/install-win10#install-the-windows-subsystem-for-linux) 또는 [Windows Server](/windows/wsl/install-on-server#enable-the-windows-subsystem-for-linux-wsl)에 대한 WSL 설치 지침을 따릅니다.
1. Windows에서 bash를 시작하고, 한 가지를 제외하고 [물리적 Ubuntu 컴퓨터](#physical-ubuntu-computer)의 이전 지침을 따릅니다. 3단계의 경우 WSL이 systemd/systemctl 인터페이스를 현재 지원하지 않기 때문에 대신 `rtvsd` 명령을 사용하여 서비스를 시작합니다.

### <a name="local-or-remote-docker-container-clean-build"></a>로컬 또는 원격 Docker 컨테이너(빌드 정리)

1. 아래 내용으로 Docker 파일을 만듭니다. 여기서는 원격 R 서비스 디먼 및 최신 버전의 R을 설치합니다. **참고**: 이 스크립트는 "foobar" 암호를 사용하여 "ruser1"이라는 사용자를 만듭니다. 이 항목은 마지막 두 `RUN` 문에서 원하는 대로 수정할 수 있습니다.

    ```docker
    FROM ubuntu:16.04

    ARG DEBIAN_FRONTEND=noninteractive

    RUN apt-get update \
     && apt-get install -y software-properties-common python-software-properties \
     && apt-get install -y apt-transport-https \
     && rm -rf /var/lib/apt/lists/*

    RUN sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list' \
     && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 417A0893 \
     && sh -c 'echo "deb https://cran.revolutionanalytics.com/bin/linux/ubuntu xenial/" > /etc/apt/sources.list.d/cran-r.list' \
     && apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9 \
     && rm -rf /var/lib/apt/lists/* \
     && apt-get clean

    RUN apt-get update --fix-missing && apt-get update \
     && apt-get install -y dotnet-dev-1.0.4 libexplain51 libzip4 libc6 git lshw ssl-cert wget \
     && rm -rf /var/lib/apt/lists/*

    # install R
    RUN apt-get update && apt-get install -y r-base-dev
    RUN apt upgrade -y

    # install rtvs-daemon
    RUN wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current && tar -xvzf rtvs-daemon.tar.gz && ./rtvs-install -s

    RUN useradd --create-home ruser1
    RUN echo "ruser1:foobar" | chpasswd

    EXPOSE 5444
    ```

1. Docker 파일을 빌드하고 실행합니다.

    ```bash
    docker build -t myrimage .
    docker run -p 5444:5444 myrimage rtvsd
    ```

1. RTVS의 컨테이너에 연결하려면 `https://localhost:5444` 경로, `<<unix>>\ruser1` 사용자 이름 및 `foobar` 암호를 사용합니다. 컨테이너를 원격 컴퓨터에서 실행하는 경우 대신 `https://remote-host-name:5444`를 경로로 사용합니다. */etc/rtvs/rtvsd.config.json*을 업데이트하여 포트를 변경할 수 있습니다.

### <a name="container-running-on-azure-container-instances"></a>Azure Container Instances에서 실행하는 컨테이너

1. [로컬 또는 원격 Docker 컨테이너(빌드 정리)](#local-or-remote-docker-container-clean-build)의 지침에 따라 이미지를 만듭니다.
1. Docker 허브 또는 Azure Container Repository에 컨테이너를 푸시합니다.
1. Azure CLI를 시작하고 `az login` 명령을 사용하여 로그인합니다.
1. `rtvsd`를 `systemd` 서비스로 실행하도록 컨테이너를 설정하지 않은 경우 `--command-line "rtvsd"`를 사용하여 컨테이너를 만드는 `az container create` 명령을 사용합니다. 아래 명령에서 이미지는 Docker 허브에 연결하도록 합니다. 컨테이너 리포지토리 자격 증명 인수를 명령줄에 추가하여 Azure Container Repository를 사용할 수도 있습니다.

    ```bash
    az container create --image myimage:latest --name myaz-container --resource-group myaz-container-res --ip-address public --port 5444 --cpu 2 --memory 4 --command-line "rtvsd"
    ```

1. `az container list` 명령을 사용하여 상태를 확인합니다. `provisioningState`: `Succeeded`를 찾습니다.
1. 프로비전에 성공하는 경우 이제 컨테이너에 연결할 수 있습니다. `ipAddress` 필드에서 공용 IP 주소를 찾습니다. 여기서는 Docker 파일의 자격 증명을 사용하여 RTVS의 컨테이너에 연결합니다.
