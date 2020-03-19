---
title: Visual Studio 제거
titleSuffix: ''
description: Visual Studio를 제거하는 방법을 단계별로 알아봅니다.
ms.date: 12/19/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: fd21f01f89cb4fe4507775670968496cbb5f99f5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115007"
---
# <a name="uninstall-visual-studio"></a>Visual Studio 제거

이 페이지에서는 개발자를 위한 통합 생산성 도구 제품군인 Visual Studio를 제거하는 과정을 안내합니다.

> [!NOTE]
> 이 토픽은 Windows의 Visual Studio에 적용됩니다. Mac용 Visual Studio는 [Mac용 Visual Studio 제거](/visualstudio/mac/uninstall)를 참조하세요.

::: moniker range="vs-2017"

1. 컴퓨터에서 Visual Studio 설치 관리자를 찾습니다.

     예를 들어 Windows 10의 1주년 업데이트 이상을 실행하는 컴퓨터에서 **시작**을 선택하고 **V** 문자로 스크롤하면 **Visual Studio 설치 관리자**로 나열됩니다.

     ![Visual Studio 설치 관리자](media/locate-the-visual-studio-installer.png "Microsoft Visual Studio 설치 관리자 찾기")

   > [!NOTE]
   > 일부 컴퓨터에서는 Visual Studio 설치 관리자가 **Microsoft Visual Studio 설치 관리자**로 문자 **“M”** 아래에 나열될 수 있습니다.<br/><br/> 또는 다음 위치에서 Visual Studio 설치 관리자를 찾을 수 있습니다.`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. 설치 관리자에서 설치한 Visual Studio의 버전을 찾습니다. 그런 다음, **추가**를 선택한 다음, **제거**를 선택합니다.

     ![Visual Studio 2017 제거](media/uninstall-visual-studio.png "Visual Studio 2017 제거")

1. **확인**을 클릭하여 선택을 확인합니다.

나중에 마음이 바뀌어 Visual Studio 2017을 다시 설치하려면 Visual Studio 설치 관리자를 다시 시작한 다음 선택 영역 화면에서 **설치**를 선택하면 됩니다.

## <a name="uninstall-visual-studio-installer"></a>Visual Studio 설치 관리자 제거

컴퓨터에서 Visual Studio 2017과 Visual Studio 설치 관리자의 모든 설치를 완전히 제거하려면 [앱 및 기능]에서 제거합니다.

1. Windows 10의 경우 "여기에 입력하여 검색" 상자에 **앱 및 기능**을 입력합니다.
1. **Microsoft Visual Studio 2017**(또는 **Visual Studio 2017**)을 찾습니다.
1. **제거**를 선택합니다.
1. 그런 다음, **Microsoft Visual Studio 설치 관리자**를 찾습니다.
1. **제거**를 선택합니다.

::: moniker-end

::: moniker range="vs-2019"

1. 컴퓨터에서 Visual Studio 설치 관리자를 찾습니다.

     예를 들어 Windows 10을 실행하는 컴퓨터에서 **시작**을 선택한 다음, **Visual Studio 설치 관리자**로 나열되는 **V** 문자로 스크롤합니다.

     ![Visual Studio 설치 관리자 열기](media/vs-2019/vs-installer-windows-start.png "Visual Studio 설치 관리자 열기")

     > [!NOTE]
     > 다음 위치에서 Visual Studio 설치 관리자를 찾을 수도 있습니다.
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    계속하기 전에 설치 관리자를 업데이트해야 할 수 있습니다. 그렇다면 지시를 따르세요.

1. 설치 관리자에서 설치한 Visual Studio의 버전을 찾습니다. 그런 다음, **추가**를 선택한 다음, **제거**를 선택합니다.

     ![Visual Studio 2019 제거](media/vs-2019/vs-installer-uninstall.png "Visual Studio 2019 제거")

1. **확인**을 클릭하여 선택을 확인합니다.

     ![Visual Studio 확인 제거](media/vs-2019/uninstall-visualstudio-confirm.png "Visual Studio 2019를 제거할 것인지 확인")

나중에 마음이 바뀌어 Visual Studio 2019를 다시 설치하려면 Visual Studio 설치 관리자를 다시 시작하여 **사용 가능** 탭을 선택하고 설치할 Visual Studio 버전을 선택한 다음, **설치**를 선택합니다.

## <a name="uninstall-visual-studio-installer"></a>Visual Studio 설치 관리자 제거

Visual Studio 2019와 Visual Studio 설치 관리자를 컴퓨터에서 제거하려면 [앱 및 기능]에서 제거합니다.

1. Windows 10의 경우 "여기에 입력하여 검색" 상자에 **앱 및 기능**을 입력합니다.
1. **Visual Studio 2019**를 찾습니다.
1. **제거**를 선택합니다.
1. 그런 다음, **Microsoft Visual Studio 설치 관리자**를 찾습니다.
1. **제거**를 선택합니다.

::: moniker-end

## <a name="remove-all-files"></a>모든 파일 제거

치명적인 오류가 발생하고 이전 지침을 사용하여 Visual Studio를 제거할 수 없는 경우 대신 사용할 것을 고려할 수 있는 "최후의 수단" 옵션이 있습니다. 모든 Visual Studio 설치 파일 및 제품 정보를 완전히 제거하는 방법에 대한 자세한 내용은 [Visual Studio 제거](remove-visual-studio.md) 페이지를 참조하세요.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참고 항목

* [Visual Studio 수정](modify-visual-studio.md)
* [Visual Studio 업데이트](update-visual-studio.md)
