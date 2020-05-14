---
title: Microsoft Visual Studio 원격 디버깅 모니터에 연결할 수 없습니다. Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.remote_debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: a1d959fc-3817-491c-831b-e6b768a3877a
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d62e7ce1c419a9c53e40e1ecf2f71497d60d7a23
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77477059"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 오류 메시지는 **프로세스에 연결** 대화 상자에 잘못된 Visual Studio 원격 디버깅 모니터 이름을 입력한 경우에 나타납니다. 원격 디버깅 모니터 이름은 일반적으로 원격으로 디버깅하기 위해 연결하려는 컴퓨터의 이름과 동일합니다. 이 메시지는 원격 컴퓨터가 네트워크에 없거나, 원격 컴퓨터에 원격 디버깅 모니터가 올바르게 설치되지 않았거나, 네트워크 문제 또는 방화벽으로 인해 원격 컴퓨터에 액세스할 수 없는 경우에 나타날 수 있습니다.  
  
> [!IMPORTANT]
> 자세한 도움말이 필요한 경우 [Talk to Us](../ide/talk-to-us.md) 에서 Microsoft에 문의하는 방법을 참조하세요.  
  
## <a name="i-got-this-message-while-i-was-debugging-locally"></a>로컬로 디버그하는 동안 이 메시지가 수신됨  
 로컬로 디버그하는 동안 이 메시지가 수신된 경우 바이러스 백신 소프트웨어 또는 타사 방화벽 때문일 수 있습니다. Visual Studio는 32비트 애플리케이션이므로 64비트 버전의 원격 디버거를 사용하여 64비트 애플리케이션을 디버그합니다. 두 프로세스는 로컬 컴퓨터 내의 로컬 네트워크를 사용하여 통신합니다. 컴퓨터에서 나가는 네트워크 트래픽이 없지만 타사 보안 소프트웨어가 통신을 차단할 수 있습니다.  
  
 다음 섹션에서는 이 메시지가 수신되는 몇 가지 다른 이유 및 문제를 해결하기 위해 수행할 수 있는 작업을 보여 줍니다.  
  
## <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 원격 컴퓨터에 Visual Studio 원격 디버깅 모니터가 설치되어 실행되고 있는지 확인합니다. 원격 디버거 및 설치 방법에 대 한 자세한 내용은 [원격 디버깅](../debugger/remote-debugging.md)을 참조 하세요.  
  
- Visual Studio에서 프로젝트 속성을 확인합니다(**프로젝트/속성/디버깅**). **원격 서버 이름** 이 올바른지 확인합니다.  
  
- 네트워크에서 원격 컴퓨터에 액세스할 수 있는지 확인합니다.  
  
## <a name="the-remote-machine-is-not-reachable"></a>원격 컴퓨터에 연결할 수 없음  
 원격 컴퓨터를 [ping](https://technet.microsoft.com/library/ee624059\(v=ws.10\).aspx) 하려고 합니다. Ping에 응답하지 않으면 원격 도구도 연결할 수 없습니다. 원격 컴퓨터를 다시 부팅하거나 네트워크에서 올바르게 구성되었는지 확인합니다.  
  
## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>원격 디버거 버전이 Visual Studio 버전과 일치하지 않음  
 로컬로 실행하는 Visual Studio 버전이 원격 컴퓨터에서 실행되는 원격 디버깅 모니터 버전과 일치해야 합니다. 이 문제를 해결하려면 일치하는 버전의 원격 디버깅 모니터를 다운로드하여 설치합니다. Visual studio [구독](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015) 으로 이동 하 여 사용자의 visual studio 버전에 맞는 올바른 버전의 원격 디버거를 찾습니다.

## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>로컬 및 원격 컴퓨터의 인증 모드가 서로 다름  

 로컬 및 원격 컴퓨터에서 동일한 인증 모드를 사용해야 합니다. 이 문제를 해결하려면 두 컴퓨터에서 모두 동일한 인증 모드를 사용 중인지 확인합니다. **도구/옵션** 대화 상자에서 원격 디버거의 인증 모드를 변경할 수 있습니다.  
  
 인증 모드에 대한 자세한 내용은 [Windows 인증 개요](https://technet.microsoft.com/library/hh831472.aspx)를 참조하세요.  
  
## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>원격 디버거가 다른 사용자 계정으로 실행되고 있음  
 다음 방법 중 하나를 사용하여 이 문제를 해결할 수 있습니다.  
  
- 원격 디버거를 중지하고 로컬 컴퓨터에서 사용 중인 계정으로 다시 시작할 수 있습니다.  
  
- **/allow \<사용자 이름>** 매개 변수를 사용하여 명령줄에서 원격 디버거를 시작할 수 있습니다. `msvsmon /allow <username@computer>`  
  
- 원격 디버거의 사용 권한에 사용자를 추가할 수 있습니다(원격 디버거 창, **도구 / 사용 권한**).  
  
- 이전 단계에서 메서드를 사용할 수 없는 경우 모든 사용자가 원격 디버깅을 수행하도록 허용할 수 있습니다. 원격 디버거 창에서 **도구 / 옵션** 대화 상자로 이동합니다. **인증 안 함**을 선택하는 경우 **모든 사용자가 디버깅할 수 있도록 허용**을 선택할 수 있습니다. 그러나 선택 항목이 없거나 개인 네트워크에 있는 경우에만 이 옵션을 사용해야 합니다.  
  
## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>원격 컴퓨터의 방화벽이 원격 디버거로 들어오는 연결을 허용하지 않습니다.  
 Visual Studio와 원격 디버거 간의 통신을 허용하도록 Visual Studio 컴퓨터의 방화벽 및 원격 컴퓨터의 방화벽을 구성해야 합니다. 원격 디버거에서 사용 중인 포트에 대한 자세한 내용은 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)을 참조하세요. Windows 방화벽을 구성하는 방법에 대한 자세한 내용은 [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md)을 참조하세요.  
  
## <a name="anti-virus-software-is-blocking-the-connections"></a>바이러스 백신 소프트웨어가 연결을 차단함  
 Windows 바이러스 백신 소프트웨어는 원격 디버거 연결을 허용하지만 일부 타사 바이러스 백신 소프트웨어가 차단할 수도 있습니다. 이러한 연결을 허용하는 방법을 알아보려면 해당 바이러스 백신 소프트웨어에 대한 설명서를 확인합니다.  
  
## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>네트워크 보안 정책에서 원격 컴퓨터와 Visual Studio 간의 통신을 차단함  
 네트워크 보안을 검토하여 통신을 차단하지 않는지 확인합니다. Windows 네트워크 보안 정책에 대한 자세한 내용은 [보안 관리](https://msdn.microsoft.com/library/windows/desktop/ms721855\(v=vs.85\).aspx)를 참조하세요.  
  
## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>네트워크 사용량이 너무 많아 원격 디버깅을 지원할 수 없음  
 다른 시간에 원격 디버깅을 수행하거나 다른 시간에 네트워크 작업을 다시 예약해야 할 수도 있습니다.  
  
## <a name="more-help"></a>자세한 도움말  
 명령줄 스위치를 포함하여 원격 디버거에 대한 자세한 도움말을 보려면 브라우저에서 다음을 엽니다.  
  
 **res://C:\Program%20Files\Microsoft%20Visual%20Studio%2014.0\Common7\IDE\Remote%20Debugger\x64\msvsmon.exe/help.htm**  
  
## <a name="see-also"></a>참고 항목  
 [원격 디버깅](../debugger/remote-debugging.md)
