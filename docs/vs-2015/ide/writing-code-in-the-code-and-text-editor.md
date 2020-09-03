---
title: 코드 및 텍스트 편집기에서 코드 작성 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.texteditor
dev_langs:
- JScript
- VB
- CSharp
helpviewer_keywords:
- code editor, word wrap
- outlining
- code, editing
- squiggles
- code editor, outlining
- code editor, error and warning markers
- word wrap
- code editor, syntax coloring
- code editor, go to definition
- diff
- code editor [Visual Studio]
- code editor, diff
- error and warning markers
- code editor, navigation bar
- code editor, customizing
- comment selection
- code editor, tabify
- brace matching
- code editor, line numbers
- printing
- code editor, brace matching
- code editor, squiggles
- code editor, features
- line numbers
- go to definition
- syntax coloring
- code editor, navigate to
- code editor, comparing files
- code editor, zoom
- code editor
- code files
- go to line
- tabify
- zoom
- navigate to
- line break characters
- code editor, virtual space
- code editor, change tracking
- code editor, comment selection
- code editor, printing
- virtual space
- code editor, line break characters
- code editor, go to line
- code
ms.assetid: cb53ab9a-5b76-4759-b9e8-7bf32298ecbe
caps.latest.revision: 46
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aa647d8a8d52588481d18347cb3400141978bd20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548033"
---
# <a name="writing-code-in-the-code-and-text-editor"></a>코드 및 텍스트 편집기에서 코드 작성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Visual Studio 편집기에서는 코드를 더 쉽게 작성 및 관리할 수 있는 다양한 기능을 제공합니다. 개요를 사용하여 여러 코드 블록을 확장 및 축소할 수 있습니다. IntelliSense, **개체 브라우저**및 호출 계층 구조를 사용하여 사용 중인 코드에 대해 자세히 알아볼 수 있습니다. **다음 탐색**, **정의로 이동**및 **모든 참조 찾기**와 같은 기능을 사용하여 코드 내부를 탐색할 수 있습니다. 코드 조각이 있는 코드 블록을 삽입할 수 있고 **사용법에서 생성**과 같은 기능을 사용하여 코드를 생성할 수 있습니다. 이전에 Visual Studio 2015 편집기를 사용한 적이 없을 경우 빠른 개요를 보려면 [코드 편집](https://www.visualstudio.com/features/ide-vs) 을 참조하세요.

 다양한 방법으로 코드를 볼 수 있습니다. 솔루션의 클래스 뷰를 표시하려면 **클래스 뷰** 창을 열거나 **솔루션 탐색기** 의 클래스 파일 아래의 노드를 확장합니다.

 단일 파일이나 여러 파일에 대한 텍스트를 검색하고 바꿀 수 있습니다. 자세한 내용은 [텍스트 찾기 및 바꾸기](../ide/finding-and-replacing-text.md)를 참조 하십시오. 정규식을 사용하면 이제 찾기 및 바꾸기에 .NET 정규식이 사용됩니다. 자세한 내용은 [Visual Studio에서 정규식 사용](../ide/using-regular-expressions-in-visual-studio.md)을 참조하세요.

 다양한 Visual Studio 언어가 다양한 기능 집합을 제공하고 경우에 따라 기능은 언어별로 다르게 동작합니다. 이들 차이점은 대부분 기능 설명에 지정되지만 자세한 내용은 특정 Visual Studio 언어에 대한 섹션에서 확인할 수 있습니다.

> [!IMPORTANT]
> 사용 중인 Visual Studio 버전 및 설정이 IDE의 기능에 영향을 줄 수 있습니다. 이 항목에 설명된 내용과 다를 수 있습니다.

## <a name="editor-features"></a>편집기 기능

|기능|설명|
|-|-|
|구문 색 지정|코드 및 태그 파일의 일부 구문 요소에는 구분을 위해 다른 색이 지정됩니다. 예를 들어 키워드(예: C#의 `using` 및 Visual Basic의 `Imports` )는 한 색이지만 형식(예: `Console` 및 `Uri`)은 다른 색입니다. 문자열 리터럴 및 주석과 같은 기타 구문 요소에도 색이 지정됩니다. C++에서는 색을 사용하여 기타 토큰 사이에서 형식, 열거형 및 매크로를 구분합니다.<br /><br /> 각 형식에 대 한 기본 색을 볼 수 있으며 **도구** 메뉴에서 열 수 있는 [글꼴 및 색, 환경, 옵션 대화 상자](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)에서 특정 구문 요소의 색을 변경할 수 있습니다.|
|오류 및 경고 표식|코드를 추가하고 솔루션을 빌드할 때 코드에는 (a) 다른 색이 지정된 물결 무늬 밑줄(물결선) 또는 (b) 전구가 나타납니다. 빨간색 물결선은 구문 오류를 나타내고, 파란색 물결선은 컴파일러 오류를 나타내고, 녹색 물결선은 경고를 나타내고, 자주색 물결선은 기타 유형 오류를 나타냅니다. [전구](../ide/perform-quick-actions-with-light-bulbs.md) 는 문제에 대한 수정 내용을 제안하고 수정 내용을 쉽게 적용할 수 있도록 합니다.<br /><br /> **도구/옵션/환경/글꼴 및 색** 대화 상자에서 각 오류 및 경고 물결선의 기본 색을 확인할 수 있습니다. **구문 오류**, **컴파일러 오류**, **경고**및 **기타 오류**를 찾아보세요.|
|중괄호 일치|코드 파일에서 삽입 지점이 여는 괄호에 배치되면 여는 괄호와 닫는 괄호가 강조 표시됩니다. 이 기능을 통해 잘못 배치되거나 누락된 괄호를 즉시 파악할 수 있습니다. **자동 구분 기호 강조 표시** 설정 (**도구/옵션/텍스트 편집기**)을 사용 하 여 중괄호 일치를 설정 하거나 해제할 수 있습니다. **글꼴 및 색** 설정 (**도구/옵션/환경**)에서 강조 표시 색을 변경할 수 있습니다. **중괄호 일치(강조 표시)** 또는 **중괄호 일치(사각형)** 를 찾아보세요.|
|줄 번호|코드 창의 왼쪽 여백에 줄 번호를 표시할 수 있습니다. 줄 번호는 기본적으로 표시되지 않습니다. **텍스트 편집기 모든 언어** 설정 (**도구/옵션/텍스트 편집기/모든 언어**)에서이 옵션을 설정할 수 있습니다. 해당 언어에 대 한 설정을 변경 하 여 개별 프로그래밍 언어의 줄 번호를 표시할 수 있습니다 (**도구/옵션/ \<language> 텍스트 편집기/**). 줄 번호를 인쇄하려면 인쇄 대화 상자에서 **줄 번호 포함**을 선택해야 합니다.|
|변경 내용 추적|왼쪽 여백의 색을 사용하여 파일에서 수행한 변경을 계속 추적할 수 있습니다. 파일이 열린 후 변경되었으나 저장되지 않은 내용은 왼쪽 여백(선택 여백)에 노란색 막대로 나타냅니다. 변경 내용을 저장하면(파일을 닫기 전) 막대가 녹색으로 바뀝니다. 파일을 저장하고 나서 변경을 실행 취소하면 막대가 주황색으로 바뀝니다. 이 기능을 해제 하 고 설정 하려면 **텍스트 편집기** 설정 (**도구/옵션/텍스트 편집기**)에서 **변경 내용 추적** 옵션을 변경 합니다.|
|코드 및 텍스트 선택|줄 집합이 아니라 텍스트의 사각형 부분을 선택하는 상자 모드 또는 표준 연속 스트림 모드에서 텍스트를 선택할 수 있습니다. 상자 모드에서 선택 하려면 ALT 키를 누른 채 마우스를 선택 영역 위로 끌거나 ALT + SHIFT +를 누릅니다 \<arrow key> . 선택 영역에는 선택 영역의 첫 번째 문자와 마지막 문자로 정의된 사각형 안의 모든 문자가 포함됩니다. 선택 영역으로 입력하거나 붙여넣은 모든 내용이 각 줄의 같은 지점에 삽입됩니다.|
|확대/축소|코드 창을 확대하거나 축소하려면 CTRL 키를 누른 채 마우스의 스크롤 휠을 이동하거나 CTRL + SHIFT + .를 눌러 확대하고 CTRL + SHIFT + ,를 눌러 축소합니다. 코드 창의 왼쪽 아래에 있는  확대/축소 상자를 사용하여 특정 확대/축소 백분율을 설정할 수도 있습니다. 도구 창에서는 확대/축소 기능이 작동하지 않습니다.|
|가상 공간|기본적으로 Visual Studio 편집기의 줄은 마지막 문자 뒤에서 끝나므로 줄 끝 부분에서 오른쪽 화살표 키를 누르면 커서가 다음 줄의 시작 부분으로 이동합니다. 다른 편집기에서는 줄이 마지막 문자 뒤에서 끝나지 않고 커서를 줄의 아무 곳에나 배치할 수 있습니다. **도구/옵션/텍스트 편집기/모든 언어** 설정에서 편집기의 가상 공간을 사용할 수 있습니다. **가상 공간** 또는 **자동 줄 바꿈**의 하나를 사용할 수 있지만 둘 다 사용할 수는 없습니다.|
|인쇄|**인쇄** 대화 상자의 옵션을 사용하여 파일을 인쇄할 때 줄 번호를 포함하거나 축소된 코드 영역을 숨길 수 있습니다. **페이지 설정** 대화 상자에서 **페이지 머리글**을 선택하여 파일의 전체 경로와 이름을 인쇄하도록 선택할 수도 있습니다.<br /><br /> **도구/옵션/환경/글꼴 및 색** 대화 상자에서 컬러 인쇄 옵션을 설정할 수 있습니다. **설정 표시** 목록에서 **프린터** 를 선택하여 컬러 인쇄를 사용자 지정합니다. 파일 인쇄 시 파일 편집과 다른 색을 지정할 수 있습니다.|
|전역 실행 취소 및 다시 실행|**편집** 메뉴에서 **마지막 전역 작업 실행 취소** 및 **마지막 전역 작업 다시 실행** 명령을 선택하면 여러 파일에 영향을 미치는 전역 작업이 실행 취소되거나 다시 실행됩니다. 전역 작업에는 클래스 또는 네임스페이스 이름 바꾸기, 솔루션에서 찾기 및 바꾸기 작업 수행, 데이터베이스 리팩터링 또는 여러 파일을 변경하는 기타 작업이 포함됩니다. 작업이 적용된 솔루션을 닫은 후에도 현재 Visual Studio 세션에서 전역 실행 취소 및 다시 실행 명령을 작업에 적용할 수 있습니다.|

## <a name="advanced-editing-features"></a>고급 편집 기능
 **편집/고급** 하위 메뉴에서 다양한 고급 기능을 찾을 수 있습니다. 모든 이들 기능을 모든 형식의 코드 파일에서 사용할 수 있는 것은 아닙니다.

|기능|설명|
|-|-|
|문서 서식|적절한 코드 줄 들여쓰기를 설정하고 중괄호를 문서의 개별 줄로 이동합니다.|
|선택 영역 서식|적절한 코드 줄 들여쓰기를 설정하고 중괄호를 선택 영역의 개별 줄로 이동합니다.|
|선택한 줄의 공백을 탭으로|해당할 경우 선행 공백을 탭으로 변경합니다.|
|선택한 줄의 탭을 공백으로|선행 탭을 공백으로 변경합니다. 파일의 모든 공백을 탭으로 변환하거나 모든 탭을 공백으로 변환하려면 `Edit.ConvertSpacesToTabs` 및 `Edit.ConvertTabsToSpaces` 명령을 사용하면 됩니다. 이들 명령은 Visual Studio 메뉴에 표시되지 않지만 빠른 실행 창이나 명령 창에서 호출할 수 있습니다.|
|대문자로|선택 영역의 모든 문자를 대문자로 변경하거나, 선택 영역이 없으면 삽입 지점의 문자를 대문자로 변경합니다.|
|소문자로|선택 영역의 모든 문자를 소문자로 변경하거나, 선택 영역이 없으면 삽입 지점의 문자를 소문자로 변경합니다.|
|문서 유효성 검사|JScript 코드 파일의 유효성을 검사합니다.|
|가로 공백 삭제|현재 줄의 끝에 있는 탭이나 공백을 삭제합니다.|
|공백 보기|공백을 두껍게 올라온 점으로 표시하고 탭을 화살표로 표시합니다. 파일 끝은 사각형 문자 모양으로 표시됩니다. **도구/옵션/텍스트 편집기/모든 언어/자동 줄 바꿈/자동 줄 바꿈에 대 한 표시 문자 표시** 가 선택 된 경우에도 해당 문자 모양이 표시 됩니다.|
|자동 줄 바꿈|문서의 모든 줄이 코드 창에 표시됩니다. 텍스트 편집기 모든 언어 설정(**도구/옵션/텍스트 편집기/모든 언어**)에서 자동 줄 바꿈을 설정 및 해제할 수 있습니다.|
|선택 영역의 주석 처리 제거|주석 문자를 선택 영역이나 현재 줄에 추가합니다.|
|선택 영역을 주석으로 처리|선택 영역이나 현재 줄에서 주석 문자를 제거합니다.|
|줄 들여쓰기|탭이나 해당 공백을 선택한 줄이나 현재 줄에 추가합니다.|
|줄 내어쓰기|선택한 줄이나 현재 줄에서 탭이나 해당 공백을 제거합니다.|
|태그 선택|XML 또는 HTML과 같은 태그를 포함한 문서에서 태그를 선택합니다.|
|태그 내용 선택|XML 또는 HTML과 같은 태그를 포함한 문서에서 내용을 선택합니다.|

## <a name="navigate-in-the-code-window"></a>코드 창에서 탐색
 여러 가지 방법으로 문서 내에서 이동할 수 있습니다. 표준 작업 이외에 도구 모음에서 **뒤로 탐색** (또는 CTRL + 빼기) 및 **앞으로 탐색** (CTRL + SHIFT + 빼기) 단추를 사용하여 삽입 지점을 활성 문서의 이전 위치로 이동하거나 더 최근 위치로 돌아갈 수 있습니다. 이들 단추는 삽입 지점의 마지막 20개 위치를 유지합니다.

 ![앞으로 및 뒤로 탐색 단추](../ide/media/vs2015-nav-buttons.png "VS2015_Nav_buttons")

 코드 창에서 향상된 스크롤 막대를 사용하여 코드의 조감도를 볼 수도 있습니다. 맵 모드에서는 커서를 스크롤 막대의 위/아래로 이동할 때 코드 미리 보기를 확인할 수 있습니다. 자세한 내용은 [How to: Track Your Code by Customizing the Scrollbar](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)을 참조하세요.

 다음 명령은 코드 관련 탐색 방법입니다.

|명령|설명|
|-|-|
|로 가다 \<line number>|(**편집/이동** 또는 CTRL + G): 활성 문서에서 특정 줄 번호로 이동합니다.|
|다음 탐색|(**편집/탐색** 또는 CTRL + ,): 활성 솔루션에서 기호나 파일을 찾습니다. 이를 통해 쿼리에서 적합한 일치 결과 집합을 선택할 수 있습니다. 카멜 표기법 및 밑줄 문자를 사용하여 기호를 키워드로 구분하는 방식으로 기호에 포함된 키워드를 검색할 수 있습니다.|
|모든 참조 찾기|(상황에 맞는 메뉴): 솔루션에서 선택한 요소에 대한 참조를 모두 찾습니다.|
|정의로 이동|(상황에 맞는 메뉴 또는 F12 키): 선택한 요소의 정의를 찾습니다.|
|정의 피킹|(상황에 맞는 메뉴 또는 Alt+F12 키): 선택한 요소의 정의를 찾고 팝업 창에 표시합니다. 자세한 내용은 [방법: 정의 피킹 (peeking)을 사용 하 여 코드 보기 및 편집 (Alt + F12)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)을 참조 하세요.|
|다음 메서드, 이전 메서드|(**편집/다음 메서드, 이전 메서드**) Visual Basic 코드 파일에서 이들 명령을 사용하여 삽입 지점을 다른 메서드로 이동합니다.|
|참조 강조 표시|소스 코드에서 기호를 클릭하면 해당 기호의 모든 인스턴스가 문서에서 강조 표시됩니다. 강조 표시된 기호에는 선언 및 참조와 **모든 참조 찾기** 에서 반환하는 다양한 기타 기호가 포함될 수 있습니다. 여기에는 클래스, 개체, 변수, 메서드 및 속성의 이름이 포함됩니다. Visual Basic 코드에서 많은 컨트롤 구조체에 대한 키워드도 강조 표시됩니다. 다음 또는 이전 강조 표시된 기호로 이동하려면 CTRL+SHIFT+아래쪽 화살표 또는 CTRL+SHIFT+위쪽 화살표를 누릅니다. **도구/옵션/환경/글꼴 및 색/강조 표시 된 참조** 에서 강조 표시 색을 변경할 수 있습니다.|
|코드 관련 정보 찾기|코드 편집기에서 CodeLens를 사용하면 변경 내용 및 변경한 사용자, 참조, 버그, 작업 항목, 코드 검토, 단위 테스트 상태 같은 특정 코드에 대한 정보를 찾을 수 있습니다. Visual Studio Enterprise를 Team Foundation Server에서 사용할 경우 CodeLens는 화면 표시처럼 작동합니다. [코드 변경 내용 및 기타 기록 찾기](../ide/find-code-changes-and-other-history-with-codelens.md)를 참조하세요.|

 코드 창 위쪽에 표시되는 두 드롭다운 상자인 **탐색 모음**을 사용하여 코드 파일을 탐색할 수도 있습니다. 이 탐색 모음을 통해 특정 형식 또는 형식 내 멤버 중 하나로 직접 이동할 수 있습니다. 탐색 모음은 Visual Basic, C# 및 C++ 코드 파일에서 표시됩니다.

 탐색 모음을 숨기려면 텍스트 편집기 모든 언어 설정 (**도구/옵션/텍스트 편집기/모든 언어**)에서 **탐색 모음** 옵션을 변경 하거나 개별 언어에 대 한 설정을 변경할 수 있습니다. 다음과 같이 드롭다운 상자에서 탐색할 수 있습니다.

- 코드 창에서 탐색 모음으로 포커스를 이동하려면 바로 가기 키 조합 CTRL+F2를 누릅니다.

- 탐색 모음에서 코드 창으로 포커스를 반환하려면 ESC 키를 누릅니다.

- 탐색 모음에서 항목 간에 포커스를 이동하려면 TAB 키를 누릅니다.

- 포커스가 지정된 탐색 모음 항목을 선택하고 IDE로 돌아가려면 ENTER 키를 누릅니다.

- 클래스 또는 형식으로 이동하려면 왼쪽 드롭다운에서 해당 이름을 클릭합니다.

- 클래스의 프로시저로 직접 이동하려면 오른쪽 드롭다운에서 프로시저를 클릭합니다.

  부분 클래스에서 현재 코드 파일 외부에 정의된 멤버는 회색으로 표시될 수 있습니다.

## <a name="find-code-using-navigate-to"></a>탐색을 사용하여 코드 찾기
Visual Studio의 "탐색" 명령은 코드 파일, 파일 경로 및 코드 기호에서 지정한 요소를 찾기 쉽도록 포커스가 있는 코드 검색을 수행합니다. 찾기, 파일에서 찾기 등의 다른 텍스트 검색과 달리 탐색은 파일, 폼, 코드 모듈 등 실제 코드가 있는 영역으로 검색을 제한합니다. 예를 들어 전체 솔루션에서 찾기 또는 파일에서 찾기를 사용하여 ASP.NET 웹 애플리케이션에서 문자열을 검색하는 경우 코드 설명에 있는 문자열의 인스턴스까지 포함하여 여러 개의 결과가 표시될 수 있습니다. 그러나 탐색을 사용 하 여 코드 설명에서 문자열의 인스턴스를 무시 하 고 단일 함수만 가져올 수 있습니다.

### <a name="navigate-code-using-navigate-to"></a>탐색을 사용하여 코드 탐색

1. Visual Studio에서 솔루션 또는 폴더를 엽니다.
1. 주 메뉴에서 **편집**, **탐색**을 선택하거나 **Ctrl+,** 를 누릅니다.

    코드 편집기의 위쪽 모서리에 작은 텍스트 상자가 나타납니다.
1. 텍스트 상자에 찾으려는 코드 요소의 이름을 입력합니다.

    ![탐색 창](../ide/media/vside-navigatetowindow.png "탐색 창")

    입력 시 텍스트 상자 아래의 드롭다운 목록에 결과가 나타납니다.
1. 요소로 이동하려면 목록에서 선택합니다.

### <a name="filter-your-search"></a>검색 필터링

검색을 코드 기호로만 제한 하려면 탐색에 " \@ " 문자를 붙입니다. 예를 들어 `@application`을 검색하는 경우 탐색 시 "application" 단어가 포함된 클래스만 표시됩니다.

코드에서 캐멀(camel) 대/소문자를 사용하는 경우 코드 요소 이름의 대문자만 입력하여 코드 요소를 더 빠르게 찾을 수 있습니다. 예를 들어 코드에 `ViewSwitcher`라는 구성 요소가 있는 경우 탐색 창에서 이름의 대문자(`"VS"`)만 입력하면 찾을 수 있습니다.

![창 탐색 - 대문자를 사용한 검색](../ide/media/vside-capitalsearch.png "창 탐색 - 대문자를 사용한 검색")

이 기능은 코드에 긴 이름이 있는 경우에 특히 유용합니다.

## <a name="customize-the-editor"></a>편집기 사용자 지정
 **설정 가져오기 및 내보내기**: **도구** 메뉴에서 **설정 가져오기 및 내보내기 마법사** 를 사용하여 다른 개발자와 설정을 공유하거나, 설정이 표준을 준수하도록 하거나, Visual Studio 기본 설정으로 돌아갈 수 있습니다. 일반 설정 또는 언어와 프로젝트 관련 설정을 변경할 수 있습니다.

 **키보드 매핑**: 도구/옵션/환경/키보드 설정에서 새 바로 가기 키를 정의하거나 기존 바로 가기 키를 다시 정의할 수 있습니다. 바로 가기 키에 대 한 자세한 내용은 [기본 바로 가기 키](../ide/default-keyboard-shortcuts-in-visual-studio.md)를 참조 하세요.

 언어별 편집기 옵션에 대한 자세한 내용은 다음을 참조하세요.

- [Visual Basic 설정](https://msdn.microsoft.com/library/2712b3b1-18f2-430c-ae91-28468bbf5f32)

- [C#용 Visual Studio 개발 환경 사용](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)

- [Options, Text Editor, JavaScript, Formatting](../ide/reference/options-text-editor-javascript-formatting.md)

## <a name="in-this-section"></a>섹션 내용

- [텍스트 찾기 및 바꾸기](../ide/finding-and-replacing-text.md)

- [인코딩 및 줄 바꿈](../ide/encodings-and-line-breaks.md)

- [개요](../ide/outlining.md)

- [리팩터링](../ide/refactoring-in-visual-studio.md)

- [생산성 팁](../ide/productivity-tips-for-visual-studio.md)

- [IntelliSense 사용](../ide/using-intellisense.md)

- [편집기 사용자 지정](../ide/customizing-the-editor.md)

- [방법: 스크롤 막대를 사용자 지정 하 여 코드 추적](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)

- [방법: 정의 피킹 (Peeking)을 사용 하 여 코드 보기 및 편집 (Alt + F12)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

- [전구를 사용하여 빠른 작업 수행](../ide/perform-quick-actions-with-light-bulbs.md)

- [코드 조각](../ide/code-snippets.md)

- [도구 상자 사용](../ide/using-the-toolbox.md)

- [코드 구조 보기](../ide/viewing-the-structure-of-code.md)

- [코드에 책갈피 설정](../ide/setting-bookmarks-in-code.md)

- [작업 목록 사용](../ide/using-the-task-list.md)

- [코드 변경 내용 및 기타 기록 찾기](../ide/find-code-changes-and-other-history-with-codelens.md)

## <a name="see-also"></a>관련 항목
 [Visual Studio IDE](../ide/visual-studio-ide.md)
