---
title: Visual Basic 개발자를 위한 편집 소개
description: Visual Studio의 코드 편집기에 대한 이 10분 소개에서는 Visual Studio에서 Visual Basic 코드를 보다 쉽게 작성, 탐색 및 이해하는 몇 가지 방법을 보여줍니다.
ms.custom: seodec18, get-started
ms.date: 11/20/2018
ms.technology: vs-ide-general
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: c46120c369fa130e83620549ca0bc084a5075f7f
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87235149"
---
# <a name="learn-to-use-the-code-editor-with-visual-basic"></a>코드 편집기를 사용하여 Visual Basic을 작업하는 방법 알아보기

Visual Studio의 코드 편집기에 대한 이 10분 소개에서 코드를 파일에 추가하여 Visual Studio에서 Visual Basic 코드를 더욱 쉽게 작성, 탐색 및 이해하는 몇 가지 방법을 살펴봅니다.

::: moniker range="vs-2017"

> [!TIP]
> 아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 페이지로 이동하여 체험용으로 설치합니다.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> 아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads) 페이지로 이동하여 체험용으로 설치합니다.

::: moniker-end

이 문서에서는 이미 Visual Basic에 친숙하다고 가정합니다. 그렇지 않은 경우 먼저 [Visual Studio에서 Visual Basic 시작하기](../../get-started/visual-basic/tutorial-console.md)와 같은 자습서를 살펴보는 것이 좋습니다.

> [!TIP]
> 이 문서와 함께 수행하려면 Visual Studio에 대해 Visual Basic 설정을 선택했는지 확인합니다. IDE(통합 개발 환경)의 설정 선택에 대한 자세한 내용은 [환경 설정 선택](visual-studio-ide.md#select-environment-settings)을 참조하세요.

## <a name="create-a-new-code-file"></a>새 코드 파일 만들기

새 파일을 만들고 일부 코드를 추가하여 시작합니다.

::: moniker range="vs-2017"

1. Visual Studio를 엽니다.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio를 엽니다. **Esc** 키를 누르거나 시작 창에서 **코드를 사용하지 않고 계속**을 클릭하여 개발 환경을 엽니다.

::: moniker-end

2. 메뉴 모음의 **파일** 메뉴에서 **새 파일**을 선택합니다.

3. **새 파일** 대화 상자의 **일반** 범주 아래에서 **Visual Basic 클래스**를 선택한 다음, **열기**를 선택합니다.

   Visual Basic의 구조를 사용하여 편집기에서 새 파일이 열립니다. (구문 강조와 같은 코드 편집기에서 제공하는 일부 혜택을 가져오기 위해 전체 Visual Studio 프로젝트를 만들 필요가 없다는 것을 이미 알 수 있습니다. 코드 파일만 있으면 됩니다.)

   ![Visual Studio의 Visual Basic 코드 파일](media/tutorial-editor.png)

## <a name="use-code-snippets"></a>코드 조각 사용

Visual Studio에서는 일반적으로 사용되는 코드 블록을 쉽고 빠르게 생성하는 데 사용할 수 있는 유용한 *코드 조각*을 제공합니다. [코드 조각](../../ide/code-snippets.md)은 Visual Basic, C# 및 C++를 비롯한 다양한 프로그래밍 언어에서 사용할 수 있습니다. Visual Basic **Sub** 코드 조각을 파일에 추가해 보겠습니다.

1. `End Class`라는 줄 위에 커서를 놓고, **sub**를 입력합니다.

   `Sub` 키워드 및 **Sub** 코드 조각을 삽입하는 방법에 대한 정보가 포함된 팝업 대화 상자가 표시됩니다.

   ![Visual Studio의 코드 조각에 대한 IntelliSense](media/tutorial-intellisense-snippet.png)

1. **탭** 키를 두 번 눌러 코드 조각을 삽입합니다.

   Sub 프로시저 `MySub()`에 대한 개요가 파일에 추가됩니다.

사용 가능한 코드 조각은 프로그래밍 언어마다 다릅니다. **편집** > **IntelliSense** > **조각 삽입**을 선택하여(또는 **Ctrl**+**K**, **Ctrl**+**X**를 눌러서) Visual Basic에 대해 사용 가능한 코드 조각을 확인할 수 있습니다. Visual Basic의 경우 코드 조각은 다음 범주에 대해 사용할 수 있습니다.

![Visual Basic 코드 조각 목록](media/tutorial-code-snippet-list.png)

컴퓨터에 파일이 있는지, 텍스트 파일에 쓰는지, 레지스트리 값을 읽는지, SQL 쿼리를 실행하는지, [For Each...Next 문](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)을 만드는지 등을 확인하는 코드 조각이 있습니다.

## <a name="comment-out-code"></a>코드 주석 처리

Visual Studio의 메뉴 모음에 있는 단추 행인 도구 모음은 코딩할 때 생산성을 높일 수 있습니다. 예를 들어 IntelliSense 완성 모드를 설정/해제하거나, 줄 들여쓰기를 늘리거나 줄이거나, 컴파일하지 않은 코드를 주석으로 처리할 수 있습니다. ([IntelliSense](../../ide/using-intellisense.md)는 다른 메서드와 비교하여 일치하는 메서드 목록을 표시하는 코딩 지원 도구입니다.) 이 섹션에서는 일부 코드를 주석 처리합니다.

![편집기 도구 모음 단추](media/tutorial-editor-toolbar.png)

1. 다음 코드를 `MySub()` 프로시저 본문에 붙여넣습니다.

   ```vb
   ' _words is a string array that we'll sort alphabetically
   Dim _words = New String() {
   "the",
   "quick",
   "brown",
   "fox",
   "jumps"
   }

   Dim morewords = New String() {
   "over",
   "the",
   "lazy",
   "dog"
   }

   Dim query = From word In _words
               Order By word.Length
               Select word
   ```

1. `morewords` 배열을 사용하지 않지만 나중에 사용할 것이므로 완전히 삭제하지 않습니다. 대신 해당 줄을 주석으로 처리해 보겠습니다. 닫는 중괄호에 대한 `morewords`의 전체 정의를 선택한 다음, 도구 모음에서 **선택한 줄 주석 처리** 단추를 선택합니다. 키보드 사용을 선호하는 경우 **Ctrl**+**K**, **Ctrl**+**C** 키를 누릅니다.

   ![단추 주석 처리](media/tutorial-comment-out.png)

   Visual Basic 주석 문자 `'`를 선택한 각 줄의 시작 부분에 추가하여 코드를 주석으로 처리합니다.

## <a name="collapse-code-blocks"></a>코드 블록 축소

코드 섹션을 축소하여 관심 있는 부분에만 집중할 수 있습니다. 연습하려면 `_words` 배열을 하나의 코드 줄로 축소합니다. `Dim _words = New String() {`이라고 표시된 줄 여백에 있는 작은 회색 상자 안에 빼기 기호를 선택합니다. 또는 키보드 사용자인 경우 배열 정의의 아무 곳에나 커서를 두고 **Ctrl**+**M**, **Ctrl**+**M**을 누릅니다.

![축소 단추 개요](media/tutorial-collapse.png)

코드 블록은 줄임표(`...`) 뒤에 있는 첫 번째 줄로 축소됩니다. 코드 블록을 다시 확장하려면 더하기 기호가 있는 동일한 회색 상자를 클릭하거나 **Ctrl**+**M**, **Ctrl**+**M**을 다시 누릅니다. 이 기능은 [개요](../../ide/outlining.md)라고 하고 긴 메서드 또는 전체 클래스를 축소하는 경우에 특히 유용합니다.

## <a name="view-symbol-definitions"></a>기호 정의 보기

Visual Studio 편집기를 사용하면 형식, 메서드 등 정의를 쉽게 검사할 수 있습니다. 예를 들어 기호가 참조되는 **정의로 이동**을 선택하는 것이 정의가 포함되는 파일을 탐색하는 한 가지 방법입니다. [정의 피킹](../../ide/go-to-and-peek-definition.md#peek-definition)을 사용하는 것도 작업 중인 파일에서 포커스를 이동하지 않는 더욱 빠른 방식입니다. `String` 형식의 정의를 피킹하겠습니다.

1. `String` 단어를 마우스 오른쪽 단추로 클릭하고 콘텐츠 메뉴에서 **정의 피킹**을 선택합니다. 또는 **Alt**+**F12** 키를 누릅니다.

   `String` 클래스의 정의를 포함한 팝업 창이 표시됩니다. 팝업 창 내에서 스크롤하거나 피킹된 코드에서 다른 형식의 정의에 피킹할 수도 있습니다.

   ![정의 피킹 창](media/tutorial-peek-definition.png)

1. 팝업 창의 오른쪽 위에서 "x"가 포함된 작은 상자를 선택하여 피킹된 정의 창을 닫습니다.

## <a name="use-intellisense-to-complete-words"></a>IntelliSense를 사용하여 단어 자동 완성

[IntelliSense](../../ide/using-intellisense.md)는 코딩할 때 매우 유용한 리소스입니다. 형식의 사용 가능한 멤버에 대한 정보 또는 메서드의 다른 오버 로드에 대한 매개 변수 세부 정보를 표시할 수 있습니다. 또한 IntelliSense를 사용하여 구분할 수 있을 정도로 문자를 입력한 후에 단어를 자동 완성할 수 있습니다. 콘솔 창에 순서가 지정된 문자열을 출력하는 코드 줄을 추가하겠습니다. 여기가 이동할 프로그램의 출력에 대한 표준 위치입니다.

1. `query` 변수 아래에 다음 코드를 입력하기 시작합니다.

   ```vb
   For Each str In qu
   ```

   IntelliSense에 `query` 기호에 대한 **요약 정보**가 표시됩니다.

   ![Visual Studio에서 IntelliSense 단어 완성](media/tutorial-intellisense-completion-list.png)

1. IntelliSense의 단어 자동 완성 기능을 사용하여 `query` 단어의 나머지 부분을 삽입하려면 **탭** 키를 누릅니다.

1. 코드 블록을 다음 코드와 같이 완성합니다.

   ```vb
   For Each str In query
       Console.WriteLine(str)
   Next
   ```

## <a name="refactor-a-name"></a>이름 리팩터링

누구도 처음부터 제대로 코딩할 수 없습니다. 변경할 수 있는 작업 중 하나는 변수 또는 메서드의 이름입니다. Visual Studio의 [리팩터링](../../ide/refactoring-in-visual-studio.md) 기능을 사용하여 `_words` 변수 이름을 `words`로 변경해 보겠습니다.

1. `_words` 변수의 정의 위에 커서를 놓고 마우스 오른쪽 단추로 클릭하거나 상황에 맞는 메뉴에서 **이름 바꾸기**를 선택합니다.

   편집기의 오른쪽 위에 팝업 **이름 바꾸기** 대화 상자가 나타납니다.

1. 변수 `_words`를 계속 선택한 상태에서 **단어**의 원하는 이름을 입력합니다. 쿼리에서 `words`에 대한 참조 이름이 자동으로 바뀝니다. **Enter**를 누르거나 **적용**을 클릭하기 전에 **이름 바꾸기** 팝업 상자에서 **주석 포함** 확인란을 선택합니다.

   ![이름 바꾸기 대화 상자](media/tutorial-rename.png)

1. **Enter**를 누르거나 **적용**을 클릭합니다.

   코드 주석의 `words`에 대한 참조뿐만 아니라 `words`의 두 항목 이름이 모두 변경됩니다.

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [프로젝트 및 솔루션에 대한 자세한 정보](tutorial-projects-solutions.md)

## <a name="see-also"></a>참조

- [코드 조각](../../ide/code-snippets.md)
- [코드 탐색](../../ide/navigating-code.md)
- [개요](../../ide/outlining.md)
- [정의로 이동 및 정의 피킹(Peeking)](../../ide/go-to-and-peek-definition.md)
- [리팩터링](../../ide/refactoring-in-visual-studio.md)
- [IntelliSense 사용](../../ide/using-intellisense.md)
