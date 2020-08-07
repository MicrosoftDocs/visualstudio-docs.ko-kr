---
title: JavaScript 개발자를 위한 편집 소개
description: Visual Studio의 코드 편집기에 대한 이 소개에서는 Visual Studio에서 JavaScript 코드를 보다 쉽게 작성, 탐색 및 이해하는 몇 가지 방법을 보여줍니다.
ms.date: 12/13/2018
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: f48e7a8be8d902a487ae4f7fdac9e6d85f7b5517
ms.sourcegitcommit: b8ec700fc4c14c68c6ce280f29c19870261990d8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87453763"
---
# <a name="learn-to-use-the-code-editor"></a>코드 편집기를 사용하는 방법 알아보기

Visual Studio의 코드 편집기에 대한 간략한 소개에서는 Visual Studio에서 코드를 보다 쉽게 작성, 탐색 및 이해하는 몇 가지 방법을 보여줍니다.

> [!TIP]
> 아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads/) 페이지로 이동하여 체험용으로 설치합니다. 수행 중인 앱 개발 형식에 따라 Visual Studio와 함께 **Node.js 개발 워크로드**를 설치해야 할 수 있습니다. TypeScript용 언어 서비스를 가져오는 방법에 대한 자세한 내용은 [TypeScript 지원](../javascript/javascript-in-vs-2019.md#typescript-support)을 참조하세요.

이 문서에서는 이미 JavaScript 개발에 친숙하다고 가정합니다. 그렇지 않은 경우 먼저 [Node.js 및 Express 앱 만들기](../javascript/tutorial-nodejs.md)와 같은 자습서를 살펴보는 것이 좋습니다.

## <a name="add-a-new-project-file"></a>새 프로젝트 파일 추가

IDE를 사용하여 프로젝트에 새 파일을 추가할 수 있습니다.

1. Visual Studio에서 프로젝트를 연 상태에서 솔루션 탐색기(오른쪽 창)에서 폴더 또는 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **추가** > **새 항목**을 선택합니다.

1. **새 파일** 대화 상자의 **일반** 범주에서 추가할 파일 형식을 선택합니다(예: **JavaScript 파일**을 선택한 다음, **열기** 선택).

    새 파일이 프로젝트에 추가되고 편집기에서 열립니다.

## <a name="use-intellisense-to-complete-words"></a>IntelliSense를 사용하여 단어 자동 완성

IntelliSense는 코딩할 때 매우 유용한 리소스입니다. 형식의 사용 가능한 멤버에 대한 정보 또는 메서드의 다른 오버 로드에 대한 매개 변수 세부 정보를 표시할 수 있습니다. 다음 코드에서 `Router()`를 입력하면 전달할 수 있는 인수 형식이 표시됩니다. 이를 시그니처 도움말이라고 합니다.

![IntelliSense 사용](../javascript/media/write-code-signature-checking.png)

또한 IntelliSense를 사용하여 구분할 수 있을 정도로 문자를 입력한 후에 단어를 자동 완성할 수 있습니다. 다음 코드에서 `data` 문자열 뒤에 커서를 놓고 `get`을 입력하면 IntelliSense는 이전 코드에 정의된 함수나 프로젝트에 추가한 타사 라이브러리에 정의된 함수를 보여줍니다.

![IntelliSense 사용](../javascript/media/write-code-intellisense.png)

IntelliSense는 프로그래밍 요소 위로 마우스를 가져다 놓을 때 형식에 대한 정보를 표시할 수도 있습니다.

IntelliSense 정보를 제공하기 위해 언어 서비스는 TypeScript *d.ts* 파일과 JSDoc 주석을 사용할 수 있습니다. 가장 일반적인 JavaScript 라이브러리의 경우 *d.ts* 파일이 자동으로 다운로드됩니다. IntelliSense 정보를 얻는 방법에 대한 자세한 내용은 [JavaScript IntelliSense](../ide/javascript-intellisense.md?toc=/visualstudio/javascript/toc.json)를 참조하세요.

## <a name="check-syntax"></a>구문 검사

언어 서비스는 ESLint를 사용하여 구문 검사 및 linting을 제공합니다. 편집기에서 구문 검사 옵션을 설정하려면 **도구** > **옵션** > **JavaScript/TypeScript** > **Linting**을 선택합니다. linting 옵션은 글로벌 ESLint 구성 파일을 가리킵니다.

다음 코드에서는 식에 녹색 구문 강조 표시(녹색 물결선)가 표시됩니다. 구문 강조 표시 위에 마우스를 가져갑니다.

![구문 오류 보기](../javascript/media/write-code-syntax-checking.png)

이 메시지의 마지막 줄는 언어 서비스에서 쉼표(`,`)를 예상했음을 알려줍니다. 녹색 오류 표시선은 경고를 나타냅니다. 빨간색 오류 표시선은 오류를 나타냅니다.

아래쪽 창에서 **오류 목록** 탭을 클릭하면 파일 이름 및 줄 번호와 함께 경고 및 설명을 볼 수 있습니다.

![오류 목록 보기](../javascript/media/write-code-error-list.png)

`"data"` 앞에 쉼표(`,`)를 추가하여 이 코드를 수정할 수 있습니다.

린팅에 대한 자세한 내용은 [린팅](https://github.com/microsoft/JSTSdocs/blob/master/articles/editor/linting.md)을 참조하세요.

## <a name="comment-out-code"></a>코드 주석 처리

Visual Studio의 메뉴 모음에 있는 단추 행인 도구 모음은 코딩할 때 생산성을 높일 수 있습니다. 예를 들어 IntelliSense 완성 모드를 선택/해제하거나([IntelliSense](../ide/using-intellisense.md)는 기타 항목 중에 메서드 일치 항목 목록을 표시하는 코딩 지원임), 줄 내어쓰기를 늘리고 줄이거나, 컴파일하지 않으려는 코드를 주석 처리할 수 있습니다. 이 섹션에서는 일부 코드를 주석 처리합니다.

편집기에서 코드 줄을 하나 이상 선택한 다음, 도구 모음에서 **선택한 줄을 주석으로 처리** 단추 ![단추 주석 처리](../javascript/media/write-code-comment-out.png)를 선택합니다. 키보드 사용을 선호하는 경우 **Ctrl**+**K**, **Ctrl**+**C** 키를 누릅니다.

JavaScript 주석 문자 `//`를 선택한 각 줄의 시작 부분에 추가하여 코드를 주석으로 처리합니다.

## <a name="collapse-code-blocks"></a>코드 블록 축소

코드의 일부 영역 보기를 정리해야 할 경우 축소할 수 있습니다. 함수의 첫 번째 줄 여백에 있는 작은 회색 상자 안에 빼기 기호를 선택합니다. 또는 키보드 사용자인 경우 생성자 코드의 아무 곳에 커서를 두고 **Ctrl**+**M**, **Ctrl**+**M** 키를 누릅니다.

![축소 단추 개요](../javascript/media/write-code-collapse-code.png)

코드 블록은 줄임표(`...`) 뒤에 있는 첫 번째 줄로 축소됩니다. 코드 블록을 다시 확장하려면 더하기 기호가 있는 동일한 회색 상자를 클릭하거나 **Ctrl**+**M**, **Ctrl**+**M**을 다시 누릅니다. 이 기능은 [개요](../ide/outlining.md)라고 하며 긴 함수 또는 전체 클래스를 축소하는 경우에 특히 유용합니다.

## <a name="view-definitions"></a>정의 보기

Visual Studio 편집기를 사용하면 형식, 함수 등 정의를 쉽게 검사할 수 있습니다. 예를 들어 프로그래밍 요소가 참조되는 모든 위치에서 **정의로 이동**을 선택하는 것이 정의를 포함하는 파일로 이동하는 한 가지 방법입니다. [정의 피킹](../ide/go-to-and-peek-definition.md#peek-definition)을 사용하는 것도 작업 중인 파일에서 포커스를 이동하지 않는 더욱 빠른 방식입니다. 아래 예제에서 `render` 메서드의 정의를 살펴보겠습니다.

`render`를 마우스 오른쪽 단추로 클릭하고 콘텐츠 메뉴에서 **정의 피킹**을 선택합니다. 또는 **Alt**+**F12** 키를 누릅니다.

   `render` 메서드의 정의를 포함한 팝업 창이 표시됩니다. 팝업 창 내에서 스크롤하거나 피킹된 코드에서 다른 형식의 정의에 피킹할 수도 있습니다.

   ![정의 피킹 창](../javascript/media/write-code-peek-definition.png)

팝업 창의 오른쪽 위에서 "x"가 포함된 작은 상자를 선택하여 피킹된 정의 창을 닫습니다.

## <a name="use-code-snippets"></a>코드 조각 사용

Visual Studio에서는 일반적으로 사용되는 코드 블록을 쉽고 빠르게 생성하는 데 사용할 수 있는 유용한 *코드 조각*을 제공합니다. [코드 조각](../ide/code-snippets.md)은 JavaScript를 비롯한 다양한 프로그래밍 언어에서 사용할 수 있습니다. 코드 파일에 `for` 루프를 추가해 보겠습니다.

코드 조각을 삽입할 위치에 커서를 놓고 마우스 오른쪽 단추로 클릭하여 **코드 조각** > **코드 조각 삽입**을 선택합니다.

![Visual Studio의 코드 조각](../javascript/media/write-code-insert-snippet.png)

**코드 조각 삽입** 상자가 편집기에 나타납니다. **일반**을 선택한 다음, 목록에서 **for** 항목을 두 번 클릭합니다.

![Visual Studio의 for 루프용 코드 조각](../javascript/media/write-code-insert-snippet-for-loop.png)

이렇게 하면 코드에 `for` 루프 코드 조각이 추가됩니다.

```javascript
for (var i = 0; i < length; i++) {

}
```

**편집** > **IntelliSense** > **코드 조각 삽입**을 선택한 다음, 언어의 폴더를 선택하여 언어에 사용 가능한 코드 조각을 확인할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [코드 조각](../ide/code-snippets.md)
- [코드 탐색](../ide/navigating-code.md)
- [개요](../ide/outlining.md)
- [정의로 이동 및 정의 피킹(Peeking)](../ide/go-to-and-peek-definition.md)
- [리팩터링](../ide/refactoring-in-visual-studio.md)
- [IntelliSense 사용](../ide/using-intellisense.md)
