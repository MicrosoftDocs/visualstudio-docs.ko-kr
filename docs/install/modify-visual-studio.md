---
title: Visual Studio 수정
titleSuffix: ''
description: Visual Studio를 수정하는 방법을 단계별로 알아봅니다.
ms.date: 02/10/2019
ms.topic: how-to
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 2ec3ae3f253997b86c2403ce57d5e8db6e9920b4
ms.sourcegitcommit: 9e15138a34532b222e80f6b42b1a9de7b2fe0175
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85419187"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>워크로드와 구성 요소를 추가하거나 제거하여 Visual Studio 수정

::: moniker range="vs-2019"

Visual Studio를 쉽게 수정할 수 있어 원하는 때에 원하는 대로 포함할 수 있습니다. 이렇게 하려면 Visual Studio 설치 관리자를 열어 워크로드 및 구성 요소를 추가하거나 제거합니다.

::: moniker-end

::: moniker range="vs-2017"

수행하려는 작업에 맞게 Visual Studio를 쉽게 개인 설정할 수 있을 뿐만 아니라 더 쉽게 사용자 지정할 수도 있습니다. 이렇게 하려면 새로운 Visual Studio 설치 관리자를 열고 원하는 대로 변경하면 됩니다.

::: moniker-end

방법은 다음과 같습니다.

>[!IMPORTANT]
>Visual Studio를 설치, 업데이트 또는 수정하려면 관리 권한이 있는 계정으로 로그온해야 합니다. 자세한 내용은 [사용자 권한 및 Visual Studio](../ide/user-permissions-and-visual-studio.md)를 참조하세요.

>[!NOTE]
> 다음 절차에서는 인터넷 연결이 있다고 가정합니다.
>
> 이전에 만든 Visual Studio [오프라인 설치](create-an-offline-installation-of-visual-studio.md)를 수정하는 방법에 대한 자세한 내용은 [Visual Studio의 네트워크 기반 설치 업데이트](update-a-network-installation-of-visual-studio.md) 페이지와 [네트워크 기반 Visual Studio 배포에 대한 업데이트 제어](controlling-updates-to-visual-studio-deployments.md) 페이지를 참조하세요.

## <a name="open-the-visual-studio-installer"></a>Visual Studio 설치 관리자 열기

::: moniker range="vs-2017"

1. 컴퓨터에서 Visual Studio 설치 관리자를 찾습니다.

     예를 들어 Windows 10을 실행하는 컴퓨터에서 **시작**을 선택한 다음, **Visual Studio 설치 관리자**로 나열되는 **V** 문자로 스크롤합니다.

     ![Visual Studio 설치 관리자](media/locate-the-visual-studio-installer.png "Microsoft Visual Studio 설치 관리자 찾기")

     >[!TIP]
     >일부 컴퓨터에서는 Visual Studio 설치 관리자가 **Microsoft Visual Studio 설치 관리자**로 문자 **“M”** 아래에 나열될 수 있습니다.<br/><br/> 또는 다음 위치에서 Visual Studio 설치 관리자를 찾을 수 있습니다.`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. 설치 관리자를 연 다음 **수정**을 선택합니다.

     ![Visual Studio 시작 또는 수정](media/modify-visual-studio.png "Visual Studio 2017 수정")

     > [!IMPORTANT]
     > 보류 중인 업데이트가 있는 경우 수정 단추는 다른 위치에 있습니다. 이러한 방식으로 Visual Studio를 업데이트하지 않고 수정할 수 있습니다. **자세히**를 클릭한 다음, **수정**을 선택합니다.
     >
     > ![Visual Studio 업데이트 또는 수정](media/modify-or-update-visual-studio.png "Visual Studio 2017 업데이트 또는 수정")

::: moniker-end

::: moniker range="vs-2019"

1. 컴퓨터에서 Visual Studio 설치 관리자를 찾습니다.

     예를 들어 Windows 10을 실행하는 컴퓨터에서 **시작**을 선택한 다음, **Visual Studio 설치 관리자**로 나열되는 **V** 문자로 스크롤합니다.

     ![Windows에서 Visual Studio 설치 관리자 열기](media/vs-2019/vs-installer-windows-start.png "Visual Studio 설치 관리자 열기")

     > [!NOTE]
     > 다음 위치에서 Visual Studio 설치 관리자를 찾을 수도 있습니다.
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    계속하기 전에 설치 관리자를 업데이트해야 할 수 있습니다. 그렇다면 지시를 따르세요.

1. 설치 관리자에서 설치한 Visual Studio의 버전을 찾은 다음, **수정**을 선택합니다.

     ![Visual Studio 업데이트 또는 수정](media/vs-2019/vs-installer-modify.png "Visual Studio 2019 업데이트 또는 수정")

     > [!IMPORTANT]
     > 보류 중인 업데이트가 있는 경우 수정 단추는 다른 위치에 있습니다. 원할 경우 이러한 방식으로 Visual Studio를 업데이트하지 않고 수정할 수 있습니다. **자세히**를 선택한 다음, **수정**을 선택합니다.
     >
     > ![Visual Studio 업데이트 또는 수정](media/vs-2019/modify-update-visual-studio.png "Visual Studio 2019 업데이트 또는 수정")

::: moniker-end

## <a name="modify-workloads"></a>작업 수정

::: moniker range="vs-2017"

 [워크로드](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/)에는 사용 중인 프로그래밍 언어 또는 플랫폼에 필요한 기능이 포함됩니다. 작업을 사용하여 원하는 시기에 원하는 작업을 지원하도록 Visual Studio를 수정할 수 있습니다.

1. Visual Studio 설치 관리자에서 **작업** 탭을 선택한 후 원하는 워크로드를 선택하거나 선택 취소합니다.

    ![Visual Studio 2017 설치 대화 상자](media/modify-workloads.png "Visual Studio 2019에서 워크로드 선택")

1. 기본 **다운로드하는 동안 설치** 옵션 또는 **모두 다운로드한 후 설치** 옵션을 허용할지 여부를 선택합니다.

    ![Visual Studio 2017 설치 옵션](media/vs-2019/vs-installer-choose-install-or-download.png "다운로드하는 동안 설치하거나 먼저 다운로드하고 나중에 설치하도록 선택")

    "모두 다운로드한 후 설치" 옵션은 먼저 다운로드한 다음, 나중에 설치하려는 경우에 유용합니다.

1. **수정**을 선택합니다.

1. 새 워크로드가 설치된 후 Visual Studio 설치 관리자에서 **시작**을 선택하여 Visual Studio를 엽니다.

::: moniker-end

::: moniker range="vs-2019"

 작업에는 사용 중인 프로그래밍 언어 또는 플랫폼에 필요한 기능이 포함되어 있습니다. 작업을 사용하여 원하는 시기에 원하는 작업을 지원하도록 Visual Studio를 수정할 수 있습니다.

 > [!TIP]
>개발에 필요한 도구 및 구성 요소 번들에 대한 자세한 내용은 [Visual Studio 워크로드](https://visualstudio.microsoft.com/vs/#workloads)를 참조하세요.

1. Visual Studio 설치 관리자에서 **워크로드** 탭을 선택한 후 원하는 워크로드를 선택하거나 선택 취소합니다.

    ![Visual Studio 2019 설치 대화 상자](media/vs-2019/vs-installer-modify-workloads.png "Visual Studio 2019에서 워크로드 선택")

1. 기본 **다운로드하는 동안 설치** 옵션 또는 **모두 다운로드한 후 설치** 옵션을 허용할지 여부를 선택합니다.

    ![Visual Studio 2019 설치 옵션](media/vs-2019/vs-installer-choose-install-or-download.png "다운로드하는 동안 설치하거나 먼저 다운로드하고 나중에 설치하도록 선택")

    "모두 다운로드한 후 설치" 옵션은 먼저 다운로드한 다음, 나중에 설치하려는 경우에 유용합니다.

1. **수정**을 선택합니다.

1. 새 워크로드가 설치된 후 Visual Studio 설치 관리자에서 **시작**을 선택하여 Visual Studio를 엽니다.

::: moniker-end

## <a name="modify-individual-components"></a>개별 구성 요소 수정

Visual Studio 설치를 사용자 지정하기 위해 워크로드를 사용하지 않으려면 Visual Studio 설치 관리자에서 **개별 구성 요소** 탭을 선택하고 원하는 구성 요소를 선택한 다음 지시를 따릅니다.

>[!TIP]
> SSDT(SQL Server Data Tools) 구성 요소에 대한 자세한 내용은 [Visual Studio용 SSDT 다운로드 및 설치](/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-ver15)를 참조하세요.

## <a name="modify-language-packs"></a>언어 팩 수정

기본적으로 설치 관리자는 처음 실행될 때 운영 체제의 언어와 일치시킵니다. 그러나 원하는 경우 언제든지 언어를 변경할 수 있습니다. 이렇게 하려면 Visual Studio 설치 관리자에서 **언어 팩** 탭을 선택하고 원하는 언어를 선택한 다음 지시를 따릅니다.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참고 항목

* [Visual Studio 워크로드 및 구성 요소 ID 목록](workload-and-component-ids.md)
* [Visual Studio 업데이트](update-visual-studio.md)
* [Visual Studio의 네트워크 기반 설치 업데이트](update-a-network-installation-of-visual-studio.md)
* [서비스 기준선에서 Visual Studio 업데이트](update-servicing-baseline.md)
* [네트워크 기반 Visual Studio 배포에 대한 업데이트 제어](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio 제거](uninstall-visual-studio.md)
