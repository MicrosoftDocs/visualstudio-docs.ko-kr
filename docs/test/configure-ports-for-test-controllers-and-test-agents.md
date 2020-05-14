---
title: 테스트 컨트롤러 및 테스트 에이전트 포트 구성
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- firewalls, configuring for test agents
- firewalls, configuring for test controllers
- test agents, firewalls
- test controllers, firewalls
- agents, firewalls
- controllers, firewalls
ms.assetid: 211edbd7-9fe4-4251-ba85-8bec4363261b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2228f5ac4dce4743fa6dafbb321f0106b5d6cc11
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595945"
---
# <a name="configure-ports-for-test-controllers-and-test-agents"></a>테스트 컨트롤러 및 테스트 에이전트 포트 구성

테스트 컨트롤러, 테스트 에이전트 및 클라이언트에 기본적으로 사용되는 들어오는 포트를 변경할 수 있습니다. 테스트 컨트롤러, 테스트 에이전트 또는 클라이언트를 포트 설정이 충돌하는 다른 소프트웨어와 함께 사용하려는 경우 포트를 변경해야 할 수 있습니다. 테스트 컨트롤러와 클라이언트 간의 방화벽 제한으로 인해 포트를 변경해야 할 수도 있습니다. 이 경우 테스트 컨트롤러에서 클라이언트로 결과를 보낼 수 있게 하기 위해 방화벽에 대해 해당 포트를 허용하도록 수동으로 구성할 수 있습니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

다음 그림에서는 테스트 컨트롤러, 테스트 에이전트 및 클라이언트 간의 연결 지점을 보여 줍니다. 이 그림에서는 들어오는 연결과 나가는 연결에 사용되는 포트와 이러한 포트에 사용되는 보안 제한 사항을 간략하게 보여 줍니다.

![테스트 컨트롤러와 테스트 에이전트 포트 및 보안](../test/media/test-controller-agent-firewall.png)

## <a name="incoming-connections"></a>들어오는 연결

테스트 컨트롤러에 사용되는 기본 포트는 6901이고 테스트 에이전트의 기본 포트는 6910입니다. 클라이언트에서는 기본적으로 테스트 컨트롤러로부터 테스트 결과를 받는 데 사용되는 임의의 포트를 사용합니다. 테스트 컨트롤러에서는 들어오는 모든 연결에 대해 발신자를 인증하고 해당 발신자가 특정 보안 그룹에 속하는지 확인합니다.

- **테스트 컨트롤러** 들어오는 연결에는 TCP 포트 6901이 사용됩니다. 필요한 경우 수신 포트를 구성할 수 있습니다. 자세한 내용은 [수신 포트 구성](#configure-the-incoming-ports)을 참조하세요.

    테스트 컨트롤러에서는 테스트 에이전트와 클라이언트로 나가는 연결을 만들 수 있어야 합니다.

    > [!NOTE]
    > 테스트 컨트롤러에서 들어오는 **파일 및 프린터 공유** 연결이 열려 있어야 합니다.

- **테스트 에이전트** 들어오는 연결에는 TCP 포트 6910이 사용됩니다. 필요한 경우 수신 포트를 구성할 수 있습니다. 자세한 내용은 [수신 포트 구성](#configure-the-incoming-ports)을 참조하세요.

   테스트 에이전트에서는 테스트 컨트롤러로 나가는 연결을 만들 수 있어야 합니다.

- **클라이언트** 기본적으로 들어오는 연결에는 임의의 TCP 포트가 사용됩니다. 필요한 경우 수신 포트를 구성할 수 있습니다. 자세한 내용은 [수신 포트 구성](#configure-the-incoming-ports)을 참조하세요.

   테스트 컨트롤러에서 클라이언트에 처음으로 연결할 때는 방화벽 알림이 표시될 수 있습니다.

   Windows Server 2008에서는 방화벽 알림이 기본적으로 해제되어 있으므로 들어오는 연결을 허용할 수 있도록 클라이언트 프로그램(*devenv.exe*, *mstest.exe*, *mlm.exe*)에 대한 방화벽 예외를 수동으로 추가해야 합니다.

## <a name="outgoing-connections"></a>나가는 연결

나가는 모든 연결에는 임의의 TCP 포트가 사용됩니다.

- **테스트 컨트롤러** 테스트 컨트롤러에서는 에이전트와 클라이언트로 나가는 연결을 만들 수 있어야 합니다.

- **테스트 에이전트** 테스트 에이전트에서는 컨트롤러로 나가는 연결을 만들 수 있어야 합니다.

- **클라이언트** 클라이언트에서는 컨트롤러로 나가는 연결을 만들 수 있어야 합니다.

## <a name="configure-the-incoming-ports"></a>수신 포트 구성

테스트 컨트롤러와 테스트 에이전트에 대한 포트를 구성하려면 다음 지침에 따르십시오.

- **컨트롤러 서비스** *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config* 파일을 편집하여 포트의 값을 수정합니다.

    ```xml
    <appSettings>
      <add key="ControllerServicePort" value="6901"/>
    </appSettings>
    ```

- **에이전트 서비스** *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTAgentService.exe.config* 파일을 편집하여 포트를 수정합니다.

    ```xml
    <appSettings>
      <add key="AgentServicePort" value="6910"/>
    </appSettings>
    ```

- **클라이언트** 레지스트리 편집기를 사용하여 다음 레지스트리(**DWORD**) 값을 추가합니다. 클라이언트에서는 테스트 컨트롤러로부터 데이터를 받기 위해 지정된 범위의 포트 중 하나를 사용합니다.

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeStart**

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeEnd**

## <a name="see-also"></a>참고 항목

- [테스트 에이전트 설치 및 구성](../test/lab-management/install-configure-test-agents.md)
