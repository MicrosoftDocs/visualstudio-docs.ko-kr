---
title: 옵션, 텍스트 편집기, C#, IntelliSense
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
helpviewer_keywords:
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 87a167a75f3b06522da77d562b0137df89757975
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596218"
---
# <a name="options-text-editor-c-intellisense"></a>옵션, 텍스트 편집기, C#, IntelliSense

**IntelliSense** 옵션 페이지를 사용하여 C#용 IntelliSense의 동작에 영향을 주는 설정을 수정합니다. 이 옵션 페이지에 액세스하려면 **도구** > **옵션**을 선택한 다음, **텍스트 편집기** > **C#**  > **IntelliSense**를 선택합니다.

**IntelliSense** 옵션 페이지에는 다음과 같은 옵션이 포함되어 있습니다.

## <a name="completion-lists"></a>완성 목록

- 문자가 입력된 후 완성 목록 표시*

   이 옵션을 선택하면 입력하기 시작할 때 IntelliSense에서 자동으로 완성 목록을 표시합니다. 이 옵션을 선택하지 않으면 IntelliSense 완성은 **IntelliSense** 메뉴를 선택하거나 **Ctrl**+**Space**를 눌러 사용할 수 있습니다.

- 문자를 삭제하면 완성 목록 표시

- 완성 목록 항목에서 일치하는 부분 강조 표시

- 완성 항목 필터 표시

## <a name="snippets-behavior"></a>코드 조각 동작

- 코드 조각 포함 안 함

   이 옵션을 선택하면 IntelliSense에서는 C# 코드 조각의 별칭을 완성 목록에 추가하지 않습니다.

- 코드 조각 항상 포함

   이 옵션을 선택하면 IntelliSense에서는 C# 코드 조각의 별칭을 완성 목록에 추가합니다. 코드 조각 별칭이 키워드(예: [class](/dotnet/csharp/language-reference/keywords/class))와 같은 경우 키워드는 바로 가기로 대체됩니다. 자세한 내용은 [C# 코드 조각](../../ide/visual-csharp-code-snippets.md)을 참조하세요.

- 식별자 뒤에 ?-Tab을 입력하면 코드 조각 포함

   이 옵션을 선택하면 IntelliSense에서는 식별자 뒤에 **?** +**Tab**을 누르면 C# 코드 조각의 별칭을 완성 목록에 추가합니다.

## <a name="enter-key-behavior"></a>키 입력 동작

- Enter 키를 누를 때 새 줄 추가 안 함

   완성 목록에서 항목을 선택하고 **Enter**를 누른 후 새 줄이 자동으로 추가되지 않도록 지정합니다.

- 단어를 모두 입력한 후 &lt;Enter&gt; 키를 누르면 새 줄 추가

   완성 목록에 입력할 모든 문자를 입력하고 나서 **Enter** 키를 누르면 새 줄이 자동으로 추가되고 커서가 새 줄로 이동하도록 지정합니다.

   예를 들어 `else`를 입력하고 **Enter** 키를 누르면 편집기에 다음과 같이 표시됩니다.

   `else`

   `|`(커서 위치)

   그러나 `el`만 입력하고 **Enter** 키를 누르면 편집기에 다음과 같이 표시됩니다.

   `else|`(커서 위치)

- Enter 키를 누를 때 항상 새 줄 추가

   완성 목록에 입력할 *모든* 문자를 입력하고 나서 **Enter** 키를 누르면 새 줄이 자동으로 추가되고 커서가 새 줄로 이동하도록 지정합니다.

## <a name="show-name-suggestions"></a>이름 제안 표시

최근에 선택한 멤버에 대해 자동 개체 이름 완성을 수행합니다.

## <a name="see-also"></a>참고 항목

- [옵션 대화 상자, 환경, 일반](../../ide/reference/general-environment-options-dialog-box.md)
- [IntelliSense 사용](../../ide/using-intellisense.md)
