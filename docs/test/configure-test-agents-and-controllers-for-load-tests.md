---
title: 부하 테스트를 위한 테스트 에이전트/테스트 컨트롤러 구성
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, test agents and controllers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fe6811f4deaa5958b050a8f93f74e48e2dc73f38
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809291"
---
# <a name="overview-of-test-agents-and-test-controllers-for-running-load-tests"></a>부하 테스트 실행에 대한 테스트 에이전트 및 테스트 컨트롤러 개요

Visual Studio 는 실제 또는 가상 머신을 사용하여 앱에 대해 시뮬레이션된 부하를 생성할 수 있습니다. 이러한 컴퓨터는 단일 테스트 컨트롤러와 하나 이상의 테스트 에이전트로 설정되어야 합니다. 테스트 컨트롤러 및 테스트 에이전트를 사용하여 단일 컴퓨터에서 생성하는 것보다 많은 부하를 생성할 수 있습니다.

> [!NOTE]
> 또한 클라우드 기반 부하 테스트를 사용하여 동시에 웹 사이트에 액세스하는 여러 사용자의 부하를 생성하는 가상 머신을 제공할 수 있습니다. 그러나 클라우드 호스팅 가상 머신에서 테스트 컨트롤러/테스트 에이전트 설치를 사용하는 것은 지원되지 않습니다. [Azure Test Plans를 사용하여 부하 테스트 실행](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts)에서 클라우드 기반 부하 테스트에 대해 자세히 알아보세요.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-simulation-architecture"></a>부하 시뮬레이션 아키텍처

부하 시뮬레이션 아키텍처는 Visual Studio 클라이언트, 테스트 컨트롤러 및 테스트 에이전트로 구성됩니다.

- 클라이언트는 테스트를 개발하고 테스트를 실행하며 테스트 결과를 확인하는 데 사용됩니다.

- 테스트 컨트롤러는 테스트 에이전트를 관리하고 테스트 결과를 수집하는 데 사용됩니다.

- 테스트 에이전트는 테스트를 실행하는 데 사용되며 테스트 설정에 정의된 시스템 정보 및 ASP.NET 프로파일링 데이터를 비롯한 데이터를 수집합니다.

이 아키텍처는 다음과 같은 이점을 제공합니다.

- 테스트 컨트롤러에 테스트 에이전트를 더 추가하여 부하 생성 확장

- 동일한 컴퓨터나 다른 컴퓨터에서 클라이언트, 테스트 컨트롤러 및 테스트 에이전트 소프트웨어를 설치할 수 있는 유연성 다음은 그 예입니다.

   **로컬 구성:**

  - 컴퓨터1: Visual Studio, 컨트롤러, 에이전트

    ![컨트롤러 및 에이전트를 사용하는 로컬 컴퓨터](./media/load-test-configa.png)

    **일반 원격 구성:**

  - 컴퓨터1 및 컴퓨터2: Visual Studio(여러 테스터가 같은 컨트롤러를 사용할 수 있음)

  - 컴퓨터3: 컨트롤러(여기에도 에이전트가 설치되어 있을 수 있음)

  - 컴퓨터4-n: 컴퓨터3의 컨트롤러와 모두 연결된 에이전트

    ![컨트롤러 및 에이전트를 사용하는 원격 컴퓨터](./media/load-test-configb.png)

테스트 컨트롤러는 일반적으로 여러 테스트 에이전트를 관리하지만 하나의 에이전트는 단일 컨트롤러와만 연결될 수 있습니다. 개발자 팀에서 각 테스트 에이전트를 공유할 수 있습니다. 이 아키텍처를 사용하면 테스트 에이전트의 수를 쉽게 늘릴 수 있으므로 더 큰 부하를 생성할 수 있습니다.

## <a name="test-agent-and-test-controller-interaction"></a>테스트 에이전트 및 테스트 컨트롤러 상호 작용

테스트 컨트롤러는 테스트를 실행하기 위한 테스트 에이전트 집합을 관리합니다. 테스트 컨트롤러는 테스트 에이전트와 통신하여 테스트를 시작 또는 중지하고 테스트 에이전트 상태를 추적하거나 테스트 결과를 수집합니다.

### <a name="test-controller"></a>테스트 컨트롤러

테스트 컨트롤러는 테스트 실행을 위한 일반적인 아키텍처를 제공하고 부하 테스트 실행을 위한 특수 기능을 포함합니다. 테스트 컨트롤러는 모든 테스트 에이전트에서 부하 테스트를 보내고 모든 테스트 에이전트가 테스트를 초기화할 때까지 기다립니다. 모든 테스트 에이전트가 준비되면 테스트 컨트롤러는 테스트 에이전트에 메시지를 보내 테스트를 시작합니다.

### <a name="test-agent"></a>테스트 에이전트

테스트 에이전트는 테스트 컨트롤러의 새 테스트 시작 요청을 수신하는 서비스로 실행됩니다. 테스트 에이전트가 요청을 받으면 테스트 에이전트 서비스에서 테스트를 실행하는 프로세스를 시작합니다. 각 테스트 에이전트는 같은 부하 테스트를 실행합니다.

관리자가 테스트 에이전트에 가중치를 할당하고 테스트 에이전트의 가중치에 따라 부하가 분산됩니다. 예를 들어 테스트 에이전트 1에는 가중치 30이 부여되고 테스트 에이전트 2에는 가중치 70이 부여되고 부하가 1,000명의 사용자로 설정되면 테스트 에이전트 1은 300명의 가상 사용자를 시뮬레이트하지만 테스트 에이전트 2는 700명의 가상 사용자를 시뮬레이트하게 됩니다. [Visual Studio를 사용하여 테스트 컨트롤러 및 테스트 에이전트 관리](../test/manage-test-controllers-and-test-agents.md)를 참조하세요.

테스트 에이전트는 테스트 집합 및 시뮬레이션 매개 변수 집합을 입력으로 사용합니다. 주요 개념은 테스트를 실행하는 컴퓨터에 대해 테스트가 독립적이라는 점입니다.

## <a name="test-controller-and-test-agent-connection-points"></a>테스트 컨트롤러 및 테스트 에이전트 연결 지점

다음 그림에서는 테스트 컨트롤러, 테스트 에이전트 및 클라이언트 간의 연결 지점을 보여 줍니다. 이 그림에서는 들어오는 연결과 나가는 연결에 사용되는 포트와 이러한 포트에 사용되는 보안 제한 사항을 간략하게 보여 줍니다.

![테스트 컨트롤러와 테스트 에이전트 포트 및 보안](./media/test-controller-agent-firewall.png)

자세한 내용은 [테스트 컨트롤러 및 테스트 에이전트용 포트 구성](../test/configure-ports-for-test-controllers-and-test-agents.md)을 참조하세요.

## <a name="test-controller-and-agent-installation-information"></a>테스트 컨트롤러 및 에이전트 설치 정보

테스트 컨트롤러 및 테스트 에이전트에 대한 하드웨어 및 소프트웨어 요구 사항, 설치 절차 및 최적의 성능을 위한 환경 구성에 대한 중요 정보는 [테스트 에이전트 설치 및 구성](../test/lab-management/install-configure-test-agents.md)을 참조하세요.

## <a name="use-the-test-controller-and-test-agent-with-unit-tests"></a>단위 테스트에서 테스트 컨트롤러 및 테스트 에이전트 사용

테스트 컨트롤러와 하나 이상의 에이전트를 설치한 다음에는 부하 테스트를 위한 테스트 설정에서 테스트 컨트롤러에 원격 실행을 사용할지 여부를 지정할 수 있습니다. 또한 테스트 설정의 에이전트와 연결된 역할에 사용할 데이터 및 진단 어댑터를 지정할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [테스트 에이전트 설치 및 구성](../test/lab-management/install-configure-test-agents.md)
