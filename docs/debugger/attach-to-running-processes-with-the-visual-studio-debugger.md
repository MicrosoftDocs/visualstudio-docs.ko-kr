---
title: 디버거를 사용 하 여 실행 중인 프로세스에 연결 | Microsoft Docs
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
ms.openlocfilehash: f2f00cde0c2ea3fad79c0f5ef75f3c33ad7afc22
ms.sourcegitcommit: c98e0ccf236765b44e47095ee52836cb012e3854
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78257191"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Visual Studio 디버거에서 실행 중인 프로세스에 연결
로컬 또는 원격 컴퓨터에서 실행 중인 프로세스에 Visual Studio 디버거를 연결할 수 있습니다. 프로세스를 실행 한 후 **디버그** > **프로세스에 연결** 을 선택 하거나 Visual Studio에서 **Ctrl**+**Alt**+**P** 를 누르고 **프로세스에 연결** 대화 상자를 사용 하 여 디버거를 프로세스에 연결 합니다.

**프로세스에 연결** 을 사용 하 여 로컬 또는 원격 컴퓨터에서 실행 중인 앱을 디버그 하거나, 여러 프로세스를 동시에 디버그 하거나, visual studio에서 생성 되지 않은 앱을 디버그 하거나, 디버거가 연결 된 visual studio에서 시작 하지 않은 앱을 디버그할 수 있습니다. 예를 들어 디버거를 사용 하지 않고 응용 프로그램을 실행 하 고 예외를 발생 하는 경우 응용 프로그램을 실행 하는 프로세스에 디버거를 연결 하 고 디버깅을 시작할 수 있습니다.

> [!TIP]
> 디버깅 시나리오에서 **프로세스에 연결** 을 사용할지 여부를 모를 경우 [일반적인 디버깅 시나리오](#BKMK_Scenarios)를 참조 하십시오.

## <a name="BKMK_Attach_to_a_running_process"></a>로컬 컴퓨터에서 실행 중인 프로세스에 연결

이전에 연결한 프로세스에 빠르게 다시 연결 하려면 [프로세스에](#BKMK_reattach)다시 연결을 참조 하세요.

원격 컴퓨터에서 프로세스를 디버깅 하려면 [원격 컴퓨터의 프로세스에 연결](#BKMK_Attach_to_a_process_on_a_remote_computer)을 참조 하세요.

::: moniker range=">= vs-2019"
Linux Docker 컨테이너에서 .NET Core 프로세스를 디버깅 하려면 [Linux docker 컨테이너에 연결](#BKMK_Docker_Attach)을 참조 하세요.
::: moniker-end

**로컬 컴퓨터의 프로세스에 연결 하려면 다음을 수행 합니다.**

1. Visual Studio에서 **디버그** > **프로세스에 연결** 을 선택 하거나 **ctrl**+**Alt**+**P**를 눌러 **프로세스에 연결** 대화 상자를 엽니다.

   **연결 유형은** **Default**로 설정 해야 합니다. **연결 대상은** 로컬 컴퓨터 이름 이어야 합니다.

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

2. **사용 가능한 프로세스** 목록에서 연결 하려는 프로세스를 찾아 선택 합니다.

   - 프로세스를 신속 하 게 선택 하려면 프로세스 **필터** 상자에 이름을 입력 하거나 첫 번째 문자를 입력 합니다.

   - 프로세스 이름을 모르는 경우 목록을 찾아보거나 일반적인 프로세스 이름에 대 한 [일반적인 디버깅 시나리오](#BKMK_Scenarios) 를 확인 합니다.

   >[!TIP]
   >**프로세스에 연결** 대화 상자가 열려 있는 동안 프로세스를 시작 및 중지할 수 있으므로 실행 중인 프로세스의 목록이 항상 최신이 아닐 수 있습니다. 언제 든 지 **새로 고침** 을 선택 하 여 현재 목록을 볼 수 있습니다.

3. **연결 대상** 필드에서 디버깅할 코드 형식이 나열 되는지 확인 합니다. 기본 **자동** 설정은 대부분의 앱 유형에 서 작동 합니다.

   수동으로 코드 형식을 선택 하려면:
   1. **선택**을 클릭합니다.
   1. **코드 형식 선택** 대화 상자에서 **다음 코드 형식 디버깅**을 선택 합니다.
   1. 디버그할 코드 형식을 선택 합니다.
   1. **확인**을 선택합니다.

4. **연결**을 선택합니다.

>[!NOTE]
>디버깅을 위해 여러 앱에 연결할 수 있지만 한 번에 하나의 앱만 디버거에서 활성화 됩니다. Visual Studio **디버그 위치** 도구 모음이 나 **프로세스** 창에서 활성 앱을 설정할 수 있습니다.

## <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> 원격 컴퓨터의 프로세스에 연결

**프로세스에 연결** 대화 상자에서 원격 컴퓨터를 선택 하 고, 해당 컴퓨터에서 실행 되는 사용 가능한 프로세스 목록을 확인 하 고, 디버깅을 위해 하나 이상의 프로세스에 연결할 수도 있습니다. 원격 디버거 (*msvsmon.exe*)가 원격 컴퓨터에서 실행 되 고 있어야 합니다. 자세한 내용은 [원격 디버깅](../debugger/remote-debugging.md)을 참조 하세요.

IIS에 배포 된 ASP.NET 응용 프로그램을 디버깅 하는 방법에 대 한 자세한 지침은 원격 [iis 컴퓨터에서 원격 디버깅 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)을 참조 하세요.

**원격 컴퓨터에서 실행 중인 프로세스에 연결 하려면 다음을 수행 합니다.**

1. Visual Studio에서 **디버그** > **프로세스에 연결** 을 선택 하거나 **ctrl**+**Alt**+**P**를 눌러 **프로세스에 연결** 대화 상자를 엽니다.

2. 대부분의 경우 **연결 형식은** **기본값** 이어야 합니다. **연결 대상** 상자에서 다음 방법 중 하나를 사용 하 여 원격 컴퓨터를 선택 합니다.

   - **연결 대상**옆에 있는 드롭다운 화살표를 선택 하 고 드롭다운 목록에서 컴퓨터 이름을 선택 합니다.
   - **연결 대상** 상자에 컴퓨터 이름을 입력 하 고 **enter**키를 누릅니다.

     Visual Studio에서 필요한 포트를 컴퓨터 이름에 추가 하는지 확인 합니다 .이 이름은 **\<원격 컴퓨터 이름 >:p ort** 형식으로 표시 됩니다.

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > 원격 컴퓨터 이름을 사용 하 여 연결할 수 없는 경우 IP 주소와 포트 주소를 사용 합니다 (예: `123.45.678.9:4022`). 4024는 Visual Studio 2019 x64 원격 디버거의 기본 포트입니다. 다른 원격 디버거 포트 할당은 [원격 디버거 포트 할당](remote-debugger-port-assignments.md)을 참조 하세요.

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > 원격 컴퓨터 이름을 사용 하 여 연결할 수 없는 경우 IP 주소와 포트 주소를 사용 합니다 (예: `123.45.678.9:4022`). 4022는 Visual Studio 2017 x64 원격 디버거의 기본 포트입니다. 다른 원격 디버거 포트 할당은 [원격 디버거 포트 할당](remote-debugger-port-assignments.md)을 참조 하세요.

     ::: moniker-end

   - **연결 대상** 상자 옆의 **찾기** 단추를 선택 하 여 **원격 연결** 대화 상자를 엽니다. **원격 연결** 대화 상자에는 로컬 서브넷에 있거나 컴퓨터에 직접 연결 된 모든 장치가 나열 됩니다. 원격 장치를 검색 하려면 서버에서 [UDP 포트 3702을 열어야](../debugger/remote-debugger-port-assignments.md) 할 수도 있습니다. 원하는 컴퓨터 또는 장치를 선택 하 고 **선택**을 클릭 합니다.

   > [!NOTE]
   > **연결 유형** 설정은 디버깅 세션 간에 유지 됩니다. **연결 대상** 설정은 해당 대상에서 성공적으로 디버깅 연결에 성공한 경우에만 디버깅 세션 간에 유지 됩니다.

3. **사용 가능한 프로세스** 목록을 채우려면 **새로 고침** 을 클릭 합니다.

    >[!TIP]
    >**프로세스에 연결** 대화 상자가 열려 있는 동안 프로세스를 시작 및 중지할 수 있으므로 실행 중인 프로세스의 목록이 항상 최신이 아닐 수 있습니다. 언제 든 지 **새로 고침** 을 선택 하 여 현재 목록을 볼 수 있습니다.

4. **사용 가능한 프로세스** 목록에서 연결 하려는 프로세스를 찾아 선택 합니다.

   - 프로세스를 신속 하 게 선택 하려면 프로세스 **필터** 상자에 이름을 입력 하거나 첫 번째 문자를 입력 합니다.

   - 프로세스 이름을 모르는 경우 목록을 찾아보거나 일반적인 프로세스 이름에 대 한 [일반적인 디버깅 시나리오](#BKMK_Scenarios) 를 확인 합니다.

   - 모든 사용자 계정에서 실행 중인 프로세스를 찾으려면 **모든 사용자의 프로세스 표시** 확인란을 선택 합니다.

     >[!NOTE]
     >신뢰할 수 없는 사용자 계정에서 소유한 프로세스에 연결하면 보안 경고 확인 대화 상자가 나타납니다. 자세한 내용은 참조 하세요. [보안 경고: 신뢰할 수 없는 사용자가 소유한 프로세스에 연결 하면 위험할 수 있습니다. 다음 정보가 의심 스 럽 또는 확실 하지 않은 경우이 프로세스에 연결 하지 않는](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)합니다.

5. **연결 대상** 필드에서 디버깅할 코드 형식이 나열 되는지 확인 합니다. 기본 **자동** 설정은 대부분의 앱 유형에 서 작동 합니다.

   수동으로 코드 형식을 선택 하려면:
   1. **선택**을 클릭합니다.
   1. **코드 형식 선택** 대화 상자에서 **다음 코드 형식 디버깅**을 선택 합니다.
   1. 디버그할 코드 형식을 선택 합니다.
   1. **확인**을 선택합니다.

6. **연결**을 선택합니다.

>[!NOTE]
>디버깅을 위해 여러 앱에 연결할 수 있지만 한 번에 하나의 앱만 디버거에서 활성화 됩니다. Visual Studio **디버그 위치** 도구 모음이 나 **프로세스** 창에서 활성 앱을 설정할 수 있습니다.

원격 데스크톱 (터미널 서비스) 세션에서 디버깅할 때 사용 가능한 **프로세스** 목록에 사용 가능한 모든 프로세스가 표시 되지 않는 경우도 있습니다. 사용자 계정이 제한 된 사용자로 Visual Studio를 실행 하는 경우 세션 0에서 실행 되는 프로세스는 **사용 가능한 프로세스** 목록에 표시 되지 않습니다. 세션 0은 서비스 및 w3wp.exe *를 비롯 한*다른 서버 프로세스에 사용 됩니다. 관리자 계정으로 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 를 실행하거나 터미널 서비스 세션 대신 서버 콘솔에서 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 를 실행하여 이 문제를 해결할 수 있습니다.

이러한 해결 방법을 둘 다 사용할 수 없는 경우 세 번째 방법으로 Windows 명령줄에서 `vsjitdebugger.exe -p <ProcessId>`를 실행하여 프로세스에 연결합니다. *Tlist.exe*를 사용 하 여 프로세스 ID를 결정할 수 있습니다. *tlist.exe*를 얻으려면 [WDK 및 WinDbg 다운로드](/windows-hardware/drivers/download-the-wdk)에서 Debugging Tools for Windows를 다운로드하여 설치합니다.

::: moniker range=">= vs-2019"

## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>SSH를 사용 하 여 Linux에서 실행 되는 .NET Core 프로세스에 연결

자세한 내용은 [SSH를 사용 하 여 Linux에서 실행 되는 원격 디버그 .Net Core](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)를 참조 하세요.

## <a name="BKMK_Docker_Attach"></a>Linux Docker 컨테이너에서 실행 되는 프로세스에 연결

**프로세스에 연결** 대화 상자를 사용 하 여 로컬 또는 원격 컴퓨터의 Linux .Net Core Docker 컨테이너에서 실행 되는 프로세스에 Visual Studio 디버거를 연결할 수 있습니다.

> [!IMPORTANT]
> 이 기능을 사용 하려면 .NET Core 플랫폼 간 개발 워크 로드를 설치 하 고 소스 코드에 대 한 로컬 액세스 권한이 있어야 합니다.

**Linux Docker 컨테이너에서 실행 중인 프로세스에 연결 하려면 다음을 수행 합니다.**

1. Visual Studio에서 **디버그 > 프로세스에 연결 (CTRL + ALT + P)** 을 선택 하 여 **프로세스에 연결** 대화 상자를 엽니다.

![프로세스에 연결 메뉴](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. **연결 유형** 을 **Docker (Linux 컨테이너)** 로 설정 합니다.
3. **찾기 ...** 를 선택 하 여 **Docker 컨테이너 선택** 대화 상자를 통해 **연결 대상을** 설정 합니다.

    Docker 컨테이너 프로세스는 로컬 또는 원격으로 디버그할 수 있습니다.
    
    **Docker 컨테이너 프로세스를 로컬로 디버깅 하려면:**
    1. **DOCKER CLI 호스트** 를 **로컬 컴퓨터로**설정 합니다.
    1. 목록에서 연결할 실행 중인 컨테이너를 선택 하 고 **확인**을 누릅니다.
    
    ![Docker 컨테이너 선택 메뉴](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")
 
    **B. Docker 컨테이너 프로세스를 원격으로 디버깅 하려면:**
    
    > [!NOTE] 
    > Docker 컨테이너에서 실행 중인 프로세스에 원격으로 연결 하는 방법에는 두 가지가 있습니다. SSH를 사용 하는 첫 번째 옵션은 로컬 컴퓨터에 Docker 도구를 설치 하지 않은 경우에 적합 합니다.  Docker 도구를 로컬로 설치 하 고 원격 요청을 허용 하도록 구성 된 Docker 디먼이 있는 경우 Docker 디먼을 사용 하 여 두 번째 옵션을 사용해 보세요.

    1. ***SSH를 통해 원격 컴퓨터에 연결 하려면:***
        1. **추가 ...** 를 선택 하 여 원격 시스템에 연결 합니다.<br/>
        ![원격 시스템에 연결](../debugger/media/connect-remote-system.png "원격 시스템에 연결")
        1. SSH 또는 디먼에 연결한 후에 연결할 실행 중인 컨테이너를 선택 하 고 **확인**을 누릅니다.

    
    1. ***[Docker 디먼을](https://docs.docker.com/engine/reference/commandline/dockerd/) 통해 프로세스를 실행 하는 원격 컨테이너로 대상을 설정 하려면***
        1. **Docker 호스트 (선택 사항)** 에서 디먼 주소 (예: TCP, IP 등)를 지정 하 고 새로 고침 링크를 클릭 합니다.
        1. 데몬을 성공적으로 연결한 후에 연결할 실행 중인 컨테이너를 선택 하 고 **확인**을 누릅니다.

4. **사용 가능한 프로세스** 목록에서 해당 컨테이너 프로세스를 선택 하 고 **연결** 을 선택 하 여 Visual C# Studio에서 컨테이너 프로세스 디버깅을 시작 합니다.

    ![완료 된 Docker 연결 메뉴](../debugger/media/docker-attach-complete.png "완료 된 Docker 연결 메뉴")


::: moniker-end

## <a name="BKMK_reattach"></a>프로세스에 다시 연결

**프로세스에** 다시 연결 (**Shift**+**Alt**+**P**)을 ** > 선택 하** 여 이전에 연결한 프로세스에 신속 하 게 다시 연결할 수 있습니다. 이 명령을 선택 하는 경우 디버거는 먼저 이전 프로세스 ID와 일치 하는 항목을 검색 하 여 이전 프로세스 이름과 일치 하는 경우에 연결 하는 마지막 프로세스에 연결을 시도 합니다. 일치 하는 항목이 없거나 여러 프로세스에 동일한 이름이 있는 경우 **프로세스에 연결** 대화 상자가 열리며,이를 통해 올바른 프로세스를 선택할 수 있습니다.

> [!NOTE]
> **프로세스에** 다시 연결 명령은 Visual Studio 2017부터 사용할 수 있습니다.

## <a name="BKMK_Scenarios"></a>일반적인 디버깅 시나리오

다음 표에서는 연결 **에 연결** 을 사용할지 여부를 결정 하는 데 도움이 되도록 및 연결할 프로세스를 보여 줍니다. 다음 표에서는 사용 가능한 경우 추가 지침에 대 한 링크와 함께 몇 가지 일반적인 디버깅 시나리오를 보여 줍니다. (목록은 완전 하지 않습니다.)

UWP (유니버설 Windows 앱) 앱과 같은 일부 앱 형식의 경우 프로세스 이름에 직접 연결 하지 않고 Visual Studio의 **설치 된 응용 프로그램 패키지 디버그** 메뉴 옵션 (표 참조)을 사용 합니다.

디버거에서 C++로 작성된 코드에 연결하려면 코드에 `DebuggableAttribute`가 있어야 합니다. 이 특성은 [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) 링커 옵션으로 링크하여 자동으로 코드에 추가할 수 있습니다.

클라이언트 쪽 스크립트 디버깅의 경우 브라우저에서 스크립트 디버깅을 사용 하도록 설정 해야 합니다. Chrome에서 클라이언트 쪽 스크립트를 디버깅 하려면 코드 형식으로 **웹 키트** 를 선택 하 고, 앱 유형에 따라 모든 Chrome 인스턴스를 닫고 디버깅 모드에서 브라우저를 시작 해야 할 수 있습니다 (명령줄에서 `chrome.exe --remote-debugging-port=9222` 입력).

연결할 실행 중인 프로세스를 신속 하 게 선택 하려면 Visual Studio에서 **Ctrl**+**Alt**+**P**를 입력 한 다음 프로세스 이름의 첫 문자를 입력 합니다.

|시나리오|Debug 메서드|프로세스 이름|노트 및 링크|
|-|-|-|-|
|IIS 서버에서 원격 디버그 ASP.NET 4 또는 4.5|원격 도구를 사용 하 여 **프로세스에 연결**|*w3wp.exe*|원격 [IIS 컴퓨터의 원격 디버깅 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) 을 참조 하세요.|
|IIS 서버의 원격 디버그 ASP.NET Core|원격 도구를 사용 하 여 **프로세스에 연결**|*dotnet* 또는 *appname .exe*|앱 배포의 경우 [IIS에 게시](https://docs.asp.net/en/latest/publishing/iis.html)를 참조 하세요. 디버깅 [은 원격 IIS 컴퓨터의 원격 디버깅 ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) 를 참조 하세요.|
|지원 되는 앱 형식에 대해 로컬 IIS 서버에서 클라이언트 쪽 스크립트 디버깅 |**프로세스에 연결** 사용|*chrome*, *MicrosoftEdgeCP*또는 *iexplore.exe*|스크립트 디버깅을 사용 하도록 설정 해야 합니다. Chrome의 경우 디버그 모드에서 Chrome을 실행 하 고 **연결 대상** 필드에서 **Webkit 코드** 를 선택 해야 합니다.|
|로컬 컴퓨터 C#에서, Visual Basic 또는 C++ 앱 디버그|표준 디버깅 (**F5**) 또는 **프로세스에 연결을 사용 합니다** .|*\<appname>.exe*|대부분의 시나리오에서는 표준 디버깅을 사용 하 고 **프로세스에 연결**하지 않습니다.|
|Windows 데스크톱 응용 프로그램 원격 디버그|원격 도구|해당 없음| [원격 디버그 C# 또는 앱 Visual Basic](../debugger/remote-debugging-csharp.md) 또는 [앱 원격 디버그를 C++ ](../debugger/remote-debugging-cpp.md) 참조 하세요.|
|Linux에서 .NET Core 디버그|**프로세스에 연결** 사용|*dotnet.exe*|SSH를 사용 하려면 [ssh를 사용 하 여 Linux에서 실행 되는 원격 디버그 .Net Core](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)를 참조 하세요. |
|디버거를 사용 하지 않고 앱을 시작한 후 로컬 컴퓨터에서 ASP.NET 앱 디버그|**프로세스에 연결** 사용|*iiexpress.exe*|이렇게 하면 프로 파일링 하는 경우와 같이 앱을 더 빠르게 로드 하는 데 도움이 될 수 있습니다. |
|서버 프로세스에서 지원 되는 다른 앱 유형 디버깅|서버가 원격 이면 원격 도구를 사용 하 여 **프로세스에 연결** 합니다.|*chrome*, *iexplore.exe*또는 기타 프로세스|필요한 경우 리소스 모니터를 사용 하 여 프로세스를 식별 하는 데 도움을 줍니다. [원격 디버깅](../debugger/remote-debugging.md)을 참조하세요.|
|UWP (유니버설 Windows 앱), OneCore, HoloLens 또는 IoT 앱 원격 디버그|설치된 앱 패키지 디버그|해당 없음|**프로세스에 연결을** 사용 하는 대신 [설치 된 앱 패키지 디버그](debug-installed-app-package.md) 를 참조 하세요.|
|Visual Studio에서 시작 하지 않은 UWP (유니버설 Windows 앱), OneCore, HoloLens 또는 IoT 앱 디버그|설치된 앱 패키지 디버그|해당 없음|**프로세스에 연결을** 사용 하는 대신 [설치 된 앱 패키지 디버그](debug-installed-app-package.md) 를 참조 하세요.|

## <a name="use-debugger-features"></a>디버거 기능 사용

프로세스에 연결할 때 Visual Studio 디버거의 전체 기능 (예: 중단점 적중)을 사용 하려면 앱이 로컬 소스와 기호와 정확히 일치 해야 합니다. 즉, 디버거가 올바른 [기호 (.pdb) 파일](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)을 로드할 수 있어야 합니다. 기본적으로이 경우 디버그 빌드가 필요 합니다.

원격 디버깅 시나리오의 경우 Visual Studio에서 이미 열려 있는 소스 코드 (또는 소스 코드의 복사본)가 있어야 합니다. 원격 컴퓨터의 컴파일된 응용 프로그램 이진 파일은 로컬 컴퓨터와 동일한 빌드에서 가져와야 합니다.

일부 로컬 디버깅 시나리오에서는 응용 프로그램에 올바른 기호 파일이 있는 경우 소스에 액세스 하지 않고 Visual Studio에서 디버그할 수 있습니다. 기본적으로이 경우 디버그 빌드가 필요 합니다. 자세한 내용은 [기호 및 소스 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)을 참조 하세요.

## <a name="BKMK_Troubleshoot_attach_errors"></a> 연결 오류 문제 해결
 실행 중인 프로세스에 디버거를 연결할 때 이 프로세스에는 한 가지 이상의 코드 형식이 포함될 수 있습니다. 디버거가 연결될 수 있는 코드 형식이 **코드 형식 선택** 대화 상자에서 표시되고 선택됩니다.

 때로는 디버거가 한 코드 형식에는 연결되고 다른 코드 형식에는 연결되지 않을 수도 있습니다. 이러한 문제는 원격 컴퓨터에서 실행 중인 프로세스에 연결하려 할 때 발생할 수 있습니다. 원격 컴퓨터에 설치된 원격 디버깅 구성 요소가 일부 코드 형식만 지원하고 다른 코드 형식은 지원하지 않을 수도 있습니다. 데이터베이스를 직접 디버깅하기 위해 두 개 이상의 프로세스에 연결하려는 경우에도 이 문제가 발생할 수 있습니다. SQL 디버깅은 단일 프로세스에 대한 연결만 지원합니다.

 디버거를 일부 코드 형식에 연결할 수 있는 경우 연결에 실패 한 형식을 식별 하는 메시지가 표시 됩니다.

 적어도 하나의 코드 형식에 디버거가 성공적으로 연결되면 프로세스 디버깅을 진행할 수 있습니다. 이 경우 성공적으로 연결된 코드 형식만 디버깅할 수 있습니다. 프로세스에서 연결 되지 않은 코드는 계속 실행 되지만 중단점을 설정 하거나 데이터를 보거나 해당 코드에 대 한 다른 디버깅 작업을 수행할 수 없습니다.

 디버거를 코드 형식에 연결 하지 못한 이유에 대 한 자세한 정보를 원하는 경우 해당 코드 형식에만 다시 연결 해 보세요.

 **코드 형식에 연결하지 못한 이유에 대한 자세한 정보를 얻으려면:**

1. 프로세스에서 분리합니다. **디버그** 메뉴에서 **모두 분리**를 선택 합니다.

1. 연결에 실패 한 코드 유형만 선택 하 여 프로세스에 다시 연결 합니다.

    1. **프로세스에 연결** 대화 상자의 **사용 가능한 프로세스** 목록에서 프로세스를 선택합니다.

    2. **선택**을 선택합니다.

    3. **코드 형식 선택** 대화 상자에서 **다음 코드 형식 디버깅** 을 선택하고 연결에 실패한 코드 형식을 선택합니다. 다른 코드 형식을 선택 취소 합니다.

    4. **확인**을 선택합니다.

    5. **프로세스에 연결** 대화 상자에서 **연결**을 선택 합니다.

    이렇게 하면 연결이 완전히 실패하고 자세한 오류 메시지가 나타납니다.

## <a name="see-also"></a>참고 항목

- [여러 프로세스 디버그](../debugger/debug-multiple-processes.md)
- [Just-In-Time 디버깅](../debugger/just-in-time-debugging-in-visual-studio.md)
- [원격 디버깅](../debugger/remote-debugging.md)
