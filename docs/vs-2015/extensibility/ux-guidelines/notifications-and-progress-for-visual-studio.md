---
title: 알림 및 진행
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f17b875f0637883222a633cb1082ad24788d4c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842150"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Visual Studio의 알림 및 진행률
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="notification-systems"></a><a name="BKMK_NotificationSystems"></a> 알림 시스템

### <a name="overview"></a>개요
 Visual Studio에서 소프트웨어 개발 작업과 관련 하 여 발생 하는 상황을 사용자에 게 알리는 몇 가지 방법이 있습니다.

 모든 종류의 알림을 구현할 때:

- **알림 수를 최소 유효 수로 유지** 합니다. 알림 메시지는 대부분의 Visual Studio 사용자 또는 특정 기능/기능 영역의 사용자에 게 적용 됩니다. 알림을 과도 하 게 사용 하면 사용자를 추적 하거나 시스템의 사용 편의성을 저하 시킬 수 있습니다.

- 더 복잡 한 선택 및 추가 작업을 수행 하기 위해 사용자가 적절 한 컨텍스트를 호출 하는 데 사용할 수 있는 **명확 하 고 조치 가능한 메시지** 를 제공 하 고 있는지 확인 합니다.

- **동기 및 비동기 메시지를 적절 하 게 제공 합니다.** 동기 알림은 웹 서비스가 충돌 하거나 코드 예외가 throw 되는 경우와 같이 즉각적인 주의가 필요한 항목을 의미 합니다. 사용자는 모달 대화 상자와 같이 입력이 필요한 방식으로 바로 이러한 상황에 대해 알려야 합니다. 비동기 알림은 사용자가 알고 있어야 하지만 즉시 작업을 수행할 필요가 없는 것입니다. 예를 들어 빌드 작업이 완료 되거나 웹 사이트 배포가 완료 됩니다. 이러한 메시지는 더 자주 사용 되어야 하며 사용자의 작업 흐름을 방해 하지 않습니다.

- **필요한 경우에만 모달 대화 상자를 사용 하 여 사용자가** 메시지를 승인 하거나 대화 상자에 결정을 내리기 전에 추가 작업을 수행 하지 못하도록 합니다.

- **앰비언트 알림이 더 이상 유효 하지 않은 경우 제거 합니다.** 사용자가 알림을 받은 문제를 해결 하기 위한 조치를 이미 취한 경우 알림을 해제할 필요가 없습니다.

- **알림은 거짓 상관 관계를 유발할 수 있습니다.** 사용자는 실제로 인과 관계 없는 경우 해당 작업 중 하나 이상이 알림을 트리거 했을 수 있습니다. 컨텍스트, 트리거 및 알림의 원본에 대 한 알림 메시지에서 지워야 합니다.

### <a name="choosing-the-right-method"></a>올바른 방법 선택
 이 표를 사용 하 여 메시지를 사용자에 게 알리는 올바른 방법을 선택 하는 데 도움을 받을 수 있습니다.

|메서드|Windows Server Update Services와 함께|사용 안 함|
|------------|---------|----------------|
|[모달 오류 메시지 대화 상자](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|계속 하기 전에 사용자 응답이 필요한 경우에 사용 합니다.|사용자를 차단 하 고 흐름을 중단할 필요가 없는 경우에는를 사용 하지 마십시오. 메시지를 방해가 되지 않는 다른 방식으로 표시할 수 있는 경우에는 모달 대화 상자를 사용 하지 마십시오.|
|[IDE 상태 표시줄](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|프로세스 상태와 관련 된 앰비언트 텍스트 정보가 있는 경우를 사용 합니다.|단독으로 사용 하지 마십시오. 다른 피드백 메커니즘과 함께 사용 하는 것이 가장 좋습니다.|
|[포함된 정보 표시줄](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|도구 창이 나 문서 창에서를 사용 하 여 진행률, 오류 상태, 결과 및/또는 실행 가능한 정보를 알립니다.|정보 표시줄이 배치 된 위치와 관련이 없는 경우에는를 사용 하지 마십시오.<br /><br /> 문서/도구 창 외부에서는 사용 하지 마십시오.|
|[마우스 커서 변경](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|프로세스를 진행 하는 것을 알리는 데 사용할 수 있습니다. 끌기/놓기가 진행 중이거나 마우스 커서가 그리기 모드와 같은 특정 모드에 있을 때와 같이 마우스에 상태 변화가 있음을 알리는 데도 사용 됩니다.|짧은 진행률 변경에는를 사용 하지 않고 커서의 펄럭이는 (예: 전체 프로세스가 아닌 더 긴 프로세스의 일부에 연결 된 경우)를 사용 하지 마십시오.|
|[진행률 표시기](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|진행률 (활성화 상태의 또는 확정 되지 않음)을 보고 해야 하는 경우에 사용 합니다. 각각에 대 한 다양 한 진행률 표시기 유형과 특정 사용법이 있습니다. [진행률 지표](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators)를 참조 하세요.||
|[Visual Studio 알림 창](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|알림 창은 공개적으로 확장할 수 없습니다. 그러나 visual studio 또는 패키지에 대 한 업데이트에 대 한 정보 알림과 함께 라이선스와 관련 된 중요 한 문제를 비롯 하 여 Visual Studio에 대 한 다양 한 메시지를 전달 하는 데 사용 됩니다.|다른 유형의 알림에는를 사용 하지 마십시오.|
|[오류 목록](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|문제가 있는 사용자의 현재 오픈 솔루션에 직접 관련 된 문제가 발생 하는 경우 (오류/경고/정보) 코드에서 작업을 수행 해야 할 수 있습니다.<br /><br /> 예를 들면 다음과 같습니다.<br /><br /> -컴파일러 메시지 (오류/경고/정보)<br /><br /> -코드 분석기/코드에 대 한 진단 메시지<br /><br /> -빌드 메시지<br /><br /> 프로젝트 또는 솔루션 파일과 관련 된 문제에 적합할 수 있지만 솔루션 탐색기 표시를 먼저 고려해 야 합니다.|사용자의 오픈 솔루션 코드와 관계가 없는 항목에는를 사용 하지 마세요.|
|편집기 알림: 전구|열려 있는 파일에 존재 하는 문제를 해결 하는 데 사용할 수 있는 수정 프로그램이 있는 경우를 사용 합니다.<br /><br /> 리팩터링와 같이 요청 시 사용자 코드에서 수행 되는 빠른 작업을 호스트 하는 데 전구도 사용 해야 합니다 .이 경우에는 "알림 스타일"이 표시 되지 않습니다.|열려 있는 파일과 관계가 없는 항목에는를 사용 하지 마십시오.|
|편집기 알림: 물결선|를 사용 하 여 열려 있는 코드의 특정 범위 (예: 오류에 대 한 빨간색 물결선)와 관련 된 문제를 사용자에 게 알립니다.|열려 있는 코드의 특정 범위와 관련이 없는 항목에는를 사용 하지 마십시오.|
|[포함 된 상태 표시줄](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|를 사용 하 여 특정 도구 창, 문서 창 또는 대화 상자 창의 컨텍스트 내에서 콘텐츠나 프로세스와 관련 된 상태를 제공 합니다.|특정 창 내에서 콘텐츠와 관련이 없는 일반 제품 알림, 프로세스 또는 항목에는를 사용 하지 마세요.|
|[Windows 트레이 알림](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|를 사용 하 여 in-proc 프로세스 또는 보조 응용 프로그램에 대 한 알림을 노출 합니다.|IDE와 관련 된 알림에 사용 하지 마세요.|
|[알림 풍선](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|를 사용 하 여 원격 프로세스를 알리거나 IDE **외부** 에서 변경 합니다.|IDE **내에서** 프로세스를 사용자에 게 알리는 수단으로를 사용 하지 마세요.|

### <a name="notification-methods"></a>알림 방법

#### <a name="modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a> 모달 오류 메시지 대화 상자
 모달 오류 메시지 대화 상자는 사용자의 확인 또는 작업이 필요한 오류 메시지를 표시 하는 데 사용 됩니다.

 ![모달 오류 메시지](../../extensibility/ux-guidelines/media/0901-01-modalerrormessage.png "0901-01_ModalErrorMessage")

 **데이터베이스에 대해 잘못 된 연결 문자열을 사용자에 게 알리는 모달 오류 메시지 대화 상자**

#### <a name="ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a> IDE 상태 표시줄
 사용자에 게 표시 되는 상태 표시줄 텍스트는 모든 컴퓨터 환경 및 Windows 플랫폼에 대 한 특정 경험과 관련이 있습니다. 숙련 된 Windows 사용자가 상태 표시줄에서 변경을 놓칠 수도 있지만 Visual Studio 고객 기반은 두 영역 모두에서 발생 합니다. 따라서 상태 표시줄은 정보를 제공 하는 데 가장 적합 하거나 다른 위치에 표시 되는 정보에 대 한 중복 된 큐로 사용 됩니다. 사용자가 즉시 해결 해야 하는 모든 종류의 중요 정보는 대화 상자 또는 알림 도구 창에서 제공 해야 합니다.

 Visual Studio 상태 표시줄은 여러 유형의 정보를 표시할 수 있도록 설계 되었습니다. 피드백, 디자이너, 진행률 표시줄, 애니메이션 및 클라이언트에 대 한 영역으로 구분 됩니다.

 사용자 의견 영역 및 디자이너 영역은 항상 표시 됩니다. 진행률 표시줄과 애니메이션 영역은 항상 동적 이며 사용자 컨텍스트에 따라 달라 집니다. 디자이너 영역에는 텍스트 메시지에 대 한 해당 리소스에서 끌어온 문자열의 길이에 따라 결정 되는 정적 너비가 있습니다. 이렇게 하면 코드를 변경할 필요 없이 지역화를 통해 너비를 조정할 수 있습니다. 영어의 경우이 문자열의 너비는 약 220 픽셀입니다. 디자이너 영역은 정상적으로 동작 하며, 피드백 영역에는 나머지 공간이 들어 있습니다.

 상태 표시줄에는 IDE가 디버그 모드에 있을 때와 같이 다양 한 IDE 상태 변경을 전달 하 여 시각적 관심사 및 기능 값을 추가 하도록 색이 표시 됩니다.

 ![IDE 상태 표시줄 색 변경](../../extensibility/ux-guidelines/media/0901-02-idestatusbar.png "0901-02_IDEStatusBar")

 **IDE 상태 표시줄 색**

#### <a name="embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a> 포함 된 정보 표시줄
 정보 표시줄은 문서 창이 나 도구 창의 위쪽에서 사용자에 게 상태나 조건을 알리기 위해 사용할 수 있습니다. 사용자가 쉽게 조치를 취할 수 있도록 명령을 제공할 수도 있습니다. 정보 표시줄은 표준 셸 컨트롤입니다. 사용자 고유의를 만들지 마세요 .이는 IDE의 다른 사용자와 일관 되 게 작동 하 고 표시 됩니다. 구현 세부 정보 및 사용 지침에 대해서는 [정보 표시줄](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) 을 참조 하세요.

 ![포함된 정보 표시줄](../../extensibility/ux-guidelines/media/0901-03-embeddedinfobar.png "0901-03_EmbeddedInfobar")

 **문서 창에 포함 된 정보 표시줄을 통해 사용자에 게 IDE가 기록 디버깅 모드에 있음을 경고 하 고 편집기는 표준 디버깅 모드에서와 동일한 방식으로 응답 하지 않습니다.**

#### <a name="mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a> 마우스 커서 변경
 마우스 커서를 변경 하는 경우 VSColor 서비스에 연결 되 고 이미 커서와 연결 된 색을 사용 합니다. 커서 변경 내용은 진행 중인 작업을 나타내는 데 사용할 수 있으며, 사용자가 개체를 끌어서 놓거나 개체를 선택 하는 데 사용할 수 있는 대상 위로 마우스를 이동 하는 영역을 나타내는 데에도 사용할 수 있습니다.

 사용 가능한 모든 CPU 시간이 작업에 대해 예약 되어야 하는 경우에만 사용 중/대기 마우스 커서를 사용 하 여 사용자가 추가 입력을 표현 하지 못하도록 합니다. 다중 스레딩을 사용 하는 잘 작성 된 응용 프로그램을 사용 하는 대부분의 경우 사용자가 다른 작업을 수행할 수 없게 되는 시간은 드물게 발생 합니다.

 커서 변경은 다른 곳에 표시 되는 정보에 대 한 중복 된 신호로 유용 합니다. 사용자가 해결 해야 하는 중요 한 작업을 전달 하려고 할 때 특히 사용자와 통신 하는 유일한 방법으로 커서 변경을 사용 하지 마세요.

#### <a name="progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a> 진행률 표시기
 진행률 표시기는 완료 하는 데 몇 초 이상이 소요 되는 프로세스 동안 사용자 의견을 제공 하는 데 중요 합니다. 진행률 표시기는 현재 위치 (진행 중인 작업의 시작 지점 근처), 포함 된 상태 표시줄, 모달 대화 상자 또는 Visual Studio 상태 표시줄에 표시 될 수 있습니다. 사용 및 구현과 관련 된 [진행률 표시기](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) 의 지침을 따릅니다.

#### <a name="visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a> Visual Studio 알림 창
 Visual Studio 알림 창은 개발자에 게 라이선스, 환경 (Visual Studio), 확장 및 업데이트에 대해 알립니다. 사용자는 개별 알림을 해제할 수도 있고 특정 유형의 알림을 무시 하도록 선택할 수도 있습니다. 무시 된 알림 목록은 **도구 > 옵션** 페이지에서 관리 됩니다.

 알림 창은 현재 확장할 수 없습니다.

 ![Visual Studio 알림 창](../../extensibility/ux-guidelines/media/0901-06-vsnotificationswindow.png "0901-06_VSNotificationsWindow")

 **Visual Studio 알림 도구 창**

#### <a name="error-list"></a><a name="BKMK_ErrorList"></a> 오류 목록
 오류 목록 내의 알림은 컴파일 및 빌드 프로세스 중에 발생 한 오류 및 경고를 나타내며 사용자가 코드에서 특정 코드 오류를 탐색할 수 있도록 합니다.

 ![오류 목록](../../extensibility/ux-guidelines/media/0901-08-errorlist.png "0901-08_ErrorList")

 **Visual Studio의 오류 목록**

#### <a name="embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a> 포함 된 상태 표시줄
 IDE 상태 표시줄은 동적 이므로 클라이언트 영역 컨텍스트가 활성 문서 창으로 설정 되 고 사용자의 컨텍스트 및/또는 시스템 응답에서 정보가 업데이트 되는 경우 정보를 지속적으로 표시 하거나 장기 비동기 프로세스에 상태를 제공 하기 어렵습니다. 예를 들어 IDE 상태 표시줄은 여러 실행에 대 한 테스트 실행 결과에 대 한 알림 및/또는 즉시 실행 가능한 항목 선택에 적합 하지 않습니다. 사용자가 선택 하거나 프로세스를 시작 하는 문서 또는 도구 창의 컨텍스트에서 이러한 상태 정보를 유지 하는 것이 중요 합니다.

 ![포함된 상태 표시줄](../../extensibility/ux-guidelines/media/0901-09-embeddedstatusbar.png "0901-09_EmbeddedStatusBar")

 **Visual Studio의 포함 된 상태 표시줄**

#### <a name="windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a> Windows 트레이 알림
 Windows 알림 영역은 Windows 작업 표시줄의 시스템 클록 옆에 있습니다. 대부분의 유틸리티 및 소프트웨어 구성 요소는이 영역에 아이콘을 제공 하므로 사용자가 화면 해상도 변경 또는 소프트웨어 업데이트 가져오기와 같은 시스템 차원의 작업에 대 한 상황에 맞는 메뉴를 얻을 수 있습니다.

 환경 수준 알림은 Windows 알림 영역이 아니라 Visual Studio 알림 허브에 표시 되어야 합니다.

#### <a name="notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a> 알림 풍선
 알림 거품은 편집기/디자이너 내에서 정보로 표시 되거나 Windows 알림 영역의 일부로 표시 될 수 있습니다. 사용자는 나중에 해결할 수 있는 문제로 이러한 거품을 인식 하며이는 중요 하지 않은 알림에 대 한 장점입니다. 거품은 사용자가 즉시 해결 해야 하는 중요 한 정보에 적합 하지 않습니다. Visual Studio에서 알림 거품을 사용 하는 경우 [알림 거품에 대 한 Windows 바탕 화면 지침](https://msdn.microsoft.com/library/windows/desktop/dn742472\(v=vs.85\).aspx)을 따릅니다.

 ![알림 거품형](../../extensibility/ux-guidelines/media/0901-07-notificationbubbles.png "0901-07_NotificationBubbles")

 **Visual Studio에 사용 되는 Windows 알림 영역의 알림 거품형**

## <a name="progress-indicators"></a><a name="BKMK_ProgressIndicators"></a> 진행률 표시기

### <a name="overview"></a>개요
 진행률 표시기는 알림 시스템에서 사용자 의견을 제공 하는 중요 한 부분입니다. 프로세스 및 작업이 완료 되 면 사용자에 게 알려줍니다. 친숙 한 표시기 유형에는 진행률 표시줄, 회전 커서 및 애니메이션 아이콘이 있습니다. 진행률 표시기의 유형 및 배치는 보고 되는 내용 및 프로세스나 작업 완료에 소요 되는 시간을 포함 하 여 컨텍스트에 따라 달라 집니다.

#### <a name="factors"></a>요소
 적절 한 표시기 유형을 확인 하려면 다음 요소를 결정 해야 합니다.

1. **타이밍:** 작업에 소요 되는 시간

2. **모달:** 작업이 환경에 모달 인지 여부 (프로세스가 완료 될 때까지 UI 잠그기)

3. **영구/임시:** 진행률의 최종 결과를 보고 하 고 나중에 볼 수 있어야 하는지 여부

4. **활성화 상태의/확정** 안 됨: 작업 종료 시간 및 진행률을 계산할 수 있는지 여부

5. **그래픽/텍스트 위치:** 진행률 또는 프로세스를 인라인, 메시지 본문 또는 트리 컨트롤과 같은 특정 컨트롤에서 캡처하도록 할지 여부입니다.

6. **근접:** 진행률을 관련 된 UI에 근접 하 게 표시할지 여부를 지정 합니다. (예를 들어, 상태 표시줄에 있을 수 있으며,이는 멀리 떨어져 있거나 프로세스를 시작한 단추 근처에 있어야 하나요?)

#### <a name="determinate-progress"></a>활성화 상태의 진행률

|진행률 유형|사용 시기 및 방법|메모|
|-------------------|-------------------------|-----------|
|진행률 표시줄 (활성화 상태의)|예상 >5 초입니다.<br /><br /> 프로세스 세부 정보에 대 한 텍스트 설명을 포함할 수 있습니다.|애니메이션에 텍스트를 포함 **하지 않습니다** .|
|정보 표시줄|컨텍스트 UI와 연결 된 메시지입니다. [정보 표시줄](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)를 참조 하세요.<br /><br /> 프로세스 세부 정보에 대 한 텍스트 설명을 포함할 수 있습니다.|여러 프로세스를 표시 해야 하는 경우 여러 정보 표시줄를 사용 **하지 마세요** . 누적 진행률 표시줄을 대신 사용 합니다.|
|출력 창|일시적인 알림: 사용자가 완료 후 세부 정보를 **검토** 하려는 앱 수준 프로세스입니다.|사용자가 나중에 데이터를 참조 해야 하는 경우에는 사용 **하지 마세요** .|
|로그 파일|완료 후 세부 정보를 **저장** 하는 것이 중요 한 경우에는 intransient 알림과 쌍을 이룹니다.||
|상태 표시줄|일시적인 알림: 앱 수준 프로세스를 완료 한 후에는 사용자가 세부 정보를 **요구 하지** 않습니다.<br /><br /> 포함 된 진행률 표시줄을 포함 합니다.<br /><br /> 프로세스 세부 정보에 대 한 텍스트 설명을 포함할 수 있습니다.||

#### <a name="indeterminate-progress"></a>확정 되지 않은 진행률

|진행률 유형|사용 시기 및 방법|메모|
|-------------------|-------------------------|-----------|
|진행률 표시줄 (비활성화)|예상 >5 초입니다.<br /><br /> 프로세스 세부 정보에 대 한 텍스트 설명을 포함할 수 있습니다.|애니메이션에 텍스트를 포함 **하지 않습니다** .|
|서 점 (가로 애니메이션 가로 점)|서버로 라운드트립 합니다.<br /><br /> 부모 컨테이너의 위쪽에서 컨텍스트의 근처에 배치 됩니다.|전체 컨테이너에서 부모로 사용 하지 않는 경우를 사용 **하지 마세요** .|
|회전자 (진행률 링)|컨텍스트 UI에 연결 된 프로세스 또는 공간을 고려 하는 프로세스입니다.<br /><br /> 프로세스 세부 정보에 대 한 텍스트 설명을 포함할 수 있습니다.||
|정보 표시줄|컨텍스트 UI와 연결 된 메시지입니다. [정보 표시줄](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)를 참조 하세요.|여러 프로세스를 표시 해야 하는 경우 여러 정보 표시줄를 사용 **하지 마세요** . 누적 진행률 표시줄을 대신 사용 합니다.|
|출력 창|일시적인 알림: 사용자가 완료 후 세부 정보를 **검토** 하려는 앱 수준 프로세스입니다.|세션 간에 유지 해야 하는 정보에는를 사용 **하지 마세요** .|
|로그 파일|완료 후 세부 정보를 **저장** 하는 것이 중요 한 경우에는 intransient 알림과 쌍을 이룹니다.||
|상태 표시줄|일시적인 알림: 앱 수준 프로세스를 완료 한 후에는 사용자가 세부 정보를 **요구 하지** 않습니다.<br /><br /> 포함 된 진행률 표시줄을 포함 합니다.<br /><br /> 프로세스 세부 정보에 대 한 텍스트 설명을 포함할 수 있습니다.||

### <a name="progress-indicator-types"></a>진행률 표시기 유형

#### <a name="progress-bars"></a>진행률 표시줄

##### <a name="indeterminate"></a>않음
 ![비활성화 상태의 진행률 표시줄](../../extensibility/ux-guidelines/media/0901-04-indeterminate.png "0901-04_Indeterminate")

 **비활성화 상태의 진행률 표시줄**

 "비활성화"는 작업 또는 프로세스의 전반적인 진행률을 확인할 수 없음을 의미 합니다. 제한 없는 시간을 필요로 하거나 알 수 없는 개체에 액세스 하는 작업에 대해 불확정 진행률 표시줄을 사용 합니다. 텍스트 설명을 사용 하 여 발생 하는 상황에 대 한 설명을 제공 합니다. 시간 제한을 사용 하 여 시간 기반 작업에 범위를 지정 합니다. 확정 되지 않은 진행률 표시줄 애니메이션을 사용 하 여 진행 상태를 표시 하지만 다른 정보는 제공 하지 않습니다. 정확성만을 기준으로 하 여 결정 되지 않은 진행률 표시줄을 선택 하지 마세요.

##### <a name="determinate"></a>활성화 상태의
 ![활성화 상태의 진행률 표시줄](../../extensibility/ux-guidelines/media/0901-05-determinate.png "0901-05_Determinate")

 **활성화 상태의 진행률 표시줄**

 "활성화 상태의"은 해당 시간을 정확 하 게 예측할 수 없는 경우에도 작업 또는 프로세스에 제한 된 시간이 소요 됨을 의미 합니다. 완료를 명확 하 게 표시 합니다. 작업이 완료 되지 않은 경우에는 진행률 표시줄이 100%로 이동 하지 않도록 합니다. 활성화 상태의 진행률 표시줄 애니메이션은 왼쪽에서 오른쪽으로 0에서 100%까지 이동 합니다.

 작업 중에 진행률 표시기를 뒤로 이동 하지 않습니다. 작업을 시작 하 고 종료 될 때 100%에 도달 하면 막대는 계속 해 서 앞으로 이동 해야 합니다. 진행률 표시줄의 점은 관련 된 단계 수에 관계 없이 전체 작업에 소요 되는 시간을 사용자에 게 제공 하는 것입니다.

##### <a name="concurrent-reporting-stacked-progress-bars"></a>동시 보고 (누적 진행률 표시줄)
 작업에 시간이 오래 걸리는 경우 (몇 분이 걸릴 수 있음) 작업에 대 한 전체 진행률을 보여 주는 두 개의 진행률 표시줄과 현재 단계를 진행 하는 데 사용할 수 있습니다. 예를 들어, 설치 프로그램에서 많은 파일을 복사 하는 경우 한 가지 진행률 표시줄을 사용 하 여 전체 프로세스에서 현재 파일이 나 디렉터리를 복사 하는 비율을 나타내는 동안 전체 프로세스가 수행 되는 시간을 나타낼 수 있습니다. 누적 진행률 표시줄을 사용 하 여 5 개 이상의 동시 작업 또는 프로세스를 보고 하지 않습니다. 보고할 동시 작업 또는 프로세스가 다섯 개 이상 있는 경우에는 취소 단추가 있는 모달 대화 상자를 사용 하 여 진행률 정보를 출력 창에 보고 합니다.

##### <a name="textual-descriptions"></a>텍스트 설명
 텍스트 설명을 사용 하 여 발생 하는 작업과 예상 완료 시간을 함께 제공 합니다. 작업이 수행 되는 기간을 결정 하는 것이 불가능 한 경우 피드백을 제공 하는 데 더 나은 선택은 진행률 표시줄이 아닌 애니메이션 아이콘이 될 수 있습니다.

 Visual Studio는 Visual Studio에 통합 된 모든 제품에서 사용할 수 있는 상태 표시줄에 표준 진행률 표시줄을 제공 합니다. 진행률 표시줄에 애니메이션을 적용 하는 동안 발생 하는 상황에 대 한 텍스트 설명은 상태 표시줄 텍스트를 업데이트할 수 있습니다.

#### <a name="other-progress-indicators"></a>기타 진행률 표시기

##### <a name="ants-animated-horizontal-dots"></a>서 점 (가로 애니메이션 가로 점)
 ![진행률 ants](../../extensibility/ux-guidelines/media/0903-01-ants.png "0903-01_Ants")

 "공동 작업"에 애니메이션 된 가로 점이 있으면 결정 되지 않은 왕복 서버 프로세스에 대 한 시각적 참조가 제공 됩니다.

##### <a name="spinner-progress-ring"></a>회전자 (진행률 링)
 ![진행률 회전자](../../extensibility/ux-guidelines/media/0903-02-spinner.png "0903-02_Spinner")

 회전자 ("진행 링"이 라고도 함)는 컨텍스트 UI와 관련 하 여 주로 사용 되는 결정 되지 않은 진행률 표시기입니다. 텍스트 범주 헤더, 메시징, 컨트롤 등의 관련 콘텐츠와 근접 하 게 회전자를 표시 합니다.

##### <a name="cursor-feedback"></a>커서 피드백
 2-7 초 사이에 수행 되는 작업의 경우 커서 피드백을 제공 합니다. 일반적으로이는 운영 체제에서 제공 하는 대기 커서를 사용 하는 것을 의미 합니다. 지침은 MSDN 문서 [커서. Wait 속성](https://msdn.microsoft.com/library/system.windows.input.cursors.wait\(v=vs.110\).aspx)을 참조 하세요.

#### <a name="progress-indicator-locations"></a>진행률 표시기 위치

##### <a name="status-bar"></a>상태 표시줄
 상태 표시줄은 사용자의 작업을 중단 하지 않고 메시지 및 유용한 정보를 사용자에 게 표시 하는 기능을 응용 프로그램에 제공 합니다. 일반적으로 창의 아래쪽에 표시 되는 진행률 상태는 진행률 표시줄 표시기와 함께 진행률 측정값에 대 한 메시지를 포함 하는 도구 설명 창이 됩니다.

 ![진행률 표시줄을 사용하는 상태 표시줄](../../extensibility/ux-guidelines/media/0903-03-statusbarprogressbar.png "0903-03_StatusBarProgressBar")

 **진행률 표시줄을 사용하는 상태 표시줄**

 ![메시징을 사용하는 상태 표시줄](../../extensibility/ux-guidelines/media/0903-04-statusbarmessage.png "0903-04_StatusBarMessage")

 **텍스트 설명이 있는 상태 표시줄**

##### <a name="infobar"></a>정보 표시줄
 상태 표시줄과 마찬가지로, 정보 표시줄에는 진행률 표시줄 또는 회전자와 같이 확정 되지 않은 진행률 표시기와 쌍으로 연결 될 수 있는 상황에 맞는 알림 및 메시징이 제공 됩니다. 정보 표시줄에서 세부적인 수준 진행률 또는 활성화 상태의 진행률 표시를 제공 해서는 안 됩니다. [정보 표시줄](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)를 참조 하세요.

 ![진행률 표시줄 및 메시징을 사용하는 정보 표시줄](../../extensibility/ux-guidelines/media/0903-05-infobar.png "0903-05_InfoBar")

 **진행률 표시줄 및 텍스트 설명이 포함 된 정보 표시줄**

 ![창 내의 정보 표시줄](../../extensibility/ux-guidelines/media/0903-06-infobarinwindow.png "0903-06_InfoBarInWindow")

 **코드 분석 창 내 정보 표시줄**

##### <a name="inline"></a>인라인
 인라인 진행률 표시는 진행 로더 형식 중 하나로 표시 될 수 있습니다. 일반적으로 진행률 표시기는 메시징과 페어링 되지만 반드시 필요한 것은 아닙니다.

 ![인라인 진행률 회전자](../../extensibility/ux-guidelines/media/0903-07-inlinespinner.png "0903-07_InlineSpinner")

 **텍스트 설명과 함께 사용 되는 회전자**

 ![인라인 누적 진행률 표시줄](../../extensibility/ux-guidelines/media/0903-08-inlinestackedprogress.png "0903-08_InlineStackedProgress")

 **활성화 상태의 누적 진행률 표시줄**

 ![인라인 진행률 메시징](../../extensibility/ux-guidelines/media/0903-09-inlinetext.png "0903-09_InlineText")

 **인라인 텍스트 서버 탐색기: 새로 고치는 중 ...**

##### <a name="tool-windows"></a>도구 창
 전역 진행률 표시는 도구 모음 바로 아래에 있는 확정 되지 않은 진행률 막대로 표시 됩니다.

 ![전역 비활성화 상태의 진행률 표시줄](../../extensibility/ux-guidelines/media/0903-23-globalindeterminate.png "0903-23_GlobalIndeterminate")

 **팀 탐색기 전역 확정 되지 않은 진행률 표시줄**

##### <a name="dialogs"></a>대화 상자
 대화에는 진행률 로더 형식이 모두 포함 될 수 있습니다. 진행률 표시기는 메시징과 함께 사용할 수 있으며 여러 단계의 진행률 표시와 함께 사용 하 여 세분화 된 하위 프로세스를 나타낼 수 있습니다.

 ![여러 진행률 표시기 유형이 있는 대화 상자](../../extensibility/ux-guidelines/media/0903-11-dialog.png "0903-11_Dialog")

 **동시 프로세스 및 여러 진행률 표시기 유형을 포함 하는 Visual Studio 대화 상자**

 ![진행률 로더 및 메시징이 있는 대화 상자](../../extensibility/ux-guidelines/media/0903-12-dialog2.png "0903-12_Dialog2")

 **진행률 로더 및 메시징 인라인 명령을 포함 하는 Visual Studio 대화 상자**

##### <a name="document-well"></a>문서 웰
 문서 웰은 여러 진행률 로더 형식을 컨트롤과 함께 표시할 수 있습니다.

 ![문서의 진행률 메시징](../../extensibility/ux-guidelines/media/0903-13-documentwell.png "0903-13_DocumentWell")

 **확정 되지 않은 진행률 표시줄의 도구 모음**

##### <a name="output-window"></a>출력 창
 출력 창은 인라인 텍스트 메시징을 통해 프로세스 진행 및 진행 중인 진행 상태를 처리 하는 데 적합 합니다. 출력 창 진행률 보고와 함께 상태 표시줄을 사용 해야 합니다.

 ![출력 창의 진행률 메시징](../../extensibility/ux-guidelines/media/0903-14-outputwindow.png "0903-14_OutputWindow")

 **진행 중인 프로세스 상태 및 대기 메시징으로 출력 창**

## <a name="infobars"></a><a name="BKMK_Infobars"></a> 정보 표시줄

### <a name="overview"></a>개요
 정보 표시줄 사용자에 게 주목 지점에 가까운 표시기를 제공 하 고, 공유 정보 표시줄 컨트롤을 사용 하 여 시각적 모양 및 상호 작용의 일관성을 보장 합니다.

 ![정보 표시줄](../../extensibility/ux-guidelines/media/0904-01-infobar.png "0904-01_Infobar")

 **Visual Studio의 정보 표시줄**

#### <a name="appropriate-uses-for-an-infobar"></a>정보 표시줄에 적절 한 사용

- 사용자에 게 현재 컨텍스트와 관련 된 차단 되지 않지만 중요 한 메시지를 제공 하려면

- UI가 기록 디버깅과 같은 일부 상호 작용에 영향을 주는 특정 상태 또는 조건에 있음을 나타내려면

- 확장으로 인해 성능 문제가 발생 하는 경우와 같이 시스템에서 문제를 감지 했음을 사용자에 게 알리기 위해

- 편집기에서 파일에 혼합 된 탭과 공백이 있는 것으로 감지 되는 경우와 같이 사용자에 게 쉽게 작업을 수행할 수 있는 방법을 제공 합니다.

##### <a name="do"></a>권장 사항:

- 정보 표시줄 메시지 텍스트를 지점으로 짧게 유지 합니다.

- 링크 및 단추에 대 한 텍스트를 간결 하 게 유지 합니다.

- 사용자에 게 제공 하는 "작업" 옵션이 최소화 되어 필요한 동작만 표시 되도록 합니다.

##### <a name="dont"></a>안 함:

- 도구 정보를 사용 하 여 도구 모음에 배치 해야 하는 표준 명령을 제공 합니다.

- 모달 대화 상자 대신 정보 표시줄을 사용 합니다.

- 창 외부에서 부동 메시지를 만듭니다.

- 동일한 창 내의 여러 위치에서 여러 정보 표시줄를 사용 합니다.

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>여러 정보 표시줄 동시에 표시 될 수 있나요?
 예, 여러 정보 표시줄 동시에 표시 될 수 있습니다. 가장 먼저 표시 되는 첫 번째 정보 표시줄이 표시 되 고 맨 위에 표시 되는 첫 번째 정보 표시줄이 표시 되 고 첫 번째로 제공 되는 순서 대로 표시 됩니다.

 사용자에 게 한 번에 최대 3 개의 정보 표시줄 표시 되 고 그 후에는 정보 표시줄를 사용할 수 있는 경우 정보 표시줄 지역이 스크롤할 수 있게 됩니다.

### <a name="creating-an-infobar"></a>정보 표시줄 만들기
 정보 표시줄에는 왼쪽에서 오른쪽으로 4 개의 섹션이 있습니다.

- **아이콘:** 여기에서 경고 아이콘과 같이 정보 표시줄에 표시할 아이콘을 추가할 수 있습니다.

- **텍스트:** 텍스트를 추가 하 여 필요한 경우 텍스트 내 링크와 함께 시나리오/상황을 설명 합니다. 텍스트를 간결 하 게 유지 해야 합니다.

- **작업:** 이 섹션에는 사용자가 정보 표시줄에서 수행할 수 있는 작업에 대 한 링크와 단추가 포함 됩니다.

- **닫기 단추:** 오른쪽의 마지막 섹션에는 닫기 단추가 있을 수 있습니다.

#### <a name="creating-a-standard-infobar-in-managed-code"></a>관리 코드에서 표준 정보 표시줄 만들기
 InfoBarModel 클래스를 사용 하 여 정보 표시줄의 데이터 소스를 만들 수 있습니다. 다음 네 가지 생성자 중 하나를 사용 합니다.

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

 하이퍼링크, 동작 단추 및 아이콘이 있는 텍스트를 사용 하 여 InfoBarModel을 만드는 예제는 다음과 같습니다.

 ![하이퍼링크가 포함된 정보 표시줄](../../extensibility/ux-guidelines/media/0904-02-infobarhyperlink.png "0904-02_InfobarHyperlink")

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
 네이티브 코드의 정보 표시줄을 제공 하기 위해 IVsInfoBar 같은 인터페이스를 구현 합니다.

```
public interface IVsInfoBar
{
    IVsInfoBarActionItemCollection ActionItems { get; }
    ImageMoniker Image { get; }
    bool IsCloseButtonVisible { get; }
    IVsInfoBarTextSpanCollection TextSpans { get; }
}

```

#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>정보 표시줄에서 정보 표시줄 UIElement 가져오기
 InfoBarModel 또는 IVsInfoBar 표시줄 구현은 UI에 표시 되기 위해 UIElement로 전환 되어야 하는 데이터 모델입니다. SVsInfoBarUIFactory/IVsInfoBarUIFactory 서비스를 사용 하 여 UIElement를 검색할 수 있습니다.

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
 정보 표시줄는 다음 위치 중 하나 이상에 표시 될 수 있습니다.

- 도구 창

- 문서 탭 내에서

> [!IMPORTANT]
> 전역 컨텍스트에 대 한 메시지를 제공 하기 위해 정보 표시줄을 배치할 수 있습니다. 이는 도구 모음과 문서 웰 사이에 표시 됩니다. IDE의 "점프 및 jerk"에서 문제가 발생 하 고 반드시 필요한 경우에만 피해 야 하므로이 방법은 사용 하지 않는 것이 좋습니다.

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>ToolWindowPane에 정보 표시줄 배치
 ToolWindowPane 정보 표시줄 (IVsInfoBar) 메서드를 사용 하 여 도구 창에 정보 표시줄을 추가할 수 있습니다. 이 API는 IVsInfoBar 표시줄 (기본 구현인 InfoBarModel) 또는 IVsUIElement를 추가할 수 있습니다.

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>문서에 정보 표시줄 배치 또는 비 ToolWindowPane
 모든 IVsWindowFrame에 정보 표시줄을 저장 하려면 VSFPROPID_InfoBarHost 속성을 사용 하 여 프레임에 대 한 IVsInfoBarHost를 가져온 다음 정보 표시줄 UIElement를 추가 합니다.

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

#### <a name="placing-an-infobar-in-the-main-window"></a>주 창에 정보 표시줄 배치
 주 창에 정보 표시줄을 저장 하려면 IVsShell 서비스의 VSSPROPID_MainWindowInfoBarHost를 사용 하 여 주 창의 IVsInfoBarHost를 가져온 다음 정보 표시줄 UIElement를 추가 합니다.

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>사용자가 내 정보 표시줄에서 작업을 수행 하는 시기를 알 수 있나요?
 예, 모든 이벤트 작업을 정보 표시줄 작성자에 게 반환 합니다. 그러면 정보 표시줄 작성자가 정보 표시줄의 사용자 선택에 따라 IDE에서 작업을 수행 합니다. 정보 표시줄는 닫기 단추를 클릭 한 호스트에서 자동으로 제거 되지만, 닫기 후 다른 정보 표시줄를 제거 해야 하는 경우 추가 작업이 필요 합니다. 또한 원격 분석은 각 정보 표시줄에 독립적으로 기록해 야 합니다.

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>ToolWindowPane에서 정보 표시줄 이벤트 받기
 ToolWindowPane에는 정보 표시줄에 대 한 두 개의 이벤트가 있습니다. ToolWindowPane의 정보 표시줄이 닫히면 InfoBarClosed 이벤트가 발생 합니다. InfoBarActionItemClicked 이벤트는 정보 표시줄 내의 하이퍼링크나 단추를 클릭할 때 발생 합니다.

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>UIElement에서 직접 정보 표시줄 이벤트 받기
 IVsInfoBarUIElement. Advise는 정보 표시줄의 UIElement에서 직접 이벤트를 구독 하는 데 사용할 수 있습니다. IVsInfoBarUIEvents를 구현 하면 작성자가 닫기 및 클릭 이벤트를 받을 수 있습니다.

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

## <a name="error-validation"></a><a name="BKMK_ErrorValidation"></a> 오류 유효성 검사
 필수 필드를 건너뛰거나 잘못 된 형식으로 데이터를 입력 하는 경우와 같이 사용자가 허용 되지 않는 정보를 입력 하는 경우 차단 팝업 오류 대화 상자를 사용 하는 대신 컨트롤의 컨트롤 유효성 검사 나 사용자 의견을 사용 하는 것이 좋습니다.

### <a name="field-validation"></a>필드 유효성 검사
 폼 및 필드 유효성 검사는 컨트롤, 아이콘 및 도구 설명의 세 가지 구성 요소로 구성 됩니다. 여러 형식의 컨트롤이이를 사용할 수 있지만 텍스트 상자는 예제로 사용 됩니다.

 ![필드 유효성 검사 &#40;비어&#41;](../../extensibility/ux-guidelines/media/0905-01-fieldvalidation.png "0905-01_FieldValidation")

 필드가 필요한 경우에는 워터 마크 텍스트가 있어야 **\<Required>** 하며, 필드 배경은 연한 노랑 (vscolor: `Environment.ControlEditRequiredBackground` ) 이어야 하 고 전경 (vscolor:)은 회색 이어야 합니다 `Environment.ControlEditRequiredHintText` .

 !["필수" 레이블이 있는 필드 유효성 검사](../../extensibility/ux-guidelines/media/0905-02-fieldvalidationrequired.png "0905-02_FieldValidationRequired")

 이 프로그램은 포커스가 다른 컨트롤로 이동 하거나 사용자가 [확인] 커밋 단추를 클릭 하거나 사용자가 문서 또는 양식을 저장할 때 컨트롤이 *입력 한 잘못 된 내용* 상태에 있음을 확인할 수 있습니다.

 잘못 된 콘텐츠 상태가 확인 되 면 컨트롤 내부 또는 바로 옆에 아이콘이 표시 됩니다. 아이콘 또는 컨트롤 가리키기에 오류를 설명 하는 도구 설명이 표시 됩니다. 또한 잘못 된 상태를 만드는 컨트롤 주위에 1 픽셀 테두리가 표시 되어야 합니다.

 ![필드 유효성 검사 레이아웃 사양](../../extensibility/ux-guidelines/media/0905-03-layoutspecs.png "0905-03_LayoutSpecs")

 **필드 유효성 검사에 대 한 레이아웃 사양**

#### <a name="acceptable-variations-for-icon-location"></a>아이콘 위치에 대해 허용 되는 변형
 사용자가 유효성 검사 오류에 대해 알고 있어야 하는 수많은 고유 사례가 있습니다. UI의 컨트롤 형식 및 구성을 고려 하 여 상황에 적합 한 아이콘 배치를 선택 합니다.

 ![아이콘 위치에 적합한 위치](../../extensibility/ux-guidelines/media/0905-04-iconlocation.png "0905-04_IconLocation")

 **필드 유효성 검사 아이콘 위치에 대해 허용 되는 변형**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>서버 또는 네트워크 연결에 대 한 라운드트립이 필요한 유효성 검사
 경우에 따라 콘텐츠를 확인 하는 데 서버에 대 한 라운드트립이 필요 하며, 사용자 진행률, 확인 됨 및 오류 상태를 표시 하는 것이 중요 합니다. 아래 그림은 이러한 사례와 권장 UI의 예를 보여 줍니다.

 ![서버에 대한 왕복과 관련된 유효성 검사](../../extensibility/ux-guidelines/media/0905-05-roundtrip.png "0905-05_RoundTrip")

 **서버에 대한 왕복과 관련된 유효성 검사**

 컨트롤의 오른쪽에 사용할 수 있는 충분 한 공간을 제공 해야 합니다. 및 "Retry" 텍스트

#### <a name="in-place-warning-text"></a>내부 경고 텍스트
 오류 상태에서 컨트롤에 가까운 오류 메시지를 넣을 수 있는 공간이 있는 경우 도구 설명만 사용 하는 것이 좋습니다.

 ![&#45;발생 경고](../../extensibility/ux-guidelines/media/0905-06-inplacewarning.png "0905-06_InPlaceWarning")

 **내부 경고 텍스트**

#### <a name="watermarks"></a>워터마크
 경우에 따라 전체 컨트롤 또는 창이 오류 상태에 있습니다. 이 경우 워터 마크를 사용 하 여 오류를 표시 합니다.

 ![워터마크](../../extensibility/ux-guidelines/media/0905-07-watermark.png "0905-07_Watermark")

 **워터 마크 필드 유효성 검사**
