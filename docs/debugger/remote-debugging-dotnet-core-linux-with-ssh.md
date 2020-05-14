---
title: Linux의 .NET Core 원격 디버그 | Microsoft Docs
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
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/29/2020
ms.locfileid: "78200868"
---
# <a name="remote-debug-net-core-on-linux-using-ssh"></a>SSH를 사용하여 Linux의 .NET Core 원격 디버그

Visual Studio 2017부터 SSH를 통해 Linux에서 실행되는 .NET Core 프로세스에 연결할 수 있습니다. 이 문서에서는 디버깅을 설정하는 방법과 디버그하는 방법을 설명합니다.

## <a name="prerequisites"></a>사전 요구 사항

Visual Studio 컴퓨터에서 **ASP.NET 및 웹 개발** 워크로드 또는 **.NET Core 플랫폼 간 개발** 워크로드를 설치해야 합니다.

Linux 서버에서 SSH 서버를 설치해야 합니다(curl 또는 wget을 사용하여 압축을 풀고 설치). 예를 들어 Ubuntu에서 다음을 실행하여 이 작업을 수행할 수 있습니다.

``` cmd
sudo apt-get install openssh-server unzip curl
```

## <a name="build-and-deploy-the-application"></a>애플리케이션 빌드 및 배포

디버그할 애플리케이션을 준비하려면

- 애플리케이션을 빌드할 때 디버그 구성을 사용하는 것이 좋습니다. 리테일 컴파일 코드(릴리스 구성)는 디버그 의해 컴파일 코드보다 디버그하기 훨씬 어렵습니다. 릴리스 구성을 사용해야 하는 경우 먼저 내 코드만을 사용하지 않도록 설정합니다. 이 설정을 해제하려면 **도구** > **옵션** > **디버깅**을 선택한 다음 **내 코드만 사용**을 선택 취소합니다.

- 프로젝트가 [이식 가능 PDB](https://github.com/OmniSharp/omnisharp-vscode/wiki/Portable-PDBs)(기본 설정)를 생성하도록 구성되었는지, PDB가 DLL과 동일한 위치에 있는지 확인합니다. Visual Studio에서 이를 구성하려면 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성** > **빌드** > **고급** > **디버깅 정보**를 선택합니다.

디버그하기 전에 여러 가지 방법을 사용하여 앱을 배포할 수 있습니다. 예를 들어 다음 작업을 할 수 있습니다.

- 소스를 대상 컴퓨터에 복사하고 Linux 컴퓨터의 ```dotnet build```를 사용하여 빌드합니다.

- Windows에서 앱을 빌드하고 빌드 아티팩트를 Linux 컴퓨터로 전송합니다. (빌드 아티팩트는 애플리케이션 자체, 애플리케이션이 종속될 수 있는 런타임 라이브러리 및 *.deps.json* 파일로 구성됩니다.)

## <a name="attach-the-debugger"></a>디버거 연결

컴퓨터가 구성되면 Linux 컴퓨터에서 애플리케이션을 시작합니다. 그러면 디버거를 연결할 준비가 된 것입니다.

1. Visual Studio에서 **디버그** > **프로세스에 연결...** 을 선택합니다.

1. **연결 형식** 목록에서 **SSH**를 선택합니다.

1. **연결 대상**을 대상 컴퓨터의 IP 주소 또는 호스트 이름으로 변경합니다.

1. 디버그할 프로세스를 찾습니다.

   코드는 고유한 프로세스 이름 또는 dotnet이라는 프로세스에서 실행됩니다. 원하는 프로세스를 찾으려면 프로세스의 명령줄 인수를 보여 주는 **Title** 열을 확인합니다.

   다음 예제에서는 **프로세스에 연결** 대화 상자에 SSH 전송을 사용하는 원격 Linux 컴퓨터의 프로세스 목록이 표시된 것을 볼 수 있습니다.

   ![Linux 프로세스에 연결](media/remote-debug-linux-over-ssh-attach.png)

1. **연결**을 선택합니다.

1. 표시되는 대화 상자에서 디버그하려는 코드의 형식을 선택합니다. **관리형(UNIX용 .NET Core)** 을 선택합니다.

1. Visual Studio 디버깅 기능을 사용하여 앱을 디버그합니다.

   다음 예제에서 Visual Studio 디버거가 원격 Linux 컴퓨터에서 실행되는 코드의 중단점에서 중지된 것을 볼 수 있습니다.

   ![중단점 도달](media/remote-debug-linux-over-ssh-hit-breakpoint.png)