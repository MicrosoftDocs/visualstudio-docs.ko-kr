---
title: 마우스 없이 Visual Studio 사용
titleSuffix: ''
description: 키보드만 사용하여 Visual Studio IDE(통합 개발 환경) 내에서 코드를 탐색하고 작성하는 방법을 알아봅니다.
ms.date: 05/10/2019
ms.topic: conceptual
helpviewer_keywords:
- Toolbox, shortcut keys
- shortcut keys [Visual Studio]
- windows [Visual Studio], accessibility
- dialog boxes [Visual Studio], shortcut keys
- accessibility [Visual Studio]
ms.assetid: d71a4cc1-d352-4164-8538-3f9fa070a331
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3b1beb2ccb6b3e3e2b74ed7deaf2f31443ee2466
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569025"
---
# <a name="how-to-use-the-keyboard-exclusively"></a>단독으로 키보드를 사용하는 방법

바로 가기 키를 사용하면 Visual Studio IDE를 쉽게 탐색하고 코드를 작성할 수 있습니다. 이 문서에서는 바로 가기 키를 보다 효과적으로 사용할 수 있는 몇 가지 방법을 살펴보겠습니다.

Visual Studio 명령 바로 가기 키의 전체 목록은 [기본 바로 가기 키](../../ide/default-keyboard-shortcuts-in-visual-studio.md)를 참조하세요.

::: moniker range="vs-2017"

> [!TIP]
> 접근성 업데이트에 대한 자세한 내용은 [Visual Studio 2017의 접근성 향상](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) 블로그 게시물을 참조하세요.

::: moniker-end

> [!NOTE]
> 사용 중인 Visual Studio의 설정 또는 버전에 따라 표시되는 대화 상자와 메뉴 명령이 도움말에서 설명된 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [재설정 설정](../environment-settings.md#reset-settings)을 참조하세요.

## <a name="toolbox-controls"></a>도구 상자 컨트롤

마우스를 사용하지 않고 도구 상자의 컨트롤을 폼 또는 디자이너에 추가하려면

1. 메뉴 모음에서 **보기** > **도구 상자**를 선택합니다.

2. **Ctrl**+**위쪽 화살표** 또는 **Ctrl**+**아래쪽 화살표** 키를 사용하여 현재 **도구 상자** 탭의 섹션 간에 이동합니다.

3. **위쪽 화살표** 키 또는 **아래쪽 화살표** 키를 사용하여 섹션의 컨트롤 간에 이동합니다.

4. 컨트롤을 선택한 후 **Enter** 키를 사용하여 양식 또는 디자이너에 컨트롤을 추가합니다.

## <a name="dialog-box-options"></a>대화 상자 옵션

키보드만 사용하여 대화 상자의 옵션 간에 이동하고 옵션 설정을 변경하려면

1. **Tab** 또는 **Shift**+**Tab**을 사용하여 대화 상자의 컨트롤 간에 위아래로 이동합니다.

2. 옵션 설정을 변경하려면:

   - 라디오 단추의 경우 **위쪽 화살표** 및 **아래쪽 화살표** 키를 사용하여 선택을 변경합니다.

   - 확인란의 경우 **스페이스바**를 사용하여 선택하거나 선택 취소합니다.

   - 드롭다운 목록의 경우 **Alt**+**아래쪽 화살표** 키를 사용하여 항목을 표시한 다음, **위쪽 화살표** 및 **아래쪽 화살표** 키를 사용하여 선택한 항목을 변경합니다.

   - 단추의 경우 **Enter**를 선택하여 호출합니다.

   - 눈금의 경우 화살표 키를 사용하여 탐색합니다. 눈금의 드롭다운 목록의 경우 **Shift**+**Alt**+**아래쪽 화살표 키**를 사용하여 항목을 표시한 다음, **위쪽 화살표** 및 **아래쪽 화살표** 키를 사용하여 선택한 항목을 변경합니다.

## <a name="navigate-between-windows-and-files"></a>창과 파일 간의 이동

- 편집기 또는 디자이너에서 파일 간에 이동하려면 **Ctrl**+**Tab** 바로 가기 키를 선택하여 **활성 파일**이 선택된 IDE 탐색기를 표시합니다. **Ente**r 키를 선택하여 강조 표시된 파일로 이동합니다.

- 도킹된 도구 창 간에 이동하려면 **Alt**+**F7** 바로 가기 키를 선택하여 **활성 도구 창**이 선택된 IDE 탐색기를 표시합니다. **Enter** 키를 선택하여 강조 표시된 창으로 이동합니다.

## <a name="move-and-dock-tool-windows"></a>도구 창 이동 및 도킹

1. 이동할 도구 창으로 이동하고 포커스를 지정합니다.

2. **창** 메뉴에서 **도킹 가능** 옵션을 선택합니다.

3. **Alt**+**스페이스바**를 누르고 나서 **이동**을 선택합니다.

   도킹 안내 다이아몬드가 나타납니다.

4. 화살표 키를 사용하여 창을 새 위치로 이동합니다.

   화살표 키를 사용함에 따라 마우스 포인터가 창과 함께 이동합니다.

5. 새 위치에 도달한 경우 화살표 키를 사용하여 마우스 포인터를 안내 다이아몬드의 올바른 부분 위로 이동합니다.

   도구 창의 윤곽이 새 도킹 위치에 나타납니다.

6. **Enter** 키를 누릅니다.

   도구 창이 새 도킹 위치의 제자리에 맞춰집니다.

## <a name="see-also"></a>참고 항목

* [바로 가기 키 식별 및 사용자 지정](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)
* [접근성 팁과 요령](../../ide/reference/accessibility-tips-and-tricks.md)
* [기본 바로 가기 키](../../ide/default-keyboard-shortcuts-in-visual-studio.md)
* [Microsoft 제품의 접근성](https://www.microsoft.com/accessibility/)
