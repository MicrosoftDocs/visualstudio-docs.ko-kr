---
title: Linux의 원격 디버그 .NET Core | Microsoft Docs
ms.date: 02/26/2020
ms.topic: conceptual
helpviewer_keywords:
- remote debugging, linux
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23bc0fa990a79b1855ec382f42248a0f847c3c9c
ms.sourcegitcommit: 3d64bfb9bf85395357effe054db9a9afaa0be5ea
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/29/2020
ms.locfileid: "78200868"
---
# <a name="remote-debug-net-core-on-linux-using-ssh"></a>SSH를 사용 하 여 Linux에서 .NET Core 원격 디버그

Visual Studio 2017부터 SSH를 통해 Linux에서 실행 되는 .NET Core 프로세스에 연결할 수 있습니다. 이 문서에서는 디버깅을 설정 하는 방법과 디버그 하는 방법을 설명 합니다.

## <a name="prerequisites"></a>사전 요구 사항

Visual Studio 컴퓨터에서 **ASP.NET 및 웹 개발** 워크 로드 또는 **.net Core 플랫폼 간 개발** 워크 로드를 설치 해야 합니다.

Linux 서버에서 SSH 서버를 설치 하 고, 압축을 풀고, 설치 하는 데 말아 또는 wget을 사용 해야 합니다. 예를 들어 Ubuntu에서 다음을 실행 하 여이 작업을 수행할 수 있습니다.

``` cmd
sudo apt-get install openssh-server unzip curl
```

## <a name="build-and-deploy-the-application"></a>애플리케이션 빌드 및 배포

디버깅을 위해 응용 프로그램을 준비 하려면:

- 응용 프로그램을 빌드할 때 디버그 구성을 사용 하는 것이 좋습니다. 사전 컴파일된 코드 (릴리스 구성)는 디버그에 의해 컴파일된 코드 보다 디버그 하기가 훨씬 어렵습니다. 릴리스 구성을 사용 해야 하는 경우 먼저 내 코드만를 사용 하지 않도록 설정 합니다. 이 설정을 사용 하지 않으려면 **도구** > **옵션** > **디버깅**을 선택 하 고 **내 코드만 사용**을 선택 취소 합니다.

- 프로젝트가 [이식 가능한 pdb](https://github.com/OmniSharp/omnisharp-vscode/wiki/Portable-PDBs) (기본 설정)를 생성 하도록 구성 되어 있는지 확인 하 고 PDS가 DLL과 동일한 위치에 있는지 확인 합니다. Visual Studio에서이를 구성 하려면 프로젝트를 마우스 오른쪽 단추로 클릭 한 다음 **속성** > **선택** 하 > **고급** > **디버깅 정보**를 선택 합니다.

디버깅 하기 전에 여러 가지 방법을 사용 하 여 앱을 배포할 수 있습니다. 예를 들어, 다음을 수행할 수 있습니다.

- 소스를 대상 컴퓨터에 복사 하 고 Linux 컴퓨터의 ```dotnet build```를 사용 하 여 빌드합니다.

- Windows에서 앱을 빌드하고 빌드 아티팩트를 Linux 컴퓨터로 전송 합니다. (빌드 아티팩트는 응용 프로그램 자체, 종속 될 수 있는 런타임 라이브러리 및 *. deps. json* 파일로 구성 됩니다.)

## <a name="attach-the-debugger"></a>디버거 연결

컴퓨터가 구성 되 면 Linux 컴퓨터에서 응용 프로그램을 시작 하 고 디버거를 연결할 준비가 된 것입니다.

1. Visual Studio에서 **디버그** > **프로세스에 연결**...을 선택 합니다.

1. **연결 유형** 목록에서 **SSH**를 선택 합니다.

1. **연결 대상을** 대상 컴퓨터의 IP 주소 또는 호스트 이름으로 변경 합니다.

1. 디버깅할 프로세스를 찾습니다.

   코드는 고유한 프로세스 이름 또는 dotnet 이라는 프로세스에서 실행 됩니다. 관심 있는 프로세스를 찾으려면 해당 프로세스에 대 한 명령줄 인수를 보여 주는 **제목** 열을 선택 합니다.

   다음 예제에서는 **프로세스에 연결** 대화 상자에 표시 된 SSH 전송을 통해 원격 Linux 컴퓨터의 프로세스 목록을 볼 수 있습니다.

   ![Linux 프로세스에 연결](media/remote-debug-linux-over-ssh-attach.png)

1. **연결**을 선택합니다.

1. 표시 되는 대화 상자에서 디버깅 하려는 코드의 형식을 선택 합니다. **관리 (Unix 용 .Net Core)** 를 선택 합니다.

1. Visual Studio 디버깅 기능을 사용 하 여 앱을 디버깅 합니다.

   다음 예제에서 Visual Studio 디버거는 원격 Linux 컴퓨터에서 실행 되는 코드의 중단점에서 중지 된 것을 볼 수 있습니다.

   ![중단점 도달](media/remote-debug-linux-over-ssh-hit-breakpoint.png)