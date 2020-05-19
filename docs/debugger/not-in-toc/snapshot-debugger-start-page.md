---
title: 스냅샷 디버거의 시작 페이지
ms.date: 07/14/2018
robots: noindex, nofollow
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf2aba33089623dc98a90c23166291bb2d6e7123
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905270"
---
# <a name="getting-started-with-the-snapshot-debugger"></a>스냅샷 디버거 시작

이제 Visual Studio 스냅샷 디버거는 서비스에 연결되며 디버깅을 지원하기 위해 스냅샷 수집을 시작할 수 있습니다.

스냅샷 디버거를 사용하려면 코드에서 일부 snappoint를 설정하고 단추를 클릭하여 스냅샷 수집을 시작한 후 시나리오를 실행합니다. snappoint를 설정한 코드를 실행하면 애플리케이션의 스냅샷이 생성됩니다. 그런 다음, 진단 도구 창에서 Visual Studio를 클릭하여 스냅샷을 엽니다. 이제 로컬의 경우처럼 서비스에서 스냅샷을 디버그할 수 있습니다. 자세한 지침은 계속 읽어 보세요.

## <a name="collect-and-view-snapshots"></a>스냅샷 수집 및 보기

스냅샷 디버거는 애플리케이션에서 스냅샷을 수집합니다. 스냅샷은 특정 시점의 애플리케이션의 사진과 비슷합니다. 코드에서 snappoint를 설정하여 스냅샷을 수집할 시점과 위치를 Visual Studio에 알립니다. 조사하고 있는 문제에 대한 스냅샷을 얻는 데 필요한 조건을 snappoint에서 설정합니다.

### <a name="set-a-snappoint"></a>snappoint 설정

1. 코드 편집기에서 snappoint를 설정하려는 코드 줄 옆의 왼쪽 제본용 여백을 클릭합니다. 실행 예정임을 알고 있는 코드인지 확인하세요.

    ![편집기에서 snappoint 설정](../media/snapshot-startpage-set-snappoint.png)

    왼쪽을 클릭하면 자주색 육각형이 표시됩니다.

2. **컬렉션 시작**을 클릭하여 snappoint를 켭니다.

### <a name="open-a-snapshot"></a>스냅샷 열기

1. snappoint가 적중되면 오른쪽 진단 도구 창에 스냅샷이 표시됩니다. 창이 열리지 않는 경우 **디버그** > **창** > **진단 도구 표시**를 선택하여 창을 열 수 있습니다.

    ![진단 도구 창의 스냅샷](../media/snapshot-startpage-diagsession-window.png)

2. 스냅샷을 두 번 클릭하여 엽니다.

### <a name="inspect-snapshot-data"></a>스냅샷 데이터 검사

이 보기에서 변수를 마우스로 가리켜 DataTips를 보고 로컬, 조사식 및 호출 스택 창을 사용하며 식을 계산할 수도 있습니다.

웹 사이트 자체는 계속 라이브 상태이며 최종 사용자는 영향을 받지 않습니다. 기본적으로 snappoint당 스냅샷 하나만 캡처됩니다. 즉, 스냅샷을 캡처한 후에는 snappoint가 꺼집니다. snappoint에서 또 하나의 스냅샷을 캡처하려면 **컬렉션 업데이트**를 클릭하여 snappoint를 다시 켤 수 있습니다.

### <a name="set-a-logpoint"></a>logpoint 설정

1. snappoint 아이콘(자주색 육각형)을 마우스 오른쪽 단추로 클릭하고 **설정**을 선택합니다.

2. **snappoint 설정** 창에서 **작업**을 선택합니다.

    ![snappoint 조건](../media/snapshot-startpage-logpoint.png)

3. **메시지** 필드에 기록할 로그 메시지를 입력합니다. 로그 메시지에서 변수를 중괄호 안에 배치하여 변수를 평가할 수도 있습니다.

    **출력 창으로 보내기**를 선택하는 경우 logpoint가 적중되면 진단 도구 창에 메시지가 표시됩니다.

    **애플리케이션 로그로 보내기**를 선택하는 경우 logpoint가 적중되면 App Insights와 같이 `System.Diagnostics.Trace`(또는 .NET Core에서는 `ILogger`)의 메시지를 볼 수 있는 모든 위치에 메시지가 표시됩니다.

## <a name="learn-more"></a>자세한 내용

스냅샷 디버거에 대한 자세한 내용은 [문서 페이지](../debug-live-azure-applications.md)에서 확인할 수 있습니다. 버그를 쉽게 찾을 수 있도록 조건을 설정하는 방법에 대해 자세히 알아보세요.

## <a name="dont-show-me-this-again"></a>다시 표시 안 함

스냅샷 디버거를 연결할 때 스냅샷 디버거 시작 페이지를 다시 표시하지 않으려면 **도구** > **옵션** > **스냅샷 디버거**에서 **세션을 시작할 때 ‘시작’ 페이지 표시** 옵션을 변경합니다.

![스냅샷 디버거 도구 옵션 페이지](../media/snapshot-startpage-tools-options.png)
