---
title: 디버거에서 실행 중인 프로세스에 연결 | Microsoft Docs
ms.custom: seodec18
ms.date: 06/12/2020
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
ms.openlocfilehash: 5970e7e4408c826058cb27590254b278d4cdb9b7
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281008"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Visual Studio 디버거에서 실행 중인 프로세스에 연결

로컬 또는 원격 컴퓨터에서 실행 중인 프로세스에 Visual Studio 디버거를 연결할 수 있습니다. 프로세스가 실행된 후 **디버그** > **프로세스에 연결**을 선택하거나 Visual Studio에서 **Ctrl**+**Alt**+**P**를 누르고, **프로세스에 연결** 대화 상자를 사용하여 프로세스에 디버거를 연결합니다.

**프로세스에 연결**을 사용하여 로컬 또는 원격 컴퓨터에서 실행 중인 앱을 디버그하거나, 여러 프로세스를 동시에 디버그하거나, Visual Studio에서 생성되지 않은 앱을 디버그하거나, 디버거가 연결된 Visual Studio에서 시작하지 않은 앱을 디버그할 수 있습니다. 예를 들어 디버거를 사용하지 않고 앱을 실행해 예외가 발생하는 경우 앱을 실행하는 프로세스에 디버거를 연결하고 디버깅을 시작할 수 있습니다.

> [!TIP]
> 디버깅 시나리오에 **프로세스에 연결**을 사용하고 있는지 확실하지 않은 경우 [일반적인 디버깅 시나리오](#BKMK_Scenarios)를 참조하세요.

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> 로컬 컴퓨터에서 실행 중인 프로세스에 연결

이전에 연결한 프로세스에 빠르게 다시 연결하려면 [프로세스에 다시 연결](#BKMK_reattach)을 참조하세요.

**로컬 컴퓨터의 프로세스에 연결하려면**

1. Visual Studio에서 **디버그** > **프로세스에 연결**(또는 **Ctrl**+**Alt**+**P**)을 선택하여 **프로세스에 연결** 대화 상자를 엽니다.

1. **연결 형식**을 확인합니다.

   대부분의 시나리오에서는 **기본값**을 사용할 수 있습니다. 일부 시나리오에는 다른 연결 형식이 필요할 수 있습니다. 자세한 내용은 이 문서의 다른 섹션 또는 [일반적인 디버깅 시나리오](#BKMK_Scenarios)를 참조하세요.

1. **연결 대상**을 로컬 컴퓨터 이름으로 설정합니다.

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

1. **사용 가능한 프로세스** 목록에서 연결하려는 프로세스를 찾아 선택합니다.

   - 프로세스를 신속하게 선택하려면 **프로세스 필터링** 상자에 해당 이름 또는 첫 글자를 입력합니다.

   - 프로세스 이름을 모르는 경우 목록을 탐색하거나 일반적인 프로세스 이름에 대한 [일반적인 디버깅 시나리오](#BKMK_Scenarios)를 참조하세요.

   >[!TIP]
   >**프로세스에 연결** 대화 상자가 열려 있는 동안 배경에서 프로세스를 시작 및 중지할 수 있으므로 실행 중인 프로세스의 목록이 항상 최신 상태인 것은 아닙니다. 언제든지 **새로 고침**을 선택하여 현재 목록을 볼 수 있습니다.

1. **연결 대상** 필드에서 디버그할 코드 형식이 표시되어 있는지 확인합니다. 기본 **자동** 설정은 대부분의 앱 유형에서 작동합니다.

   **기본값** 연결 형식을 사용하는 경우 연결하려는 코드 형식을 수동으로 선택할 수 있습니다. 그렇지 않으면 **선택** 옵션이 해제될 수 있습니다.

   수동으로 코드 형식을 선택하려면
   1. **선택**을 클릭합니다.
   1. **코드 형식 선택** 대화 상자의 **다음 코드 형식 디버그**를 선택합니다.
      목록의 프로세스에 연결하려고 할 때 오류가 발생하는 경우 [코드 형식 선택](../debugger/select-code-type-dialog-box.md) 대화 상자를 사용하여 [문제를 해결](#BKMK_Troubleshoot_attach_errors)할 수 있습니다.
   1. 디버그할 코드 형식을 선택합니다.
   1. **확인**을 선택합니다.

1. **연결**을 선택합니다.

>[!NOTE]
>디버깅을 위해 여러 앱에 연결할 수 있지만 한 번에 하나의 앱만 디버거에서 활성화됩니다. Visual Studio **디버그 위치** 도구 모음 또는 **프로세스** 창에서 활성 앱을 설정할 수 있습니다.

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> 원격 컴퓨터의 프로세스에 연결

또한 **프로세스에 연결** 대화 상자에서 원격 컴퓨터를 선택하고 해당 컴퓨터에서 실행되는 사용 가능한 프로세스 목록을 확인하여 디버깅을 위해 하나 이상의 프로세스에 연결할 수 있습니다. 원격 디버거(*msvsmon.exe*)가 원격 컴퓨터에서 실행되고 있어야 합니다. 자세한 내용은 [원격 디버깅](../debugger/remote-debugging.md)을 참조하세요.

IIS에 배포된 ASP.NET 애플리케이션을 디버그하는 방법에 대한 자세한 지침은 [원격 IIS 컴퓨터의 ASP.NET 원격 디버그](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)를 참조하세요.

**원격 컴퓨터에서 실행 중인 프로세스에 연결하려면**

1. Visual Studio에서 **디버그** > **프로세스에 연결**(또는 **Ctrl**+**Alt**+**P**)을 선택하여 **프로세스에 연결** 대화 상자를 엽니다.

1. **연결 형식**을 확인합니다.

   대부분의 시나리오에서는 **기본값**을 사용할 수 있습니다. Linux 또는 컨테이너화된 앱 디버깅과 같은 일부 시나리오에는 다른 연결 형식이 필요합니다. 자세한 내용은 이 문서의 다른 섹션 또는 [일반적인 디버깅 시나리오](#BKMK_Scenarios)를 참조하세요.

1. **연결 대상** 상자에서 다음 방법 중 하나를 사용하여 원격 컴퓨터를 선택합니다.

   - **연결 대상**옆에 있는 드롭다운 화살표를 선택하고 드롭다운 목록에서 컴퓨터 이름을 선택합니다.
   - **연결 대상** 상자에 컴퓨터 이름을 입력하고 **Enter 키**를 누릅니다.

     Visual Studio에서 **\<remote computer name>:포트** 형식으로 표시되는 컴퓨터 이름에 필요한 포트를 추가하는지 확인합니다.

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > 원격 컴퓨터 이름을 사용하여 연결할 수 없는 경우 IP 및 포트 주소를 사용해 보세요(예: `123.45.678.9:4022`). 4024는 Visual Studio 2019 x64 원격 디버거의 기본 포트입니다. 다른 원격 디버거 포트 할당은 [원격 디버거 포트 할당](remote-debugger-port-assignments.md)을 참조하세요.

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > 원격 컴퓨터 이름을 사용하여 연결할 수 없는 경우 IP 및 포트 주소를 사용해 보세요(예: `123.45.678.9:4022`). 4022는 Visual Studio 2017 x64 원격 디버거의 기본 포트입니다. 다른 원격 디버거 포트 할당은 [원격 디버거 포트 할당](remote-debugger-port-assignments.md)을 참조하세요.

     ::: moniker-end

   - **연결 대상** 상자 옆에 있는 **찾기** 단추를 선택하여 **원격 연결** 대화 상자를 엽니다. **원격 연결** 대화 상자에는 로컬 서브넷에 있거나 컴퓨터에 직접 연결된 모든 디바이스가 나열되어 있습니다. 원격 디바이스를 검색하려면 서버에서 [UDP 포트 3702를 열어야](../debugger/remote-debugger-port-assignments.md) 할 수 있습니다. 원하는 컴퓨터 또는 디바이스를 선택한 다음 **선택**을 클릭합니다.

   > [!NOTE]
   > **연결 형식** 설정은 디버깅 세션 간에 유지됩니다. **연결 대상** 설정은 해당 대상을 사용하여 디버깅 연결에 성공한 경우에만 디버깅 세션 간에 유지됩니다.

3. **새로 고침**을 클릭하여 **사용 가능한 프로세스** 목록을 채웁니다.

    >[!TIP]
    >**프로세스에 연결** 대화 상자가 열려 있는 동안 배경에서 프로세스를 시작 및 중지할 수 있으므로 실행 중인 프로세스의 목록이 항상 최신 상태인 것은 아닙니다. 언제든지 **새로 고침**을 선택하여 현재 목록을 볼 수 있습니다.

4. **사용 가능한 프로세스** 목록에서 연결하려는 프로세스를 찾아 선택합니다.

   - 프로세스를 신속하게 선택하려면 **프로세스 필터링** 상자에 해당 이름 또는 첫 글자를 입력합니다.

   - 프로세스 이름을 모르는 경우 목록을 탐색하거나 일반적인 프로세스 이름에 대한 [일반적인 디버깅 시나리오](#BKMK_Scenarios)를 참조하세요.

   - 모든 사용자 계정으로 실행되는 프로세스를 찾으려면 **모든 사용자의 프로세스 표시** 확인란을 선택합니다.

     >[!NOTE]
     >신뢰할 수 없는 사용자 계정에서 소유한 프로세스에 연결하면 보안 경고 확인 대화 상자가 나타납니다. 자세한 내용은 다음을 참조하세요. [보안 경고: 신뢰할 수 없는 사용자가 소유한 프로세스에 연결하면 위험할 수 있습니다. 다음 정보가 의심스럽거나 확실하지 않은 경우 이 프로세스에 연결하지 마십시오](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).

5. **연결 대상** 필드에서 디버그할 코드 형식이 표시되어 있는지 확인합니다. 기본 **자동** 설정은 대부분의 앱 유형에서 작동합니다.

   **기본값** 연결 형식을 사용하는 경우 연결하려는 코드 형식을 수동으로 선택할 수 있습니다. 그렇지 않으면 **선택** 옵션이 해제될 수 있습니다.

   수동으로 코드 형식을 선택하려면
   1. **선택**을 클릭합니다.
   1. **코드 형식 선택** 대화 상자의 **다음 코드 형식 디버그**를 선택합니다.
      목록의 프로세스에 연결하려고 할 때 오류가 발생하는 경우 [코드 형식 선택](../debugger/select-code-type-dialog-box.md) 대화 상자를 사용하여 [문제를 해결](#BKMK_Troubleshoot_attach_errors)할 수 있습니다.
   1. **확인**을 선택합니다.

6. **연결**을 선택합니다.

>[!NOTE]
>디버깅을 위해 여러 앱에 연결할 수 있지만 한 번에 하나의 앱만 디버거에서 활성화됩니다. Visual Studio **디버그 위치** 도구 모음 또는 **프로세스** 창에서 활성 앱을 설정할 수 있습니다.

원격 데스크톱(터미널 서비스) 세션에서 디버그할 때 **사용 가능한 프로세스** 목록에 사용 가능한 프로세스 중 일부가 표시되지 않는 경우가 있습니다. 제한된 사용자 계정으로 Visual Studio를 실행하는 경우 세션 0에서 실행 중인 프로세스는 **사용 가능한 프로세스** 목록에 표시되지 않습니다. 세션 0은 *w3wp.exe*를 비롯한 서비스 및 기타 서버 프로세스에 사용됩니다. 관리자 계정으로 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 를 실행하거나 터미널 서비스 세션 대신 서버 콘솔에서 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 를 실행하여 이 문제를 해결할 수 있습니다.

이러한 해결 방법을 둘 다 사용할 수 없는 경우 세 번째 방법으로 Windows 명령줄에서 `vsjitdebugger.exe -p <ProcessId>`를 실행하여 프로세스에 연결합니다. 프로세스 ID는 *tlist.exe*를 사용하여 확인할 수 있습니다. *tlist.exe*를 얻으려면 [WDK 및 WinDbg 다운로드](/windows-hardware/drivers/download-the-wdk)에서 Debugging Tools for Windows를 다운로드하여 설치합니다.

::: moniker range=">= vs-2019"

## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>SSH를 사용하여 Linux에서 실행되는 .NET Core 프로세스에 연결

자세한 내용은 [SSH를 사용하여 Linux에서 실행되는 .NET Core 원격 디버그](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)를 참조하세요.

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a> Linux Docker 컨테이너에서 실행되는 프로세스에 연결

**프로세스에 연결** 대화 상자를 사용하여 로컬 또는 원격 컴퓨터의 Linux .NET Core Docker 컨테이너에서 실행되는 프로세스에 Visual Studio 디버거를 연결할 수 있습니다.

> [!IMPORTANT]
> 이 기능을 사용하려면 .NET Core 플랫폼 간 개발 워크로드를 설치하고 소스 코드에 대한 로컬 액세스 권한이 있어야 합니다.

**Linux Docker 컨테이너에서 실행 중인 프로세스에 연결하려면**

1. Visual Studio에서 **디버그 > 프로세스에 연결(CTRL+ALT+P)** 을 선택하여 **프로세스에 연결** 대화 상자를 엽니다.

![프로세스에 연결 메뉴](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. **연결 형식**을 **Docker(Linux 컨테이너)** 로 설정합니다.
3. **찾기...** 를 선택하여 **Docker 컨테이너 선택** 대화 상자를 통해 **연결 대상**을 설정합니다.

    Docker 컨테이너 프로세스는 로컬 또는 원격으로 디버그할 수 있습니다.
    
    **Docker 컨테이너 프로세스를 로컬로 디버그하려면**
    1. **Docker CLI 호스트**를 **로컬 컴퓨터**로 설정합니다.
    1. 목록에서 연결할 실행 중인 컨테이너를 선택하고 **확인**을 누릅니다.
    
    ![Docker 컨테이너 메뉴 선택](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")
 
    **B. Docker 컨테이너 프로세스를 원격으로 디버그하려면**
    
    > [!NOTE] 
    > Docker 컨테이너에서 실행 중인 프로세스에 원격으로 연결하는 옵션에는 두 가지가 있습니다. SSH를 사용하는 첫 번째 옵션은 로컬 컴퓨터에 Docker 도구를 설치하지 않은 경우에 적합합니다.  Docker 도구를 로컬로 설치했고 원격 요청을 허용하도록 구성된 Docker 디먼이 있는 경우 Docker 디먼을 사용하는 두 번째 옵션을 이용해 보세요.

    1. ***SSH를 통해 원격 컴퓨터에 연결하려면***
        1. **추가...** 를 선택하여 원격 시스템에 연결합니다.<br/>
        ![원격 시스템에 연결](../debugger/media/connect-remote-system.png "원격 시스템에 연결")
        1. SSH 또는 디먼에 성공적으로 연결되면 연결하려는 실행 중 컨테이너를 선택하고 **확인**을 누릅니다.

    
    1. ***[Docker 디먼](https://docs.docker.com/engine/reference/commandline/dockerd/)을 통해 프로세스를 실행하는 원격 컨테이너를 대상으로 설정하려면***
        1. **Docker 호스트(선택 사항)** 에서 디먼 주소(예: TCP, IP 등)를 지정하고 새로 고침 링크를 클릭합니다.
        1. 디먼에 성공적으로 연결되면 연결하려는 실행 중 컨테이너를 선택하고 **확인**을 누릅니다.

4. **사용 가능한 프로세스** 목록에서 해당 컨테이너 프로세스를 선택하고 **연결**을 선택하여 Visual Studio에서 C# 컨테이너 프로세스 디버깅을 시작합니다.

    ![완료된 Docker 연결 메뉴](../debugger/media/docker-attach-complete.png "완료된 Linux Docker 연결 메뉴")
    

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a><a name="BKMK_Windows_Docker_Attach"></a> Windows Docker 컨테이너에서 실행되는 프로세스에 연결

**프로세스에 연결** 대화 상자를 사용하여 로컬 컴퓨터의 Windows Docker 컨테이너에서 실행되는 프로세스에 Visual Studio 디버거를 연결할 수 있습니다.

> [!IMPORTANT]
> .NET Core 프로세스에 이 기능을 사용하려면 .NET Core 플랫폼 간 개발 워크로드를 설치하고 소스 코드에 대한 로컬 액세스 권한이 있어야 합니다.

**Linux Docker 컨테이너에서 실행 중인 프로세스에 연결하려면**

1. Visual Studio에서 **디버그 > 프로세스에 연결**(또는 **CTRL+ALT+P**)을 선택하여 **프로세스에 연결** 대화 상자를 엽니다.

   ![프로세스에 연결 메뉴](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. **연결 형식**을 **Docker(Windows 컨테이너)** 로 설정합니다.
3. **찾기...** 를 선택하여 **Docker 컨테이너 선택** 대화 상자를 통해 **연결 대상**을 설정합니다.

    > [!IMPORTANT]
    > 대상 프로세스는 실행 중인 Docker Windows 컨테이너와 프로세서 아키텍처가 동일해야 합니다.
    
   현재는 SSH를 통해 원격 컨테이너를 대상으로 설정할 수 없고 Docker 디먼을 사용해야만 합니다.
    
    ***[Docker 디먼](https://docs.docker.com/engine/reference/commandline/dockerd/)을 통해 프로세스를 실행하는 원격 컨테이너를 대상으로 설정하려면***
    1. **Docker 호스트(선택 사항)** 에서 디먼 주소(예: TCP, IP 등)를 지정하고 새로 고침 링크를 클릭합니다. 

    1. 디먼에 성공적으로 연결되면 연결하려는 실행 중 컨테이너를 선택하고 확인을 선택합니다.
    
4. **사용 가능한 프로세스** 목록에서 해당 컨테이너 프로세스를 선택하고 **연결**을 선택하여 C# 컨테이너 프로세스 디버깅을 시작합니다.

    ![완료된 Docker 연결 메뉴](../debugger/media/docker-attach-complete-windows.png "완료된 Windows Docker 연결 메뉴")
    

5.  사용 가능한 프로세스 목록에서 해당 컨테이너 프로세스를 선택하고 **연결**을 선택하여 C# 컨테이너 프로세스 디버깅을 시작합니다.


::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a> 프로세스에 다시 연결

**디버그** > **프로세스에 다시 연결**(**Shift**+**Alt**+**P**)를 선택하여 이전에 연결한 프로세스에 신속하게 다시 연결할 수 있습니다. 이 명령을 선택하는 경우 디버거는 즉시 먼저 이전 프로세스 ID와 일치하는 항목을 검색하고 이것이 실패하면 이전 프로세스 이름과 일치하는 항목을 검색하여 사용자가 연결한 마지막 프로세스에 연결을 시도합니다. 일치하는 항목이 없거나 여러 프로세스가 동일한 이름인 경우 사용자가 올바른 프로세스를 선택할 수 있도록 **프로세스에 연결** 대화 상자가 열립니다.

> [!NOTE]
> **프로세스에 다시 연결** 명령은 Visual Studio 2017부터 사용할 수 있습니다.

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a> 일반적인 디버깅 시나리오

**프로세스에 연결** 사용 여부와 어느 프로세스를 연결할지 결정하는 데 도움이 되도록 다음 표에서는 몇 가지 일반적인 디버깅 시나리오를 추가 지침 링크(사용 가능한 경우)와 함께 제시합니다. (이 목록은 전체 목록이 아닙니다.)

UWP(유니버설 Windows 플랫폼) 앱과 같은 일부 앱 유형에서는 프로세스 이름에 직접 연결하는 대신 Visual Studio의 **설치된 앱 패키지 디버그** 메뉴 옵션을 사용합니다(표 참조).

디버거에서 C++로 작성된 코드에 연결하려면 코드에 `DebuggableAttribute`가 있어야 합니다. 이 특성은 [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) 링커 옵션으로 링크하여 자동으로 코드에 추가할 수 있습니다.

클라이언트 쪽 스크립트 디버깅의 경우 브라우저에서 스크립트 디버깅을 사용하도록 설정해야 합니다. Chrome에서 클라이언트 쪽 스크립트를 디버그하려면 **JavaScript(Chrome)** 또는 **JavaScript(Microsoft Edge - Chromium)** 를 코드 형식으로 선택합니다. 그러면 앱 유형에 따라 모든 Chrome 인스턴스를 닫고 디버깅 모드에서 브라우저를 시작해야 할 수 있습니다(명령줄에 `chrome.exe --remote-debugging-port=9222` 입력). 이전 버전의 Visual Studio에서는 Chrome용 스크립트 디버거가 **웹 키트**였습니다.

연결하려는 실행 중 프로세스를 신속하게 선택하려면 Visual Studio에서 **Ctrl**+**Alt**+**P**를 입력한 다음 프로세스 이름의 첫 글자를 입력합니다.

|시나리오|디버그 방법|프로세스 이름|참고 사항 및 링크|
|-|-|-|-|
|IIS 서버의 ASP.NET 4 또는 4.5 원격 디버그|원격 도구 및 **프로세스에 연결** 사용|*w3wp.exe*|[원격 IIS 컴퓨터의 ASP.NET 원격 디버그](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)를 참조하세요.|
|IIS 서버의 ASP.NET Core 원격 디버그|원격 도구 및 **프로세스에 연결** 사용|*w3wp.exe* 또는 *dotnet.exe*|.NET Core 3부터 *w3wp.exe* 프로세스가 기본 [앱 내 호스팅 모델](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1#hosting-models)에 사용됩니다. 앱 배포의 경우 [IIS에 게시](/aspnet/core/host-and-deploy/iis/)를 참조하세요. 자세한 내용은 [원격 IIS 컴퓨터의 ASP.NET Core 원격 디버그](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md#BKMK_attach)를 참조하세요.|
|지원되는 앱 형식에 대해 로컬 IIS 서버의 클라이언트 쪽 스크립트 디버그 |**프로세스에 연결** 사용|*chrome.exe*, *MicrosoftEdgeCP.exe* 또는 *iexplore.exe*|스크립트 디버깅을 사용하도록 설정해야 합니다. Chrome의 경우 디버그 모드에서 Chrome을 실행하고(명령줄에 `chrome.exe --remote-debugging-port=9222` 입력) **연결 대상** 필드에서 **JavaScript(Chrome)** 를 선택합니다.|
|로컬 컴퓨터에서 C#, Visual Basic 또는 C++ 앱을 디버그|표준 디버깅(**F5**) 또는 **프로세스에 연결** 을 사용|*\<appname>.exe*|대부분의 시나리오에서는 **프로세스에 연결**이 아니라 표준 디버깅을 사용합니다.|
|Windows 데스크톱 앱 원격 디버그|원격 도구|N/A| [C# 또는 Visual Basic 앱 원격 디버그](../debugger/remote-debugging-csharp.md) 또는 [C++ 앱 원격 디버그](../debugger/remote-debugging-cpp.md)을 참조하세요.|
|Linux에서 .NET Core 원격 디버그|**프로세스에 연결** 사용|*dotnet.exe*|SSH를 사용하려면 [SSH를 사용하여 Linux에서 실행되는 .NET Core 원격 디버그](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)를 참조하세요. 컨테이너화된 앱의 경우 이 문서의 이전 섹션을 참조하세요.|
|Linux에서 Python 원격 디버그|**프로세스에 연결** 사용|*debugpy*|[Python 도구에서 원격으로 연결](../python/debugging-python-code-on-remote-linux-machines.md#attach-remotely-from-python-tools)을 참조하세요.|
|디버거를 사용하지 않고 앱을 시작한 후 로컬 컴퓨터에서 ASP.NET 앱 디버깅|**프로세스에 연결** 사용|*iiexpress.exe*|이렇게 하면 프로파일링과 같은 경우에 앱을 더 빠르게 로드하는 데 도움이 될 수 있습니다. |
|서버 프로세스에서 다른 지원되는 다른 앱 유형 디버깅|서버가 원격인 경우 원격 도구 및 **프로세스에 연결** 사용|*chrome.exe*, *iexplore.exe* 또는 기타 프로세스|필요한 경우 리소스 모니터를 사용하여 프로세스를 식별합니다. [원격 디버깅](../debugger/remote-debugging.md)을 참조하세요.|
|UWP(유니버설 Windows 플랫폼) 앱, OneCore, HoloLens 또는 IoT 앱 원격 디버그|설치된 앱 패키지 디버그|N/A|**프로세스에 연결**을 사용하는 대신 [설치된 앱 패키지 디버그](debug-installed-app-package.md)를 참조하세요.|
|Visual Studio에서 시작하지 않은 UWP(유니버설 Windows 플랫폼) 앱, OneCore, HoloLens 또는 IoT 앱 디버그|설치된 앱 패키지 디버그|N/A|**프로세스에 연결**을 사용하는 대신 [설치된 앱 패키지 디버그](debug-installed-app-package.md)를 참조하세요.|

## <a name="use-debugger-features"></a>디버거 기능 사용

프로세스에 연결할 때 Visual Studio 디버거의 전체 기능(예: 중단점 적중)을 사용하려면 앱이 로컬 소스 및 기호와 정확히 일치해야 합니다. 즉, 디버거가 올바른 [기호(.pdb) 파일](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)을 로드할 수 있어야 합니다. 기본적으로 이를 위해 디버그 빌드가 필요합니다.

원격 디버깅 시나리오의 경우 Visual Studio에서 이미 열려 있는 소스 코드(또는 소스 코드의 복사본)가 있어야 합니다. 원격 컴퓨터의 컴파일된 애플리케이션 이진 파일은 로컬 컴퓨터와 동일한 빌드에서 가져와야 합니다.

일부 로컬 디버깅 시나리오에서는 애플리케이션에 올바른 기호 파일이 있는 경우 소스에 액세스하지 않고 Visual Studio에서 디버그할 수 있습니다. 기본적으로 이를 위해 디버그 빌드가 필요합니다. 자세한 내용은 [기호 파일 및 소스 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)을 참조하세요.

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> 연결 오류 문제 해결

일부 시나리오에서 디버거는 디버그할 코드 형식을 올바르게 식별하는 데 도움이 필요할 수 있습니다. 연결 값이 올바르게 설정되었지만(**사용 가능한 프로세스** 목록에서 올바른 프로세스를 볼 수 있음) 디버거가 연결되지 않는 경우 **연결 형식** 목록에서 가장 적합한 연결 형식을 선택합니다. 예를 들어 Linux 또는 Python 앱을 디버깅하는 경우 이 작업이 필요합니다. 기본 연결 형식을 사용하는 경우 이 섹션의 뒷부분에서 설명하는 대로 연결할 특정 형식의 코드를 선택할 수 있습니다.

실행 중인 프로세스에 디버거를 연결할 때 이 프로세스에는 한 가지 이상의 코드 형식이 포함될 수 있습니다. 디버거가 연결될 수 있는 코드 형식이 [코드 형식 선택](../debugger/select-code-type-dialog-box.md) 대화 상자에서 표시되고 선택됩니다.

때로는 디버거가 한 코드 형식에는 연결되고 다른 코드 형식에는 연결되지 않을 수도 있습니다. 일반적으로 다음과 같은 경우에 발생합니다.

- 원격 컴퓨터에서 실행 중인 프로세스에 연결하려고 합니다. 원격 컴퓨터에 설치된 원격 디버깅 구성 요소가 일부 코드 형식만 지원하고 다른 코드 형식은 지원하지 않을 수도 있습니다.
- 데이터베이스를 직접 디버깅하기 위해 두 개 이상의 프로세스에 연결하려고 합니다. SQL 디버깅은 단일 프로세스에 대한 연결만 지원합니다.

디버거를 일부 코드 형식에 연결할 수 있지만 모든 코드 형식에 연결할 수는 없는 경우 연결할 수 없는 형식을 알려 주는 메시지가 표시됩니다.

적어도 하나의 코드 형식에 디버거가 성공적으로 연결되면 프로세스 디버깅을 진행할 수 있습니다. 이 경우 성공적으로 연결된 코드 형식만 디버깅할 수 있습니다. 프로세스에서 연결되지 않은 코드는 계속 실행되지만 중단점을 설정하거나 데이터를 보거나 해당 코드에 다른 디버깅 작업을 수행할 수 없습니다.

특정 코드 형식에 디버거가 연결되지 않는 이유를 보다 구체적으로 확인하려면 해당 코드 형식에만 다시 연결해 보세요.

**코드 형식에 연결하지 못한 이유에 대한 자세한 정보를 얻으려면:**

1. 프로세스에서 분리합니다. **디버그** 메뉴에서 **모두 분리**를 선택합니다.

1. 연결에 실패한 코드 형식만 선택하여 프로세스에 다시 연결합니다.

    1. **프로세스에 연결** 대화 상자의 **사용 가능한 프로세스** 목록에서 프로세스를 선택합니다.

    2. **선택**을 선택합니다.

    3. **코드 형식 선택** 대화 상자에서 **다음 코드 형식 디버깅** 을 선택하고 연결에 실패한 코드 형식을 선택합니다. 다른 코드 형식을 선택 취소합니다.

    4. **확인**을 선택합니다.

    5. **프로세스에 연결** 대화 상자에서 **연결**을 선택합니다.

    이렇게 하면 연결이 완전히 실패하고 자세한 오류 메시지가 나타납니다.

## <a name="see-also"></a>참조

- [여러 프로세스 디버그](../debugger/debug-multiple-processes.md)
- [Just-In-Time 디버깅](../debugger/just-in-time-debugging-in-visual-studio.md)
- [원격 디버깅](../debugger/remote-debugging.md)
