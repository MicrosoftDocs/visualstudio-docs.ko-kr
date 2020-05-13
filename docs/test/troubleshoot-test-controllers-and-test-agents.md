---
title: 테스트 컨트롤러 및 테스트 에이전트 문제 해결
ms.date: 10/20/2016
ms.topic: troubleshooting
helpviewer_keywords:
- load tests, test controllers
- load tests, troubleshooting
- load tests, test agents
- troubleshooting, test controllers and agents in load tests
ms.assetid: 77329348-3a5d-43de-b6cb-90f93296a081
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 51d7e15ec71eec7134dfc49b3515385970e593a0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565957"
---
# <a name="strategies-for-troubleshooting-test-controllers-and-test-agents-in-load-tests"></a>부하 테스트에서 테스트 컨트롤러 및 테스트 에이전트 문제를 해결하기 위한 전략

이 토픽에서는 Visual Studio에서 테스트 컨트롤러 및 테스트 에이전트로 작업할 때 발생할 수 있는 몇 가지 일반적인 문제에 대해 설명합니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="unable-to-collect-performance-counters-on-test-agent-computer"></a>테스트 에이전트 컴퓨터에서 성능 카운터를 수집할 수 없음

부하 테스트를 실행할 때 테스트 에이전트 컴퓨터에 연결하여 성능 카운터를 수집하려고 하면 오류가 발생하는 경우가 있습니다. 성능 카운터 데이터를 원격 컴퓨터에 제공하는 서비스는 원격 레지스트리 서비스입니다. 일부 운영 체제에서는 원격 레지스트리 서비스가 자동으로 시작되지 않습니다. 이 문제를 해결하려면 원격 레지스트리 서비스를 수동으로 시작하십시오.

> [!NOTE]
> **제어판**에서 원격 레지스트리 서비스에 액세스할 수 있습니다. **관리 도구**를 선택한 다음, **서비스**를 선택합니다.

성능 카운터를 읽는 데 필요한 권한이 부족하여 이 문제가 발생할 수도 있습니다. 테스트를 로컬에서 실행하는 경우 테스트를 실행하는 사용자의 계정이 Power Users 그룹 또는 보다 권한이 많은 그룹이나 Performance Monitor Users 그룹에 속해 있어야 합니다. 테스트를 원격에서 실행하는 경우 컨트롤러 실행 자격으로 구성된 계정이 Power Users 그룹 또는 보다 권한이 많은 그룹이나 Performance Monitor Users 그룹에 속해 있어야 합니다.

## <a name="set-the-logging-level-on-a-test-controller-computer"></a>테스트 컨트롤러 컴퓨터의 로깅 수준 설정

테스트 컨트롤러 컴퓨터의 로깅 수준을 제어할 수 있습니다. 이 기능은 환경에서 부하 테스트를 실행하면서 문제를 진단할 때 유용합니다.

### <a name="to-set-the-logging-level-on-a-test-controller-computer"></a>테스트 컨트롤러 컴퓨터의 로깅 수준을 설정하려면

1. 테스트 컨트롤러 서비스를 중지합니다. 명령 프롬프트에서 `net stop vsttcontroller`를 입력합니다.

2. *QTController.exe.config* 파일을 엽니다. 이 파일은 컨트롤러 설치 디렉터리에 있습니다.

3. 파일의 시스템 진단 섹션에서 `EqtTraceLevel` 스위치 항목을 편집합니다. 코드는 다음과 비슷합니다.

    ```xml
    <system.diagnostics>
        <trace autoflush="true" indentsize="4">
            <listeners>
                <add name="myListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="d:\VSTestHost.log" />
            </listeners>
        </trace>
        <switches>
            <!-- You must use integral values for "value":
                    0 = off,
                    1 = error,
                    2 = warn,
                    3 = info,
                    4 = verbose. -->
            <add name="EqtTraceLevel" value="4" />
        </switches>
    </system.diagnostics>
    ```

4. 파일을 저장합니다.

5. 컨트롤러 서비스를 시작합니다. 명령 프롬프트에서 `net start vsttcontroller`를 입력합니다.

이 내용은 테스트 컨트롤러, 테스트 에이전트 서비스 및 테스트 에이전트 프로세스에 적용됩니다. 문제를 진단할 때는 세 가지 프로세스 모두에 로깅을 사용하는 것이 좋습니다. 로깅 수준을 설정하는 절차는 앞에서 테스트 컨트롤러를 대상으로 설명한 내용과 같으며 세 가지 프로세스에서 모두 동일합니다. 테스트 에이전트 서비스 및 에이전트 프로세스의 로깅 수준을 설정하려면 다음 구성 파일을 사용합니다.

- *QTController.exe.config* 컨트롤러 서비스

- *QTAgentService.exe.config* 에이전트 서비스

- 32비트 아키텍처의 경우 *QTDCAgent(32).exe.config* 에이전트 데이터 어댑터 프로세스

- 64비트 아키텍처의 경우 *QTDCAgent(64).exe.config* 에이전트 데이터 어댑터 프로세스

- 32비트 아키텍처의 경우 *QTAgent(32).exe.config* 에이전트 테스트 프로세스

- 64비트 아키텍처의 경우 *QTAgent(64).exe.config* 에이전트 테스트 프로세스

## <a name="bind-a-test-controller-to-a-network-adapter"></a>테스트 컨트롤러를 네트워크 어댑터에 바인딩

테스트 에이전트를 설치할 때 다음 오류가 발생할 수 있습니다.

**오류 8110. 지정된 컨트롤러 컴퓨터에 연결하거나 컨트롤러 개체에 액세스할 수 없습니다.**

네트워크 어댑터가 둘 이상인 컴퓨터에 테스트 컨트롤러를 설치하는 경우 이 오류가 발생할 수 있습니다.

> [!NOTE]
> 테스트 에이전트가 정상적으로 설치된 후 테스트를 실행할 때 비로소 이 문제가 발생할 수도 있습니다.

이 오류를 해결하려면 테스트 컨트롤러를 네트워크 어댑터 중 하나에 바인딩해야 합니다. 테스트 컨트롤러의 `BindTo` 속성을 설정한 다음 이름 대신 IP 주소에 따라 테스트 컨트롤러를 참조하도록 테스트 에이전트를 변경해야 합니다. 다음 절차에서는 이러한 단계를 보여 줍니다.

### <a name="to-obtain-the-ip-address-of-the-network-adapter"></a>네트워크 어댑터의 IP 주소를 가져오려면

1. **시작**을 선택한 다음, **실행**을 선택합니다.

     **실행** 대화 상자가 표시됩니다.

2. `cmd`를 입력한 다음, **확인**을 선택합니다.

     명령 프롬프트가 열립니다.

3. `ipconfig /all`을 입력합니다.

     네트워크 어댑터의 IP 주소가 표시됩니다. 컨트롤러를 바인딩할 네트워크 어댑터의 IP 주소를 기록해 둡니다.

### <a name="to-bind-a-test-controller-to-a-network-adapter"></a>테스트 컨트롤러를 네트워크 어댑터에 바인딩하려면

1. 테스트 컨트롤러 서비스를 중지합니다. 명령 프롬프트에서 `net stop vsttcontroller`를 입력합니다.

2. *QTController.exe.config* 파일을 엽니다. 이 파일은 *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*에 위치합니다.

3. 애플리케이션 설정에 `BindTo` 속성 항목을 추가합니다. 컨트롤러를 바인딩할 네트워크 어댑터의 IP 주소를 지정합니다. 코드는 다음과 비슷합니다.

    ```xml
    <appSettings>
        <add key="LogSizeLimitInMegs" value="20" />
        <add key="AgentSyncTimeoutInSeconds" value="120" />
        <add key="ControllerServicePort" value="6901" />
        <add key="ControllerUsersGroup" value="TeamTestControllerUsers" />
        <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins" />
        <add key="CreateTraceListener" value="no" />
        <add key="BindTo" value="<YOUR IP ADDRESS>" />
    </appSettings>
    ```

4. 파일을 저장합니다.

5. 테스트 컨트롤러 서비스를 시작합니다. 명령 프롬프트에서 `net start vsttcontroller`를 입력합니다.

### <a name="to-connect-a-test-agent-to-a-bound-controller"></a>바인딩된 컨트롤러에 테스트 에이전트를 연결하려면

- 테스트 에이전트 설치를 다시 실행합니다. 이번에는 테스트 컨트롤러 이름 대신 테스트 컨트롤러의 IP 주소를 지정합니다.

이 내용은 테스트 컨트롤러, 테스트 에이전트 서비스 및 테스트 에이전트 프로세스에 적용됩니다. 네트워크 어댑터가 둘 이상인 컴퓨터에서 실행되는 프로세스마다 `BindTo` 속성을 설정해야 합니다. `BindTo` 속성을 설정하는 절차는 앞에서 테스트 컨트롤러를 대상으로 설명한 내용과 같으며 세 가지 프로세스에서 모두 동일합니다. 테스트 에이전트 서비스 및 테스트 에이전트 프로세스의 로깅 수준을 설정하려면 [테스트 컨트롤러 컴퓨터의 로깅 수준 설정](#set-the-logging-level-on-a-test-controller-computer)에 나열된 구성 파일을 사용합니다.

## <a name="see-also"></a>참조

- [테스트 컨트롤러 및 테스트 에이전트](../test/configure-test-agents-and-controllers-for-load-tests.md)
