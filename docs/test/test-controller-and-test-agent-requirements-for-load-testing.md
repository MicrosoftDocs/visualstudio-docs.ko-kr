---
title: 부하 테스트에 대한 테스트 컨트롤러 및 테스트 에이전트 요구 사항
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, requirements
- controllers, requirements
ms.assetid: 372d97ce-12e4-46a9-9863-da508adba68f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 39b174b0b134fdfdf26570565aa6aa756ba43c92
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588644"
---
# <a name="test-controller-and-test-agent-requirements-for-load-testing"></a>부하 테스트에 대한 테스트 컨트롤러 및 테스트 에이전트 요구 사항

단위, 웹 성능, 부하 및 수동 테스트를 포함한 여러 테스트 형식이 Visual Studio에 통합되었습니다. Visual Studio를 사용하면 Visual Studio 애플리케이션 수명 주기 관리 사용자가 테스트 컨트롤러와 하나 이상의 에이전트를 사용하여 원격 컴퓨터에서 테스트를 실행할 수 있습니다. [테스트 에이전트 설치 및 구성](../test/lab-management/install-configure-test-agents.md)을 참조하세요.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="hardware-and-software-requirements"></a>하드웨어 및 소프트웨어 요구 사항

테스트 컨트롤러 컴퓨터와 테스트 에이전트 컴퓨터 모두 고유의 하드웨어 및 소프트웨어 요구 사항이 있습니다. 또한 테스트 컨트롤러 및 테스트 에이전트 컴퓨터를 여러 언어로 배포하려면 이러한 언어를 지원할 방법을 계획해야 합니다.

### <a name="hardware-requirements"></a>하드웨어 요구 사항

다음 표에서는 테스트 컨트롤러와 테스트 에이전트를 배포하기 위한 권장 하드웨어 요구 사항을 보여 줍니다.

|**Configuration**|**구성 요소**|**CPU**|**HD**|**메모리**|
|-|-------------------|-|------------|-|
|가상 사용자 수 500명 미만|테스트 에이전트|2.6GHz|10 GB|2GB|
|가상 사용자 수 1000명 미만|테스트 에이전트|이중 프로세서 2.6GHz|10 GB|2GB|
|N x 가상 사용자 수 1000명|테스트 에이전트|각각 2.6Ghz의 이중 프로세서가 있는 N개의 에이전트로 확장|10GB|2GB|
|\< 테스트 환경에서 컴퓨터 수 30대 테스트 대상 서버와 에이전트 포함|Test Controller|2.6GHz|||
|테스트 환경의 컴퓨터 수 30대의 N배. 테스트 대상 서버와 에이전트 포함|Test Controller|N개의 2.6GHz 프로세서|||

> [!NOTE]
> 가상 사용자 수는 테스트에 따라 크게 달라집니다. 이러한 차이는 주로 *인지 시간*, 즉 사용자 지연에 차이가 있기 때문에 발생합니다. 자세한 내용은 [인지 시간을 편집하여 웹 사이트 사용자 상호 작용 지연 시뮬레이션](../test/edit-think-times-in-load-test-scenarios.md)을 참조하세요. 부하 테스트에서는 웹 테스트가 일반적으로 단위 테스트보다 더 효율적이며 더 많은 부하를 생성합니다. 앞의 표에 나온 숫자는 일반적인 웹 애플리케이션에서 인지 시간이 3~5초인 상태로 웹 테스트를 실행할 경우에 유효합니다.

여기에 나오는 지침은 하드웨어 계획을 위한 일반적인 지침으로 제공됩니다. 테스트 성능은 테스트 데이터의 양과 테스트 에이전트의 개수에 따라 크게 달라집니다. 테스트 에이전트의 경우 CPU 속도와 사용 가능한 메모리에 따라 테스트 부하가 제한됩니다. 테스트 컨트롤러에는 테스트 에이전트의 개수와 테스트에 포함되는 데이터의 양에 따라 더 많은 리소스가 필요합니다.

Visual Studio를 실행하는 서버는 네트워크에 안정적으로 연결되어야 합니다(최소 대역폭: 1Mbps, 최대 대기 시간: 350밀리초). 테스트 에이전트와 테스트 컨트롤러 사이에는 방화벽이 없어야 합니다. 테스트 성능이 기대치 이하인 경우에는 하드웨어 구성을 업그레이드하는 것이 좋습니다.

### <a name="additional-hardware-considerations"></a>추가 하드웨어 고려 사항

테스트 에이전트에서는 테스트 기간과 테스트 크기에 따라 테스트 컨트롤러에 많은 양의 데이터를 생성합니다. 일반적으로 24시간 동안의 테스트 데이터 양에 대해 10GB의 추가 하드 디스크 스토리지 공간을 계획해야 합니다.

중요한 서버에는 여기서 권장하는 하드웨어 외에도 중복 전원 공급 장치, 중복 팬 등의 추가 하드웨어를 사용하는 것이 좋습니다.

### <a name="language-requirements"></a>언어 요구 사항

혼동을 피하고 작업을 간소화하려면 컴퓨터의 운영 체제 및 Team Foundation Server와 동일한 언어를 사용하도록 테스트 컨트롤러 및 테스트 에이전트를 구성해야 합니다. 테스트 에이전트와 테스트 컨트롤러가 서로 다른 컴퓨터에 설치되어 있는 경우에는 동일한 언어를 사용하도록 구성해야 합니다. 그러나 Team Foundation Server 배포 언어와 일치하기만 면 다른 언어 버전의 Visual Studio를 영어 버전 운영 체제에 설치할 수도 있습니다.

## <a name="monitor-agent-resources"></a>에이전트 리소스 모니터링

에이전트 컴퓨터를 모니터링하면 테스트 중에 실행되고 늘어나거나 줄어든 *QTAgent\*.exe* 프로세스를 관찰함으로써 필요한 리소스를 결정할 수 있습니다. *QTAgent\*.exe* 프로세스의 가장 일반적인 병목 현상은 CPU 사용률입니다. CPU 사용률이 지속적으로 90퍼센트 이상을 유지한다면 에이전트의 현재 부하량이 많은 것입니다. 그 다음의 일반적인 병목 현상은 메모리 사용량입니다. 까다로운 테스트의 경우 이러한 리소스를 모니터링함으로써 컴퓨터 리소스를 늘려야 할지 또는 테스트를 다른 방법으로 배포해야 할지를 손쉽게 결정할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [테스트 에이전트 설치 및 구성](../test/lab-management/install-configure-test-agents.md)
