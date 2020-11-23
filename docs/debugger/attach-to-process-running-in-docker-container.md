---
title: Docker 컨테이너에서 실행되는 프로세스에 연결
description: Docker 컨테이너를 실행하는 앱을 Visual Studio로 디버그하는 방법을 알아봅니다.
ms.date: 11/11/2020
ms.topic: conceptual
helpviewer_keywords:
- debugging, linux Docker container
- debugging, Docker container
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 5b32b402e2bbf85cf5c028ec2dc94821ec463644
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94674793"
---
# <a name="attach-to-a-process-running-on-a-docker-container"></a>Docker 컨테이너에서 실행되는 프로세스에 연결 

Windows Docker 컨테이너 또는 Linux .NET Core Docker 컨테이너에서 실행되는 앱을 Visual Studio로 디버그할 수 있습니다.

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a> Linux Docker 컨테이너에서 실행되는 프로세스에 연결

**프로세스에 연결** 대화 상자를 사용하여 로컬 또는 원격 컴퓨터의 Linux .NET Core Docker 컨테이너에서 실행되는 프로세스에 Visual Studio 디버거를 연결할 수 있습니다.

> [!IMPORTANT]
> 이 기능을 사용하려면 .NET Core 플랫폼 간 개발 워크로드를 설치하고 소스 코드에 대한 로컬 액세스 권한이 있어야 합니다.

**Linux Docker 컨테이너에서 실행 중인 프로세스에 연결하려면**

1. Visual Studio에서 **디버그 > 프로세스에 연결(CTRL+ALT+P)** 을 선택하여 **프로세스에 연결** 대화 상자를 엽니다.

![프로세스에 연결 메뉴](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. **연결 형식** 을 **Docker(Linux 컨테이너)** 로 설정합니다.
3. **찾기...** 를 선택하여 **Docker 컨테이너 선택** 대화 상자를 통해 **연결 대상** 을 설정합니다.

    Docker 컨테이너 프로세스는 로컬 또는 원격으로 디버그할 수 있습니다.

    **Docker 컨테이너 프로세스를 로컬로 디버그하려면**
    1. **Docker CLI 호스트** 를 **로컬 컴퓨터** 로 설정합니다.
    1. 목록에서 연결할 실행 중인 컨테이너를 선택하고 **확인** 을 누릅니다.

    ![Docker 컨테이너 메뉴 선택](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")

    **B. Docker 컨테이너 프로세스를 원격으로 디버그하려면**

    > [!NOTE]
    > Docker 컨테이너에서 실행 중인 프로세스에 원격으로 연결하는 옵션에는 두 가지가 있습니다. SSH를 사용하는 첫 번째 옵션은 로컬 컴퓨터에 Docker 도구를 설치하지 않은 경우에 적합합니다.  Docker 도구를 로컬로 설치했고 원격 요청을 허용하도록 구성된 Docker 디먼이 있는 경우 Docker 디먼을 사용하는 두 번째 옵션을 이용해 보세요.

    1. *SSH를 통해 원격 컴퓨터에 연결하려면
        1. 추가...를 선택하여 원격 시스템에 연결합니다.<br/>
        ![원격 시스템에 연결](../debugger/media/connect-remote-system.png "원격 시스템에 연결")
        1. SSH 또는 디먼에 성공적으로 연결되면 연결하려는 실행 중 컨테이너를 선택하고 **확인** 을 누릅니다.

    1. [Docker 디먼](https://docs.docker.com/engine/reference/commandline/dockerd/)을 통해 프로세스를 실행하는 원격 컨테이너를 대상으로 설정하려면*
        1. Docker 호스트(선택 사항)에서 디먼 주소(예: TCP, IP 등)를 지정하고 새로 고침 링크를 클릭합니다.
        1. 디먼에 성공적으로 연결되면 연결하려는 실행 중 컨테이너를 선택하고 **확인** 을 누릅니다.

4. **사용 가능한 프로세스** 목록에서 해당 컨테이너 프로세스를 선택하고 **연결** 을 선택하여 Visual Studio에서 C# 컨테이너 프로세스 디버깅을 시작합니다.

    ![완료된 Docker 연결 메뉴](../debugger/media/docker-attach-complete.png "완료된 Linux Docker 연결 메뉴")

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a> Windows Docker 컨테이너에서 실행되는 프로세스에 연결

**프로세스에 연결** 대화 상자를 사용하여 로컬 컴퓨터의 Windows Docker 컨테이너에서 실행되는 프로세스에 Visual Studio 디버거를 연결할 수 있습니다.

> [!IMPORTANT]
> .NET Core 프로세스에 이 기능을 사용하려면 .NET Core 플랫폼 간 개발 워크로드를 설치하고 소스 코드에 대한 로컬 액세스 권한이 있어야 합니다.

**Linux Docker 컨테이너에서 실행 중인 프로세스에 연결하려면**

1. Visual Studio에서 **디버그 > 프로세스에 연결**(또는 **CTRL+ALT+P**)을 선택하여 **프로세스에 연결** 대화 상자를 엽니다.

   ![프로세스에 연결 메뉴](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. **연결 형식** 을 **Docker(Windows 컨테이너)** 로 설정합니다.
3. **찾기...** 를 선택하여 **Docker 컨테이너 선택** 대화 상자를 통해 **연결 대상** 을 설정합니다.

    > [!IMPORTANT]
    > 대상 프로세스는 실행 중인 Docker Windows 컨테이너와 프로세서 아키텍처가 동일해야 합니다.

   현재는 SSH를 통해 원격 컨테이너를 대상으로 설정할 수 없고 Docker 디먼을 사용해야만 합니다.

    [Docker 디먼](https://docs.docker.com/engine/reference/commandline/dockerd/)을 통해 프로세스를 실행하는 원격 컨테이너를 대상으로 설정하려면*
    1. Docker 호스트(선택 사항)에서 디먼 주소(예: TCP, IP 등)를 지정하고 새로 고침 링크를 클릭합니다.

    1. 디먼에 성공적으로 연결되면 연결하려는 실행 중 컨테이너를 선택하고 확인을 선택합니다.

4. **사용 가능한 프로세스** 목록에서 해당 컨테이너 프로세스를 선택하고 **연결** 을 선택하여 C# 컨테이너 프로세스 디버깅을 시작합니다.

    ![완료된 Docker 연결 메뉴](../debugger/media/docker-attach-complete-windows.png "완료된 Windows Docker 연결 메뉴")

5.  사용 가능한 프로세스 목록에서 해당 컨테이너 프로세스를 선택하고 **연결** 을 선택하여 C# 컨테이너 프로세스 디버깅을 시작합니다.