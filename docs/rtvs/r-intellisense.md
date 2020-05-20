---
title: R 코드에 대한 IntelliSense
description: Visual Studio IntelliSense는 R 코드 입력 시 함수, 개체 멤버, 코드 조각 및 자동 완성 정보를 표시합니다.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 854f7d410e327ca92d0c5156d89bc21765e13cc7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62999043"
---
# <a name="intellisense"></a>IntelliSense

Visual Studio IntelliSense를 사용하면 코드를 작성할 때 직접 보이는 곳에 호출할 수 있는 함수, 개체 멤버, 함수 인수 및 [코드 조각](code-snippets-for-r.md)에 대한 정보가 표시됩니다. 또한 입력할 때 가능한 완성이 표시되고 **Tab** 또는 **Enter** 키를 누르면 완성됩니다. **고급** 탭에 대해서는 [편집기 옵션](editing-r-code-in-visual-studio.md#editor-options)을 참조하세요. IntelliSense는 편집기 및 [대화형 창](interactive-repl-for-r-in-visual-studio.md)에서 둘 다 사용할 수 있습니다.

![함수 시그니처를 표시하는 IntelliSense](media/intellisense-function-signature.png)

함수나 기타 문을 입력하면 IntelliSense는 이미 입력한 내용을 기준으로 필터링된(대/소문자 구분) 자동 완성 메뉴를 제공합니다.

![IntelliSense 자동 완성 메뉴](media/intellisense-auto-complete-menu.png)

**Tab** 키(또는 옵션 설정 방식에 따라 **Enter** 키 또는 **Space** 키)를 누르면 드롭다운에서 선택한 항목이 삽입됩니다. 화살표 키를 사용하여 선택을 변경할 수 있습니다.

IntelliSense는 R 개체 멤버에 대한 제안도 제공합니다.

![개체 멤버에 대한 IntelliSense 제안](media/intellisense-auto-complete-r-objects.png)

**Esc** 키를 누르면 메뉴가 완전히 닫힙니다. **Ctrl**+**Space**를 사용하여 다시 표시할 수 있습니다.

함수 호출에 대해 여는 괄호(`(`)를 입력하면 닫는 괄호(`)`)가 삽입되고 앞에서 나온 시그니처 도움말이 표시됩니다.

![함수에 대한 IntelliSense 시그니처 도움말](media/intellisense-function-signature.png)

다시 **Esc** 키를 누르면 팝업이 닫힙니다. 함수 시그니처의 경우 **Ctrl**+**Shift**+**Space**를 사용하여 다시 표시할 수 있습니다.

> [!Tip]
> 매개 변수 도움말 아래 텍스트가 숨겨져 있는 경우 **Ctrl** 키를 누르고 있으면 매개 변수 도움말 텍스트가 반투명하게 표시됩니다.

## <a name="intellisense-for-user-defined-functions-and-variables"></a>사용자 정의 함수 및 변수에 대한 IntelliSense

IntelliSense는 이름-매개 변수 완성을 포함하여 같은 파일의 사용자 함수에 적용됩니다.

![사용자 정의 함수에 대한 IntelliSense](media/intellisense-same-file-functions.png)

![사용자 정의 함수에 대한 IntelliSense 매개 변수 완성](media/intellisense-parameter-completion.png)

IntelliSense는 같은 파일 및 현재 세션의 변수에도 적용됩니다.

![IntelliSense 변수 완성](media/intellisense-variable-completion.png)

> [!Note]
> 대화형 창에서 IntelliSense는 현재 R 세션의 이름만 고려하고 프로젝트의 파일을 무시합니다.

## <a name="code-suggestions"></a>코드 제안

전구(스마트 태그라고 함)가 여백에 나타나면 Visual Studio에서는 일반적으로 사용되는 작업에 사용 가능한 바로 가기를 제안합니다. 예를 들어 편집기에서 `library` 문이 포함된 줄에 커서를 올리면 전구가 표시됩니다. 전구를 선택하면 사용 가능한 옵션이 표시됩니다.

![편집기의 R용 스마트 태그](media/intellisense-smart-tags.png)
