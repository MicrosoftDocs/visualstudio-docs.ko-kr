---
title: Windows 사용자를 위한 Mac용 Visual Studio
description: Mac용 Visual Studio의 액세스 가능성 기능과 사용하도록 설정하는 방법을 소개합니다.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/25/2019
ms.assetid: 61CB6883-08CE-470F-8599-6F7570DB756E
ms.openlocfilehash: b414026ba7297dd6c93fecdf56d9a9c58c99f294
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984266"
---
# <a name="visual-studio-for-mac-for-windows-users"></a>Windows 사용자를 위한 Mac용 Visual Studio

운영 체제 간에 마이그레이션하는 것은 어려울 수 있습니다. 사용자 인터페이스에서 메뉴 항목의 분류에 이르기까지 플랫폼 간 애플리케이션에서 종종 사소한 차이가 있습니다. 또한 사용자는 새로운 운영 체제의 사용자 인터페이스에 적응하는 학습 곡선을 갖게 됩니다. 여기에서는 Mac용 Visual Studio와 Windows용 Visual Studio의 가장 일반적인 차이점에 대해 알아봅니다. macOS와 Windows 간의 몇 가지 다른 규칙도 알아봅니다.

## <a name="keyboard-shortcuts"></a>바로 가기 키

개발자는 대부분의 작업 및 탐색에 키보드를 사용하는 데 익숙함을 느끼게 됩니다. 키보드의 일부 키는 Mac과 Windows PC 간에 공통적입니다. 복사 및 붙여넣기와 같은 키보드 작업에서 동일한 키 조합을 사용하는 것을 고려할 수 있습니다. 이러한 방식으로 매핑되지 않는 경우도 있습니다. 다행히 Mac용 Visual Studio의 키 바인딩을 Windows의 Visual Studio와 거의 일치하도록 변경할 수 있습니다.

Mac용 Visual Studio를 처음으로 실행하면 바로 가기 키 선택 창이 표시됩니다. ![키 바인딩 창](media/ide-tour-2019-keyboard-shortcut.png)

나중에 키 바인딩을 변경하려면 기본 설정에서 해당 설정을 찾을 수 있습니다. ![키 바인딩 기본 설정](media/customizing-the-ide-image10a.png)

macOS는 Windows에 대한 서로 다른 시스템 차원의 바로 가기를 사용합니다. 키 바인딩 기본 설정을 변경하면 Mac용 Visual Studio에서 익숙한 Windows 바로 가기를 사용할 수 있습니다. 그러나 macOS의 다른 영역에서는 macOS 바로 가기에 대해 잘 알고 있어야 합니다.

macOS Command(⌘) 보조 키는 일반적으로 Windows의 Control 키를 대체할 수 있습니다. 다음은 몇 가지 예제 및 자주 사용되는 바로 가기입니다.

|작업                   |Windows 바로 가기         |macOS 바로 가기      |
|-----------------------|-------------------------|--------------------|
|복사                   |`Ctrl + C`               |`⌘ + C`             |
|붙여넣기                  |`Ctrl + V`               |`⌘ + V`             |
|잘라내기                    |`Ctrl + X`               |`⌘ + X`             |
|실행 취소                   |`Ctrl + Z`               |`⌘ + Z`             |
|다시 실행                   |`Ctrl + Shift + Z`       |`⌘ + Shift + Z`     |
|커서 오른쪽 삭제 |`Delete`                 |`fn + Backspace`    |
|단어 삭제            |`Ctrl + Delete`          |`fn + ⌥ + Backspace`|

> [!TIP]
> [Apple 지원 웹 사이트](https://support.apple.com/en-us/HT201236)에서 macOS 바로 가기의 포괄적인 목록을 찾을 수 있습니다.

## <a name="menus"></a>메뉴

macOS의 메뉴는 Windows의 메뉴와 다르게 구성됩니다. Mac용 Visual Studio도 예외는 아닙니다. 여기에서 가장 일반적인 메뉴 옵션 중 일부를 찾을 수 있습니다.

|작업                   |Visual Studio(Windows)                                              |Mac용 Visual Studio                |
|-----------------------|---------------------------------------------------------------------|-------------------------------------|
|기본 설정(옵션)  |도구 > 옵션...                                                   |Visual Studio > 기본 설정...       |
|확장             |확장 > 확장 관리                                       |Visual Studio > 확장...        |
|레이아웃                |창 > 창 레이아웃 적용 > [레이아웃 선택]                       |보기 > [레이아웃 선택]               |
|Updates                |도움말 > 업데이트 확인                                             |Visual Studio > 업데이트 확인... |
|NuGet 패키지 관리자  |도구 > NuGet 패키지 관리자 > NuGet 패키지 또는 솔루션 관리... |프로젝트 > NuGet 패키지 관리...   |
|패드/창         |보기 > [패드/창 선택]                                         |보기 > 패드 > [패드/창 선택]  |
|도구 찾기             |편집 > 찾기 및 바꾸기 > [도구 선택]                              |검색 > [도구 선택]               |
|Visual Studio 정보    |도움말 > Microsoft Visual Studio 정보                                 |Visual Studio > Visual Studio 정보  

> [!NOTE]
> Mac용 Visual Studio에서 가장 일반적인 기능에 대한 개요는 [IDE 둘러보기](ide-tour.md)에서 확인할 수 있습니다.