---
title: Microsoft 비주얼 스튜디오 원격 디버깅 모니터에 연결할 수 없음 | 마이크로 소프트 문서
ms.date: 04/14/2020
ms.topic: reference
f1_keywords:
- vs.debug.error.remote_debug
- vs.debug.error.firewall.remotemachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d509292bc3c7a909289abf0c73babccfead31532
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385395"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor
원격 디버깅 모니터가 원격 컴퓨터에서 제대로 설정되지 않았거나 네트워크 문제 또는 방화벽이 있는 경우 원격 컴퓨터에 액세스할 수 없기 때문에 이 메시지가 발생할 수 있습니다.

> [!IMPORTANT]
> 제품 버그로 인해 이 메시지를 받았다고 생각되면 이 문제를 Visual Studio에 [보고하십시오.](../ide/how-to-report-a-problem-with-visual-studio.md) 자세한 도움말이 필요한 경우 [Talk to Us](../ide/feedback-options.md) 에서 Microsoft에 문의하는 방법을 참조하세요.

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>자세한 오류 메시지는 무엇입니까?

`Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` 메시지는 일반입니다. 일반적으로 오류 문자열에 보다 구체적인 메시지가 포함되어 있으며 문제의 원인을 식별하거나 보다 정확한 수정 프로그램을 검색하는 데 도움이 될 수 있습니다. 다음은 기본 오류 메시지에 추가되는 몇 가지 일반적인 오류 메시지입니다.

- [디버거가 원격 컴퓨터에 연결할 수 없습니다. 디버거가 지정된 컴퓨터 이름을 확인할 수 없습니다.](#cannot_connect)
- [원격 디버거에서 연결 요청이 거부되었습니다.](#rejected)
- [메모리 위치에 대한 잘못된 액세스](#invalid_access)
- [원격 컴퓨터에서 실행 중인 지정된 이름으로 서버가 없습니다.](#no_server)
- [요청된 이름이 유효하지만 요청된 형식의 데이터가 없습니다.](#valid_name)
- [대상 컴퓨터의 Visual Studio 원격 디버거가 이 컴퓨터에 다시 연결할 수 없습니다.](#cant_connect_back)
- [액세스가 거부됨](#access_denied)
- [보안 패키지 특정 오류가 발생했습니다.](#security_package)

## <a name="the-debugger-cannot-connect-to-the-remote-computer-the-debugger-was-unable-to-resolve-the-specified-computer-name"></a><a name="cannot_connect"></a>디버거가 원격 컴퓨터에 연결할 수 없습니다. 디버거가 지정된 컴퓨터 이름을 확인할 수 없습니다.

다음 단계를 시도합니다.

1. **프로세스 첨부** 대화 상자 또는 프로젝트 속성에 유효한 컴퓨터 이름과 포트 번호를 입력해야 합니다(속성을 설정하려면 [다음 단계를](#server_incorrect)참조). 컴퓨터 이름은 다음 형식이어야 합니다.

    `computername:port`

    > [!NOTE]
    > 포트 번호는 대상 컴퓨터에서 실행중인 [원격 디버거의 포트 번호와](../debugger/remote-debugger-port-assignments.md) *일치해야 합니다.*

2. 컴퓨터 이름이 작동하지 않으면 대신 IP 주소와 포트 번호를 사용해 보십시오.

3. 대상 컴퓨터에서 실행되는 원격 디버거 버전이 Visual Studio 버전과 일치하는지 확인합니다. 원격 디버거의 올바른 버전을 얻으려면 [원격 디버깅](../debugger/remote-debugging.md)을 참조하십시오.

    > [!TIP]
    > 프로세스에 연결하고 성공적으로 연결했지만 원하는 프로세스가 표시되지 않으면 **모든 사용자에서 프로세스 표시 확인란을**선택합니다. 이렇게 하면 다른 사용자 계정으로 연결된 프로세스가 표시됩니다.

4. 이러한 단계를 수행해도 이 오류가 해결되지 않으면 [원격 컴퓨터에 연결할 수 없습니다.](#dns)

## <a name="connection-request-was-rejected-by-the-remote-debugger"></a><a name="rejected"></a>원격 디버거에서 연결 요청이 거부되었습니다.

**프로세스에 연결** 대화 상자 또는 프로젝트 속성에서 원격 컴퓨터 이름과 포트 번호가 원격 디버거 창에 표시된 이름 및 포트 번호와 일치하는지 확인합니다. 올바르지 않으면 수정하고 다시 시도하십시오.

이러한 값이 올바르고 메시지에 **Windows 인증** 모드가 언급되어 있으면 원격 디버거가 올바른 인증 모드(도구 **> 옵션)에**있는지 확인합니다.

## <a name="the-connection-with-the-remote-endpoint-was-terminated"></a><a name="connection_terminated"></a>원격 끝점과의 연결이 종료되었습니다.

Azure App Service 앱을 디버깅하는 경우 **프로세스에 연결대신**클라우드 탐색기 또는 서버 탐색기에서 [디버거 연결](../debugger/remote-debugging-azure.md#remote_debug_azure_app_service) 명령을 사용해 보십시오.

**프로세스에 연결하여** 디버깅하는 경우:

1. **프로세스에 연결** 대화 상자 또는 프로젝트 속성에서 원격 컴퓨터 이름과 포트 번호가 원격 디버거 창에 표시된 이름 및 포트 번호와 일치하는지 확인합니다. 올바르지 않으면 수정하고 다시 시도하십시오.

2. 문제를 해결하는 데 도움이 되는 자세한 내용은 서버의 응용 프로그램 로그(Windows의 이벤트 뷰어)를 확인하십시오.

3. 그렇지 않으면 관리자 권한으로 Visual Studio를 다시 시작한 다음 다시 시도하십시오.

## <a name="invalid-access-to-memory-location"></a><a name="invalid_access"></a>메모리 위치에 대한 잘못된 액세스

내부 오류가 발생했습니다. Visual Studio를 다시 시작한 다음 작업을 다시 시도합니다.

## <a name="there-is-no-server-by-the-specified-name-running-on-the-remote-computer"></a><a name="no_server"></a>원격 컴퓨터에서 실행 중인 지정된 이름으로 서버가 없습니다.

Visual Studio에서 원격 디버거에 연결할 수 없습니다. 이 메시지는 다음과 같은 여러 가지 이유로 발생할 수 있습니다.

- 원격 디버거가 다른 사용자 계정에서 실행 중일 수 있습니다. [다음 단계](#user_accounts) 보기

- 포트가 방화벽에서 차단되었습니다. 특히 타사 방화벽을 사용하는 경우 방화벽이 [요청을 차단하지 않는지](#firewall)확인합니다.

- 원격 디버거 버전이 Visual Studio와 일치하지 않습니다. 원격 디버거의 올바른 버전을 얻으려면 [원격 디버깅](../debugger/remote-debugging.md)을 참조하십시오.

## <a name="the-requested-name-was-valid-but-no-data-of-the-requested-type-was-found"></a><a name="valid_name"></a>요청된 이름이 유효하지만 요청된 형식의 데이터가 없습니다.

원격 컴퓨터가 있지만 Visual Studio에서 원격 디버거에 연결할 수 없습니다. 이 메시지는 다음과 같은 여러 가지 이유로 발생할 수 있습니다.

- DNS 문제로 인해 연결이 차단됩니다. [다음 단계를](#dns)참조하십시오.

- 원격 디버거가 다른 사용자 계정에서 실행 중일 수 있습니다. [다음 단계를](#user_accounts)수행합니다.

- 포트가 방화벽에서 차단되었습니다. 특히 타사 방화벽을 사용하는 경우 방화벽이 [요청을 차단하지 않는지](#firewall)확인합니다.

- 원격 디버거 버전이 Visual Studio와 일치하지 않습니다. 원격 디버거의 올바른 버전을 얻으려면 [원격 디버깅](../debugger/remote-debugging.md)을 참조하십시오.

## <a name="the-visual-studio-remote-debugger-on-the-target-computer-cannot-connect-back-to-this-computer"></a><a name="cant_connect_back"></a>대상 컴퓨터의 Visual Studio 원격 디버거가 이 컴퓨터에 다시 연결할 수 없습니다.

원격 디버거가 다른 사용자 계정에서 실행 중일 수 있습니다. 원격 디버거에서 도구 **> 도구를** 열어 사용자를 원격 디버거의 사용 권한에 추가합니다. 자세한 내용은 [원격 디버거가 다른 사용자 계정에서 실행 중임을](#user_accounts)참조하십시오.

오류 메시지에 방화벽도 언급되어 있으면 로컬 컴퓨터의 방화벽이 원격 컴퓨터에서 Visual Studio로 다시 통신하지 못하게 될 수 있습니다. [다음 단계를](#firewall)참조하십시오.

## <a name="access-denied"></a><a name="access_denied"></a>액세스가 거부됨

32비트 컴퓨터에서 64비트 원격 컴퓨터에서 디버깅을 시도하는 경우 이 오류가 표시될 수 있습니다(지원되지 않음).

## <a name="a-security-package-specific-error-occurred"></a><a name="security_package"></a>보안 패키지 특정 오류가 발생했습니다.

이 문제는 Windows XP 및 Windows 7과 관련된 레거시 문제일 수 있습니다. 이 [정보를](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package)참조하십시오.

## <a name="causes-and-recommendations"></a>원인 및 권장 사항

### <a name="the-remote-machine-is-not-reachable"></a><a name="dns"></a>원격 컴퓨터에 연결할 수 없습니다.

원격 컴퓨터 이름을 사용하여 연결할 수 없는 경우 대신 IP 주소를 사용해 보십시오. 원격 컴퓨터의 명령줄에서 IPv4 주소를 얻을 수 있습니다. `ipconfig` HOSTS 파일을 사용하는 경우 올바르게 구성되어 있는지 확인합니다.

실패하면 네트워크에서 원격 컴퓨터에 액세스할 수 있는지[확인합니다(원격](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) 컴퓨터 ping). 일부 Microsoft Azure 시나리오를 제외하면 인터넷을 통한 원격 디버깅은 지원되지 않습니다.

### <a name="the-server-name-is-incorrect-or-third-party-software-is-interfering-with-the-remote-debugger"></a><a name="server_incorrect"></a>서버 이름이 올바르지 않거나 타사 소프트웨어가 원격 디버거를 방해하고 있습니다.

Visual Studio에서 프로젝트 속성을 확인하고 서버 이름이 올바른지 확인합니다. [C# 및 비주얼 기본](../debugger/remote-debugging-csharp.md#remote_csharp) 및 [C++에](../debugger/remote-debugging-cpp.md#remote_cplusplus)대한 항목을 참조하십시오. ASP.NET 경우 프로젝트 유형에 따라 **속성 / 웹 / 서버** 또는 속성 / **디버그를** 엽니다.

> [!NOTE]
> 프로세스에 연결하는 경우 프로젝트 속성의 원격 설정이 사용되지 않습니다.

서버 이름이 올바르면 바이러스 백신 소프트웨어 또는 타사 방화벽이 원격 디버거를 차단하고 있을 수 있습니다. 로컬로 디버깅할 때 Visual Studio는 32비트 응용 프로그램이기 때문에 64비트 버전의 원격 디버거를 사용하여 64비트 응용 프로그램을 디버깅할 수 있습니다. 32비트 및 64비트 프로세스는 로컬 컴퓨터 내의 로컬 네트워크를 사용하여 통신합니다. 컴퓨터에서 나가는 네트워크 트래픽이 없지만 타사 보안 소프트웨어가 통신을 차단할 수 있습니다.

### <a name="the-remote-debugger-is-running-under-a-different-user-account"></a><a name="user_accounts"></a>원격 디버거가 다른 사용자 계정에서 실행 중입니다.

원격 디버거는 기본적으로 원격 디버거를 시작한 사용자와 Administrators 그룹의 구성원만 허용합니다. 추가 사용자에게 명시적으로 사용 권한이 부여되어야 합니다.

다음 방법 중 하나를 사용하여 이 문제를 해결할 수 있습니다.

- 원격 디버거의 사용 권한에 Visual Studio 사용자를 추가합니다(원격 디버거 창에서 **도구 > 사용 권한**선택).

- 원격 컴퓨터에서 Visual Studio 컴퓨터에서 사용하는 것과 동일한 사용자 계정 및 암호로 원격 디버거를 다시 시작합니다.

    > [!NOTE]
    > 원격 서버에서 원격 디버거를 실행하는 경우 원격 디버거 앱을 마우스 오른쪽 단추로 클릭하고 **관리자로 실행을** 선택합니다(또는 원격 디버거를 서비스로 실행할 수 있음). 원격 서버에서 실행하지 않는 경우 정상적으로 시작하십시오.

- **/allow \<사용자 이름>** 매개 변수를 사용하여 명령줄에서 원격 디버거를 시작할 수 있습니다`msvsmon /allow <username@computer>`.

- 또는 모든 사용자가 원격 디버깅을 수행하도록 허용할 수 있습니다. 원격 디버거 창에서 **도구 > 옵션** 대화 상자로 이동합니다. **인증 안 함**을 선택하는 경우 **모든 사용자가 디버깅할 수 있도록 허용**을 선택할 수 있습니다. 그러나 다른 옵션이 실패하거나 개인 네트워크에 있는 경우에만 이 옵션을 시도해야 합니다.

### <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a><a name="firewall"></a>원격 컴퓨터의 방화벽은 원격 디버거에 들어오는 연결을 허용하지 않습니다.
 Visual Studio와 원격 디버거 간의 통신을 허용하도록 Visual Studio 컴퓨터의 방화벽 및 원격 컴퓨터의 방화벽을 구성해야 합니다. 원격 디버거에서 사용 중인 포트에 대한 자세한 내용은 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)을 참조하세요. Windows 방화벽을 구성하는 방법에 대한 자세한 내용은 [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md)을 참조하세요.

### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>원격 디버거 버전이 Visual Studio 버전과 일치하지 않음
 로컬로 실행하는 Visual Studio 버전이 원격 컴퓨터에서 실행되는 원격 디버깅 모니터 버전과 일치해야 합니다. 이 문제를 해결하려면 일치하는 버전의 원격 디버깅 모니터를 다운로드하여 설치합니다. 원격 디버거의 올바른 버전을 얻으려면 [원격 디버깅](../debugger/remote-debugging.md)을 참조하십시오.

### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>로컬 및 원격 컴퓨터의 인증 모드가 서로 다름
 로컬 및 원격 컴퓨터에서 동일한 인증 모드를 사용해야 합니다. 이 문제를 해결하려면 두 컴퓨터에서 모두 동일한 인증 모드를 사용 중인지 확인합니다. 인증 모드를 변경할 수 있습니다. 원격 디버거 창에서 **옵션 >** 도구 대화 상자로 이동합니다.

 인증 모드에 대한 자세한 내용은 [Windows 인증 개요](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11))를 참조하세요.

### <a name="anti-virus-software-is-blocking-the-connections"></a>바이러스 백신 소프트웨어가 연결을 차단함
 Windows 바이러스 백신 소프트웨어는 원격 디버거 연결을 허용하지만 일부 타사 바이러스 백신 소프트웨어가 차단할 수도 있습니다. 이러한 연결을 허용하는 방법을 알아보려면 해당 바이러스 백신 소프트웨어에 대한 설명서를 확인합니다.

### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>네트워크 보안 정책에서 원격 컴퓨터와 Visual Studio 간의 통신을 차단함
 네트워크 보안을 검토하여 통신을 차단하지 않는지 확인합니다. Windows 네트워크 보안 정책에 대한 자세한 내용은 [보안 정책 설정을](/windows/device-security/security-policy-settings/security-policy-settings)참조하십시오.

### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>네트워크 사용량이 너무 많아 원격 디버깅을 지원할 수 없음
 다른 시간에 원격 디버깅을 수행하거나 다른 시간에 네트워크 작업을 다시 예약해야 할 수도 있습니다.

## <a name="more-help"></a>자세한 도움말
 원격 디버거 도움말을 추가하려면 원격 디버거 의 도움말 페이지(원격 디버거에서**사용 > 도움말)를** 엽니다.

## <a name="see-also"></a>참고 항목
- [원격 디버깅](../debugger/remote-debugging.md)
