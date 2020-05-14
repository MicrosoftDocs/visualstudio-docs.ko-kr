---
title: '방법: IDE 접근성 옵션 설정'
description: 시각 장애인의 읽기와 손 장애인의 쓰기를 포함해 IDE(통합 개발 환경)가 모든 이의 사용을 도와줄 Visual Studio의 접근성 옵션을 설정 하는 방법에 대해 알아봅니다.
ms.date: 08/23/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 63bba4e8defcd727f05dbc209aa2f48f7d5f2c92
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "70107776"
---
# <a name="how-to-set-ide-accessibility-options"></a>방법: IDE 접근성 옵션 설정

Visual Studio에는 시력이 약한 사용자와 읽기와 손으로 글씨를 쓰기 어려운 사용자를 지원하는 기능이 포함되어 있습니다. 예를 들어 편집기에서 텍스트의 크기 및 색, 도구 모음에 있는 텍스트 및 단추의 크기, 기능 또는 문을 완성하는 데 도움이 되는 설정을 변경할 수 있습니다.

또한 Visual Studio에서는 가장 자주 입력되는 문자의 접근성을 높이는 Dvorak 키보드 레이아웃을 지원합니다. Visual Studio에서 사용 가능한 기본 키보드 바로 가기를 사용자 지정할 수도 있습니다. 자세한 내용은 [바로 가기 키 식별 및 사용자 지정](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)을 참조하세요.

> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 여기서 설명하는 것과 다를 수도 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [재설정 설정](../environment-settings.md#reset-settings)을 참조하세요.

::: moniker range="vs-2017"

> [!TIP]
> 접근성에 대한 최신 업데이트에 대한 자세한 내용은 [Accessibility improvements in Visual Studio 2017 version 15.3(Visual Studio 2017 버전 15.3의 접근성 향상)](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) 블로그 게시물을 참조하세요.

::: moniker-end

## <a name="editors-dialogs-and-tool-windows"></a>편집기, 대화 상자 및 도구 창

기본적으로 Visual Studio의 대화 상자와 도구 창에서는 운영 체제와 같은 글꼴 크기 및 색을 사용합니다. IDE, 대화 상자, 도구 모음 및 도구 창의 프레임에 대한 색 설정은 색 테마인 밝은 테마 또는 어두운 테마에 따라 결정됩니다. 다음과 같은 [옵션 대화 상자에서 현재 색 테마를 변경할 수 있습니다. 환경 > 일반](../../ide/reference/general-environment-options-dialog-box.md)

편집기의 코드 보기에서 팝업 창을 표시할 수도 있습니다. 이러한 창에는 현재 개체의 사용 가능한 멤버 함수나 문을 완성하기 위한 매개 변수가 표시될 수 있습니다. 입력이 어려울 경우 이러한 창이 유용할 수 있습니다. 그러나 이러한 창은 코드 편집기에 집중하는 데 방해가 되어 일부 사용자에게 문제가 될 수 있습니다.

팝업 창을 끄는 방법은 다음과 같습니다.

1. **도구** 메뉴에서 **옵션**을 선택합니다.

1. **텍스트 편집기** > **모든 언어** > **일반**을 선택합니다.

1. **멤버 목록 자동 표시** 및 **매개 변수 정보** 확인란의 선택을 취소합니다.

자신의 작업 방식에 가장 적합하게 IDE(통합 개발 환경)에서 창을 다시 정렬할 수 있습니다. 각 도구 창을 도킹 또는 고정 해제하거나, 숨기거나, 자동으로 숨길 수 있습니다. 창 레이아웃을 변경하는 방법에 대한 자세한 내용은 [창 레이아웃 사용자 지정](../../ide/customizing-window-layouts-in-visual-studio.md)을 참조하세요.

### <a name="change-the-size-of-text"></a>텍스트 크기 변경

**도구** > **옵션** > **환경** > **글꼴 및 색**을 사용하여 **명령** 창, **직접 실행** 창 및 **출력** 창과 같은 텍스트 기반 도구 창에 대한 설정을 변경할 수 있습니다.

**설정 표시** 드롭다운 목록에서 **[모든 텍스트 도구 창]** 을 선택하면 기본 설정은 **항목 전경** 및 **항목 배경** 드롭다운 목록에 **기본값**으로 나열됩니다. **사용자 지정** 단추를 선택하여 이러한 설정을 변경할 수 있습니다.

텍스트가 편집기에 표시되는 방식에 대한 설정을 변경할 수도 있습니다. 방법은 다음과 같습니다.

1. **도구** 메뉴에서 **옵션**을 선택합니다.

1. **환경** > **글꼴 및 색**을 선택합니다.

1. **설정 표시** 드롭다운 메뉴에서 옵션을 선택합니다.

    편집기에서 텍스트의 글꼴 크기를 변경하려면 **텍스트 편집기**를 선택합니다.

    텍스트 기반 도구 창에서 텍스트의 글꼴 크기를 변경하려면 **[모든 텍스트 도구 창]** 을 선택합니다.

    편집기에서 도구 설명 텍스트의 글꼴 크기를 변경하려면 **편집기 도구 설명**을 선택합니다.

    문 완성 팝업에서 텍스트의 글꼴 크기를 변경하려면 **문 완성**을 선택합니다.

1. **표시 항목**에서 **일반 텍스트**를 선택합니다.

1. **글꼴**에서 새 글꼴 종류를 선택합니다.

1. **크기**에서 새 글꼴 크기를 선택합니다.

    > [!TIP]
    > 텍스트 기반 도구 창 및 편집기의 텍스트 크기를 다시 설정하려면 **기본값 사용**을 선택합니다.

7. **확인**을 선택합니다.

### <a name="change-the-colors-that-are-used-in-the-ide"></a>IDE에서 사용되는 색 변경

편집기에서 텍스트, 여백 표시기, 공백 및 코드 요소의 기본색을 변경할 수 있습니다. 방법은 다음과 같습니다.

1. **도구** 메뉴에서 **옵션**을 선택합니다.

1. **환경** 폴더에서 **글꼴 및 색**을 선택합니다.

1. **설정 표시**에서 **텍스트 편집기**를 선택합니다.

1. **표시 항목**에서 변경해야 하는 표시가 포함된 항목을 선택합니다(예: **일반 텍스트**, **표시기 여백**, **공백 표시**, **HTML 특성 이름** 또는 **XML 특성**).

1. 다음 옵션 중에서 표시 설정을 선택합니다. **항목 전경**, **항목 배경** 및 **볼드**

1. **확인**을 선택합니다.

> [!TIP]
> 운영 체제의 모든 애플리케이션 창에 고대비 색을 사용하려면 **왼쪽 Alt**+**왼쪽 Shift**+**PrtScn**을 누릅니다. Visual Studio가 열릴 경우 닫았다가 다시 열면 고대비 색이 완전히 구현됩니다.

## <a name="toolbars"></a>도구 모음

도구 모음의 사용 가능성과 접근성을 개선하기 위해 도구 모음 단추에 텍스트를 추가할 수 있습니다.

### <a name="to-assign-text-to-toolbar-buttons"></a>도구 모음 단추에 텍스트를 할당하려면

1. **도구** 메뉴에서 **사용자 지정**을 선택합니다.

1. **사용자 지정** 대화 상자에서 **명령** 탭을 선택합니다.

1. **도구 모음**을 선택하고 텍스트를 표시할 단추가 포함된 도구 모음 이름을 선택합니다.

1. 목록에서 변경할 명령을 선택합니다.

1. **선택 사항 수정**을 선택합니다.

1. **이미지 및 텍스트**를 선택합니다.

### <a name="to-modify-the-displayed-text-in-a-button"></a>단추에 표시된 텍스트를 수정하려면

1. **선택 사항 수정**을 다시 선택합니다.

1. **이름** 옆의 삽입은 선택된 단추에 대한 새 캡션을 제공합니다.

## <a name="see-also"></a>참조

* [Visual Studio의 접근성 기능](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Mac용 Visual Studio 접근성](/visualstudio/mac/accessibility/)
* [액세스 가능한 애플리케이션 설계를 위한 리소스](../../ide/reference/resources-for-designing-accessible-applications.md)
