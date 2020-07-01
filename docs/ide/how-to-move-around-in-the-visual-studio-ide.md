---
title: IDE에서 이동하는 방법
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.NextDocumentWindowNav
- IDE navigator
ms.assetid: 6c36b6eb-c93f-496b-af08-4199f7afd8bd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1052deb04a93d11349ef9beb2ff667893095902f
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769848"
---
# <a name="how-to-move-around-in-the-visual-studio-ide"></a>방법: Visual Studio IDE에서 이동

IDE(통합 개발 환경)는 기본 설정이나 프로젝트 요구 사항에 따라 몇 가지 방법으로 창에서 창으로 이동하고 파일에서 파일로 이동할 수 있도록 하기 위해 설계되었습니다. 편집기에 열려 있는 파일 전체를 순환하거나 IDE의 모든 활성 도구 창을 순환하도록 선택할 수 있습니다. 마지막으로 액세스한 순서에 관계없이 편집기에 열려 있는 원하는 파일로 직접 전환할 수도 있습니다. 이러한 기능은 IDE에서 작업할 때 생산성을 높이는 데 유용할 수 있습니다.

> [!NOTE]
> 대화 상자에서 사용할 수 있는 옵션과 메뉴 명령의 이름 및 위치는 실제 설정이나 버전에 따라 이 문서에서 설명하는 것과 다를 수 있습니다. 이 문서는 **일반** 설정을 염두에 두고 작성되었습니다. 설정을 **일반** 또는 **Visual C++** 설정 등으로 변경하려면 **도구** > **설정 가져오기 및 내보내기**를 선택한 다음, **모두 다시 설정**을 선택합니다.

## <a name="keyboard-shortcuts"></a>바로 가기 키

Visual Studio의 거의 모든 메뉴 명령에는 바로 가기 키가 있습니다. 또한 사용자가 직접 바로 가기를 만들 수도 있습니다. 자세한 내용은 [바로 가기 키 식별 및 사용자 지정](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)을 참조하세요.

## <a name="navigate-among-files-in-the-editor"></a>편집기에서 파일 탐색

몇 가지 방법을 사용하여 편집기에 열려 있는 파일 간을 이동할 수 있습니다. 액세스한 순서에 따라 파일 간을 이동하거나, IDE 탐색기를 사용하여 현재 열려 있는 파일을 신속하게 찾거나, 항상 표시되도록 즐겨 찾는 파일을 탭 저장소에 고정할 수 있습니다.

뒤로 탐색 및 앞으로 탐색을 사용하면 Microsoft Internet Explorer에서 기록을 보기 위해 뒤로 및 앞으로를 사용하는 경우와 비슷하게 액세스한 순서에 따라 편집기에 열려 있는 파일 전체를 순환합니다.

### <a name="to-move-through-open-files-in-order-of-use"></a>사용한 순서대로 열려 있는 파일 간을 이동하려면

- 가장 최근에 액세스한 순서대로 열려 있는 문서를 활성화하려면 **Ctrl**+ **-** (하이픈)을 누릅니다.

- 역순으로 열려 있는 문서를 활성화하려면 **Ctrl**+**Shift**+ **-** (하이픈)를 누릅니다.

    > [!NOTE]
    > **뒤로 탐색** 및 **앞으로 탐색**은 **보기** 메뉴에서도 찾을 수 있습니다.

**IDE 탐색기**, 편집기의 **활성 파일** 목록 또는 **창** 대화 상자를 사용하여, 마지막으로 파일에 액세스한 시점과 관계없이 편집기에 열려 있는 특정 파일로 전환할 수도 있습니다.

**IDE 탐색기**는 Windows 애플리케이션 전환기와 매우 유사하게 작동합니다. IDE 탐색기는 메뉴에서 사용할 수 없으며 바로 가기 키를 사용해서만 액세스할 수 있습니다. 두 명령 중 하나를 사용하여 **IDE 탐색기**(아래 참조)에 액세스하고 순환하려는 순서에 따라 파일 전체를 순환할 수 있습니다.

![Visual Studio IDE 탐색기](../ide/media/vs2015_ide_navigator.png)

`Window.PreviousDocumentWindowNav`는 가장 최근에 액세스한 파일을 이동할 수 있도록 하고 `Window.NextDocumentWindowNav`는 역순으로 이동할 수 있도록 합니다. **일반 개발 설정**은 **Shift**+**Alt**+**F7**을 `Window.PreviousDocumentWindowNav`에, **Alt**+**F7**을 `Window.NextDocumentWindowNav`에 할당합니다.

> [!NOTE]
> 사용하고 있는 설정 조합에 이 명령에 할당된 바로 가기 키 조합이 아직 없는 경우 **옵션** 대화 상자의 **키보드** 페이지를 사용하여 사용자 고유의 사용자 지정 명령을 할당할 수 있습니다. 자세한 내용은 [바로 가기 키 식별 및 사용자 지정](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)을 참조하세요.

### <a name="to-switch-to-specific-files-in-the-editor"></a>편집기에서 특정 파일로 전환하려면

- **Ctrl**+**Tab**을 눌러 **IDE 탐색기**를 표시합니다. **Ctrl** 키를 누른 상태에서 전환하려는 파일을 선택할 때까지 **Tab** 키를 반복해서 누릅니다.

    > [!TIP]
    > **활성 파일** 목록을 이동하는 순서를 반대로 하려면 **Ctrl**+**Shift** 키를 누른 상태에서 **Tab** 키를 누릅니다.

    \- 또는-

- 편집기의 오른쪽 위에서 **활성 파일** 단추를 선택한 다음 전환할 목록에서 파일을 선택합니다.

    \- 또는-

- 메뉴 모음에서 **창** > **창**을 선택합니다.

- 목록에서 보려는 파일을 선택한 다음 **활성화**를 선택합니다.

## <a name="navigate-among-tool-windows-in-the-ide"></a>IDE에서 도구 창 탐색

**IDE 탐색기**를 사용하여 IDE에서 연 도구 창 전체를 순환할 수도 있습니다. 두 명령 중 하나를 사용하여 **IDE 탐색기**에 액세스하고 순환하려는 순서에 따라 도구 창 전체를 순환할 수 있습니다. `Window.PreviousToolWindowNav`는 가장 최근에 액세스한 파일을 이동할 수 있도록 하고 `Window.NextToolWindowNav`는 역순으로 이동할 수 있도록 합니다. **일반 개발 설정**은 **Shift**+**Alt**+**F7**을 `Window.PreviousDocumentWindowNav`에, **Alt**+**F7**을 `Window.NextDocumentWindowNav`에 할당합니다.

> [!NOTE]
> 사용하고 있는 설정 조합에 이 명령에 할당된 바로 가기 키 조합이 아직 없는 경우 **옵션** 대화 상자의 **키보드** 페이지를 사용하여 사용자 고유의 사용자 지정 명령을 할당할 수 있습니다. 자세한 내용은 [바로 가기 키 식별 및 사용자 지정](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)을 참조하세요.

### <a name="to-switch-to-a-specific-tool-window-in-the-ide"></a>IDE에서 특정 도구 창으로 전환하려면

- **Alt**+**F7**을 눌러 **IDE 탐색기**를 표시합니다. **Alt** 키를 누른 상태에서 전환하려는 창을 선택할 때까지 **F7** 키를 반복해서 누릅니다.

    > [!TIP]
    > **활성 도구 창** 목록을 이동하는 순서를 반대로 하려면 **Shift**+**Alt** 키를 누른 상태에서 **F7** 키를 누릅니다.

## <a name="see-also"></a>참고 항목

- [창 레이아웃 사용자 지정](../ide/customizing-window-layouts-in-visual-studio.md)
- [기본 바로 가기 키](../ide/default-keyboard-shortcuts-in-visual-studio.md)
