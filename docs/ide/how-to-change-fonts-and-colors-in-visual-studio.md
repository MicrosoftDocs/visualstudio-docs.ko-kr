---
title: 글꼴 및 색 변경
ms.date: 06/01/2020
ms.topic: how-to
helpviewer_keywords:
- Visual Studio, color themes
- color themes, Visual Studio
ms.assetid: 60d91ba1-244b-4c43-847f-60b744f1352a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0eb2373117b382cb19f374581ada45a5732b9c4c
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284690"
---
# <a name="how-to-change-fonts-and-colors-in-visual-studio"></a>방법: Visual Studio에서 글꼴 및 색 변경

여러 가지 방법으로 Visual Studio에서 글꼴과 색을 변경할 수 있습니다. 예를 들어 기본 파란색 테마를 짙은 테마("어둡게 모드"라고도 함)로 변경할 수 있습니다. 그리고 기본 글꼴 및 텍스트 크기를 다른 글꼴 및 크기로 변경할 수 있습니다.

## <a name="change-the-color-theme"></a>색 테마 변경

Visual Studio에서 IDE 프레임 및 도구 창의 색 테마를 변경하는 방법은 다음과 같습니다.

1. 메뉴 모음에서 **도구** > **옵션**을 차례로 선택합니다.

1. 옵션 목록에서 **환경** > **일반**을 선택합니다.

1. **색 테마** 목록에서 기본 **파란색** 테마, **밝게** 테마, **어둡게** 테마 또는 **파란색(고대비)** 테마를 선택합니다.

   ![색 테마를 변경하는 옵션 대화 상자의 스크린샷](media/fonts-colors-theme.png "색 테마를 변경하는 데 사용할 수 있는 옵션 대화 상자의 스크린샷")

    > [!NOTE]
    > 색 테마를 변경하면 IDE의 텍스트가 기본값 또는 이전에 해당 테마에서 사용자 지정된 글꼴과 크기로 변환됩니다.

    :::moniker range="vs-2017"

    > [!TIP]
    > [Visual Studio 2017용 색 테마 편집기](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor)를 설치하여 고유한 Visual Studio 테마를 만들고 편집할 수 있습니다.

    :::moniker-end

    :::moniker range="vs-2019"

    > [!TIP]
    > [Visual Studio 색 테마 디자이너](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner)를 설치하여 고유한 Visual Studio 테마를 만들고 편집할 수 있습니다.

    :::moniker-end

## <a name="change-fonts-and-text-size"></a>글꼴 및 텍스트 크기 변경

글꼴 및 텍스트 크기를 모든 IDE 프레임 및 도구 창에 대해 변경하거나 특정 창 또는 텍스트 요소에 대해서만 변경할 수 있습니다. 편집기에서도 글꼴 및 텍스트 크기를 변경할 수 있습니다.

### <a name="to-change-the-font-and-text-size-in-the-ide"></a>IDE에서 글꼴 및 텍스트 크기를 변경하려면

1. 메뉴 모음에서 **도구** > **옵션**을 차례로 선택합니다.

1. 옵션 목록에서 **환경** > **글꼴 및 색**을 선택합니다.

1. **설정 표시** 목록에서 **환경**을 선택합니다.

   ![IDE에서 글꼴 및 색을 변경하는 옵션 대화 상자의 스크린샷](media/fonts-colors-environment.png "IDE에서 글꼴 및 색을 변경하는 옵션 대화 상자의 스크린샷")

    > [!NOTE]
    > 도구 창에서만 글꼴을 변경하려면 **설정 표시** 목록에서 **모든 텍스트 도구 창**을 선택합니다.

1. **글꼴** 및 **크기** 옵션을 수정하여 IDE의 글꼴과 텍스트 크기를 변경합니다.

1. **표시 항목**에서 해당 항목을 선택하고 **항목 전경** 및 **항목 배경** 옵션을 수정합니다.

### <a name="to-change-the-font-and-text-size-in-the-editor"></a>편집기에서 글꼴 및 텍스트 크기를 변경하려면

1. 메뉴 모음에서 **도구** > **옵션**을 차례로 선택합니다.

1. 옵션 목록에서 **환경** > **글꼴 및 색**을 선택합니다.

1. **설정 표시** 목록에서 **텍스트 편집기**를 선택합니다.

   ![편집기에서 글꼴 및 색을 변경하는 옵션 대화 상자의 스크린샷](media/fonts-colors-text-editor.png "편집기에서 글꼴 및 색을 변경하는 옵션 대화 상자의 스크린샷")

1. **글꼴** 및 **크기** 옵션을 수정하여 편집기의 글꼴과 텍스트 크기를 변경합니다.

1. **표시 항목**에서 해당 항목을 선택하고 **항목 전경** 및 **항목 배경** 옵션을 수정합니다.

자세한 내용은 [편집기 글꼴 및 색 변경](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md) 페이지를 참조하세요.

## <a name="accessibility-options"></a>접근성 옵션

시력이 낮은 사용자를 위한 색 테마 옵션이 있습니다. 컴퓨터의 모든 앱 및 UI에서 고대비 옵션을 사용하거나 Visual Studio에서만 고대비 옵션을 사용할 수 있습니다.

### <a name="use-windows-high-contrast"></a>Windows 고대비 사용

다음 절차 중 하나를 사용하여 Windows 고대비 옵션을 설정/해제합니다.

- Windows 또는 Microsoft 애플리케이션에서 **왼쪽 Alt**+**왼쪽 Shift**+**PrtScn** 키를 누릅니다.

- Windows에서 **시작** > **설정** > **접근성** > **고대비**를 선택합니다.

    > [!WARNING]
    > Windows 고대비 설정은 컴퓨터의 모든 애플리케이션 및 UI에 영향을 줍니다.

### <a name="use-visual-studio-extra-contrast"></a>Visual Studio 고대비 사용

다음 절차를 사용하여 Visual Studio 고대비 옵션을 설정/해제합니다.

1. Visual Studio의 메뉴 모음에서 **도구** > **옵션**을 선택한 다음 옵션 목록에서 **환경** > **일반**을 선택합니다.

1. **색 테마** 드롭다운 목록에서 **파란색(고대비)** 테마를 선택한 다음 **확인**을 선택합니다.

사용할 수 있는 다른 Visual Studio 접근성 옵션에 대한 자세한 내용은 [Visual Studio의 접근성 기능](../ide/reference/accessibility-features-of-visual-studio.md) 페이지를 참조하세요.

> [!TIP]
> 현재 Visual Studio에서 사용할 수 없지만 유용하다고 생각되는 색 또는 글꼴에 대한 접근성 옵션이 있는 경우 [Visual Studio Developer Community](https://developercommunity.visualstudio.com/)에서 **기능 제안**을 선택하여 알려주세요. 이 포럼에 대한 자세한 내용은 [기능 제안](../ide/suggest-a-feature.md) 페이지를 참조하세요.

## <a name="next-steps"></a>다음 단계

글꼴 및 색 구성표를 변경할 수 있는 모든 UI(사용자 인터페이스) 요소에 대한 자세한 내용을 보려면 [글꼴 및 색, 환경, 옵션 대화 상자](../ide/reference/fonts-and-colors-environment-options-dialog-box.md) 페이지를 참조하세요.

## <a name="see-also"></a>참조

- [코드 편집기 글꼴 및 색 변경](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)
- [Visual Studio 코드 편집기의 기능](../ide/writing-code-in-the-code-and-text-editor.md)