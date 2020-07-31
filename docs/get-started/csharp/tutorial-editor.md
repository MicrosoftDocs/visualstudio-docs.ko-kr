---
title: C# 개발자를 위한 편집 소개
description: Visual Studio의 코드 편집기에 대한 이 10분 소개에서는 Visual Studio에서 C# 코드를 보다 쉽게 작성, 탐색 및 이해하는 몇 가지 방법을 보여줍니다.
ms.custom: seodec18, get-started
ms.date: 11/20/2018
ms.technology: vs-ide-general
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 72a74c967849703feeb427d89891a023326ca6b7
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234967"
---
# <a name="learn-to-use-the-code-editor-with-c"></a>코드 편집기를 사용하여 C#를 작업하는 방법 알아보기

Visual Studio의 코드편집기에 대한 이 10분 소개에서 코드를 파일에 추가하여 Visual Studio에서 C# 코드를 더욱 쉽게 작성, 탐색 및 이해하는 몇 가지 방법을 살펴봅니다.

::: moniker range="vs-2017"

> [!TIP]
> 아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 페이지로 이동하여 체험용으로 설치합니다.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> 아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads) 페이지로 이동하여 체험용으로 설치합니다.

::: moniker-end

이 문서에서는 이미 C#에 친숙하다고 가정합니다. 그렇지 않은 경우 먼저 [Visual Studio에서 C# 및 ASP.NET Core 시작하기](tutorial-aspnet-core.md)와 같은 자습서를 살펴보는 것이 좋습니다.

> [!TIP]
> 이 문서와 함께 수행하려면 Visual Studio에 대해 C# 설정을 선택했는지 확인합니다. IDE(통합 개발 환경)의 설정 선택에 대한 자세한 내용은 [환경 설정 선택](visual-studio-ide.md#select-environment-settings)을 참조하세요.

## <a name="create-a-new-code-file"></a>새 코드 파일 만들기

새 파일을 만들고 일부 코드를 추가하여 시작합니다.

::: moniker range="vs-2017"

1. Visual Studio를 엽니다.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio를 엽니다. **Esc** 키를 누르거나 시작 창에서 **코드를 사용하지 않고 계속**을 클릭하여 개발 환경을 엽니다.

::: moniker-end

2. 메뉴 모음의 **파일** 메뉴에서 **새로 만들기** > **파일**을 선택하거나 **Ctrl**+**N**을 누릅니다.

3. **새 파일** 대화 상자의 **일반** 범주 아래에서 **Visual C# 클래스**를 선택한 다음 **열기**를 선택합니다.

   C# 클래스의 구조를 사용하여 편집기에서 새 파일이 열립니다. (전체 Visual Studio 프로젝트를 만들어서 코드 편집기에서 제공하는 일부 혜택을 가져올 필요가 없습니다. 코드 파일만 있으면 됩니다.)

   ![Visual Studio의 C# 코드 파일](../media/tutorial-editor.png)

## <a name="use-code-snippets"></a>코드 조각 사용

Visual Studio에서는 일반적으로 사용되는 코드 블록을 쉽고 빠르게 생성하는 데 사용할 수 있는 유용한 *코드 조각*을 제공합니다. [코드 조각](../../ide/code-snippets.md)은 C#, Visual Basic 및 C++를 포함하여 다양한 프로그래밍 언어에서 사용할 수 있습니다. C# `void Main` 코드 조각을 파일에 추가하겠습니다.

1. 파일에서 마지막 닫는 괄호 **}** 바로 위에 커서를 놓고, `svm`(`static void Main`&mdash;의미를 알 수 없는 경우 너무 걱정하지 마세요라는 의미임) 문자를 입력합니다.

   `svm` 코드 조각에 대한 정보를 포함한 팝업 대화 상자가 표시됩니다.

   ![Visual Studio의 코드 조각에 대한 IntelliSense](../media/tutorial-intellisense-snippet.png)

1. **탭** 키를 두 번 눌러 코드 조각을 삽입합니다.

   `static void Main()` 메서드 서명이 파일에 추가됩니다. [Main()](/dotnet/csharp/programming-guide/main-and-command-args/) 메서드는 C# 애플리케이션의 진입점입니다.

사용 가능한 코드 조각은 프로그래밍 언어마다 다릅니다. **편집** > **IntelliSense** > **코드 조각 삽입**을 선택하거나 **Ctrl**+**K**, **Ctrl**+**X**를 눌러 언어의 폴더를 선택하여 언어에 사용 가능한 코드 조각을 확인할 수 있습니다. C#의 경우 목록은 다음과 같습니다.

![C# 코드 조각 목록](../media/tutorial-code-snippet-list.png)

목록에는 [클래스](/dotnet/csharp/programming-guide/classes-and-structs/classes), [생성자](/dotnet/csharp/programming-guide/classes-and-structs/constructors), [for](/dotnet/csharp/language-reference/keywords/for) 루프, [if](/dotnet/csharp/language-reference/keywords/if-else) 또는 [switch](/dotnet/csharp/language-reference/keywords/switch) 문 등을 만들기 위한 코드 조각이 포함됩니다.

## <a name="comment-out-code"></a>코드 주석 처리

Visual Studio의 메뉴 모음에 있는 단추 행인 도구 모음은 코딩할 때 생산성을 높일 수 있습니다. 예를 들어 IntelliSense 완성 모드를 선택/해제하거나([IntelliSense](../../ide/using-intellisense.md)는 기타 항목 중에 메서드 일치 항목 목록을 표시하는 코딩 지원임), 줄 내어쓰기를 늘리고 줄이거나, 컴파일하지 않으려는 코드를 주석 처리할 수 있습니다. 이 섹션에서는 일부 코드를 주석 처리합니다.

![편집기 도구 모음](../media/tutorial-editor-toolbar.png)

1. 다음 코드를 `Main()` 메서드 본문에 붙여넣습니다.

    ```csharp
    // _words is a string array that we'll sort alphabetically
    string[] _words = {
        "the",
        "quick",
        "brown",
        "fox",
        "jumps"
    };

    string[] morewords = {
        "over",
        "the",
        "lazy",
        "dog"
    };

    IEnumerable<string> query = from word in _words
                                orderby word.Length
                                select word;
    ```

1. `morewords` 변수를 사용하지 않지만 나중에 사용할 것이므로 완전히 삭제하지 않습니다. 대신 해당 줄을 주석으로 처리해 보겠습니다. 닫는 세미콜론에 대한 `morewords`의 전체 정의를 선택한 다음, 도구 모음에서 **선택한 줄 주석 처리** 단추를 선택합니다. 키보드 사용을 선호하는 경우 **Ctrl**+**K**, **Ctrl**+**C** 키를 누릅니다.

   ![단추 주석 처리](../media/tutorial-comment-out.png)

   C# 주석 문자 `//`를 선택한 각 줄의 시작 부분에 추가하여 코드를 주석으로 처리합니다.

## <a name="collapse-code-blocks"></a>코드 블록 축소

코드의 보기를 정리하도록 생성된 `Class1`에 대한 빈 [생성자](/dotnet/csharp/programming-guide/classes-and-structs/constructors)를 표시하지 않으려면 축소할 수 있습니다. 생성자의 첫 번째 줄 여백에 있는 작은 회색 상자 안에 빼기 기호를 선택합니다. 또는 키보드 사용자인 경우 생성자 코드의 아무 곳에 커서를 두고 **Ctrl**+**M**, **Ctrl**+**M** 키를 누릅니다.

![축소 단추 개요](../media/tutorial-collapse.png)

코드 블록은 줄임표(`...`) 뒤에 있는 첫 번째 줄로 축소됩니다. 코드 블록을 다시 확장하려면 더하기 기호가 있는 동일한 회색 상자를 클릭하거나 **Ctrl**+**M**, **Ctrl**+**M**을 다시 누릅니다. 이 기능은 [개요](../../ide/outlining.md)라고 하고 긴 메서드 또는 전체 클래스를 축소하는 경우에 특히 유용합니다.

## <a name="view-symbol-definitions"></a>기호 정의 보기

Visual Studio 편집기를 사용하면 형식, 메서드 등 정의를 쉽게 검사할 수 있습니다. 예를 들어 **정의로 이동**을 선택하거나 기호가 참조되는 모든 곳에서 **F12**를 누르는 것이 정의가 포함되는 파일을 탐색하는 한 가지 방법입니다. [정의 피킹](../../ide/go-to-and-peek-definition.md#peek-definition)을 사용하는 것도 작업 중인 파일에서 포커스를 이동하지 않는 더욱 빠른 방식입니다. `string` 형식의 정의를 피킹하겠습니다.

1. `string`의 모든 항목을 마우스 오른쪽 단추로 클릭하고 콘텐츠 메뉴에서 **정의 피킹**을 선택합니다. 또는 **Alt**+**F12** 키를 누릅니다.

   `String` 클래스의 정의를 포함한 팝업 창이 표시됩니다. 팝업 창 내에서 스크롤하거나 피킹된 코드에서 다른 형식의 정의에 피킹할 수도 있습니다.

   ![정의 피킹 창](../media/tutorial-peek-definition.png)

1. 팝업 창의 오른쪽 위에서 "x"가 포함된 작은 상자를 선택하여 피킹된 정의 창을 닫습니다.

## <a name="use-intellisense-to-complete-words"></a>IntelliSense를 사용하여 단어 자동 완성

[IntelliSense](../../ide/using-intellisense.md)는 코딩할 때 매우 유용한 리소스입니다. 형식의 사용 가능한 멤버에 대한 정보 또는 메서드의 다른 오버 로드에 대한 매개 변수 세부 정보를 표시할 수 있습니다. 또한 IntelliSense를 사용하여 구분할 수 있을 정도로 문자를 입력한 후에 단어를 자동 완성할 수 있습니다. 콘솔 창에 순서가 지정된 문자열을 출력하는 코드 줄을 추가하겠습니다. 여기가 이동할 프로그램의 출력에 대한 표준 위치입니다.

1. `query` 변수 아래에 다음 코드를 입력하기 시작합니다.

   ```csharp
   foreach (string str in qu
   ```

   IntelliSense에 `query` 기호에 대한 **요약 정보**가 표시됩니다.

   ![Visual Studio에서 IntelliSense 단어 완성](../media/tutorial-intellisense-completion-list.png)

1. IntelliSense의 단어 자동 완성 기능을 사용하여 `query` 단어의 나머지 부분을 삽입하려면 **탭** 키를 누릅니다.

1. 코드 블록을 다음 코드와 같이 완성합니다. `Console.WriteLine` 코드를 생성하기 위해 `cw`을 입력한 다음 **탭** 키를 두 번 눌러서 using 코드 조각을 사용할 수 있습니다.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactor-a-name"></a>이름 리팩터링

누구도 처음부터 제대로 코딩할 수 없습니다. 변경할 수 있는 작업 중 하나는 변수 또는 메서드의 이름입니다. Visual Studio의 [리팩터링](../../ide/refactoring-in-visual-studio.md) 기능을 사용하여 `_words` 변수 이름을 `words`로 변경해 보겠습니다.

1. `_words` 변수의 정의 위에 커서를 두거나, 마우스 오른쪽 단추로 클릭하거나 상황에 맞는 메뉴에서 **이름 바꾸기**를 선택하거나, **Ctrl**+**R**, **Ctrl**+**R** 키를 누릅니다.

   편집기의 오른쪽 위에 팝업 **이름 바꾸기** 대화 상자가 나타납니다.

1. 원하는 이름 **단어**를 입력합니다. 쿼리에서 `words`에 대한 참조 이름이 자동으로 바뀝니다. **Enter** 키를 누르기 전에 **이름 바꾸기** 팝업 상자에서 **주석 포함** 확인란을 선택합니다.

   ![이름 바꾸기 대화 상자](../media/tutorial-rename.png)

1. **Enter** 키를 누릅니다.

   `words`의 두 항목 이름 및 코드 주석에서 `words`에 대한 참조도 변경했습니다.

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [프로젝트 및 솔루션에 대한 자세한 정보](../tutorial-projects-solutions.md)

## <a name="see-also"></a>참조

- [코드 조각](../../ide/code-snippets.md)
- [코드 탐색](../../ide/navigating-code.md)
- [개요](../../ide/outlining.md)
- [정의로 이동 및 정의 피킹(Peeking)](../../ide/go-to-and-peek-definition.md)
- [리팩터링](../../ide/refactoring-in-visual-studio.md)
- [IntelliSense 사용](../../ide/using-intellisense.md)
