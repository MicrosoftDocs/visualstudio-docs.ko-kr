---
title: 테스트 컨트롤러 및 테스트 에이전트의 시간 제한 기간
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- agents, configuring
- agetns, timeouts
- controllers, configuring
- controllers, timeouts
ms.assetid: 777d0db5-0073-458a-a2a3-58b1c1f24c60
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7b06dc7d363cefd568a6e1432582744f486fa222
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287287"
---
# <a name="how-to-specify-timeout-periods-for-test-controllers-and-test-agents"></a>방법: 테스트 컨트롤러 및 테스트 에이전트의 시간 제한 기간 지정

테스트 컨트롤러와 테스트 에이전트 모두에는 모두 상호 간에 또는 데이터 소스로부터 응답을 받을 때까지 기다릴 시간을 지정하는 몇 가지 제한 시간 설정이 있으며 이 시간이 지나면 테스트가 실패하고 오류가 발생합니다. 경우에 따라 토폴로지 또는 다른 환경 문제의 요구 사항을 충족하기 위해 이 제한 시간 값을 편집해야 할 수 있습니다. 제한 시간 값을 편집하려면 다음 절차에서 설명하는 대로 테스트 컨트롤러나 테스트 에이전트와 연결된 XML 구성 파일을 편집합니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

테스트 컨트롤러 또는 테스트 에이전트의 다양한 제한 시간 설정을 편집하려면 아래 표의 키 이름 및 값을 사용하여 다음 구성 파일을 수정합니다.

- 테스트 컨트롤러: *QTController.exe.config*

    |키 이름|Description|값|
    |-|-----------------|-|
    |AgentConnectionTimeoutInSeconds|에이전트 ping 요청을 기다릴 시간(초)으로, 이후에는 연결이 끊어진 것으로 간주됩니다.|"n"초|
    |AgentSyncTimeoutInSeconds|동기화 테스트 실행을 시작할 때 모든 에이전트가 동기화되기를 기다릴 시간(초)으로, 이후에는 실행이 중단됩니다.|"n"초|
    |AgentInitializeTimeout|테스트 실행 시작 시 모든 에이전트 및 해당 데이터 수집기가 초기화되기를 기다릴 시간(초)으로, 이후에는 테스트 실행이 중단됩니다. 데이터 수집기를 사용하는 경우 이 값은 충분히 커야 합니다.|"n"초 기본값: "120"(2분)|
    |AgentCleanupTimeout|모든 에이전트 및 해당 데이터 수집기가 정리되기를 기다릴 시간(초)으로, 이후에는 테스트 실행이 완료됩니다. 데이터 수집기를 사용하는 경우 이 값은 충분히 커야 합니다.|"n"초 기본값: "120"(2분)|

- 테스트 에이전트: *QTAgentService.exe.config*

    |키 이름|Description|값|
    |-|-----------------|-|
    |ControllerConnectionPeriodInSeconds|컨트롤러에 연결을 시도할 간격을 나타내는 시간(초)입니다.|"n"초 기본값: "30"(30초)|
    |RemotingTimeoutSeconds|원격 호출이 지속될 수 있는 최대 시간(초)입니다.|"n"초 기본값: "600"(10분)|
    |StopTestRunCallTimeoutInSeconds|호출을 통해 테스트 실행이 중지되기를 기다릴 시간(초)입니다.|"n"초 기본값: "120"(2분)|
    |GetCollectorDataTimeout|데이터 수집기를 기다릴 시간(초)입니다.|"n"초 기본값: "300"(5분)|

## <a name="to-specify-agent-timeout-options-for-a-test-controller"></a>테스트 컨트롤러에 대한 에이전트 제한 시간 옵션을 지정하려면

1. *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*에 있는 *QTCcontroller.exe.config* XML 구성 파일을 엽니다.

2. `<appSettings>` 태그를 찾습니다.

    ```xml
    <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentConnectionTimeoutInSeconds" value="120"/>
      <add key="AgentSyncTimeoutInSeconds" value="300"/>
      <add key="ControllerServicePort" value="6901"/>
      <add key="ControllerUsersGroup" value="TeamTestControllerUsers"/>
      <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins"/>
      <add key="CreateTraceListener" value="no"/>
    </appSettings>
    ```

3. 테스트 컨트롤러의 제한 시간 키 중 하나에 대한 기존 값을 편집합니다. 예를 들어 `AgentConnectionTimeoutInSeconds` 키의 기본값을 2분에서 3분으로 변경할 수 있습니다.

    ```xml
    <add key="AgentConnectionTimeoutInSeconds" value="180"/>
    ```

    또는

    다른 키를 추가하고 제한 시간 값을 지정합니다. 예를 들어 `AgentInitializeTimeout` 섹션에 `<appSettings>` 키를 추가하고 해당 값을 5분으로 지정할 수 있습니다.

    ```xml
    <appSettings>
            <add key="AgentInitializeTimeout" value="300"/>
    </appSettings>
    ```

## <a name="to-specify-agent-timeout-options-for-a-test-agent"></a>테스트 에이전트에 대한 에이전트 제한 시간 옵션을 지정하려면

1. *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*에 있는 *QTAgentService.exe.config* XML 구성 파일을 엽니다.

2. `<appSettings>` 태그를 찾습니다.

    ```xml
    <appSettings>
      <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentServicePort" value="6910"/>
      <add key="ControllerConnectionPeriodInSeconds" value="30"/>
      <add key="StopTestRunCallTimeoutInSeconds" value="120"/>
      <add key="CreateTraceListener" value="no"/>
      <add key="GetCollectorDataTimeout" value="300"/>
    </appSettings>  </appSettings>
    ```

3. 테스트 에이전트의 제한 시간 키 중 하나에 대한 기존 값을 편집합니다. 예를 들어 `ControllerConnectionPeriodInSeconds` 키의 기본값을 30초에서 1분으로 변경할 수 있습니다.

    ```xml
    <add key="ControllerConnectionPeriodInSeconds" value="60"/>
    ```

    또는

    다른 키를 추가하고 제한 시간 값을 지정합니다. 예를 들어 `RemotingTimeoutSeconds` 섹션에 `<appSettings>` 키를 추가하고 해당 값을 15분으로 지정할 수 있습니다.

    ```xml
    <appSettings>
            <add key=" RemotingTimeoutSeconds " value="900"/>
    </appSettings>
    ```

## <a name="see-also"></a>참고 항목

- [테스트 에이전트 설치 및 구성](../test/lab-management/install-configure-test-agents.md)
- [부하 테스트 로깅 설정 수정](../test/modify-load-test-logging-settings.md)
- [테스트 컨트롤러 및 테스트 에이전트 포트 구성](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [방법: 네트워크 어댑터에 테스트 컨트롤러 또는 테스트 에이전트 바인딩](../test/how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter.md)
