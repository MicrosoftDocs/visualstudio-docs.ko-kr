---
title: Visual Studio 업데이트
titleSuffix: ''
description: 가장 최신 릴리스로 Visual Studio를 업데이트하는 방법을 단계별로 알아봅니다.
ms.date: 07/31/2019
ms.custom: seodec18
ms.topic: conceptual
ms.prod: visual-studio-windows
ms.technology: vs-installation
helpviewer_keywords:
- update [Visual Studio]
- change [Visual Studio]
f1_keywords:
- VS.ToolsOptionsPages.Environment.ProductUpdates
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 19da163c76724ae56c0e3d83f1ed795333d081d5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77453397"
---
# <a name="update-visual-studio-to-the-most-recent-release"></a>Visual Studio를 최신 릴리스 버전으로 업데이트

::: moniker range="vs-2017"

항상 최신 기능, 수정 사항 및 개선 사항을 사용할 수 있도록 Visual Studio 2017의 [최신 릴리스](/visualstudio/releasenotes/vs2017-relnotes/)로 업데이트하는 것이 좋습니다.

최신 버전을 사용해 보려는 경우 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)를 대신 다운로드 및 설치합니다.

> [!IMPORTANT]
> Visual Studio를 설치, 업데이트 또는 수정하려면 관리 권한이 있는 계정으로 로그온해야 합니다. 자세한 내용은 [사용자 권한 및 Visual Studio](../ide/user-permissions-and-visual-studio.md)를 참조하세요.
>
> [!NOTE]
> 이 토픽은 Windows의 Visual Studio에 적용됩니다. Mac용 Visual Studio는 [Mac용 Visual Studio 업데이트](/visualstudio/mac/update)를 참조하세요.

## <a name="update-visual-studio-2017-version-156-or-later"></a>Visual Studio 2017 버전 15.6 이상 업데이트

IDE 내에서 바로 사용하기 쉽도록 설치 및 업데이트 환경이 간소화되었습니다. 버전 15.6 이상에서 최신 버전의 Visual Studio로 업데이트하는 방법은 다음과 같습니다.

### <a name="using-the-notifications-hub"></a>알림 허브 사용

업데이트가 있으면 Visual Studio에 해당 알림 플래그가 있습니다.

1. 작업을 저장합니다.

1. 알림 플래그를 선택하여 **알림** 허브를 열고 설치할 업데이트를 선택합니다.

   ![알림 허브를 사용하여 Visual Studio 2017 업데이트](media/vs-install-notifications-hub-15dot6.png "Visual Studio 2017의 알림 허브")

      > [!TIP]
      > Visual Studio 2017 버전의 업데이트는 누적되므로 항상 최신 버전 번호를 사용하여 설치하세요.

1. **업데이트** 대화 상자가 열리면 **지금 업데이트**를 선택합니다.

    ![알림 허브의 업데이트 대화 상자를 사용하여 Visual Studio 2017 업데이트](media/vs-update-now-from-notifications-hub.png "Visual Studio의 알림 허브에서 표시되는 업데이트 대화 상자")

     사용자 액세스 제어 대화 상자가 열리면 **예**를 선택합니다. “잠시 기다려 주세요.” 대화 상자가 잠시 열릴 수 있으며, 그런 다음, Visual Studio 설치 관리자가 열려 업데이트를 시작합니다.

     ![버전 15.6의 새로운 Visual Studio 설치 관리자 환경](media/visual-studio-15dot6-installer.png "버전 15.6의 새로운 Visual Studio 설치 관리자 환경")

     업데이트가 계속됩니다. 업데이트가 완료되면 Visual Studio가 다시 시작됩니다.

     > [!NOTE]
     > Visual Studio를 관리자 모드로 실행하는 경우에는 업데이트 후 Visual Studio를 수동으로 다시 시작해야 합니다.

### <a name="using-the-ide"></a>IDE 사용

업데이트를 확인한 다음, Visual Studio의 메뉴 표시줄에서 업데이트를 설치할 수 있습니다.

1. 작업을 저장합니다.

1. **도움말** > **업데이트 확인**을 선택합니다.

     ![Visual Studio 버전 15.6의 새 도움말 메뉴](media/vs-help-menu-check-for-updates.png "Visual Studio 버전 15.6의 새 도움말 메뉴")

1. **업데이트** 대화 상자가 열리면 **지금 업데이트**를 선택합니다.

   이전 섹션에서 설명한 대로 업데이트가 진행되고, 업데이트가 완료되면 Visual Studio가 다시 시작됩니다.

   > [!NOTE]
   > Visual Studio를 관리자 모드로 실행하는 경우에는 업데이트 후 Visual Studio를 수동으로 다시 시작해야 합니다.

### <a name="using-the-visual-studio-installer"></a>Visual Studio 설치 관리자 사용

이전 버전의 Visual Studio와 마찬가지로, Visual Studio 설치 관리자를 사용하여 업데이트를 설치할 수 있습니다.

1. 작업을 저장합니다.

1. 설치 관리자를 엽니다. 계속하기 전에 Visual Studio 설치 관리자를 업데이트해야 할 수도 있습니다.

   > [!NOTE]
   > Windows 10을 실행하는 컴퓨터에서는 **V** 문자 아래에 **Visual Studio 설치 관리자**로 설치 관리자가 나타나거나, **M** 문자 아래에 **Microsoft Visual Studio 설치 관리자**로 나타납니다.

1. 설치 관리자의 **제품** 페이지에서 이전에 설치한 Visual Studio 버전을 찾습니다.

1. 업데이트를 사용할 수 있는 경우 **업데이트** 단추가 표시됩니다. (설치 관리자가 업데이트를 사용할 수 있는지 여부를 확인하는 데 몇 초 정도 걸릴 수 있습니다.)

   **업데이트** 단추를 선택하여 업데이트를 설치합니다.

     ![Visual Studio 설치 관리자를 사용하여 Visual Studio 2017 업데이트](media/update-visual-studio.png "Visual Studio 설치 관리자를 사용하여 Visual Studio 2017 업데이트")

## <a name="update-visual-studio-2017-version-155-or-earlier"></a>Visual Studio 2017 버전 15.5 또는 이전 버전 업데이트

이전 버전을 사용하는 경우 Visual Studio 2017 버전 15.0~버전 15.5에서 업데이트를 적용하는 방법은 다음과 같습니다.

### <a name="update-by-using-the-notifications-hub"></a>알림 허브를 사용하여 업데이트

1. 업데이트가 있으면 Visual Studio에 해당 알림 플래그가 있습니다.

   ![알림 허브를 사용하여 Visual Studio 2017 업데이트](media/notification-flag.png "Visual Studio의 업데이트 알림 플래그")

   알림 플래그를 선택하여 **알림** 허브를 엽니다.

   ![알림 허브를 사용하여 Visual Studio 2017 업데이트](media/notifications-hub.png "Visual Studio의 알림 허브")

      > [!TIP]
      > Visual Studio 2017 버전의 업데이트는 누적되므로 항상 최신 버전 번호를 사용하여 설치하세요.

1. **“Visual Studio 업데이트” 사용 가능**을 선택하여 **확장 및 업데이트** 대화 상자를 엽니다.

   ![알림 허브를 사용하여 Visual Studio 2017 업데이트](media/notifications-hub-select.png "Visual Studio의 알림 허브")

1. **확장 및 업데이트** 대화 상자에서 **업데이트** 단추를 선택합니다.

   ![알림 허브를 사용하여 Visual Studio 2017 업데이트](media/notifications-extensions-and-updates.png "Visual Studio의 확장 및 업데이트 대화 상자")

#### <a name="more-about-visual-studio-notifications"></a>Visual Studio 알림 상세 정보

Visual Studio는 Visual Studio 자체나 구성 요소에 사용 가능한 업데이트가 있을 때와, Visual Studio 환경에서 특정 이벤트가 발생했을 때 이를 사용자에게 알립니다.

* 알림 플래그가 노랑이면 설치할 수 있는 Visual Studio 제품 업데이트가 있습니다.
* 알림 플래그가 빨강이면 라이선스에 문제가 있습니다.
* 알림 플래그가 검정이면 확인이 필요한 선택적 또는 정보 메시지가 있습니다.

알림 플래그를 선택하여 **알림** 허브를 열고 조치할 알림을 선택합니다. 또는 알림을 무시하거나 해제합니다.

 ![알림 허브에서 선택적 또는 정보 메시지 보기](media/notification-flag-optional.png "Visual Studio의 선택적 또는 정보 메시지 알림 플래그")

알림을 무시하도록 선택한 경우 Visual Studio에서 알림 표시를 중지합니다. 무시된 알림 목록을 다시 설정하려면 알림 허브에서 **설정** 단추를 선택합니다.

   ![알림 허브에서 설정 단추를 선택하여 알림 옵션 보기](media/vs-notifications-hub-settings-button.png "알림 허브에서 설정 단추를 선택하여 알림 옵션 보기")

### <a name="update-by-using-the-visual-studio-installer"></a>Visual Studio 설치 관리자를 사용하여 업데이트

1. 설치 관리자를 엽니다. 계속하기 전에 설치 관리자를 업데이트해야 할 수 있습니다. 이 경우 업데이트하라는 메시지가 나타납니다.

   > [!NOTE]
   > Windows 10을 실행하는 컴퓨터에서는 **V** 문자 아래에 **Visual Studio 설치 관리자**로 설치 관리자가 나타나거나, **M** 문자 아래에 **Microsoft Visual Studio 설치 관리자**로 나타납니다.

1. 설치 관리자의 **제품** 페이지에서 이전에 설치한 Visual Studio 버전을 찾습니다.

1. 업데이트를 사용할 수 있는 경우 **업데이트** 단추가 표시됩니다. (설치 관리자가 업데이트를 사용할 수 있는지 여부를 확인하는 데 몇 초 정도 걸릴 수 있습니다.)

   **업데이트** 단추를 선택하여 업데이트를 설치합니다.

     ![Visual Studio 설치 관리자를 사용하여 Visual Studio 2017 업데이트](media/update-visual-studio.png "Visual Studio 설치 관리자를 사용하여 Visual Studio 업데이트")

::: moniker-end

::: moniker range="vs-2019"

항상 최신 기능, 수정 사항 및 개선 사항을 사용할 수 있도록 Visual Studio 2019의 [최신 릴리스](/visualstudio/releases/2019/release-notes/)로 업데이트하는 것이 좋습니다.

아직 Visual Studio 2019를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads) 페이지로 이동하여 체험용으로 설치합니다. 현재 다른 버전의 Visual Studio를 사용 중인 경우 [Visual Studio 버전을 나란히 설치](../install/install-visual-studio-versions-side-by-side.md)하거나 [이전 버전의 Visual Studio를 제거](../install/uninstall-visual-studio.md)할 수 있습니다.

> [!IMPORTANT]
> Visual Studio를 설치, 업데이트 또는 수정하려면 관리 권한이 있는 계정으로 로그온해야 합니다. 자세한 내용은 [사용자 권한 및 Visual Studio](../ide/user-permissions-and-visual-studio.md)를 참조하세요.
>
> [!NOTE]
> 이 토픽은 Windows의 Visual Studio에 적용됩니다. Mac용 Visual Studio는 [Mac용 Visual Studio 업데이트](/visualstudio/mac/update)를 참조하세요.

Visual&nbsp;Studio&nbsp;2019를 업데이트하는 방법은 다음과 같습니다.

## <a name="use-the-visual-studio-installer"></a>Visual Studio 설치 관리자 사용

1. 설치 관리자를 엽니다.

     ![Windows에서 Visual Studio 설치 관리자 열기](media/vs-2019/vs-installer-windows-start.png "Visual Studio 설치 관리자 열기")

   계속하기 전에 설치 관리자를 업데이트해야 할 수 있습니다. 그렇다면 지시를 따르세요.

1. 설치 관리자에서 설치한 Visual Studio의 버전을 찾습니다.

   예를 들어 이전에 Visual&nbsp;Studio Community&nbsp;2019를 설치했으며 업데이트가 있는 경우, **업데이트 사용 가능** 메시지가 설치 관리자에 표시됩니다.

     ![업데이트할 Visual Studio 2019 버전 선택](media/vs-2019/vs-installer-update-visual-studio-community.png "업데이트할 Visual Studio 2019 버전 선택")

1. **업데이트**를 선택하여 업데이트를 설치합니다.

    ![업데이트 단추를 선택하여 업데이트 설치](media/vs-2019/vs-installer-choose-update-visual-studio-community.png "업데이트 단추를 선택하여 업데이트 설치")

1. 업데이트가 완료되면 컴퓨터를 다시 시작하라는 메시지가 표시될 수 있습니다. 그러면 컴퓨터를 다시 시작한 후 평상시와 같은 방법으로 Visual Studio를 시작합니다.

   컴퓨터를 다시 시작하라는 메시지가 표시되지 않으면 **시작**을 선택하여 설치 관리자에서 Visual Studio를 시작합니다.

    ![시작 단추를 선택하여 Visual Studio 시작](media/vs-2019/choose-launch-visual-studio-community.png "시작 단추를 선택하여 Visual Studio 시작")

## <a name="use-the-ide"></a>IDE 사용

업데이트를 확인한 다음, Visual Studio 2019의 메뉴 표시줄 또는 검색 상자를 사용하여 설치할 수 있습니다.

### <a name="open-visual-studio"></a>Visual Studio 열기

1. Windows **시작** 메뉴에서 **Visual Studio 2019**를 선택합니다.

    ![Visual Studio 2019 열기](media/vs-2019/vs-installer-visual-studio-2019.png "Windows에서 Visual Studio 2019 열기")

1. **시작**에서 IDE를 여는 옵션을 선택합니다.

    ![Visual Studio 설치 관리자 열기](media/vs2019-choose-option-from-get-started.png "Visual Studio 설치 관리자 열기")

    Visual Studio가 열립니다. IDE에 **Visual Studio 2019 업데이트** 메시지가 표시됩니다.

    ![IDE의 'Visual Studio 2019 업데이트' 메시지](media/vs-2019/update-visual-studio-ide-message.png "IDE의 'Visual Studio 2019 업데이트' 메시지")

1. **Visual Studio 2019 업데이트** 메시지에서 **세부 정보 보기**를 선택합니다.

   ![Visual Studio 2019 IDE 업데이트 메시지에서 세부 정보 보기 단추 선택](media/vs-2019/update-visual-studio-ide-view-details.png "Visual Studio 2019 업데이트 메시지에서 세부 정보 보기 단추 선택")

1. **업데이트 다운로드 및 설치 준비** 대화 상자에서 **업데이트**를 선택합니다.

     !['업데이트 다운로드 및 설치 준비' 대화 상자에서 업데이트 단추 선택](media/vs-2019/update-ready-install-visual-studio-community-from-ide.png "'업데이트 다운로드 및 설치 준비' 대화 상자에서 업데이트 단추 선택")

   Visual Studio가 업데이트되고, 닫힌 다음, 다시 열립니다.

### <a name="in-visual-studio"></a>Visual Studio에서

1. 메뉴 모음에서 **도움말**을 선택한 다음, **업데이트 확인**을 선택합니다.

     ![도움말 메뉴에서 '업데이트 확인' 선택](media/vs-2019/vs-ide-check-updates-help-menu.png "도움말 메뉴에서 '업데이트 확인' 선택")

    > [!NOTE]
    > IDE의 검색 상자를 사용하여 업데이트를 확인할 수도 있습니다. **Ctrl**+**Q**를 누르고, “업데이트 확인”을 입력한 다음, 일치하는 검색 결과를 선택합니다.

1. **업데이트 사용 가능** 대화 상자에서 **업데이트**를 선택합니다.

     !['업데이트 다운로드 및 설치 준비' 대화 상자에서 업데이트 단추 선택](media/vs-2019/update-visual-studio-community-from-ide.png "'업데이트 다운로드 및 설치 준비' 대화 상자에서 업데이트 단추 선택")

   Visual Studio가 업데이트되고, 닫힌 다음, 다시 열립니다.

## <a name="use-the-notifications-hub"></a>알림 허브 사용

1. Visual Studio에서 작업을 저장합니다.

1. Visual Studio IDE의 오른쪽 아래 모퉁이에서 알림 아이콘을 선택하여 **알림** 허브를 엽니다.

   ![Visual Studio IDE의 알림 아이콘](media/vs-2019/notification-bar.png "Visual Studio IDE의 알림 아이콘")

1. **알림 허브**에서 설치할 업데이트를 선택한 다음, **세부 정보 보기**를 선택합니다.

     ![Visual Studio 2019의 알림 허브](media/vs-2019/notification-hub-update.png "Visual Studio 2019의 알림 허브")

      > [!TIP]
      > Visual Studio 2019 버전의 업데이트는 누적되므로 항상 최신 버전 번호를 사용하여 설치하세요.

1. **업데이트 사용 가능** 대화 상자에서 **업데이트**를 선택합니다.

   Visual Studio가 업데이트되고, 닫힌 다음, 다시 열립니다.

## <a name="customize-update-settings"></a>업데이트 설정 사용자 지정

설치 모드를 변경하고 자동 다운로드를 선택하는 등의 방법으로 Visual Studio에서 업데이트 설정을 사용자 지정할 수 있습니다.

선택할 수 있는 설치 모드는 두 가지입니다.

* **다운로드하는 동안 설치**
* **모두 다운로드한 후 설치**

**업데이트 자동 다운로드** 설정을 선택하여 컴퓨터가 유휴 상태일 때 업데이트가 다운로드되도록 할 수 있습니다.

방법은 다음과 같습니다.

1. 메뉴 모음에서 **도구** > **옵션**을 선택합니다.

2. **환경**을 확장한 다음 **제품 업데이트**를 선택합니다.

    ![Visual Studio의 업데이트 설정](media/vs-2019/update-settings-options.png)

3. Visual Studio 업데이트에 대한 설치 모드 및 자동 다운로드 옵션을 선택합니다.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참고 항목

* [Visual Studio 버전 side-by-side 설치](install-visual-studio-versions-side-by-side.md)
* [Visual Studio의 네트워크 기반 설치 업데이트](update-a-network-installation-of-visual-studio.md)
* [서비스 기준선에서 Visual Studio 업데이트](update-servicing-baseline.md)
* [네트워크 기반 Visual Studio 배포에 대한 업데이트 제어](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio 수정](modify-visual-studio.md)
* [Visual Studio 제거](uninstall-visual-studio.md)
