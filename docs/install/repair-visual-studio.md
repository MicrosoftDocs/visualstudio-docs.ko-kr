---
title: Visual Studio 복구
titleSuffix: ''
description: Visual Studio 2017의 설치를 복구하는 방법 알아보기
ms.date: 06/15/2020
ms.custom: seodec18
ms.topic: how-to
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: fda72206059e5c14c46d332e44ea0de481004296
ms.sourcegitcommit: 9e15138a34532b222e80f6b42b1a9de7b2fe0175
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85418966"
---
# <a name="repair-visual-studio"></a>Visual Studio 복구

경우에 따라 Visual Studio 설치가 손상되거나 훼손됩니다. 복구는 업데이트를 포함하여 모든 설치 작업에서 설치 시간 문제를 해결하는 데 유용합니다.

## <a name="when-to-use-repair"></a>복구를 사용하는 경우
* 설치 페이로드 문제가 있는 경우. 이 문제는 디스크에 파일을 쓸 수 없는 경우에 발생할 수 있으며 손상된 파일을 삭제하여 수정할 수 없습니다. 복구는 필요한 파일을 다시 가져올 수 있습니다. 
* 클라이언트 쪽 다운로드 문제가 있는 경우. 연결 또는 프록시 문제를 해결한 경우에는 복구가 도움이 될 수 있습니다. 
* Visual Studio를 업데이트하는 데 문제가 있는 경우. 복구가 일반적인 업데이트 문제를 해결합니다. 

> [!TIP] 
> 설치 문제가 Windows Installer와 같은 기본 Windows 서비스의 문제로 인해 발생한 경우 복구에서도 동일한 문제가 발생할 수 있습니다. 시스템 문제에는 손상된 Windows Installer 또는 불안정한 인터넷 연결이 포함될 수 있습니다. 시스템 문제를 확인하려면 설치 작업에서 생성된 오류 보고서를 사용합니다.

> [!NOTE] 
> Visual Studio를 복구하면 사용자 설정이 초기화되고 이미 있던 어셈블리가 다시 설치됩니다. 제품 문제가 발생한 경우 복구를 통해 문제가 해결되지 않을 수 있으므로 [Visual Studio 피드백 티켓](https://developercommunity.visualstudio.com/content/problem/post.html?space=8)을 만듭니다.

## <a name="how-to-repair"></a>복구 방법
::: moniker range="vs-2017"

1. 컴퓨터에서 **Visual Studio 설치 관리자**를 찾습니다.

     예를 들어 Windows 10 1주년 업데이트 이상을 실행하는 컴퓨터에서 **시작**을 선택한 다음, **V** 문자로 스크롤하면 **Visual Studio 설치 관리자**로 나열됩니다.

   > [!NOTE]
   > 일부 컴퓨터에서는 Visual Studio 설치 관리자가 **Microsoft Visual Studio 설치 관리자**로 문자 **“M”** 아래에 나열될 수 있습니다.
   >
   > 또는 다음 위치에서 Visual Studio 설치 관리자를 찾을 수 있습니다.`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. 설치 관리자를 열고 **자세히**를 선택한 후 **복구**를 선택합니다.

    ![Visual Studio 설치 관리자에서 Visual Studio 복구](media/repair-visual-studio.png "Visual Studio 설치 관리자에서 Visual Studio 복구")

   > [!NOTE]
   > Visual Studio를 복구하면 환경이 다시 설정됩니다. 권한 상승, 사용자 설정 및 프로필 없이 설치된 사용자별 확장과 같은 로컬 사용자 지정은 제거됩니다. 테마, 색상, 키 바인딩과 같은 동기화된 설정이 복원됩니다.
   >

   > [!TIP]
   > **복구** 옵션은 Visual Studio의 설치된 인스턴스에만 나타납니다. **복구** 옵션이 표시되지 않으면 Visual Studio 설치 관리자에 “설치됨”이 아닌 “사용 가능”으로 나열된 버전에서 **자세히**를 선택한 것일 수 있습니다.

::: moniker-end

::: moniker range="vs-2019"

1. 컴퓨터에서 **Visual Studio 설치 관리자**를 찾습니다.

     예를 들어 Windows 10을 실행하는 컴퓨터에서 **시작**을 선택한 다음, **Visual Studio 설치 관리자**로 나열되는 **V** 문자로 스크롤합니다.

     ![Visual Studio 설치 관리자 열기](media/vs-2019/vs-installer-windows-start.png "Visual Studio 설치 관리자 열기")

     > [!NOTE]
     > 다음 위치에서 Visual Studio 설치 관리자를 찾을 수도 있습니다.
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    계속하기 전에 설치 관리자를 업데이트해야 할 수 있습니다. 그렇다면 지시를 따르세요.

1. 설치 관리자에서 설치한 Visual Studio의 버전을 찾습니다. 그런 다음, **자세히**를 선택하고 **복구**를 선택합니다.

     ![Visual Studio 2019 복구](media/vs-2019/vs-installer-repair.png "Visual Studio 2019 복구")

   > [!NOTE]
   > Visual Studio를 복구하면 환경이 다시 설정됩니다. 권한 상승, 사용자 설정 및 프로필 없이 설치된 사용자별 확장과 같은 로컬 사용자 지정은 제거됩니다. 테마, 색상, 키 바인딩과 같은 동기화된 설정이 복원됩니다.
   >

   > [!TIP]
   > **복구** 옵션은 Visual Studio의 설치된 인스턴스에만 나타납니다. **복구** 옵션이 표시되지 않으면 Visual Studio 설치 관리자에 “설치됨”이 아닌 “사용 가능”으로 나열된 버전에서 **자세히**를 선택한 것일 수 있습니다.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참조

* [Visual Studio 설치](install-visual-studio.md)
* [Visual Studio 업데이트](update-visual-studio.md)
* [Visual Studio 제거](uninstall-visual-studio.md)
* [Visual Studio 설치 및 업그레이드 문제 해결](troubleshooting-installation-issues.md)
