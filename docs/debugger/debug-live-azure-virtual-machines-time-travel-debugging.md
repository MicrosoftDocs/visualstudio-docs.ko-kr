---
title: Azure VM의 시간 이동 디버깅 라이브 ASP.NET
description: 스냅샷 디버거를 사용하여 Azure Virtual Machines에서 라이브 ASP.NET 앱을 기록 및 재생하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 04/11/2019
ms.topic: how-to
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- aspnet
- azure
ms.openlocfilehash: eb0db0bab5295925f71a81645e64fdeb5f2077df
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809572"
---
# <a name="record-and-replay-live-aspnet-apps-on-azure-virtual-machines-using-the-snapshot-debugger"></a>스냅샷 디버거를 사용하여 Azure Virtual Machines에서 라이브 ASP.NET 앱 기록 및 재생

Visual Studio Enterprise의 TTD(시간 이동 디버깅) 미리 보기는 Azure VM(Virtual Machine)에서 실행되는 웹앱을 기록한 다음, 실행 경로를 정확히 재구성하고 재생하는 기능을 제공합니다. TTD는 스냅샷 디버거와 통합되며 원하는 횟수만큼 각 코드 줄을 되감거나 재생할 수 있으므로 프로덕션 환경에서만 발생할 수 있는 문제를 격리하고 식별하는 데 도움이 됩니다.

TTD 기록 캡처는 애플리케이션을 중지하지 않습니다. 그러나 TDD 기록은 실행 중인 프로세스에 상당한 오버헤드를 추가하여 프로세스 크기와 활성 스레드 수를 비롯한 여러 요소를 기준으로 속도를 늦춥니다.

이 기능은 Visual Studio 2019 릴리스의 미리 보기에서 Go Live 라이선스와 함께 제공됩니다.

이 자습서에서 다음을 수행합니다.

> [!div class="checklist"]
> * 시간 이동 디버깅을 사용하도록 설정한 상태로 스냅샷 디버거 시작
> * snappoint를 설정하고 시간 이동 기록 수집
> * 시간 이동 기록 디버깅 시작

## <a name="prerequisites"></a>사전 요구 사항

* Azure VM(Virtual Machines)에 대한 시간 이동 디버깅은 **Azure 개발 워크로드**가 포함된 Visual Studio 2019 Enterprise 이상에서만 사용할 수 있습니다. (**개별 구성 요소** 탭의 **디버깅 및 테스트** > **스냅샷 디버거**에서 찾을 수 있습니다.)

    아직 설치되지 않은 경우 [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/)를 설치하세요.

* 시간 이동 디버깅은 다음 Azure VM 웹앱에서 사용할 수 있습니다.
  * .NET Framework 4.8 이상에서 실행되는 ASP.NET 애플리케이션(AMD64)

## <a name="start-the-snapshot-debugger-with-time-travel-debugging-enabled"></a>시간 이동 디버깅을 사용하도록 설정한 상태로 스냅샷 디버거 시작

1. 시간 이동 기록을 수집할 프로젝트를 엽니다.

    > [!IMPORTANT]
    > TTD를 시작하려면 Azure VM 서비스에 게시된 것과 ‘동일한 버전의 소스 코드’를 열어야 합니다.

1. **디버그 &gt; 스냅샷 디버거 연결...** 을 선택합니다. 웹앱이 배포된 Azure VM 및 Azure 스토리지 계정을 선택합니다. **시간 이동 디버깅 사용** 미리 보기 옵션을 선택한 다음, **연결**을 클릭합니다.

      ![Azure 리소스 선택](../debugger/media/time-travel-debugging-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > 처음 VM의 **스냅샷 디버거 연결**을 선택하면 IIS가 자동으로 다시 시작됩니다.

    **모듈**에 대한 메타데이터는 처음에 활성화되지 않습니다. 웹앱으로 이동하면 **컬렉션 시작** 단추가 활성화됩니다. Visual Studio가 이제 스냅샷 디버깅 모드입니다.

   ![스냅샷 디버깅 모드](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > Application Insights 사이트 확장도 스냅샷 디버깅을 지원합니다. “사이트 확장이 최신 상태가 아님” 오류 메시지가 표시되면 [스냅샷 디버깅에 대한 문제 해결 팁 및 알려진 문제](../debugger/debug-live-azure-apps-troubleshooting.md)에서 업그레이드 세부 정보를 참조하세요.

   Azure VM의 모든 모듈이 로드되면 **모듈** 창에 표시됩니다(이 창을 열려면 **디버그 > 창 > 모듈** 선택).

   ![모듈 창 확인](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint-and-collect-a-time-travel-recording"></a>snappoint를 설정하고 시간 이동 기록 수집

1. 코드 편집기에서 snappoint를 설정하려는 메서드에서 왼쪽 제본용 여백을 클릭합니다. 실행 예정임을 알고 있는 코드인지 확인하세요.

   ![snappoint 설정](../debugger/media/time-travel-debugging-set-snappoint-settings.png)

1. snappoint 아이콘(속이 빈 공)을 마우스 오른쪽 단추로 클릭하고 **작업**을 선택합니다. **스냅샷 설정** 창에서 **작업** 확인란을 클릭합니다. 그런 다음, **이 메서드 종료 시점까지 시간 이동 기록을 수집하세요.** 확인란을 클릭합니다.

   ![메서드 끝까지 시간 이동 추적 수집](../debugger/media/time-travel-debugging-set-snappoint-action.png)

1. **컬렉션 시작**을 클릭하여 snappoint를 켭니다.

   ![snappoint 켜기](../debugger/media/snapshot-start-collection.png)

## <a name="take-a-snapshot"></a>스냅샷 가져오기

snappoint가 설정되어 있으면 snappoint가 배치된 코드 줄이 실행될 때마다 스냅샷을 캡처합니다. 이러한 실행은 서버의 실제 요청으로 인해 발생할 수도 있습니다. 강제로 snappoint가 적중되도록 하려면 웹 사이트의 브라우저 보기로 이동하여 snappoint가 적중되도록 하는 데 필요한 모든 작업을 수행하세요.

## <a name="start-debugging-a-time-travel-recording"></a>시간 이동 기록 디버깅 시작

1. snappoint가 적중되면 진단 도구 창에 스냅샷이 표시됩니다. 이 창을 열려면 **디버그 > Windows > 진단 도구 표시**를 선택합니다.

   ![snappoint 열기](../debugger/media/snapshot-diagsession-window.png)

1. 스냅샷 보기 링크를 클릭하여 코드 편집기에서 시간 이동 기록을 엽니다.
  
   **계속** 및 **반대로 계속 진행** 단추를 사용하면 TTD에서 기록한 모든 코드 줄을 실행할 수 있습니다. 또한 **디버그** 도구 모음에서 **다음 문 표시**, **한 단계씩 코드 실행**, **프로시저 단위 실행**, **프로시저 나가기**, **한 단계씩 뒤로 실행**, **뒤로 단위 실행**, **뒤로 프로시저 나가기** 등을 사용할 수 있습니다.

   ![디버깅 시작](../debugger/media/time-travel-debugging-step-commands.png)

   **로컬**, **좌식** 및 **호출 스택** 창을 사용할 수도 있으며 식을 계산할 수도 있습니다.

   ![스냅샷 데이터 검사](../debugger/media/time-travel-debugging-start-debugging.png)

    웹 사이트 자체는 계속 라이브 상태이며 최종 사용자는 후속 TTD 활동의 영향을 받지 않습니다. 기본적으로 snappoint당 하나의 스냅샷만 캡처됩니다. 하나의 스냅샷이 캡처되면 해당 snappoint가 꺼집니다. snappoint에서 또 하나의 스냅샷을 캡처하려면 **컬렉션 업데이트**를 클릭하여 snappoint를 다시 켤 수 있습니다.

**도움이 필요하세요?** [문제 해결 및 알려진 문제](../debugger/debug-live-azure-apps-troubleshooting.md)와 [스냅샷 디버깅 FAQ](../debugger/debug-live-azure-apps-faq.md) 페이지를 참조하세요.

## <a name="set-a-conditional-snappoint"></a>조건부 snappoint 설정

앱의 특정 상태를 다시 만들기 어려운 경우 조건부 snappoint 사용이 도움이 될 수 있는지 고려해보세요. 조건부 snappoint를 사용하면 검사하려는 특정 값이 변수에 포함되는 경우와 같이 앱이 원하는 상태가 될 때까지 시간 이동 기록이 수집되지 않도록 합니다. [조건은 식, 필터 또는 적중 횟수를 사용하여 설정할 수 있습니다](../debugger/debug-live-azure-apps-troubleshooting.md).

## <a name="next-steps"></a>다음 단계

이 자습서에서는 Azure Virtual Machines에 대한 시간 이동 기록을 수집하는 방법을 알아봤습니다. 스냅샷 디버거에 대한 자세한 정보를 알아볼 수 있습니다.

> [!div class="nextstepaction"]
> [스냅샷 디버깅 FAQ](../debugger/debug-live-azure-apps-faq.md)