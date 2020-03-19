---
title: Python 코드 편집
description: Python의 경우 Visual Studio는 서식, Lint, 리팩터링과 함께 풍부한 IntelliSense, 코드 조각 및 탐색 기능을 제공합니다.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: eb3e3ca5d18429c60894c42bda12328836dc6fc8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "73024730"
---
# <a name="edit-python-code"></a>Python 코드 편집

사용자는 코드 편집기에서 많은 개발 시간을 보내므로 [Visual Studio의 Python 지원](installing-python-support-in-visual-studio.md)에서 생산성 향상에 도움이 되는 기능을 제공합니다. 이러한 기능에는 IntelliSense 구문 강조 표시, 자동 완성, 시그니처 도움말, 메서드 재정의/검색 및 탐색이 포함됩니다.

또한 편집기는 Visual Studio의 **대화형** 창과 통합되므로 편집기와 창 간에 코드를 쉽게 교환할 수 있습니다. 자세한 내용은 [자습서 3단계: 대화형 REPL 창 사용](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md) 및 [대화형 창 사용 - 대화형 명령에 보내기](python-interactive-repl-in-visual-studio.md#send-to-interactive-command)를 참조하세요.

Visual Studio의 코드 편집에 대한 일반적인 설명서는 [코드 편집기의 기능](../ide/writing-code-in-the-code-and-text-editor.md)을 참조하세요. 또한 코드의 특정 섹션에 집중하는 데 도움이 되는 [개요](../ide/outlining.md)도 참조하세요.

Visual Studio **개체 브라우저**(**보기** > **다른 창** > **개체 브라우저** 또는 **Ctrl**+**W** > **J**)를 사용하여 각 모듈에 정의된 Python 클래스와 해당 클래스에 정의된 함수를 검사할 수도 있습니다.

## <a name="intellisense"></a>IntelliSense

IntelliSense는 [완성](#completions), [서명 도움말](#signature-help), [요약 정보](#quick-info) 및 [코드 색 지정](#code-coloring)을 제공합니다. Visual Studio 2017 버전 15.7 이상은 [형식 힌트](#type-hints)도 지원합니다.

성능을 향상시키기 위해 Visual Studio 2017 버전 15.5 이하의 IntelliSense는 프로젝트의 각 Python 환경에 대해 생성된 완성 데이터베이스를 사용합니다. 패키지를 추가, 제거 또는 업데이트할 경우 데이터베이스를 새로 고쳐야 할 수 있습니다. 데이터베이스 상태는 **Python 환경** 창(**솔루션 탐색기**의 형제)의 **IntelliSense** 탭에 표시됩니다([환경 창 참조](python-environments-window-tab-reference.md) 확인).

Visual Studio 2017 버전 15.6 이상에서는 데이터베이스에 종속되지 않는 IntelliSense 완성을 제공하는 다른 방법을 사용합니다.

### <a name="completions"></a>완성

완성은 문, 식별자 및 편집기의 현재 위치에 적절히 입력될 수 있는 다른 단어로 표시됩니다. 목록에 표시된 내용은 컨텍스트를 기반으로 하며, 잘못되었거나 불필요한 옵션을 생략하도록 필터링됩니다. 완성은 종종 다른 문(예: `import`) 및 연산자(마침표 포함)를 입력하여 트리거되지만, 언제든지 **Ctrl**+**J** > **스페이스** 키를 눌러 표시되도록 할 수 있습니다.

![Visual Studio 편집기에서 멤버 완성](media/code-editing-completions-simple.png)

완성 목록이 열리면 화살표 키와 마우스를 사용하거나 계속 입력하여 원하는 완성을 검색할 수 있습니다. 더 많은 글자를 입력함에 따라 목록이 자세히 필터링되어 더 확실한 완성을 보여 줍니다. 다음과 같은 바로 가기를 사용할 수도 있습니다.

- 'parse'와 같이 이름의 시작 부분에 없는 글자를 입력하면 'argparse'를 찾습니다.
- 'abc'와 같이 단어의 시작 부분에 있는 글자만 입력하면 'AbstractBaseClass'를 찾거나 'air'를 입력하면 'as_integer_ratio'를 찾습니다.
- 'b64'와 같이 문자를 건너뛰면 'base64'를 찾습니다.

몇 가지 예:

![Visual Studio 편집기에서 필터링이 포함된 멤버 완성](media/code-editing-completion-filtering.png)

변수 또는 값 뒤에 마침표를 입력하면 멤버 완성이 자동으로 표시되어 잠재적인 형식의 메서드와 특성을 보여줍니다. 변수가 둘 이상의 형식일 수 있는 경우 목록에는 모든 형식의 모든 가능성 및 각 완성을 지원하는 형식을 나타내는 추가 정보가 포함됩니다. 완성이 가능한 모든 형식으로 지원되는 경우 주석 없이 표시됩니다.

![Visual Studio 편집기에서 여러 유형의 멤버 완성](media/code-editing-completion-types.png)

기본적으로 “dunder” 멤버(이중 밑줄로 시작하고 끝나는 멤버)는 표시되지 않습니다. 일반적으로 해당 멤버는 직접 액세스하면 안 됩니다. 그러나 완성이 필요한 경우 선행 이중 밑줄을 입력하면 다음과 같은 완성이 목록에 추가됩니다.

![Visual Studio 편집기에서 전용 멤버 완성](media/code-editing-completion-dunder.png)

`import` 및 `from ... import` 문은 가져올 수 있는 모듈의 목록을 표시합니다. `from ... import`의 경우에는 지정된 모듈에서 가져올 수 있는 멤버가 목록에 포함됩니다.

![Visual Studio 편집기에서 가져오기 완료](media/code-editing-completion-import.png)

`raise` 및 `except` 문은 오류 형식이 될 수 있는 클래스의 목록을 표시합니다. 목록에 모든 사용자 정의 예외가 포함되지는 않지만, 적합한 기본 제공 예외를 빠르게 찾을 수 있습니다.

![Visual Studio 편집기에서 예외 완성](media/code-editing-completion-exception.png)

@를 입력하면 데코레이터가 시작되고, 잠재적 데코레이터가 표시됩니다. 이러한 항목 중 많은 항목은 데코레이터로 사용할 수 없으므로 라이브러리 설명서를 확인하여 사용할 항목을 결정합니다.

![Visual Studio 편집기에서 데코레이터 완성](media/code-editing-completion-decorator.png)

> [!Tip]
> **도구** > **옵션** > **텍스트 편집기** > **Python** > **고급**을 통해 완성 동작을 구성할 수 있습니다. 여기서 **검색 문자열 기준 필터 목록**은 입력 시 완성 제안 필터링을 적용하며(기본적으로 선택한 상태), **멤버 완성에서 멤버 교집합 표시**는 가능한 모든 형식에서 지원되는 완성만 표시합니다(기본적으로 선택 취소됨). [옵션 - 완성 결과](python-support-options-and-settings-in-visual-studio.md#completion-results)를 참조하세요.

### <a name="type-hints"></a>형식 힌트

*Visual Studio 2017 버전 15.7 이상*

Python 3.5+([PEP 484](https://www.python.org/dev/peps/pep-0484/) (python.org)의 "형식 힌트”는 인수 형식, 반환 값, 클래스 속성을 표시하는 함수와 클래스에 대한 주석 구문입니다. IntelliSense는 함수 호출, 인수 및 해당 주석이 있는 변수 위에 마우스를 가져가면 형식 힌트를 표시합니다.

다음 예제에서는 `Vector` 클래스가 `List[float]`로 선언되며 `scale` 함수가 인수와 반환 값 모두에 대한 형식 힌트를 포함합니다. 해당 함수에 대한 호출 위로 마우스를 가져가면 형식 힌트가 표시됩니다.

![함수 호출에 마우스를 가져가면 형식 힌트 표시](media/code-editing-type-hints1.png)

다음 예제에서는 `Employee` 클래스의 주석 처리된 속성이 특성에 대한 IntelliSense 완료 팝업에서 어떻게 표시되는지 확인할 수 있습니다.

![형식 힌트를 표시하는 IntelliSense 완료](media/code-editing-type-hints2.png)

오류는 일반적으로 런타임까지는 표시되지 않기 때문에 프로젝트 전체에서 형식 힌트의 유효성을 검사하는 것이 유용합니다. 이를 위해 Visual Studio는 **솔루션 탐색기**의 바로 가기 메뉴 명령 **Python** > **Mypy 실행**을 통해 업계 표준 MyPy 도구를 통합합니다.

![솔루션 탐색기에서 MyPy 바로 가기 메뉴 실행](media/code-editing-type-hints-run-mypy.png)

명령을 실행하면 필요할 경우 mypy 패키지를 설치하라는 메시지가 표시됩니다. 그런 다음, Visual Studio가 mypy를 실행하여 프로젝트의 모든 Python 파일에서 형식 힌트의 유효성을 검사합니다. Visual Studio **오류 목록** 창에 오류가 표시됩니다. 창에서 항목을 선택하면 코드의 해당 줄로 이동합니다.

간단한 예로 다음 함수 정의에는 `input` 인수의 형식이 `str`임을 표시하는 형식 힌트가 포함되어 있으나 이 함수에 대한 호출에서는 정수를 전달하려 합니다.

```python
def commas_to_colons(input: str):
    items = input.split(',')
    items = [x.strip() for x in items]
    return ':'.join(items)

commas_to_colons(1)
```

이 코드에서 **Run Mypy** 명령을 사용하면 다음 오류가 생성됩니다.

![형식 힌트의 유효성을 검사하는 mypy 결과 예](media/code-editing-type-hints-validation-error.png)

::: moniker range="vs-2017"
> [!Tip]
> Python 3.5 이전 버전의 경우 Visual Studio는 Typeshed ‘스텁 파일’( *.pyi*)을 통해 사용자가 입력한 형식 힌트도 표시합니다.  코드에 형식 힌트를 직접 포함하지 않고자 하거나, 형식 힌트를 직접 사용하지 않는 라이브러리에 대한 형식 힌트를 만들려는 경우 스텁 파일을 사용할 수 있습니다. 자세한 내용은 mypy 프로젝트 wiki에서 [Python 모듈에 대한 스텁 만들기](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules)를 참조하세요.
>
> 현재는 Visual Studio에서 주석의 형식 힌트를 지원하지 않습니다.
::: moniker-end
::: moniker range=">=vs-2019"
> [!Tip]
> Python 3.5 이전 버전의 경우 Visual Studio는 Typeshed ‘스텁 파일’( *.pyi*)을 통해 사용자가 입력한 형식 힌트도 표시합니다.  코드에 형식 힌트를 직접 포함하지 않고자 하거나, 형식 힌트를 직접 사용하지 않는 라이브러리에 대한 형식 힌트를 만들려는 경우 스텁 파일을 사용할 수 있습니다. 자세한 내용은 mypy 프로젝트 wiki에서 [Python 모듈에 대한 스텁 만들기](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules)를 참조하세요.
>
> Visual Studio에는 Python 2 및 3에 대한 Typeshed 파일의 번들 집합이 포함되어 있으므로 추가 다운로드가 필요하지 않습니다. 하지만 다른 파일 집합을 사용하려는 경우 **도구** > **옵션** > **Python** > **언어 서버** 옵션에서 경로를 지정할 수 있습니다. [옵션 - 언어 서버](python-support-options-and-settings-in-visual-studio.md#language-server-options)를 참조하세요.
>
> 현재는 Visual Studio에서 주석의 형식 힌트를 지원하지 않습니다.
::: moniker-end

### <a name="signature-help"></a>서명 도움말

함수를 호출하는 코드를 작성할 때 여는 `(`를 입력하면 시그니처 도움말이 표시되며, 사용할 수 있는 설명서와 매개 변수 정보를 보여 줍니다. 또한 함수 호출 내에서 **Ctrl**+**Shift**+**스페이스** 키를 사용하여 표시할 수도 있습니다. 표시되는 정보는 함수의 소스 코드에 있는 설명서 문자열에 따라 다르지만 모든 기본값이 포함됩니다.

![Visual Studio 편집기의 시그리처 도움말](media/code-editing-signature-help.png)

> [!Tip]
> 서명 도움말을 사용하지 않으려면 **도구** > **옵션** > **텍스트 편집기** > **Python** > **일반**으로 이동하여 **문 완성** > **매개 변수 정보**의 선택을 취소합니다.

### <a name="quick-info"></a>요약 정보

식별자 위로 마우스 포인터를 가져가면 요약 정보 도구 설명이 표시됩니다. 식별자에 따라 요약 정보는 잠재적인 값이나 형식, 사용 가능한 모든 설명서, 반환 형식 및 정의 위치를 표시할 수 있습니다.

![Visual Studio 편집기의 요약 정보](media/code-editing-quick-info.png)

### <a name="code-coloring"></a>코드 색 지정

코드 색 지정은 코드 분석에서 색 변수, 명령문 및 코드의 다른 부분에 이르는 정보를 사용합니다. 예를 들어 모듈이나 클래스를 참조하는 변수는 함수 또는 다른 값과 다른 색으로 표시될 수 있으며, 매개 변수 이름은 지역 변수 또는 전역 변수와 다른 색으로 표시됩니다. 함수는 기본적으로 굵게 표시되지 않습니다.

![Visual Studio 편집기에서 코드 및 구문 색 지정](media/code-editing-code-coloring.png)

색을 사용자 지정하려면 **도구** > **옵션** > **환경** > **글꼴 및 색**으로 이동하여 **항목 표시** 목록에서 **Python** 항목을 수정합니다.

![Visual Studio에서 글꼴 및 색 옵션](media/code-editing-customize-colors.png)

> [!Tip]
> 코드 색 지정을 사용하지 않으려면 **도구** > **옵션** > **텍스트 편집기** > **Python** > **고급**으로 이동하여 **기타 옵션** > **형식별 색 이름**의 선택을 취소합니다. [옵션 - 기타 옵션](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options)을 참조하세요.

## <a name="code-snippets"></a>코드 조각

코드 조각은 바로 가기를 입력하고 **Tab** 키를 누르거나 **편집** > **IntelliSense** > **코드 조각 삽입** 및 **코드 감싸기** 명령을 사용하고 **Python**을 선택한 다음, 원하는 코드 조각을 선택하여 파일에 삽입할 수 있는 코드의 조각입니다.

예를 들어, `class`는 클래스 정의를 삽입하는 코드 조각의 바로 가기입니다. `class`를 입력하면 자동 완성 목록에 코드 조각이 표시됩니다.

![클래스 바로 가기의 코드 조각](media/code-editing-code-snippet-class.png)

**Tab** 키를 누르면 나머지 클래스가 생성됩니다. 그런 다음, 이름과 베이스 목록을 입력하고, **Tab** 키를 사용하여 강조 표시된 필드 사이를 이동하고, **Enter** 키를 눌러 본문을 입력할 수 있습니다.

![완성할 코드 조각 영역의 강조 표시](media/code-editing-code-snippets.png)

### <a name="menu-commands"></a>메뉴 명령

**편집** > **IntelliSense** > **코드 조각 삽입**메뉴 명령을 사용하는 경우 먼저 **Python**을 선택한 다음, 코드 조각을 선택합니다.

![코드 조각 삽입 명령을 통해 코드 조각 선택](media/code-editing-code-snippet-insert.png)

**편집** > **IntelliSense** > **코드 감싸기** 명령도 텍스트 편집기의 현재 선택 내용을 선택한 구조 요소 안에 유사하게 배치합니다. 예를 들어, 다음과 같은 코드가 있다고 가정해 보세요.

```python
sum = 0
for x in range(1, 100):
    sum = sum + x
```

이 코드를 선택하고 **코드 감싸기** 명령을 선택하면 사용 가능한 코드 조각 목록이 표시됩니다. 목록에서 **def**를 선택하면 선택한 코드가 함수 정의 내에 배치되며, **Tab** 키를 사용하여 강조 표시된 함수 이름과 인수 간에 탐색할 수 있습니다.

![코드 조각에 코드 감싸기 명령 사용](media/code-editing-code-snippet-surround-with.png)

### <a name="examine-available-snippets"></a>사용 가능한 코드 조각 검사

**도구** > **코드 조각 관리자** 메뉴 명령을 사용하고 언어로 **Python**을 선택하여 열린 **코드 조각 관리자**에서 사용 가능한 코드 조각을 확인할 수 있습니다.

![Visual Studio의 코드 조각 관리자](media/code-editing-code-snippets-manager.png)

사용자 고유의 코드 조각을 만들려면 [연습: 코드 조각 만들기](../ide/walkthrough-creating-a-code-snippet.md)를 참조하세요.

공유하려는 중요한 코드 조각을 작성하는 경우 자유롭게 요점에 게시하고 [알려주세요](https://github.com/Microsoft/PTVS/issues). 그러면 Visual Studio의 향후 릴리스에 포함할 수 있습니다.

## <a name="navigate-your-code"></a>코드 탐색

Visual Studio의 Python 지원에서는 소스 코드를 사용할 수 있는 라이브러리, 즉 [탐색 모음](#navigation-bar), [**정의로 이동**](#go-to-definition), [**다음 탐색**](#navigate-to) 및 [**모든 참조 찾기**](#find-all-references)를 포함하여 코드 내에서 빠르게 탐색할 수 있는 여러 가지 방법을 제공합니다. Visual Studio [**개체 브라우저**](../ide/viewing-the-structure-of-code.md#BKMK_ObjectBrowser)를 사용할 수도 있습니다.

### <a name="navigation-bar"></a>탐색 모음

탐색 모음은 각 편집기 창의 위쪽에 표시되며, 정의의 2단계 목록을 포함하고 있습니다. 왼쪽 드롭다운에서는 현재 파일의 최상위 클래스와 함수 정의를 포함하고 있으며, 오른쪽 드롭다운에서는 왼쪽에 표시된 범위 내의 정의 목록을 표시합니다. 편집기에서 이동하는 대로 목록이 업데이트되어 현재 컨텍스트를 보여 주며, 이러한 목록에서 항목을 선택하여 직접 이동할 수도 있습니다.

![Visual Studio 편집기의 탐색 모음](media/code-editing-navigation-bar.png)

> [!Tip]
> 탐색 모음을 숨기려면 **도구** > **옵션** > **텍스트 편집기** > **Python** > **일반**으로 이동하여 **설정** > **탐색 모음**의 선택을 취소합니다.

### <a name="go-to-definition"></a>정의로 이동

**정의로 이동**은 식별자(예: 함수 이름, 클래스 또는 변수)를 사용하여 정의된 원본 코드로 빠르게 이동합니다. 정의를 호출하려면 식별자를 마우스 오른쪽 단추로 클릭하여 **정의로 이동**을 선택하거나 식별자에 캐럿을 배치하고 **F12** 키를 누릅니다. 원본 코드를 사용할 수 있는 경우 코드 및 외부 라이브러리에서 작동합니다. 라이브러리 소스 코드를 사용할 수 없는 경우 **정의로 이동**은 모듈 참조를 위해 관련 `import` 문으로 건너뛰거나 오류를 표시합니다.

![Visual Studio에서 정의로 이동 명령](media/code-editing-go-to-definition.png)

### <a name="navigate-to"></a>탐색

**편집** > **다음 탐색** 명령(**Ctrl**+ **,** )은 문자열을 입력하고 해당 문자열을 포함하는 함수, 클래스 또는 변수를 정의하는 코드에서 가능한 일치 항목을 볼 수 있는 검색 상자를 편집기에 표시합니다. 이 기능은 **정의로 이동**과 비슷한 기능을 제공하지만 식별자를 사용하여 찾을 필요가 없습니다.

이름을 두 번 클릭하거나 화살표 키로 선택하고 **Enter** 키를 누르면 해당 식별자의 정의로 이동합니다.

![Visual Studio에서 명령으로 이동](media/code-editing-navigate-to.png)

### <a name="find-all-references"></a>모든 참조 찾기

**모든 참조 찾기**는 가져오기 및 할당을 포함하여 지정된 식별자가 정의되고 사용되는 위치를 찾는 유용한 방법입니다. 참조를 호출하려면 식별자를 마우스 오른쪽 단추로 클릭하여 **모든 참조 찾기**을 선택하거나 식별자에 캐럿을 배치하고 **Shift**+**F12**를 누릅니다. 목록에서 항목을 두 번 클릭하면 해당 위치로 이동합니다.

![모든 참조 찾기 결과](media/code-editing-find-all-references.png)

## <a name="see-also"></a>참조

- [서식](formatting-python-code.md)
- [리팩터링](refactoring-python-code.md)
- [Linter 사용](linting-python-code.md)
