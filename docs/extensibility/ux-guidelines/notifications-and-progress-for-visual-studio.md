---
title: 비주얼 스튜디오에 대한 알림 및 진행률 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f6a7ddd5d1a5a7257617b03098722e1341017b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699877"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Visual Studio의 알림 및 진행률
## <a name="notification-systems"></a><a name="BKMK_NotificationSystems"></a>알림 시스템

### <a name="overview"></a>개요
 사용자에게 소프트웨어 개발 작업에 대해 Visual Studio에서 어떤 일이 일어나고 있는지 알리는 방법에는 여러 가지가 있습니다.

 모든 종류의 알림을 구현할 때:

- 알림 수를 최소 유효 **수로 유지합니다.** 알림 메시지는 대부분의 Visual Studio 사용자 또는 특정 기능/기능 영역의 사용자에게 적용되어야 합니다. 알림의 과도한 사용은 사용자를 사이드 트랙 또는 시스템의 사용의 인식 용이성을 감소 시킬 수 있습니다.

- 사용자가 보다 복잡한 선택을 하고 추가 조치를 취하기 위해 적절한 컨텍스트를 호출하는 데 사용할 수 있는 **명확하고 실행 가능한 메시지를 표시해야 합니다.**

- **동기 및 비동기 메시지를 적절하게 표시합니다.** 동기 알림은 웹 서비스가 충돌하거나 코드 예외가 throw되는 경우와 같이 즉각적인 주의가 필요한 것을 나타냅니다. 사용자는 모달 대화 상자와 같이 입력이 필요한 방식으로 이러한 상황을 즉시 알려야 합니다. 비동기 알림은 빌드 작업이 완료되거나 웹 사이트 배포가 완료되는 경우와 같이 사용자가 알아야 하지만 즉시 조치를 취해야 하는 알림입니다. 이러한 메시지는 더 주변적이어야 하며 사용자의 작업 흐름을 중단하지 않아야 합니다.

- 사용자가 메시지를 승인하거나 대화 상자에 제시된 결정을 내리기 전에 **추가 작업을 수행하지 못하도록 필요한 경우에만 모달** 대화 상자를 사용합니다.

- **앰비언트 알림이 더 이상 유효하지 않을 때 제거합니다.** 사용자가 알림을 받은 문제를 해결하기 위해 이미 조치를 취한 경우 알림을 해제할 필요가 없습니다.

- **알림은 잘못된 상관 관계로 이어질 수 있습니다.** 사용자는 실제로 인과 관계가 없을 때 하나 이상의 작업이 알림을 트리거했다고 믿을 수 있습니다. 컨텍스트, 트리거 및 알림의 소스에 대한 알림 메시지에서 명확히 해야 합니다.

### <a name="choosing-the-right-method"></a>올바른 방법 선택
 이 표를 사용하여 사용자에게 메시지를 알리는 올바른 방법을 선택할 수 있습니다.

|방법|사용|사용 안 함|
|------------|---------|----------------|
|[모달 오류 메시지 대화 상자](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|계속하기 전에 사용자 응답이 필요한 경우에 사용합니다.|사용자를 차단하고 흐름을 중단할 필요가 없는 경우 사용하지 마십시오. 메시지를 덜 방해적인 방식으로 표시할 수 있는 경우 모달 대화 상자를 사용하지 마십시오.|
|[IDE 상태 표시줄](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|프로세스 의 상태에 관한 주변 텍스트 정보가 있는 경우에 사용합니다.|혼자 사용하지 마십시오. 다른 피드백 메커니즘과 함께 사용하는 것이 가장 좋습니다.|
|[포함된 정보 표시줄](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|도구 창 또는 문서 창에서 진행률, 오류 상태, 결과 및/또는 실행 가능한 정보를 알리는 데 사용합니다.|정보가 정보 표시줄이 배치된 위치와 관련이 없는 경우에는 사용하지 마십시오.<br /><br /> 문서/도구 창 밖에서는 사용하지 마십시오.|
|[마우스 커서 변경](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|프로세스가 진행 중임을 알리는 데 사용할 수 있습니다. 또한 드래그/드롭이 진행 중이거나 마우스 커서가 그리기 모드와 같은 특정 모드에 있는 경우와 같이 마우스에 상태 변경이 있음을 알리는 데사용됩니다.|짧은 진행률 변경이나 커서의 플러터가 발생할 가능성이 있는 경우(예: 전체 프로세스 대신 더 긴 실행 중인 프로세스의 일부에 묶일 경우) 사용하지 마십시오.|
|[진행 률 표시기](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|진행률(확정 또는 불확정)을 보고해야 하는 경우 사용합니다. 진행률 표시기 유형과 각각에 대한 특정 사용법이 다양합니다. [진행률 표시기를](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators)참조하십시오.||
|[Visual Studio 알림 창](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|알림 창은 공개적으로 확장할 수 없습니다. 그러나 라이선스에 대한 중요한 문제 및 Visual Studio 또는 패키지에 대한 업데이트에 대한 정보 알림을 포함하여 Visual Studio에 대한 다양한 메시지를 전달하는 데 사용됩니다.|다른 유형의 알림에는 사용하지 마십시오.|
|[오류 목록](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|문제가 문제가 현재 열려 있는 사용자 솔루션(오류/경고/정보)과 직접 관련이 있는 경우 코드에서 조치를 취해야 할 수 있습니다.<br /><br /> 여기에는 다음과 같은 것이 포함됩니다.<br /><br /> - 컴파일러 메시지 (오류 / 경고 / 정보)<br /><br /> - 코드 분석기 / 코드에 대한 진단 메시지<br /><br /> - 메시지 빌드<br /><br /> 프로젝트 또는 솔루션 파일과 관련된 문제에 적합할 수 있지만 먼저 솔루션 탐색기 표시를 고려하십시오.|사용자의 열린 솔루션 코드와 관계가 없는 항목에는 사용하지 마십시오.|
|편집기 알림: 전구|열려 있는 파일에 있는 문제를 해결할 수 있는 수정 프로그램이 있는 경우에 사용합니다.<br /><br /> 전구는 리팩터링과 같이 사용자 코드에서 수행되는 빠른 작업을 호스팅하는 데도 사용해야 하지만 이 경우 "알림 스타일"이 나타나지 않습니다.|열려 있는 파일과 관계가 없는 항목에는 사용하지 마십시오.|
|편집기 알림: 물결선|열려 있는 코드의 특정 범위(예: 오류에 대한 빨간색 물결선)에 대한 문제를 사용자에게 경고하는 데 사용합니다.|열려 있는 코드의 특정 범위와 관련이 없는 항목에는 사용하지 마십시오.|
|[임베디드 상태 표시줄](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|특정 도구 창, 문서 창 또는 대화 창의 컨텍스트 내에서 콘텐츠 또는 프로세스와 관련된 상태를 제공하는 데 사용합니다.|특정 창 내의 콘텐츠와 관련이 없는 일반 제품 알림, 프로세스 또는 항목에는 사용하지 마십시오.|
|[윈도우 트레이 알림](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|proc 외 프로세스 또는 컴패니언 응용 프로그램에 대한 알림을 표시하는 데 사용합니다.|IDE와 관련된 알림에는 사용하지 마십시오.|
|[알림 거품](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|원격 프로세스를 알리거나 IDE **외부에서** 변경하는 데 사용합니다.|IDE **내의** 프로세스를 사용자에게 알리기 위한 수단으로 사용하지 마십시오.|

### <a name="notification-methods"></a>알림 방법

#### <a name="modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a>모달 오류 메시지 대화 상자
 모달 오류 메시지 대화 상자는 사용자의 확인 또는 작업이 필요한 오류 메시지를 표시하는 데 사용됩니다.

 ![모달 오류 메시지](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901-01_ModalErrorMessage")

 **데이터베이스에 잘못된 연결 문자열을 사용자에게 경고하는 모달 오류 메시지 대화 상자**

#### <a name="ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a>IDE 상태 표시줄
 사용자가 상태 표시줄 텍스트를 알 수 있는 가능성은 Windows 플랫폼의 모든 컴퓨터 환경 및 특정 환경과 관련이 있습니다. Visual Studio 고객 기반은 지식이 풍부한 Windows 사용자도 상태 표시줄의 변경 내용을 놓칠 수 있지만 두 영역 모두에서 경험하는 경향이 있습니다. 따라서 상태 표시줄은 정보 제공을 위해 또는 다른 곳에서 제공되는 정보에 대한 중복 신호로 가장 적합합니다. 사용자가 즉시 확인해야 하는 모든 종류의 중요한 정보는 대화 상자 또는 알림 도구 창에 제공되어야 합니다.

 Visual Studio 상태 표시줄은 여러 유형의 정보를 표시할 수 있도록 설계되었습니다. 피드백, 디자이너, 진행률 표시줄, 애니메이션 및 클라이언트에 대한 영역으로 나뉩니다.

 피드백 영역 및 디자이너 영역은 항상 표시됩니다. 진행률 표시줄 및 애니메이션 영역은 항상 동적이며 사용자 컨텍스트를 기반으로 합니다. 디자이너 영역에는 문자 메시지에 대한 함께 제공되는 리소스에서 가져온 문자열의 길이에 따라 결정되는 정적 너비가 있습니다. 이렇게 하면 지역화를 통해 코드를 변경할 필요 없이 너비의 크기를 조정할 수 있습니다. 영어의 경우 이 문자열의 너비는 약 220픽셀입니다. 디자이너 영역은 정상적으로 행동하고 피드백 영역은 나머지 공간을 흡수합니다.

 상태 표시줄은 또한 IDE가 디버그 모드에 있을 때와 같은 다양한 IDE 상태 변경 사항을 전달하여 시각적 관심사와 기능적 가치를 추가하도록 색상이 지정됩니다.

 ![IDE 상태 표시줄 색 변경](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901-02_IDEStatusBar")

 **IDE 상태 표시줄 색상**

#### <a name="embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a>임베디드 인포바
 정보 표시줄은 문서 창 또는 도구 창 의 맨 위에 사용하여 사용자에게 상태 또는 조건을 알릴 수 있습니다. 또한 사용자가 쉽게 조치를 취할 수 있는 방법을 가질 수 있도록 명령을 제공할 수도 있습니다. 인포바는 표준 셸 컨트롤입니다. IDE의 다른 사용자와 일치하지 않는 것처럼 보이는 사용자 고유의 사용자 만들기를 피하십시오. 구현 세부 정보 및 사용 지침은 [정보 표시줄을](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) 참조하십시오.

 ![포함된 정보 표시줄](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "03_EmbeddedInfobar 0901-")

 **문서 창에 포함된 정보 표시줄은 사용자에게 IDE가 기록 디버깅 모드에 있으며 편집기가 표준 디버깅 모드에서와 동일한 방식으로 응답하지 않음을 경고합니다.**

#### <a name="mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a>마우스 커서 변경
 마우스 커서를 변경할 때 VSColor 서비스에 연결되고 커서와 이미 연결된 색상을 사용합니다. 커서 변경 사항은 진행 중인 작업뿐만 아니라 사용자가 드래그하거나, 삭제하거나, 개체를 선택하는 데 사용할 수 있는 대상 위로 마우스를 가져가는 적중 영역을 나타내는 데 사용할 수 있습니다.

 사용 가능한 모든 CPU 시간을 작업에 예약해야 하는 경우에만 사용 중/대기 마우스 커서를 사용하므로 사용자가 추가 입력을 표현할 수 없습니다. 다중 스레딩을 사용하여 잘 작성된 응용 프로그램의 경우 대부분의 경우 사용자가 다른 작업을 수행하지 못하는 경우는 드뭅니다.

 커서 변경은 다른 곳에서 제공되는 정보에 대한 중복 신호로 유용합니다. 특히 사용자가 해결해야 하는 중요한 것을 전달하려고 할 때 사용자와 통신하는 유일한 방법으로 커서 변경에 의존하지 마십시오.

#### <a name="progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a>진행 률 표시기
 진행률 표시기는 완료하는 데 몇 초 이상 걸리는 프로세스 중에 사용자에게 피드백을 제공하는 데 중요합니다. 진행률 표시기는 현재 진행 중인 작업의 시작 지점 근처, 포함된 상태 표시줄, 모달 대화 상자 또는 Visual Studio 상태 표시줄에 표시될 수 있습니다. 사용 및 구현에 관한 [진행률 표시기의](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) 지침을 따르십시오.

#### <a name="visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a>비주얼 스튜디오 알림 창
 Visual Studio 알림 창은 개발자에게 라이선스, 환경(Visual Studio), 확장 및 업데이트에 대해 알림을 보입니다. 사용자는 개별 알림을 해제하거나 특정 유형의 알림을 무시하도록 선택할 수 있습니다. 무시된 알림 목록은 도구 **> 옵션** 페이지에서 관리됩니다.

 알림 창은 현재 확장할 수 없습니다.

 ![Visual Studio 알림 창](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901-06_VSNotificationsWindow")

 **비주얼 스튜디오 알림 도구 창**

#### <a name="error-list"></a><a name="BKMK_ErrorList"></a>오류 목록
 오류 목록 내의 알림은 컴파일 및 빌드 프로세스 중에 발생한 오류 및 경고를 나타내며 사용자가 코드에서 특정 코드 오류로 이동할 수 있도록 합니다.

 ![오류 목록](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "08_ErrorList 0901-")

 **비주얼 스튜디오의 오류 목록**

#### <a name="embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a>임베디드 상태 표시줄
 IDE 상태 표시줄은 동적이므로 클라이언트 영역 컨텍스트가 활성 문서 창으로 설정되고 사용자의 컨텍스트 및/또는 시스템 응답에 대한 정보가 업데이트되므로 정보를 지속적으로 표시하거나 장기 비동기 프로세스에 상태를 지정하기가 어렵습니다. 예를 들어 IDE 상태 표시줄은 여러 실행 및/또는 즉시 실행 가능한 항목 선택에 대한 테스트 실행 결과 알림에 적합하지 않습니다. 사용자가 선택하거나 프로세스를 시작하는 문서 또는 도구 창의 컨텍스트에서 이러한 상태 정보를 유지하는 것이 중요합니다.

 ![포함된 상태 표시줄](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "09_EmbeddedStatusBar 0901-")

 **비주얼 스튜디오의 임베디드 상태 표시줄**

#### <a name="windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a>윈도우 트레이 알림
 Windows 알림 영역은 Windows 작업 표시줄의 시스템 시계 옆에 있습니다. 많은 유틸리티 및 소프트웨어 구성 요소는 사용자가 화면 해상도 변경 또는 소프트웨어 업데이트 가져오는 등 시스템 전체 작업에 대한 컨텍스트 메뉴를 얻을 수 있도록 이 영역에 아이콘을 제공합니다.

 환경 수준 알림은 Windows 알림 영역이 아닌 Visual Studio 알림 허브에 표시되어야 합니다.

#### <a name="notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a>알림 거품
 알림 거품은 편집기/디자이너 내에서 또는 Windows 알림 영역의 일부로 정보로 나타날 수 있습니다. 사용자는 이러한 거품을 나중에 해결할 수 있는 문제로 인식하므로 중요하지 않은 알림의 이점입니다. 거품은 사용자가 즉시 해결해야 하는 중요한 정보에 적합하지 않습니다. Visual Studio에서 알림 거품을 사용하는 경우 [알림 거품에 대한 Windows 데스크톱 지침을 따릅니다.](/windows/desktop/uxguide/mess-notif)

 ![알림 거품형](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901-07_NotificationBubbles")

 **비주얼 스튜디오에 사용되는 Windows 알림 영역의 알림 버블**

## <a name="progress-indicators"></a><a name="BKMK_ProgressIndicators"></a>진행 률 표시기

### <a name="overview"></a>개요
 진행률 표시기는 사용자 피드백을 제공하기 위한 알림 시스템의 중요한 부분입니다. 프로세스 및 작업이 완료될 시기를 사용자에게 알려줍니다. 친숙한 표시기 유형에는 진행률 표시줄, 회전 커서 및 애니메이션 아이콘이 포함됩니다. 진행률 표시기의 유형 및 배치는 보고되는 내용과 프로세스 또는 작업이 완료되는 데 걸리는 시간 등 컨텍스트에 따라 달라집니다.

#### <a name="factors"></a>요소
 적절한 표시기 유형을 결정하려면 다음 요소를 결정해야 합니다.

1. **타이밍:** 작업에 걸리는 시간

2. **양식:** 작업이 환경에 대한 모달인지 여부(프로세스가 완료될 때까지 UI를 잠그기)

3. **영구/과도:** 진행 상황의 최종 결과를 보고 및/또는 나중에 볼 수 있어야 하는지 여부

4. **확정/불확정:** 작업 종료 시간 및 진행률을 계산할 수 있는지 여부

5. **그래픽/텍스트 위치:** 진행률 또는 프로세스가 인라인으로 캡처되는지, 메시지 본문에 캡처되는지 또는 트리 컨트롤과 같은 특정 컨트롤인지 여부

6. **근접성:** 진행률과 관련된 UI에 근접해야 하는지 여부입니다. (예를 들어, 상태 표시줄에 있을 수 있습니다., 멀리 있을 수 있습니다., 또는 프로세스를 시작 하는 단추 근처에 있어야 합니까?)

#### <a name="determinate-progress"></a>확정 진행률

|진행 률 유형|사용 시기 및 방법|메모|
|-------------------|-------------------------|-----------|
|진행률 표시줄(확정)|예상 >5초.<br /><br /> 프로세스 세부 정보에 대한 텍스트 설명이 포함될 수 있습니다.|애니메이션에 텍스트를 **포함하지 마십시오.**|
|정보 표시줄|컨텍스트 UI와 연결된 메시징입니다. [정보 표시줄](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)을 참조하십시오.<br /><br /> 프로세스 세부 정보에 대한 텍스트 설명이 포함될 수 있습니다.|여러 프로세스를 표시해야 하는 경우 여러 정보 표시줄을 사용하지 **마십시오.** 대신 누적 된 진행률 막대를 사용합니다.|
|출력 창|일시적 알림: 완료 후 세부 정보를 **검토하려는** 앱 수준 프로세스입니다.|사용자가 나중에 데이터를 참조해야 하는 경우에는 사용하지 **마십시오.**|
|로그 파일|완료 후 세부 정보를 **저장하는** 것이 중요한 경우 불변 알림과 페어링됩니다.||
|상태 표시줄|일시적 알림: 완료 후 세부 정보가 **필요하지 않은** 앱 수준 프로세스입니다.<br /><br /> 포함된 진행률 표시줄이 포함되어 있습니다.<br /><br /> 프로세스 세부 정보에 대한 텍스트 설명이 포함될 수 있습니다.||

#### <a name="indeterminate-progress"></a>확정되지 않은 진행률

|진행 률 유형|사용 시기 및 방법|메모|
|-------------------|-------------------------|-----------|
|진행률 표시줄(확정되지 않음)|예상 >5초.<br /><br /> 프로세스 세부 정보에 대한 텍스트 설명이 포함될 수 있습니다.|애니메이션에 텍스트를 **포함하지 마십시오.**|
|개미(애니메이션 가로 점)|서버왕복.<br /><br /> 상위 컨테이너 의 맨 위에 컨텍스트 근처에 배치됩니다.|전체 컨테이너에 의해 부모가 되지 않으면 사용하지 **마십시오.**|
|스피너(진행 링)|컨텍스트 UI와 연관된 프로세스 또는 공간이 고려되는 프로세스입니다.<br /><br /> 프로세스 세부 정보에 대한 텍스트 설명이 포함될 수 있습니다.||
|정보 표시줄|컨텍스트 UI와 연결된 메시징입니다. [정보 표시줄](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)을 참조하십시오.|여러 프로세스를 표시해야 하는 경우 여러 정보 표시줄을 사용하지 **마십시오.** 대신 누적 된 진행률 막대를 사용합니다.|
|출력 창|일시적 알림: 사용자가 완료 후 세부 정보를 **검토하려는** 앱 수준 프로세스입니다.|세션 간에 유지해야 하는 정보에는 사용하지 **마십시오.**|
|로그 파일|완료 후 세부 정보를 **저장하는** 것이 중요한 경우 불변 알림과 페어링됩니다.||
|상태 표시줄|일시적 알림: 완료 후 세부 정보가 **필요하지 않은** 앱 수준 프로세스입니다.<br /><br /> 포함된 진행률 표시줄이 포함되어 있습니다.<br /><br /> 프로세스 세부 정보에 대한 텍스트 설명이 포함될 수 있습니다.||

### <a name="progress-indicator-types"></a>진행 률 표시기 유형

#### <a name="progress-bars"></a>진행률 표시줄

##### <a name="indeterminate"></a>확정 되지 않은
 ![비활성화 상태의 진행률 표시줄](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901-04_Indeterminate")

 **비활성화 상태의 진행률 표시줄**

 "확정되지 않음"은 작업 또는 프로세스의 전반적인 진행 상황을 결정할 수 없음을 의미합니다. 무한한 시간이 필요하거나 알 수 없는 수의 개체에 액세스하는 작업에는 확정되지 않은 진행률 표시줄을 사용합니다. 텍스트 설명을 사용하여 무슨 일이 일어나고 있는지 함께 수반합니다. 시간 시간을 사용하여 시간 기반 작업에 범위를 제공합니다. 확정되지 않은 진행률 표시줄은 애니메이션을 사용하여 진행률을 표시하지만 다른 정보는 제공하지 않습니다. 정확도가 부족할 수 밖에 없는 경우에만 불확실한 진행률 표시줄을 선택하지 마십시오.

##### <a name="determinate"></a>확정
 ![활성화 상태의 진행률 표시줄](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901-05_Determinate")

 **활성화 상태의 진행률 표시줄**

 "확정"은 작업 또는 프로세스가 해당 시간을 정확하게 예측할 수 없더라도 한정된 시간이 필요하다는 것을 의미합니다. 완료를 명확하게 나타냅니다. 작업이 완료되지 않는 한 진행률 표시줄이 100%로 이동하지 않도록 합니다. 확정 진행률 표시줄 애니메이션은 왼쪽에서 오른쪽으로 0에서 100%로 이동합니다.

 작업 중에 진행률 표시기를 뒤로 이동하지 마십시오. 작업이 시작될 때 막대는 꾸준히 앞으로 이동하고 작업이 끝날 때 100 %에 도달해야합니다. 진행률 표시줄의 요점은 관련된 단계 수에 관계없이 전체 작업이 걸리는 시간을 사용자에게 제공하는 것입니다.

##### <a name="concurrent-reporting-stacked-progress-bars"></a>동시 보고(누적 진행률 표시줄)
 작업에 시간이 오래 걸리는 경우(아마도 몇 분) 동안 두 개의 진행률 표시줄을 사용할 수 있으며, 하나는 작업에 대한 전반적인 진행률을 표시하고 다른 하나는 현재 단계의 진행을 보여 줄 수 있습니다. 예를 들어 설치 프로그램이 많은 파일을 복사하는 경우 하나의 진행률 표시줄을 사용하여 전체 프로세스의 소요 시간을 표시하는 데 사용할 수 있으며, 두 번째 프로세스는 현재 파일 또는 디렉터리의 복사 비율을 나타낼 수 있습니다. 누적된 진행률 표시줄을 사용하여 5개 이상의 동시 작업 또는 프로세스를 보고하지 마십시오. 보고할 동시 작업 또는 프로세스가 5개 이상 있는 경우 취소 단추를 사용하여 모달 대화 상자를 사용하고 진행률 세부 정보를 출력 창에 보고합니다.

##### <a name="textual-descriptions"></a>텍스트 설명
 텍스트 설명을 사용하여 진행 중이고 완료할 예상 시간을 함께 사용할 수 있습니다. 작업이 걸리는 시간이 얼마인지 결정할 수 없는 경우 피드백을 제공하는 것이 진행률 표시줄이 아니라 애니메이션 아이콘일 수 있습니다.

 Visual Studio는 상태 표시줄에 Visual Studio에 통합된 모든 제품에서 사용할 수 있는 표준 진행률 표시줄을 제공합니다. 진행률 표시줄이 애니메이션되는 동안 일어나는 일에 대한 텍스트 설명의 경우 상태 표시줄 텍스트를 업데이트할 수 있습니다.

#### <a name="other-progress-indicators"></a>기타 진행 지표

##### <a name="ants-animated-horizontal-dots"></a>개미(애니메이션 가로 점)
 ![진행률 ants](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903-01_Ants")

 애니메이션 된 가로 점인 "개미"는 확정되지 않은 왕복 서버 프로세스에 대한 시각적 참조를 제공합니다.

##### <a name="spinner-progress-ring"></a>스피너(진행 링)
 ![진행률 회전자](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903-02_Spinner")

 스피너("진행률 고리"라고도 함)는 컨텍스트 UI와 관련하여 주로 사용되는 불확정 진행 표시기입니다. 텍스트 범주 헤더, 메시징 또는 컨트롤과 같은 관련 콘텐츠에 근접하여 스피너를 표시합니다.

##### <a name="cursor-feedback"></a>커서 피드백
 2~7초 정도 걸리는 작업의 경우 커서 피드백을 제공합니다. 일반적으로 이는 운영 체제에서 제공하는 대기 커서를 사용하는 것을 의미합니다. 지침은 MSDN 문서 [Cursors.Wait 속성을](/dotnet/api/system.windows.input.cursors.wait)참조하십시오.

#### <a name="progress-indicator-locations"></a>진행 지표 위치

##### <a name="status-bar"></a>상태 표시줄
 상태 표시줄은 응용 프로그램에 사용자의 작업을 중단하지 않고 사용자에게 메시지와 유용한 정보를 표시할 수 있는 위치를 제공합니다. 일반적으로 창의 하단에 표시되고, 진행률 상태는 진행률 표시줄 표시기와 조합하여 진행률 측정값에 대한 메시지를 포함하는 툴팁 창이 될 것이다.

 ![진행률 표시줄을 사용하는 상태 표시줄](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903-03_StatusBarProgressBar")

 **진행률 표시줄을 사용하는 상태 표시줄**

 ![메시징을 사용하는 상태 표시줄](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903-04_StatusBarMessage")

 **텍스트 설명이 있는 상태 표시줄**

##### <a name="infobar"></a>정보 표시줄
 상태 표시줄과 마찬가지로 정보 표시줄은 상황별 알림 및 메시징을 제공하며, 이 알림은 진행률 표시줄 또는 스피너와 같은 확정되지 않은 진행률 표시기와 페어링될 수도 있습니다. 정보 표시줄은 세분화된 수준 진행률 또는 확정 진행률 표시를 제공하지 않아야 합니다. [정보 표시줄](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)을 참조하십시오.

 ![진행률 표시줄 및 메시징을 사용하는 정보 표시줄](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903-05_InfoBar")

 **진행률 표시줄 및 텍스트 설명이 있는 인포바**

 ![창 내의 정보 표시줄](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903-06_InfoBarInWindow")

##### <a name="inline"></a>인라인
 인라인 진행률 표시는 진행률 로더 유형으로 나타낼 수 있습니다. 일반적으로 진행률 표시기는 메시징과 페어링되지만 필수 사항은 아닙니다.

 ![인라인 진행률 회전자](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903-07_InlineSpinner")

 **텍스트 설명과 결합된 스피너**

 ![인라인 누적 진행률 표시줄](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903-08_InlineStackedProgress")

 **누적된 진행률 표시줄**

 ![인라인 진행률 메시징](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903-09_InlineText")

 **서버 탐색기 인라인 텍스트: 새로 고침...**

##### <a name="tool-windows"></a>도구 창
 전역 진행률 표시는 도구 모음 바로 아래에 있는 확정되지 않은 진행률 표시줄로 표시됩니다.

 ![전역 비활성화 상태의 진행률 표시줄](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903-23_GlobalIndeterminate")

 **팀 탐색기 전역 불확정 진행률 표시줄**

##### <a name="dialogs"></a>대화 상자
 대화 상자에는 진행률 로더 유형이 포함될 수 있습니다. 진행률 표시기는 메시징과 페어링할 수 있을 뿐만 아니라 여러 수준의 진행률 표시와 결합하여 세분화된 프로세스와 하위 프로세스를 나타낼 수 있습니다.

 ![여러 진행률 표시기 유형이 있는 대화 상자](../../extensibility/ux-guidelines/media/0903-11_dialog.png "11_Dialog")

 **동시 프로세스 및 여러 진행률 표시기 유형이 있는 Visual Studio 대화 상자**

 ![진행률 로더 및 메시징이 있는 대화 상자](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903-12_Dialog2")

 **진행률 로더 및 메시징 인라인 명령과 Visual Studio 대화 상자**

##### <a name="document-well"></a>잘 문서화
 문서는 컨트롤과 함께 여러 진행률 로더 유형을 표시할 수 있습니다.

 ![문서의 진행률 메시징](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903-13_DocumentWell")

 **도구 모음 아래의 확정되지 않은 진행률 표시줄**

##### <a name="output-window"></a>출력 창
 출력 창은 인라인 텍스트 메시징을 통해 프로세스 진행 및 진행 중인 상태를 처리하는 데 적합합니다. 상태 표시줄은 출력 창 진행률 보고와 함께 사용해야 합니다.

 ![출력 창의 진행률 메시징](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903-14_OutputWindow")

 **진행 중인 프로세스 상태 및 대기 메시징이 있는 출력 창**

## <a name="infobars"></a><a name="BKMK_Infobars"></a>정보 표시줄

### <a name="overview"></a>개요
 정보 막대는 사용자에게 관심 지점에 가까운 표시기를 제공하고 공유 정보 표시줄 컨트롤을 사용하면 시각적 모양과 상호 작용의 일관성을 보장합니다.

 ![정보 표시줄](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")

 **비주얼 스튜디오의 인포바**

#### <a name="appropriate-uses-for-an-infobar"></a>정보 표시줄에 대한 적절한 용도

- 사용자에게 현재 컨텍스트와 관련된 비차단이지만 중요한 메시지를 제공하려면

- UI가 기록 디버깅과 같은 일부 상호 작용 의미를 전달하는 특정 상태 또는 상태에 있음을 나타냅니다.

- 확장으로 인해 성능 문제가 발생하는 경우와 같이 시스템에서 문제가 감지되었음을 사용자에게 알리기 위해

- 편집기에서 파일이 혼합된 탭과 공백을 감지하는 경우와 같이 사용자에게 작업을 쉽게 취할 수 있는 방법을 제공합니다.

##### <a name="do"></a>수행할 작업:

- 정보 표시줄 메시지 텍스트를 짧고 요점으로 유지합니다.

- 링크와 단추에 텍스트를 간결하게 유지합니다.

- 사용자에게 제공하는 "작업" 옵션이 필요한 작업만 표시하여 최소화해야 합니다.

##### <a name="dont"></a>안 함:

- 인포바를 사용하여 도구 모음에 배치해야 하는 표준 명령을 제공합니다.

- 모달 대화 상자 대신 정보 표시줄을 사용합니다.

- 창 외부에 부동 메시지를 만듭니다.

- 동일한 창 내의 여러 위치에서 여러 정보 막대를 사용합니다.

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>여러 정보 표시줄이 동시에 표시될 수 있나요?
 예. 여러 정보 표시줄이 동시에 표시될 수 있습니다. 첫 번째 인포바상단에 는 첫 번째 인포바와 아래에 표시된 추가 정보표시줄이 있는 선착순으로 표시됩니다.

 사용자는 한 번에 최대 3개의 정보 표시줄을 볼 수 있으며, 그 이후에는 더 많은 정보 표시줄을 사용할 수 있는 경우 정보 표시줄 영역을 스크롤할 수 있게 됩니다.

### <a name="creating-an-infobar"></a>정보 표시줄 만들기
 인포바에는 왼쪽에서 오른쪽으로 네 개의 섹션이 있습니다.

- **아이콘:** 여기서 경고 아이콘과 같이 정보 표시줄에 표시할 아이콘을 추가할 수 있습니다.

- **텍스트:** 필요한 경우 텍스트 내의 링크와 함께 사용자가 있는 시나리오/상황을 설명하는 텍스트를 추가할 수 있습니다. 텍스트를 간결하게 유지해야 합니다.

- **작업:** 이 섹션에는 사용자가 정보 표시줄에서 수행할 수 있는 작업에 대한 링크와 단추가 포함되어야 합니다.

- **닫기 버튼:** 오른쪽의 마지막 섹션에는 닫기 버튼이 있을 수 있습니다.

#### <a name="creating-a-standard-infobar-in-managed-code"></a>관리 코드에서 표준 정보 표시줄 만들기
 InfoBarModel 클래스를 사용하여 정보 표시줄에 대한 데이터 원본을 만들 수 있습니다. 다음 네 가지 생성자 중 하나를 사용합니다.

```
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(string text, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(string text, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);
```

 다음은 하이퍼링크, 작업 단추 및 아이콘이 있는 일부 텍스트가 있는 InfoBarModel을 만드는 예제입니다.

 ![하이퍼링크가 포함된 정보 표시줄](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904-02_InfobarHyperlink")

```
var infoBar = new InfoBarModel(
    textSpans: new[]
    {
        new InfoBarTextSpan("This is a "),
        new InfoBarHyperlink("hyperlink"),
        new InfoBarTextSpan(" InfoBar.")
    },
    actionItems: new[]
    {
        new InfoBarButton("Click Me")
    },
    image: KnownMonikers.StatusInformation,
    isCloseButtonVisible: true);

```

#### <a name="creating-a-standard-infobar-in-native-code"></a>네이티브 코드에서 표준 정보 표시줄 만들기
 네이티브 코드에서 정보 모음을 제공 하려면 IVsInfoBar 인터페이스를 구현 합니다.

```
public interface IVsInfoBar
{
    IVsInfoBarActionItemCollection ActionItems { get; }
    ImageMoniker Image { get; }
    bool IsCloseButtonVisible { get; }
    IVsInfoBarTextSpanCollection TextSpans { get; }
}

```

#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>정보 표시줄에서 정보 표시줄 UIElement 받기
 InfoBarModel 또는 IVsInfoBar 구현은 UI에 표시하기 위해 UIElement로 전환해야 하는 데이터 모델입니다. UIElement는 SVsInfoBarUIFactory/IVsInfoBarUIFactory 서비스로 검색할 수 있습니다.

```
private bool TryCreateInfoBarUI(IVsInfoBar infoBar, out IVsInfoBarUIElement uiElement)
{
    IVsInfoBarUIFactory infoBarUIFactory = serviceProvider.GetService(typeof(SVsInfoBarUIFactory)) as IVsInfoBarUIFactory;
    if (infoBarUIFactory == null)
    {
        uiElement = null;
        return false;
    }

    uiElement = infoBarUIFactory.CreateInfoBar(infoBar);
    return uiElement != null;
}
```

### <a name="placement"></a>배치
 정보 표시줄은 다음 위치 중 하나 이상에 표시될 수 있습니다.

- 도구 창

- 문서 탭 내에서

> [!IMPORTANT]
> 전역 컨텍스트에 대한 메시지를 제공하기 위해 정보 표시줄을 배치할 수 있습니다. 이 도구 모음과 문서 간에 잘 나타납니다. IDE의 "점프 및 바보"에 문제가 발생 하기 때문에 이 권장 되지 않습니다 및 절대적으로 필요 하 고 적절 한 하지 않는 한 피해 야 한다.

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>도구창창에 정보표시줄 배치
 ToolWindowPane.AddInfoBar(IVsInfoBar) 메서드를 사용하여 도구 창에 정보 표시줄을 추가할 수 있습니다. 이 API는 IVsInfoBar(InfoBarModel이 기본 구현인) 또는 IVsUIElement를 추가할 수 있습니다.

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>문서 또는 비 ToolWindowPane에 정보 표시줄 배치
 모든 IVsWindowFrame에 정보 표시줄을 배치하려면 VSFPROPID_InfoBarHost 속성을 사용하여 프레임에 대한 IVsInfoBarHost를 가져옵니다.

```
private void AddInfoBar(IVsWindowFrame frame, IVsUIElement uiElement)
{
    IVsInfoBarHost infoBarHost;
    if (TryGetInfoBarHost(frame, out infoBarHost))
    {
        infoBarHost.AddInfoBar(uiElement);
    }
}
private bool TryGetInfoBarHost(IVsWindowFrame frame, out IVsInfoBarHost infoBarHost)
{
    object infoBarHostObj;
    if (ErrorHandler.Failed(frame.GetProperty((int)__VSFPROPID7.VSFPROPID_InfoBarHost, out infoBarHostObj)))
    {
        infoBarHost = null;
        return false;
    }

    infoBarHost = infoBarHostObj as IVsInfoBarHost;
    return infoBarHost != null;
}

```

#### <a name="placing-an-infobar-in-the-main-window"></a>기본 창에 정보 표시줄 배치
 기본 창에 정보 표시줄을 배치하려면 IVsShell 서비스의 VSSPROPID_MainWindowInfoBarHost 사용하여 기본 창의 IVsInfoBarHost를 받은 다음 정보 표시줄 UIElement를 추가합니다.

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>사용자가 내 정보표시줄에서 조치를 취하는 시기를 알 수 있나요?
 예. 모든 이벤트 작업을 정보 표시줄 작성자에게 반환합니다. 그런 다음 정보 표시줄 작성자가 정보 표시줄의 사용자 선택에 따라 IDE에서 작업을 수행합니다. 닫기 단추를 클릭한 호스트에서 정보 표시줄이 자동으로 제거되지만 닫은 후 다른 정보 표시줄을 제거해야 하는 경우 추가 작업이 필요합니다. 또한 원격 분석은 각 정보 표시줄에서 독립적으로 기록해야 합니다.

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>도구창창에서 정보표시줄 이벤트 수신
 ToolWindowPane에는 정보 표시줄에 대한 두 가지 이벤트가 있습니다. 인포바클로드 이벤트는 ToolWindowPane의 인포바(infobar)가 닫히면 발생합니다. InfoBarActionItem클릭된 이벤트는 정보 표시줄 내부의 하이퍼링크 또는 단추를 클릭하면 발생합니다.

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>UIElement에서 직접 정보 표시줄 이벤트 수신
 IVsInfoBarUIElement.Advise는 정보 표시줄의 UIElement에서 직접 이벤트를 구독하는 데 사용할 수 있습니다. IVsInfoBarUIEvents를 구현하면 작성자가 닫기 및 클릭 이벤트를 받을 수 있습니다.

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

## <a name="error-validation"></a><a name="BKMK_ErrorValidation"></a>오류 유효성 검사
 사용자가 필수 필드를 건너뛰거나 데이터가 잘못된 형식으로 입력되는 경우와 같이 허용되지 않는 정보를 입력하면 차단 팝업 오류 대화 상자를 사용하는 대신 컨트롤 유효성 검사 또는 컨트롤 근처의 피드백을 사용하는 것이 좋습니다.

### <a name="field-validation"></a>필드 유효성 검사
 양식 및 필드 유효성 검사는 컨트롤, 아이콘 및 도구 설명의 세 가지 구성 요소로 구성됩니다. 여러 유형의 컨트롤이 이 것을 사용할 수 있지만 텍스트 상자는 예제로 사용됩니다.

 ![필드 유효성 검사 &#40;빈&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905-01_FieldValidation")

 필드가 필요한 경우 ** \<필수>** 라는 워터마크 텍스트가 있어야 하며 필드 배경은 `Environment.ControlEditRequiredBackground`연한 노란색이어야 합니다(VSColor: `Environment.ControlEditRequiredHintText`) 및 전경은 회색이어야 합니다(VSColor: : ) :

 !["필수" 레이블이 있는 필드 유효성 검사](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "02_FieldValidationRequired 0905-02_FieldValidationRequired")

 포커스가 다른 컨트롤로 이동되거나 사용자가 [확인] 커밋 단추를 클릭하거나 사용자가 문서 나 양식을 저장할 때 컨트롤이 *입력되지 않은 콘텐츠* 상태에 있는지 확인할 수 있습니다.

 잘못된 콘텐츠 상태가 결정되면 컨트롤 내부 또는 아이콘 바로 옆에 아이콘이 나타납니다. 오류를 설명하는 도구 설명이 아이콘이나 컨트롤의 호버에 나타나야 합니다. 또한 잘못된 상태를 만드는 컨트롤 주위에 1픽셀 테두리가 나타나야 합니다.

 ![필드 유효성 검사 레이아웃 사양](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905-03_LayoutSpecs")

 **필드 유효성 검사를 위한 레이아웃 사양**

#### <a name="acceptable-variations-for-icon-location"></a>아이콘 위치에 대한 허용 가능한 변형
 사용자에게 유효성 검사 오류에 대해 알려야 하는 고유한 사례가 셀 수 없이 많습니다. UI의 제어 유형 과 구성을 고려하여 상황에 적합한 아이콘 배치를 선택합니다.

 ![아이콘 위치에 적합한 위치](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905-04_IconLocation")

 **필드 유효성 검사 아이콘 위치에 대한 허용 가능한 변형**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>서버 또는 네트워크 연결로 의왕복이 필요한 유효성 검사
 경우에 따라 콘텐츠를 확인하려면 서버로 의 왕복이 필요하며 사용자 진행 률, 확인 됨 및 오류 상태를 표시하는 것이 중요합니다. 아래 그림은 이 사례와 권장 UI의 예를 보여줍니다.

 ![서버에 대한 왕복과 관련된 유효성 검사](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "05_RoundTrip")

 **서버에 대한 왕복과 관련된 유효성 검사**

 "확인..." 및 "다시 시도" 텍스트.

#### <a name="in-place-warning-text"></a>장소 내 경고 텍스트
 오류 메시지를 컨트롤에 가까이 놓을 수 있는 공간이 있는 경우 도구 설명만 사용하는 것이 좋습니다.

 ![&#45;장소 경고](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "06_InPlaceWarning")

 **장소 내 경고 텍스트**

#### <a name="watermarks"></a>워터마크
 경우에 따라 전체 컨트롤 또는 창이 오류 상태에 있습니다. 이 경우 워터마크를 사용하여 오류를 나타냅니다.

 ![워터 마크](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")

 **워터마크 필드 유효성 검사**
