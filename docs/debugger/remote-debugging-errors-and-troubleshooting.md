---
title: 원격 디버깅 오류 및 문제 해결 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, errors
- debugging errors
- remote debugging, troubleshooting
- troubleshooting remote debugging
- errors [debugger], remote debugging
- remote debugging, errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b413ce193e6761d515de5bc5ef30fae8e18a3a3
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301070"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>원격 디버깅 오류 및 문제 해결

원격으로 디버깅을 시도할 때 다음과 같은 오류가 발생할 수 있습니다.

- [오류: 서버에 대해 자동으로 한 단계씩 코드를 실행할 수 없습니다.](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [오류: Microsoft Visual Studio 원격 디버깅 모니터(MSVSMON.EXE)가 원격 컴퓨터에서 실행 중인 것 같지 않습니다.](error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running.md)

- [Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [오류: 원격 컴퓨터는 원격 연결 대화 상자에 표시되지 않습니다.](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>원격 디버거를 관리자로 실행

원격 디버거를 관리자로 실행하지 않으면 문제가 발생할 수 있습니다. 예를 들어 다음과 같은 오류가 표시될 수 있습니다. EXE)는 이 프로세스를 디버깅할 수 있는 권한이 부족합니다." 원격 디버거를 서비스가 아닌 응용 프로그램으로 실행하는 경우 [다른 사용자 계정](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md) 오류가 표시될 수 있습니다.

### <a name="when-running-the-remote-debugger-as-a-service"></a>원격 디버거를 서비스로 실행할 때

원격 디버거를 s 서비스로 실행할 때는 다음과 같은 몇 가지 이유로 관리자로 실행하는 것이 좋습니다.

- 원격 디버거 서비스는 관리자의 연결만 허용하므로 관리자로 실행하여 새로운 보안 위험이 **발생하지 않습니다.**

- Visual Studio 사용자가 원격 디버거 자체보다 프로세스를 디버깅할 권한이 더 많은 경우 발생하는 오류를 방지할 수 있습니다.

- 원격 디버거의 설정 및 구성을 단순화합니다.

원격 디버거를 관리자로 실행하지 않고 디버깅할 수 있지만 이 작업을 올바르게 수행하려면 몇 가지 요구 사항이 있으며 고급 서비스 구성 단계가 필요한 경우가 많습니다.

- 원격 컴퓨터에서 사용 중인 계정에 서비스 **권한으로 로그온해야** 합니다. 오류 문서를 [다시 연결할 수 없음의](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md) "로그온을 서비스로 추가하려면" 단계를 참조하십시오.

- 계정에는 대상 프로세스를 디버깅할 수 있는 권한이 있어야 합니다. 이러한 권한을 얻으려면 디버깅할 프로세스와 동일한 계정에서 원격 디버거를 실행해야 합니다. 더 쉬운 대안은 관리자로 서비스를 실행하는 것입니다. 

- 계정은 네트워크를 통해 Visual Studio 컴퓨터에 다시 연결할 수 있어야 합니다(즉, 인증). 도메인에서 원격 디버거가 기본 제공 로컬 시스템 또는 네트워크 서비스 계정 또는 도메인 계정에서 실행 중인 경우 다시 연결하는 것이 더 쉽습니다. 기본 제공 계정에는 보안 위험을 초래할 수 있는 높은 보안 권한이 있습니다.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>원격 디버거를 응용 프로그램으로 실행할 때(일반 모드)

일반 응용 프로그램과 같이 승격되지 않은 프로세스에 연결하려는 경우 원격 디버거를 관리자로 실행하는 경우에도 문제가 되지 않습니다.

다음과 같은 여러 시나리오에서 원격 디버거를 관리자로 실행하려고 합니다.

- 다른 사용자(예: IIS 디버깅 시)로 실행되는 프로세스에 연결하거나

- 다른 프로세스를 시작 하려고 하 고 시작 하려는 프로세스는 관리자입니다.

프로세스를 시작하려는 경우 관리자로 **실행하지** 않으려는 경우 시작하려는 프로세스가 관리자가 **아니어야** 합니다.

## <a name="see-also"></a>참고 항목
- [원격 디버깅](../debugger/remote-debugging.md)