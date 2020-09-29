---
title: 네트워크 어댑터에 테스트 컨트롤러/테스트 에이전트 바인딩
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- controllers, netwrok adapter
- agents, configuring
- agents, network adapter
- controllers, configuring
ms.assetid: 7eb9290a-f9f6-4e41-9caa-796fcfaf0610
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dc590973a0a98cd9c5108c9cfe44ea957073b313
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810300"
---
# <a name="how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter"></a>방법: 네트워크 어댑터에 테스트 컨트롤러 또는 테스트 에이전트 바인딩

테스트 컨트롤러 또는 테스트 에이전트 소프트웨어가 설치된 컴퓨터에 네트워크 어댑터가 여러 개 있으면 컴퓨터 이름 대신 IP 주소를 지정하여 테스트 컨트롤러나 테스트 에이전트를 식별해야 합니다.

> [!WARNING]
> 테스트 에이전트를 설치할 때 다음 오류가 발생할 수 있습니다.
>
> **오류 8110. 지정된 컨트롤러 컴퓨터에 연결하거나 컨트롤러 개체에 액세스할 수 없습니다**
>
> 네트워크 어댑터가 둘 이상인 컴퓨터에 테스트 컨트롤러를 설치하는 경우 이 오류가 발생할 수 있습니다. 에이전트가 정상적으로 설치된 후 테스트를 실행할 때 비로소 이 문제가 발생할 수도 있습니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="bind-a-test-controller-to-a-specific-network-adapter"></a>테스트 컨트롤러를 특정 네트워크 어댑터에 바인딩

### <a name="to-obtain-the-ip-addresses-of-the-network-adapters"></a>네트워크 어댑터의 IP 주소를 가져오려면

1. Microsoft Windows에서 **시작**을 선택하고 **검색 시작** 상자를 선택한 다음, **cmd**를 입력하고 **Enter** 키를 선택합니다.

2. **ipconfig /all**을 입력합니다.

     네트워크 어댑터의 IP 주소가 표시됩니다. 컨트롤러를 바인딩할 네트워크 어댑터의 IP 주소를 기록해 둡니다.

### <a name="to-bind-a-network-adapter-to-a-test-controller"></a>네트워크 어댑터를 테스트 컨트롤러에 바인딩하려면

1. Microsoft Windows에서 **시작**을 선택하고 **검색 시작** 상자를 선택한 다음, **services.msc**를 입력하고 **Enter** 키를 선택합니다.

     **서비스** 대화 상자가 표시됩니다.

2. 결과 창의 **이름** 열에서 **Visual Studio Test Controller** 서비스를 마우스 오른쪽 단추로 클릭하고 **중지**를 선택합니다.

     또는

     관리자 권한 명령 프롬프트를 열고 명령 프롬프트에서 다음 명령을 실행합니다.

     `net stop vsttcontroller`

3. *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\\\<edition>\Common7\IDE*에 있는 *QTCcontroller.exe.config* XML 구성 파일을 엽니다.

4. `<appSettings>` 태그를 찾습니다.

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

5. `BindTo` 키를 추가하여 `<appSettings>` 섹션에서 사용할 네트워크 어댑터를 지정합니다.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. 테스트 컨트롤러 서비스를 시작합니다. 이렇게 하려면 명령 프롬프트에서 다음 명령을 실행합니다.

    `net start vsttcontroller`

    > [!WARNING]
    > 컨트롤러에 테스트 에이전트를 연결하려면 테스트 에이전트 설치를 다시 실행해야 합니다. 이번에는 컨트롤러 이름 대신 컨트롤러의 IP 주소를 지정합니다.

     이 내용은 컨트롤러, 에이전트 서비스 및 에이전트 프로세스에 적용됩니다. 네트워크 어댑터가 둘 이상인 컴퓨터에서 실행되는 프로세스마다 `BindTo` 속성을 설정해야 합니다. `BindTo` 속성을 설정하는 절차는 이 항목의 앞에서 테스트 컨트롤러를 대상으로 설명한 내용과 같으며 세 가지 프로세스에서 모두 동일합니다.

### <a name="to-bind-a-network-interface-card-to-a-test-agent"></a>네트워크 인터페이스 카드를 테스트 에이전트에 바인딩하려면

1. Microsoft Windows에서 **시작**을 선택하고 **검색 시작** 상자를 선택한 다음, **services.msc**를 입력하고 **Enter** 키를 선택합니다.

    **서비스** 대화 상자가 표시됩니다.

2. 결과 창의 **이름** 열에서 **Visual Studio 테스트 에이전트** 서비스를 마우스 오른쪽 단추로 클릭하고 **중지**를 선택합니다.

     또는

     관리자 권한 명령 프롬프트를 열고 명령 프롬프트에서 다음 명령을 실행합니다.

     **net stop vsttagent**

3. *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\\\<edition>\Common7\IDE*에 있는 *QTAgentService.exe.config* XML 구성 파일을 엽니다.

4. `<appSettings>` 태그를 찾습니다.

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

5. `BindTo` 키를 추가하여 `<appSettings>` 섹션에서 사용할 네트워크 어댑터를 지정합니다.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. 테스트 에이전트 서비스를 시작합니다. 이렇게 하려면 명령 프롬프트에서 다음 명령을 실행합니다.

    `net start vsttagent`

## <a name="see-also"></a>참조

- [테스트 에이전트 설치 및 구성](../test/lab-management/install-configure-test-agents.md)
- [부하 테스트 로깅 설정 수정](../test/modify-load-test-logging-settings.md)
- [테스트 컨트롤러 및 테스트 에이전트 포트 구성](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [방법: 테스트 컨트롤러 및 테스트 에이전트의 시간 제한 기간 지정](../test/how-to-specify-timeout-periods-for-test-controllers-and-test-agents.md)
