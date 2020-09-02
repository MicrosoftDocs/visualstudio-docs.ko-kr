---
title: R 코드 편집
description: Visual Studio는 모든 기능과 확장 사용 기능을 유지하면서 R에 맞게 조정된 편집 환경을 제공합니다.
ms.date: 11/05/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 7ecfd8f1cf50e94991ce2fd94ad94ac9815c92ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89315098"
---
# <a name="edit-r-code-in-visual-studio"></a>Visual Studio에서 R 코드 편집

RTVS(Visual Studio용 R 도구)에서는 모든 기능과 확장 사용 기능을 유지하면서 특히 R에 맞게 Visual Studio 편집 환경을 조정합니다. 예를 들어 VIM 키 바인딩을 원하는 경우 Visual Studio Marketplace에서 체험용 [VsVim 확장](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)을 설치할 수 있습니다.

이 문서의 기능 외에도 [IntelliSense](r-intellisense.md), [Lin](linting-r-code.md), [코드 조각](code-snippets-for-r.md) 및 [R Markdown](rmarkdown-with-r-in-visual-studio.md)을 참조하세요.

## <a name="syntax-highlighting"></a>구문 강조

문자열, 주석 및 키워드 등 코드의 여러 부분을 색 지정할 뿐 아니라 RTVS는 주석에서 링크를 강조하고 사용하도록 설정합니다.

![R 코드에 대한 구문 색 지정](media/editing-syntax-colors.png)

글꼴 및 특정 강조 색을 사용자 지정하려면 **도구** > **옵션** 명령을 선택하고, **환경** > **글꼴 및 색**으로 이동한 다음, **항목 표시** 상자에서 R 관련 항목에 대한 설정을 변경합니다.

![R 코드에 대한 글꼴 및 색 옵션](media/editing-syntax-colors-options.png)

Visual Studio에서는 편집기에 있는 구문 오류에 밑줄을 추가합니다.

![R 코드의 구문 오류 강조 표시](media/editing-syntax-error.png)

이 동작을 변경하려면 [편집기 옵션](#editor-options)에서 **고급** > **구문 검사** 설정을 참조하세요.

## <a name="edit-and-organize-code"></a>코드 구성 및 편집

코드를 입력할 때 RTVS에서는 [IntelliSense](r-intellisense.md) 페이지에 설명된 대로 자동 완성을 제공합니다. 또한 중괄호 및 괄호 완성과 같은 자동 서식 지정이 수행됩니다.

![인라인 서식 지정 애니메이션](media/editing-inline-formatting.gif)

많은 매개 변수가 포함된 함수 호출을 입력할 경우 일반적으로 코드를 더 쉽게 읽을 수 있도록 매개 변수를 정렬해야 합니다. RTVS에서는 매개 변수에 대해 설정한 들여쓰기를 기억하고 이후 줄에 해당 들여쓰기를 자동으로 적용합니다.

![자동 들여쓰기 애니메이션](media/editing-auto-indentation.gif)

이 동작을 변경하려면 **탭** 그룹에 대한 [편집기 옵션](#editor-options)을 참조하세요.

접을 수 있는 코드 영역에서는 편집기에 있는 코드의 일부를 일시적으로 숨길 수 있습니다. Visual Studio에서는 **고급** > **개요** >  **코드 개요** 옵션이 끄기로 설정된 경우 외에는 여러 줄 명령문의 경우처럼 자동으로 다양한 영역을 만듭니다.

고유한 영역을 만들려면 원하는 코드를 `---`로 끝나는 주석으로 둘러쌉니다. 코드 왼쪽의 작은 +/- 컨트롤을 통해 영역을 펼치거나 접을 수 있습니다.

![주석으로 접을 수 있는 영역 만들기](media/editing-collapsible-regions.gif)

**Tab** 키를 누르면 Visual Studio에서는 기본적으로 공백을 삽입합니다. [옵션, 텍스트 편집기, 탭](../ide/reference/options-text-editor-all-languages.md)의 설명대로 이 동작을 다시 변경할 수 있습니다.

## <a name="code-navigation"></a>코드 탐색

코드 탐색을 통해 R 프로그램의 소스 코드 및 해당 라이브러리에 빠르게 액세스할 수 있습니다. 이러한 기능을 사용하면 수동으로 코드를 검색할 필요 없이 작업 흐름을 따라갈 수 있습니다.

**정의로 이동**을 통해 함수 정의로 빠르게 이동하거나 인라인 미니 편집기를 표시하여 라이브러리 함수의 소스 코드를 읽습니다. 원하는 함수를 마우스 오른쪽 단추로 클릭하고 **정의로 이동**을 선택하거나 함수에 커서를 놓고 **F12**를 누릅니다.

이 명령을 사용하면 함수에 대한 소스 코드가 포함된 새 편집기 창이 열립니다. 커서는 편리하게 함수 정의의 시작 부분이 놓입니다.

마우스 오른쪽 단추 클릭 메뉴 또는 **Alt**+**F12**를 통해 호출된 **정의 피킹**은 함수의 소스 코드가 포함된 스크롤 가능한 읽기 전용 영역을 함수 호출 아래에 삽입합니다.

![정의 피킹 애니메이션](media/editing-peek-definition.gif)

## <a name="send-code-to-the-interactive-window"></a>대화형 창에 코드 보내기

대부분의 개발자는 즉각적인 테스트를 위해 편집기에서 일부 코드를 작성하고 해당 코드를 [대화형 창](interactive-repl-for-r-in-visual-studio.md)으로 보내고 싶어합니다(Read-Evaluate-Print-Loop 또는 REPL이라고도 함). R 편집기에서 **Ctrl**+**Enter**를 누르면 현재 코드 줄이 대화형 창으로 전송된 다음, 커서가 다음 줄에 놓입니다. **Ctrl**+**Enter**를 누르면 편집기에서 코드를 효과적으로 단계적으로 실행할 수 있습니다.

코드를 선택하고 **Ctrl**+**Enter**를 눌러 해당 전체 선택을 적용할 수도 있습니다. 또는 선택을 마우스 오른쪽 단추로 클릭하고 **대화형으로 실행**을 선택합니다.

## <a name="format-code"></a>코드 형식

Visual Studio의 자동 서식 지정 기능은 직접 작성한 코드 및 편집기에 붙여넣은 코드의 서식을 기본 설정에 설정된 대로 유지합니다. 항목을 선택하고, 마우스 오른쪽 단추를 클릭하고, **선택 영역 서식**(**Ctrl**+**K**,**F**)을 선택하여 해당 기본 설정을 적용합니다. 예를 들어 함수 정의가 모두 한 줄에 있는 경우:

```R
f<-function  (a){  return(a + 1) }
```

서식을 적용하면 다음과 같이 정리됩니다.

```R
f <- function(a) { return(a + 1) }
```

전체 코드 파일의 서식을 다시 지정하려면 **편집** > **고급** > **문서 서식**(**Ctrl**+**E**,**D**)을 선택합니다.

자동 서식 지정은 실행 취소할 수 있는 별도의 작업입니다. 예를 들어 코드를 편집기에 붙여넣고 서식을 적용한 경우 **편집** > **실행 취소**를 선택하거나 **Ctrl**+**Z**를 한 번 누르면 서식 지정이 되돌려집니다. 두 번째 **실행 취소**는 붙여넣기 자체를 되돌립니다.

서식 지정 옵션(서식 지정 끄기 포함)은 **텍스트 편집기** > **R** > **고급** 탭의 **도구** > **옵션**을 통해 설정됩니다. 이 페이지에는 **R 도구** > **편집기 옵션** 명령을 사용하여 직접 이동하거나 편집기에서 마우스 오른쪽 단추를 클릭하고 **서식 지정 옵션**을 선택하여 이동할 수 있습니다. 자세한 내용은 [편집기 옵션](#editor-options)을 참조하세요.

## <a name="inserting-roxygen-comments"></a>Roxygen 주석 삽입

RTVS에서는 함수의 매개 변수 이름을 사용하여 [Roxygen](https://cran.r-project.org/web/packages/roxygen2/index.html) 주석을 생성할 수 있는 바로 가기를 제공합니다. 함수 정의 위의 빈 줄에 `###`을 입력하면 됩니다.

![Roxygen 주석 삽입 애니메이션](media/editing-roxygen-comments.gif)

## <a name="editor-options"></a>편집기 옵션

편집기 관련 옵션은 **텍스트 편집기** > **R**로 이동하여 **도구** > **옵션** 명령을 통해 설정됩니다. 또는 **R 도구** > **편집기 옵션**을 사용하세요.

**일반**, **스크롤 막대** 및 **탭** 탭의 옵션은 R과 관계가 없고 오히려 모든 언어에 사용할 수 있지만 언어별로 적용되는 일반적인 Visual Studio 설정입니다. 자세한 내용은 다음 문서를 참조하세요.

- [옵션, 텍스트 편집기, 모든 언어](../ide/reference/options-text-editor-all-languages.md)
- [스크롤 막대를 사용자 지정하여 코드 추적](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)
- [옵션, 텍스트 편집기, 탭](../ide/reference/options-text-editor-all-languages-tabs.md)

**R** > **고급** 탭의 옵션은 RTVS에 관련됩니다.

| 그룹화 | 옵션 | 기본값 | 설명 |
| --- | --- | --- | --- |
| 서식 | 자동 서식 지정 | 켜기 | 입력할 때 코드 서식을 다시 지정합니다. **선택 영역 서식** 또는 **문서 서식** 명령에 영향을 미치지 않습니다. |
| | 확장된 중괄호 | 끄기 | 새 줄에 여는 중괄호({)를 배치합니다. |
| | 붙여넣을 때 서식 지정 | 켜기 | 붙여넣을 때 서식을 적용합니다. |
| | }에서 범위 서식 지정 | 켜기 | 닫는 중괄호(})를 입력한 후 범위 서식을 지정합니다. |
| | 쉼표 뒤에 공백 삽입 | 켜기 | 쉼표 뒤에 공백을 배치합니다. |
| | 키워드 뒤 공백 | 켜기 | `if`, `while` 및 `repeat` 같은 키워드 뒤에 공백을 배치합니다. |
| | { 앞 공백 | 켜기 | 여는 중괄호({) 앞에 공백을 배치합니다. |
| | = 주변 공백 | 켜기 | 등호 주변에 공백을 배치합니다. |
| IntelliSense | Enter 키를 누를 때 커밋 | 끄기 | **Enter**를 누를 때 자동 완성 선택을 커밋합니다. |
| | Space 키를 누를 때 커밋 | 끄기 | **Space**를 누를 때 자동 완성 선택을 커밋합니다.|
| | 첫 번째 문자 입력 시 완성 목록 | 켜기 | 첫 번째 문자 형식에 대한 완성 목록을 표시합니다. 끄기로 설정되면 **편집** > **IntelliSense** > **멤버 목록**(**Ctrl**+**J**)을 통해 완성 목록을 표시합니다. |
| | **Tab** 키를 누를 때 완성 목록 | 끄기 | 하나 이상의 문자를 입력하고 **Tab**을 눌러서 완성 목록을 호출합니다. |
| | 일부만 입력된 인수 이름 일치 | 끄기 | 함수 호출에 인수 이름을 입력하면 시그니처 도움말에는 가장 일치하는 인수에 대한 설명이 표시됩니다. |
| 대화형 창 | R 콘솔의 구문 검사 | 끄기 | 대화형 창에서 구문 검사를 적용합니다. 여러 줄 문에서는 구문 검사가 제대로 작동하지 않을 수 있습니다. |
| 개요 | 코드 개요 | 켜기 | 여러 줄 문 같은 영역에 대한 접을 수 있는 영역을 자동으로 만듭니다. |
| 구문 검사 | 구문 오류 표시 | 켜기 | 코드의 자동 구문 검사를 사용하도록 설정합니다. |
