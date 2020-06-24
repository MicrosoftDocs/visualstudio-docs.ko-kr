---
title: 테스트 설정을 사용하여 네트워크 에뮬레이션 구성
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, network emulation
ms.assetid: ff275cfb-5df9-4710-9a91-9caabaaad34f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 55daa1e16af45c153efced3736c46c3c27d748ac
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288184"
---
# <a name="how-to-configure-network-emulation-using-test-settings-in-visual-studio"></a>방법: Visual Studio에서 테스트 설정을 사용하여 네트워크 에뮬레이션 구성

Visual Studio에서 다양한 네트워크 환경에 처한 애플리케이션을 테스트하도록 진단 데이터 어댑터를 구성할 수 있습니다. 테스트를 실행할 때 네트워크 부하나 병목 현상을 인위적으로 조작하고 그 결과를 테스트하도록 진단 데이터 어댑터를 구성할 수도 있습니다.

> [!WARNING]
> 에뮬레이트한 네트워크보다 속도가 느린 실제 네트워크 환경에서 테스트를 실행하는 경우 더 느린 네트워크 속도에서 테스트가 실행됩니다. 속도가 더 느린 네트워크 환경을 에뮬레이트할 수는 있지만 속도가 더 빠른 네트워크 환경은 에뮬레이트할 수 없습니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

::: moniker range="vs-2017"
다음 절차에서는 구성 편집기를 통해 네트워크 에뮬레이션을 구성하는 방법을 설명합니다. 이러한 단계는 Visual Studio 및 Microsoft Test Manager의 구성 편집기에 모두 적용됩니다.
::: moniker-end
::: moniker range=">=vs-2019"
다음 절차에서는 구성 편집기를 통해 네트워크 에뮬레이션을 구성하는 방법을 설명합니다. 이러한 단계는 Visual Studio의 구성 편집기에 적용됩니다.
::: moniker-end

> [!NOTE]
> 네트워크 에뮬레이션 진단 데이터 어댑터는 Visual Studio 테스트 설정에만 적용할 수 있습니다. Microsoft Test Manager(Visual Studio 2017에서 더 이상 사용되지 않음)의 테스트 설정에는 사용되지 않습니다.

::: moniker range="vs-2017"
네트워크 에뮬레이션에는 관리자 권한이 있는 계정을 사용해야 합니다. 수동 테스트를 실행하는 로컬 역할에 대해 네트워크 에뮬레이션을 선택한 경우 관리자 권한을 사용하여 Microsoft Test Manager를 시작해야 합니다. 다른 역할에 대해 네트워크 에뮬레이션을 선택한 경우에는 해당 역할의 컴퓨터에 있는 테스트 에이전트가 Administrators 그룹의 멤버인 사용자 계정을 사용하는지 확인해야 합니다. 테스트 에이전트의 계정을 설정하는 방법에 대한 자세한 내용은 [테스트 에이전트 설치 및 구성](../test/lab-management/install-configure-test-agents.md)을 참조하세요.
::: moniker-end

> [!NOTE]
> 테스트 에이전트의 기본 계정인 네트워크 서비스 계정은 Administrators 그룹의 멤버가 아닙니다.

**진정한 네트워크 에뮬레이션**

Visual Studio는 모든 테스트 형식에 소프트웨어 기반의 진정한 네트워크 에뮬레이션을 사용합니다. 여기에는 부하 테스트가 포함됩니다. 진정한 네트워크 에뮬레이션은 네트워크 패킷을 직접 조작하여 네트워크 조건을 시뮬레이션합니다. 진정한 네트워크 에뮬레이터는 이더넷과 같은 안정적인 물리적 링크를 사용하여 유선 및 무선 네트워크 모두의 동작을 에뮬레이트할 수 있습니다. 다음과 같은 네트워크 특성이 진정한 네트워크 에뮬레이션에 통합되어 있습니다.

- 네트워크 왕복 시간(대기 시간)

- 사용 가능한 대역폭 양

- 큐 동작

- 패킷 손실

- 패킷 순서 바꾸기

- 오류 전파

진정한 네트워크 에뮬레이션은 IP 주소 또는 프로토콜(예: TCP, UDP, ICMP)을 기준으로 네트워크 패킷을 유연하게 필터링할 수도 있습니다.

진정한 네트워크 에뮬레이션은 네트워크 기반 개발자 및 테스터가 원하는 테스트 환경을 에뮬레이트하거나, 성능을 평가하거나, 변경 효과를 예측하거나, 기술 최적화에 대한 결정을 내릴 때 사용할 수 있습니다. 하드웨어 테스트 베드와 비교했을 때 진정한 네트워크 에뮬레이션은 훨씬 비용이 적게 들고 유연한 솔루션입니다.

## <a name="configure-network-emulation-for-your-test-settings"></a>테스트 설정을 사용하여 네트워크 에뮬레이션 구성

이 절차의 단계를 수행하려면 먼저 Visual Studio에서 테스트 설정을 연 다음, **데이터 및 진단** 페이지를 선택해야 합니다.

### <a name="to-configure-network-emulation-for-your-test-settings"></a>테스트 설정을 사용하여 네트워크 에뮬레이션을 구성하려면

1. 특정 네트워크를 에뮬레이트하는 데 사용할 역할을 선택합니다.

    > [!NOTE]
    > 네트워크 에뮬레이션 어댑터는 클라이언트 역할 또는 서버 역할에만 구성해야 합니다. 이 두 역할에서 어댑터를 사용할 필요는 없습니다. 어댑터에서 두 역할 간 통신에 영향을 주는 네트워크 노이즈를 에뮬레이트하므로 두 역할에서 어댑터를 사용할 필요가 없습니다. 필요한 경우를 제외하고는 네트워크 에뮬레이션 어댑터의 클라이언트 역할을 선택하여 서버 역할에서 추가 오버헤드가 발생하지 않도록 해야 합니다.

2. **네트워크 에뮬레이션**을 선택하고 **구성**을 선택합니다.

     네트워크 에뮬레이션을 구성하기 위한 대화 상자가 나타납니다.

3. **사용할 네트워크 프로필 선택** 옆에 있는 화살표를 선택하고, 테스트를 실행할 때 에뮬레이트할 네트워크 형식(예: **Cable-DSL 768Kps**)을 선택합니다.

    > [!WARNING]
    > 에뮬레이트한 네트워크보다 속도가 느린 실제 네트워크 환경에서 테스트를 실행하는 경우 더 느린 네트워크 속도에서 테스트가 실행됩니다. 속도가 더 느린 네트워크 환경을 에뮬레이트할 수는 있지만 속도가 더 빠른 네트워크 환경은 에뮬레이트할 수 없습니다.

4. 테스트 설정에 네트워크 에뮬레이션 진단 데이터 어댑터를 포함하고 있는 경우 이 어댑터를 로컬 컴퓨터에서 사용하려면 네트워크 에뮬레이션 드라이버를 해당 컴퓨터의 네트워크 어댑터 중 하나에 바인딩해야 합니다. 네트워크 에뮬레이션 드라이버는 네트워크 에뮬레이션 진단 데이터 어댑터를 사용하는 데 필요합니다. 다음 두 가지 방법으로 네트워크 에뮬레이션 드라이버를 설치하고 어댑터에 바인딩합니다.

    - **Microsoft Visual Studio 테스트 에이전트와 함께 설치된 네트워크 에뮬레이션 드라이버:** Microsoft Visual Studio 테스트 에이전트는 원격 머신과 로컬 머신 모두에서 사용할 수 있습니다. Visual Studio Test Agent를 설치하는 경우 네트워크 에뮬레이션 드라이버를 네트워크 카드에 바인딩하는 구성 단계가 설치 프로세스에 포함됩니다. 자세한 내용은 [테스트 에이전트 설치 및 구성](../test/lab-management/install-configure-test-agents.md)을 참조하세요.

    - **Microsoft Visual Studio Test Professional과 함께 설치된 네트워크 에뮬레이션 드라이버:** 네트워크 에뮬레이션을 처음 사용하는 경우 네트워크 에뮬레이션 드라이버를 네트워크 카드에 바인딩하라는 메시지가 표시됩니다.

    > [!TIP]
    > 다음 명령을 사용하여 Visual Studio 테스트 에이전트를 설치하지 않고 로컬 머신의 명령줄에서 네트워크 에뮬레이션 드라이버를 설치할 수도 있습니다. **VSTestConfig NETWORKEMULATION /install**

## <a name="see-also"></a>참조

- [테스트 설정을 사용하여 진단 정보 수집](../test/collect-diagnostic-information-using-test-settings.md)
- [수동 테스트 실행(Azure Test Plans)](/azure/devops/test/run-manual-tests?view=vsts)
