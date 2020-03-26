---
title: 디버거로 실행 중인 프로세스에 연결 | 마이크로 소프트 문서
ms.custom: seodec18
ms.date: 04/08/2019
ms.topic: conceptual
f1_keywords:
- vs.debug.processes.attach
- vs.debug.process
- vs.debug.programs
- vs.debug.detaching
- vs.debug.processes
- vs.debug.error.attach
- vs.debug.remotemachine
dev_langs:
- CSharp
- FSharp
- C++
- VB
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5305be7615e426d7792d8dd3fefb2579e2ab6be
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233017"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Visual Studio 디버거에서 실행 중인 프로세스에 연결
로컬 또는 원격 컴퓨터에서 실행 중인 프로세스에 Visual Studio 디버거를 연결할 수 있습니다. 프로세스가 실행되면**처리에 대한** **디버그** > 첨부를 선택하거나 Visual Studio에서 **Ctrl**+**Alt**+**P를** 누르고 **프로세스에 연결 대화** 상자를 사용하여 디버거를 프로세스에 연결합니다.

**[처리하기]** 을 사용하여 로컬 또는 원격 컴퓨터에서 실행 중인 앱을 디버깅하거나, 여러 프로세스를 동시에 디버깅하거나, Visual Studio에서 만들지 않은 앱을 디버깅하거나, 디버거가 연결된 Visual Studio에서 시작하지 않은 앱을 디버깅할 수 있습니다. 예를 들어 디버거 없이 앱을 실행하고 예외를 누르는 경우 디버거를 앱을 실행하는 프로세스에 연결하고 디버깅을 시작할 수 있습니다.

> [!TIP]
> 디버깅 시나리오에 **대해 프로세스에 첨부를** 사용할지 확실하지 않습니까? [일반적인 디버깅 시나리오를](#BKMK_Scenarios)참조하십시오.

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a>로컬 컴퓨터에서 실행 중인 프로세스에 연결

이전에 연결한 프로세스에 빠르게 다시 연결하려면 [프로세스에 다시 연결합니다.](#BKMK_reattach)

원격 컴퓨터에서 프로세스를 디버깅하려면 [원격 컴퓨터의 프로세스에 대한 첨부 를](#BKMK_Attach_to_a_process_on_a_remote_computer)참조하십시오.

::: moniker range=">= vs-2019"
Linux Docker 컨테이너에서 .NET 코어 프로세스를 디버깅하려면 [Linux Docker 컨테이너에 연결](#BKMK_Linux_Docker_Attach)참조
::: moniker-end

**로컬 컴퓨터의 프로세스에 연결하려면 다음을 수행하십시오.**

1. Visual Studio에서 프로세스에 대한 **디버그** > **첨부(또는** **Ctrl**+**Alt**+**P**를 눌러)를 선택하여 프로세스에 연결 대화 상자를 **엽니다.**

   **연결 유형은** 기본값으로 설정해야 **합니다.** **연결 대상은** 로컬 컴퓨터 이름이어야 합니다.

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

2. 사용 **가능한 프로세스** 목록에서 연결할 프로세스 또는 프로세스를 찾아 선택합니다.

   - 프로세스를 빠르게 선택하려면 **Filter 프로세스** 상자에 해당 이름 또는 첫 번째 문자를 입력합니다.

   - 프로세스 이름을 모르는 경우 목록을 탐색하거나 몇 가지 일반적인 프로세스 이름에 대한 [공통 디버깅 시나리오를](#BKMK_Scenarios) 참조하세요.

   >[!TIP]
   >프로세스에 연결 대화 상자가 열려 있는 동안 백그라운드에서 프로세스를 시작하고 **중지할** 수 있으므로 실행 중인 프로세스 목록이 항상 최신 이아닐 수 있습니다. 언제든지 **새로 고침을** 선택하여 현재 목록을 볼 수 있습니다.

3. **연결** 필드에서 디버깅하려는 코드 유형이 나열되어 있는지 확인합니다. 기본 **자동** 설정은 대부분의 앱 유형에서 작동합니다.

   코드 유형을 수동으로 선택하려면 다음을 수행하십시오.
   1. **선택**을 클릭합니다.
   1. 코드 **유형 선택** 대화 상자에서 **이러한 코드 유형 디버그를**선택합니다.
   1. 디버깅할 코드 유형을 선택합니다.
   1. **확인**을 선택합니다.

4. **연결**을 선택합니다.

>[!NOTE]
>디버깅을 위해 여러 앱에 연결할 수 있지만 한 번에 하나의 앱만 디버거에서 활성화됩니다. Visual Studio **디버그 위치** 도구 모음 또는 **프로세스** 창에서 활성 앱을 설정할 수 있습니다.

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a>원격 컴퓨터의 프로세스에 연결

또한 **프로세스 에 연결** 대화 상자에서 원격 컴퓨터를 선택하고, 해당 컴퓨터에서 실행 중인 사용 가능한 프로세스 목록을 보고, 디버깅을 위해 하나 이상의 프로세스에 연결할 수 있습니다. 원격*디버거(msvsmon.exe)가*원격 컴퓨터에서 실행중이어야 합니다. 자세한 내용은 [원격 디버깅](../debugger/remote-debugging.md)을 참조하십시오.

IIS에 배포된 ASP.NET 응용 프로그램을 디버깅하기 위한 자세한 내용은 [원격 IIS 컴퓨터에서 원격 디버깅 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)참조하세요.

**원격 컴퓨터에서 실행 중인 프로세스에 연결하려면 다음을 수행합니다.**

1. Visual Studio에서 프로세스에 대한 **디버그** > **첨부(또는** **Ctrl**+**Alt**+**P**를 눌러)를 선택하여 프로세스에 연결 대화 상자를 **엽니다.**

2. 대부분의 경우 **연결 유형은** **기본값이어야** 합니다. 연결 **대상** 상자에서 다음 방법 중 하나를 사용하여 원격 컴퓨터를 선택합니다.

   - **연결 대상**옆의 드롭다운 화살표를 선택하고 드롭다운 목록에서 컴퓨터 이름을 선택합니다.
   - **연결 대상** 상자에 컴퓨터 이름을 입력하고 **Enter**를 누릅니다.

     Visual Studio에서 형식에 표시되는 컴퓨터 이름에 필요한 포트를 추가하는지 확인합니다 ** \<>.**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > 원격 컴퓨터 이름을 사용하여 연결할 수 없는 경우 IP 및 포트 주소(예: )를 `123.45.678.9:4022`사용해 보십시오. 4024는 Visual Studio 2019 x64 원격 디버거의 기본 포트입니다. 다른 원격 디버거 포트 할당은 [원격 디버거 포트 할당을](remote-debugger-port-assignments.md)참조하십시오.

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > 원격 컴퓨터 이름을 사용하여 연결할 수 없는 경우 IP 및 포트 주소(예: )를 `123.45.678.9:4022`사용해 보십시오. 4022는 Visual Studio 2017 x64 원격 디버거의 기본 포트입니다. 다른 원격 디버거 포트 할당은 [원격 디버거 포트 할당을](remote-debugger-port-assignments.md)참조하십시오.

     ::: moniker-end

   - **연결 대상** 상자 옆에 있는 **찾기** 단추를 선택하여 **원격 연결** 대화 상자를 엽니다. **원격 연결** 대화 상자에는 로컬 서브넷에 있거나 컴퓨터에 직접 연결된 모든 장치가 나열됩니다. 원격 장치를 검색하려면 서버에서 [UDP 포트 3702를 열어야](../debugger/remote-debugger-port-assignments.md) 할 수 있습니다. 원하는 컴퓨터 또는 장치를 선택한 다음 **선택**을 클릭합니다.

   > [!NOTE]
   > **연결 유형** 설정은 디버깅 세션 간에 유지됩니다. **연결 대상** 설정은 해당 대상과 성공적인 디버깅 연결이 발생한 경우에만 디버깅 세션 간에 유지됩니다.

3. **새로 고침을** 클릭하여 **사용 가능한 프로세스** 목록을 채웁니다.

    >[!TIP]
    >프로세스에 연결 대화 상자가 열려 있는 동안 백그라운드에서 프로세스를 시작하고 **중지할** 수 있으므로 실행 중인 프로세스 목록이 항상 최신 이아닐 수 있습니다. 언제든지 **새로 고침을** 선택하여 현재 목록을 볼 수 있습니다.

4. 사용 **가능한 프로세스** 목록에서 연결할 프로세스 또는 프로세스를 찾아 선택합니다.

   - 프로세스를 빠르게 선택하려면 **Filter 프로세스** 상자에 해당 이름 또는 첫 번째 문자를 입력합니다.

   - 프로세스 이름을 모르는 경우 목록을 탐색하거나 몇 가지 일반적인 프로세스 이름에 대한 [공통 디버깅 시나리오를](#BKMK_Scenarios) 참조하세요.

   - 모든 사용자 계정에서 실행 중인 프로세스를 찾으려면 **모든 사용자에서 프로세스 표시** 확인란을 선택합니다.

     >[!NOTE]
     >신뢰할 수 없는 사용자 계정에서 소유한 프로세스에 연결하면 보안 경고 확인 대화 상자가 나타납니다. 자세한 내용은 [보안 경고: 신뢰할 수 없는 사용자가 소유한 프로세스에 연결하는 것은 위험할 수 있습니다. 다음 정보가 의심스럽거나 확실하지 않은 경우 이 프로세스에 연결하지 마십시오.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)

5. **연결** 필드에서 디버깅하려는 코드 유형이 나열되어 있는지 확인합니다. 기본 **자동** 설정은 대부분의 앱 유형에서 작동합니다.

   코드 유형을 수동으로 선택하려면 다음을 수행하십시오.
   1. **선택**을 클릭합니다.
   1. 코드 **유형 선택** 대화 상자에서 **이러한 코드 유형 디버그를**선택합니다.
   1. 디버깅할 코드 유형을 선택합니다.
   1. **확인**을 선택합니다.

6. **연결**을 선택합니다.

>[!NOTE]
>디버깅을 위해 여러 앱에 연결할 수 있지만 한 번에 하나의 앱만 디버거에서 활성화됩니다. Visual Studio **디버그 위치** 도구 모음 또는 **프로세스** 창에서 활성 앱을 설정할 수 있습니다.

경우에 따라 원격 데스크톱(터미널 서비스) 세션에서 디버깅할 때 **사용 가능한 프로세스** 목록에 사용 가능한 모든 프로세스가 표시되지 않습니다. 제한된 사용자 계정이 있는 사용자로 Visual Studio를 실행하는 경우 **사용 가능한 프로세스** 목록에 세션 0에서 실행 중인 프로세스가 표시되지 않습니다. 세션 0은 *w3wp.exe*를 포함한 서비스 및 기타 서버 프로세스에 사용됩니다. 관리자 계정으로 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 를 실행하거나 터미널 서비스 세션 대신 서버 콘솔에서 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 를 실행하여 이 문제를 해결할 수 있습니다.

이러한 해결 방법을 둘 다 사용할 수 없는 경우 세 번째 방법으로 Windows 명령줄에서 `vsjitdebugger.exe -p <ProcessId>`를 실행하여 프로세스에 연결합니다. *tlist.exe를*사용하여 프로세스 ID를 확인할 수 있습니다. *tlist.exe*를 얻으려면 [WDK 및 WinDbg 다운로드](/windows-hardware/drivers/download-the-wdk)에서 Debugging Tools for Windows를 다운로드하여 설치합니다.

::: moniker range=">= vs-2019"


## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>SSH를 사용하여 Linux에서 실행되는 .NET 코어 프로세스에 연결

자세한 내용은 [SSH를 사용하여 Linux에서 실행되는 원격 디버그 .NET 코어를](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)참조하십시오.

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a>Linux Docker 컨테이너에서 실행 중인 프로세스에 연결

Visual Studio 디버거를 로컬 또는 원격 컴퓨터에서 Linux .NET Core Docker 컨테이너에서 실행 중인 프로세스에 **연결하려면 [처리하기]** 대화 상자를 사용할 수 있습니다.

> [!IMPORTANT]
> 이 기능을 사용하려면 .NET Core 플랫폼 간 개발 워크로드를 설치하고 소스 코드에 로컬로 액세스할 수 있어야 합니다.

**Linux Docker 컨테이너에서 실행 중인 프로세스에 연결하려면 다음을 수행하십시오.**

1. Visual Studio에서 **프로세스에 > 연결(CTRL+ALT+P)을** 선택하여 **프로세스에 연결** 대화 상자를 엽니다.

![프로세스 메뉴에 연결](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. 연결 **유형을** **도커(Linux 컨테이너)로**설정합니다.
3. **찾기를** 선택하여 Docker 컨테이너 **선택** 대화 상자를 통해 **연결 대상을** 설정합니다.

    Docker 컨테이너 프로세스를 로컬 또는 원격으로 디버깅할 수 있습니다.
    
    **Docker 컨테이너 프로세스를 로컬로 디버깅하려면 다음을 수행하십시오.**
    1. **Docker CLI 호스트를** **로컬 컴퓨터로**설정합니다.
    1. 목록에서 연결할 실행 중인 컨테이너를 선택하고 **확인을**누를 수 있습니다.
    
    ![도커 컨테이너 메뉴 선택](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")
 
    **B. Docker 컨테이너 프로세스를 원격으로 디버깅하려면 다음을 수행합니다.**
    
    > [!NOTE] 
    > Docker 컨테이너에서 실행 중인 프로세스에 원격으로 연결하는 데는 두 가지 옵션이 있습니다. SSH를 사용하는 첫 번째 옵션은 로컬 컴퓨터에 Docker 도구가 설치되어 있지 않은 경우에 이상적입니다.  Docker 도구가 로컬에 설치되어 있고 원격 요청을 수락하도록 구성된 Docker 데몬이 있는 경우 Docker 데몬을 사용하여 두 번째 옵션을 시도하십시오.

    1. ***SSH를 통해 원격 컴퓨터에 연결하려면 다음을 수행하십시오.***
        1. 원격 시스템에 연결하려면 **추가를** 선택합니다.<br/>
        ![원격 시스템에 연결](../debugger/media/connect-remote-system.png "원격 시스템에 연결")
        1. SSH 또는 데몬에 성공적으로 연결한 후 연결할 실행 중인 컨테이너를 선택하고 **확인을**누르고 있습니다.

    
    1. ***[Docker 데몬을](https://docs.docker.com/engine/reference/commandline/dockerd/) 통해 프로세스를 실행하는 원격 컨테이너로 대상을 설정하려면***
        1. **Docker 호스트(선택 사항)에서** 데몬 주소(예: TCP, IP 등을 통해)를 지정하고 새로 고침 링크를 클릭합니다.
        1. 데몬에 성공적으로 연결한 후 연결할 실행 중인 컨테이너를 선택하고 **확인을**누르고 있습니다.

4. **사용 가능한 프로세스** 목록에서 해당 컨테이너 프로세스를 선택하고 **첨부를** 선택하여 Visual Studio에서 C# 컨테이너 프로세스디버깅을 시작합니다.

    ![완료된 도커 연결 메뉴](../debugger/media/docker-attach-complete.png "완료 리눅스 도커 연결 메뉴")
    

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a><a name="BKMK_Windows_Docker_Attach"></a>Windows Docker 컨테이너에서 실행 중인 프로세스에 연결

Visual Studio 디버거를 처리하기 첨부 대화 상자를 사용하여 로컬 컴퓨터의 Windows Docker 컨테이너에서 실행 중인 **프로세스에** 연결할 수 있습니다.

> [!IMPORTANT]
> .NET Core 프로세스에서 이 기능을 사용하려면 .NET Core 플랫폼 간 개발 워크로드를 설치하고 소스 코드에 대한 로컬 액세스 권한을 가져야 합니다.

**Windows Docker 컨테이너에서 실행 중인 프로세스에 연결하려면 다음을 수행합니다.**

1. Visual Studio에서 **프로세스에 연결>** 또는 **CTRL+ALT+P)를**선택하여 **프로세스에 연결** 대화 상자를 엽니다.

   ![프로세스 메뉴에 연결](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. 연결 **유형을** **도커(Windows 컨테이너)로**설정합니다.
3. **찾기를** 선택하여 Docker 컨테이너 **선택** 대화 상자를 사용하여 **연결 대상을** 설정합니다.

    > [!IMPORTANT]
    > 대상 프로세스에는 실행 중인 Docker Windows 컨테이너와 동일한 프로세서 아키텍처가 있어야 합니다.
    
   SSH를 통해 원격 컨테이너에 대상을 설정하는 것은 현재 사용할 수 없으며 Docker 데몬을 통해서만 수행할 수 있습니다.
    
    ***[Docker 데몬을](https://docs.docker.com/engine/reference/commandline/dockerd/) 통해 프로세스를 실행하는 원격 컨테이너로 대상을 설정하려면***
    1. **Docker 호스트(선택 사항)에서** 데몬 주소(예: TCP, IP 등을 통해)를 지정하고 새로 고침 링크를 클릭합니다. 

    1. 데몬에 성공적으로 연결한 후 연결할 실행 중인 컨테이너를 선택하고 확인을 선택합니다.
    
4. **사용 가능한 프로세스** 목록에서 해당 컨테이너 프로세스를 선택하고 **연결하여** C# 컨테이너 프로세스 디버깅을 시작합니다.

    ![완료된 도커 연결 메뉴](../debugger/media/docker-attach-complete-windows.png "완료 된 창 도커 연결 메뉴")
    

5.  사용 가능한 프로세스 목록에서 해당 컨테이너 프로세스를 선택하고 **연결하여** C# 컨테이너 프로세스 디버깅을 시작합니다.


::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a>프로세스에 다시 연결

**프로세스에 다시 연결** **디버그(Shift** > **Shift**+**Alt**+**P)를**선택하여 이전에 연결했던 프로세스에 빠르게 다시 연결할 수 있습니다. 이 명령을 선택하면 디버거는 먼저 이전 프로세스 ID와 일치시키려고 시도하고 실패한 경우 이전 프로세스 이름과 일치시켜 연결한 마지막 프로세스에 즉시 연결하려고 시도합니다. 일치하는 항목이 없거나 여러 프로세스의 이름이 같은 경우 올바른 프로세스를 선택할 수 있도록 **프로세스에 연결** 대화 상자가 열립니다.

> [!NOTE]
> **프로세스에 다시 연결** 명령은 Visual Studio 2017에서 시작할 수 있습니다.

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a>일반적인 디버깅 시나리오

**프로세스에 연결** 및 연결할 프로세스를 사용할지 여부를 결정하는 데 도움이 되는 다음 표에서는 사용 가능한 경우 더 많은 지침에 대한 링크와 함께 몇 가지 일반적인 디버깅 시나리오를 보여 줍니다. (목록이 완전하지 않습니다.)

유니버설 Windows 앱(UWP) 앱과 같은 일부 앱 유형의 경우 프로세스 이름에 직접 연결하지 않고 Visual Studio에서 **디버그 설치 앱 패키지** 메뉴 옵션을 대신 사용합니다(표 참조).

디버거에서 C++로 작성된 코드에 연결하려면 코드에 `DebuggableAttribute`가 있어야 합니다. 이 특성은 [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) 링커 옵션으로 링크하여 자동으로 코드에 추가할 수 있습니다.

클라이언트 쪽 스크립트 디버깅의 경우 브라우저에서 스크립트 디버깅을 사용하도록 설정해야 합니다. Chrome에서 클라이언트 쪽 스크립트를 디버깅하려면 **웹 키트를** 코드 유형으로 선택하고 앱 유형에 따라 모든 Chrome 인스턴스를 닫고 디버깅 모드에서 브라우저를 시작해야 할 수 있습니다(명령줄에서 입력). `chrome.exe --remote-debugging-port=9222`

Visual Studio에서 연결할 실행 중인 프로세스를 빠르게 선택하려면 **Ctrl**+**Alt**+**P를**입력한 다음 프로세스 이름의 첫 번째 문자를 입력합니다.

|시나리오|디버그 방법|프로세스 이름|메모 및 링크|
|-|-|-|-|
|IIS 서버에서 원격 디버그 ASP.NET 4 또는 4.5|원격 도구 사용 및 **프로세스에 연결**|*w3wp.exe*|[원격 IIS 컴퓨터에서 원격 디버깅 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) 보기|
|IIS 서버의 코어ASP.NET 원격 디버그|원격 도구 사용 및 **프로세스에 연결**|*dotnet.exe* 또는 *앱네임.exe*|앱 배포의 경우 [IIS에 게시를](https://docs.asp.net/en/latest/publishing/iis.html)참조하십시오. 디버깅에 대 한 [참조 원격 IIS 컴퓨터에서 코어에 ASP.NET 원격 디버깅](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|지원되는 앱 유형에 대해 로컬 IIS 서버에서 클라이언트 측 스크립트 디버그 |**프로세스에 연결 사용**|*크롬.exe,* *마이크로 소프트 에지CP.exe,* 또는 *iexplore.exe*|스크립트 디버깅을 사용하도록 설정해야 합니다. Chrome의 경우 디버그 모드에서 Chrome을 실행하고 **연결** 필드에서 **웹킷 코드를** 선택해야 합니다.|
|로컬 컴퓨터에서 C#, 시각적 기본 또는 C++ 앱 디버깅|표준**디버깅(F5)** 또는 **프로세스에 연결**|*\<앱 네임>.exe*|대부분의 시나리오에서 표준 디버깅을 사용하고 **프로세스에 연결하지**않습니다.|
|Windows 데스크톱 앱원격 디버그|원격 도구|해당 없음| [C# 또는 비주얼 베이직 앱](../debugger/remote-debugging-csharp.md) 원격 디버그 를 참조하거나 [C++ 앱 원격 디버깅](../debugger/remote-debugging-cpp.md)|
|리눅스에서 디버그 .NET 코어|**프로세스에 연결 사용**|*dotnet.exe*|SSH를 사용하려면 [SSH를 사용하여 Linux에서 실행되는 원격 디버그 .NET 코어를](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)참조하십시오. |
|디버거 없이 앱을 시작한 후 로컬 컴퓨터에서 ASP.NET 앱 디버그|**프로세스에 연결 사용**|*iiexpress.exe*|프로파일링 할 때와 같이 앱 로드 속도를 더 빠르게 만드는 데 유용할 수 있습니다. |
|서버 프로세스에서 지원되는 다른 앱 유형 디버깅|서버가 원격인 경우 원격 도구를 사용하고 **프로세스에 연결합니다.**|*chrome.exe,* *iexplore.exe,* 또는 기타 프로세스|필요한 경우 리소스 모니터를 사용하여 프로세스를 식별할 수 있습니다. [원격 디버깅](../debugger/remote-debugging.md)을 참조하십시오.|
|원격 디버깅 유니버설 윈도우 앱 (UWP), 원 코어, 홀로 렌즈, 또는 IoT 응용 프로그램|설치된 앱 패키지 디버그|해당 없음|프로세스에 연결 사용 하는 대신 [설치 된 응용 프로그램 패키지 디버그](debug-installed-app-package.md) 를 참조 **하십시오.**|
|비주얼 스튜디오에서 시작하지 않은 유니버설 윈도우 앱(UWP), OneCore, 홀로렌즈 또는 IoT 앱 디버깅|설치된 앱 패키지 디버그|해당 없음|프로세스에 연결 사용 하는 대신 [설치 된 응용 프로그램 패키지 디버그](debug-installed-app-package.md) 를 참조 **하십시오.**|

## <a name="use-debugger-features"></a>디버거 기능 사용

프로세스에 연결할 때 Visual Studio 디버거의 전체 기능을 사용하려면 앱이 로컬 소스 및 기호와 정확히 일치해야 합니다. 즉, 디버거는 올바른 [기호(.pdb) 파일을](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)로드할 수 있어야 합니다. 기본적으로 디버그 빌드가 필요합니다.

원격 디버깅 시나리오의 경우 Visual Studio에서 소스 코드(또는 소스 코드의 복사본)가 이미 열려 있어야 합니다. 원격 컴퓨터에서 컴파일된 앱 바이너리는 로컬 컴퓨터와 동일한 빌드에서 제공되어야 합니다.

일부 로컬 디버깅 시나리오에서는 올바른 심볼 파일이 앱에 있는 경우 소스에 액세스할 수 없는 Visual Studio에서 디버깅할 수 있습니다. 기본적으로 디버그 빌드가 필요합니다. 자세한 내용은 [기호 및 소스 파일 지정을](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)참조하십시오.

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> 연결 오류 문제 해결
 실행 중인 프로세스에 디버거를 연결할 때 이 프로세스에는 한 가지 이상의 코드 형식이 포함될 수 있습니다. 디버거가 연결될 수 있는 코드 형식이 **코드 형식 선택** 대화 상자에서 표시되고 선택됩니다.

 때로는 디버거가 한 코드 형식에는 연결되고 다른 코드 형식에는 연결되지 않을 수도 있습니다. 이러한 문제는 원격 컴퓨터에서 실행 중인 프로세스에 연결하려 할 때 발생할 수 있습니다. 원격 컴퓨터에 설치된 원격 디버깅 구성 요소가 일부 코드 형식만 지원하고 다른 코드 형식은 지원하지 않을 수도 있습니다. 데이터베이스를 직접 디버깅하기 위해 두 개 이상의 프로세스에 연결하려는 경우에도 이 문제가 발생할 수 있습니다. SQL 디버깅은 단일 프로세스에 대한 연결만 지원합니다.

 디버거가 전부는 아니지만 일부 코드 유형에 연결할 수 있는 경우 연결하지 못한 형식을 식별하는 메시지가 표시됩니다.

 적어도 하나의 코드 형식에 디버거가 성공적으로 연결되면 프로세스 디버깅을 진행할 수 있습니다. 이 경우 성공적으로 연결된 코드 형식만 디버깅할 수 있습니다. 프로세스에서 연결되지 않은 코드는 계속 실행되지만 중단점을 설정하거나 데이터를 보거나 해당 코드에서 다른 디버깅 작업을 수행할 수는 없습니다.

 디버거가 코드 형식에 연결하지 못한 이유에 대한 자세한 정보를 원하는 경우 해당 코드 형식에만 다시 연결해 보십시오.

 **코드 형식에 연결하지 못한 이유에 대한 자세한 정보를 얻으려면:**

1. 프로세스에서 분리합니다. **디버그** 메뉴에서 **모두 분리를**선택합니다.

1. 프로세스에 다시 연결하여 연결하지 못한 코드 유형만 선택합니다.

    1. **프로세스에 연결** 대화 상자의 **사용 가능한 프로세스** 목록에서 프로세스를 선택합니다.

    2. **선택**을 선택합니다.

    3. **코드 형식 선택** 대화 상자에서 **다음 코드 형식 디버깅** 을 선택하고 연결에 실패한 코드 형식을 선택합니다. 다른 코드 형식의 선택을 취소합니다.

    4. **확인**을 선택합니다.

    5. **프로세스에 연결** 대화 상자에서 **연결**을 선택합니다.

    이렇게 하면 연결이 완전히 실패하고 자세한 오류 메시지가 나타납니다.

## <a name="see-also"></a>참조

- [여러 프로세스 디버그](../debugger/debug-multiple-processes.md)
- [Just-In-Time 디버깅](../debugger/just-in-time-debugging-in-visual-studio.md)
- [원격 디버깅](../debugger/remote-debugging.md)
