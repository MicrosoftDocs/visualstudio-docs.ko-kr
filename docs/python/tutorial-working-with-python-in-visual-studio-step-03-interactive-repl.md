---
title: Visual Studio 자습서 3단계, 대화형 REPL의 Python
titleSuffix: ''
description: Visual Studio의 Python 기능에 대한 핵심 연습의 3단계로, Python 대화형 REPL 창을 설명합니다.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: d88d936a4b470f891f3b2bf2c353f4ef4e595c57
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90811047"
---
# <a name="step-3-use-the-interactive-repl-window"></a>3단계: 대화형 REPL 창 사용

**이전 단계: [코드 작성 및 실행](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)**

Python용 Visual Studio **대화형** 창은 일반적인 편집-빌드-디버그 주기를 크게 단축하는 풍부한 REPL(읽기-평가-인쇄-루프) 환경을 제공합니다. **대화형** 창은 Python 명령줄에 대한 REPL 환경의 모든 기능을 제공합니다. 또한 Visual Studio 편집기에서 코드를 원본 파일과 쉽게 교환할 수 있습니다. 그렇지 않으면 명령줄을 사용하여 다루기 어렵습니다.

> [!NOTE]
> REPL에 문제가 있는 경우 `ipython` 및 `ipykernel` 패키지가 설치되어 있는지 확인하고, 패키지를 설치하는 데 도움이 필요한 경우 [Python 환경 패키지 탭](./python-environments-window-tab-reference.md#packages-tab)을 참조하세요.

1. **솔루션 탐색기**에서 프로젝트의 Python 환경(예: 앞의 그림에 표시된 **Python 3.6(32비트)**)을 마우스 오른쪽 단추로 클릭하고 **대화형 창 열기**를 선택하여 **대화형** 창을 엽니다. Visual Studio 주 메뉴에서 **보기** > **다른 창** > **Python 대화형 창**을 선택할 수도 있습니다.

1. **대화형** 창은 표준 **>>>** Python REPL 프롬프트와 함께 편집기 아래에 열립니다. **환경** 드롭다운 목록을 사용하여 작업할 특정 인터프리터를 선택할 수 있습니다. **대화형** 창을 더 크게 만들려는 경우도 있습니다. 이 경우 두 창 사이에 있는 구분 기호를 끌면 됩니다.

    ![Python 대화형 창 및 크기를 조정하도록 끌기](media/vs-getting-started-python-11-interactive1b.png)

    > [!Tip]
    > 경계 구분 기호를 끌어 Visual Studio에서 모든 창의 크기를 조정할 수 있습니다. 창을 Visual Studio 프레임 밖으로 독립적으로 끌 수 있으며 프레임 내에서 원하는 대로 다시 배치할 수도 있습니다. 자세한 내용은 [창 레이아웃 사용자 지정](../ide/customizing-window-layouts-in-visual-studio.md)을 참조하세요.

1. 몇 가지 문(예: `print("Hello, Visual Studio")`) 및 식(예: `123/456`)을 입력하여 즉각적인 결과를 확인하세요.

    ![Python 대화형 창의 즉각적인 결과](media/vs-getting-started-python-12-interactive2.png)

1. 함수 정의와 같이 여러 줄로 된 문을 작성하기 시작하면 **대화형** 창에 명령줄 REPL과 달리 연속되는 줄을 위해 자동 들여쓰기를 제공하는 Python의 **...** 프롬프트가 표시됩니다.

    ![연속 문을 지원하는 Python 대화형 창](media/vs-getting-started-python-13-interactive3.png)

1. **대화형** 창은 사용자가 입력한 모든 내용의 전체 기록을 제공하고 여러 줄 기록 항목으로 명령줄 REPL을 개선합니다. 예를 들어 함수 줄을 줄별로 다시 만들지 않고 `f` 함수의 전체 정의를 단일 단위로 손쉽게 회수하고 이름을 손쉽게 `make_double`로 변경할 수 있습니다.

1. Visual Studio는 편집기 창에서 **대화형** 창으로 여러 줄의 코드를 보낼 수 있습니다. 이 기능을 사용하면 소스 파일에서 코드를 유지 관리하고 선택한 부분을 **대화형** 창에 쉽게 보낼 수 있습니다. 그런 다음 전체 프로그램을 실행하지 않고 신속한 REPL 환경에서 이러한 코드 조각을 사용하여 작업할 수 있습니다. 이 기능을 보려면 먼저 *PythonApplication1.py* 파일의 `for` 루프를 다음으로 바꿉니다.

    ```python
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        return ' ' * int(20 * cos(radians(x)) + 20) + 'o'
    ```

1. *.py* 파일에서 `import`, `from`, `make_dot_string` 함수 문을 선택합니다. 선택한 텍스트를 마우스 오른쪽 단추로 클릭하고 **대화형으로 전송**을 선택합니다(또는 **Ctrl**+**Enter**를 누름). 코드 조각이 **대화형** 창에 즉시 붙여넣어 지고 실행됩니다. 코드가 함수를 정의했으므로 해당 함수를 여러 번 호출하여 신속하게 테스트할 수 있습니다.

    ![대화형 창에 코드 보내기 및 테스트](media/vs-getting-started-python-14-interactive4.png)

    > [!Tip]
    > 선택 영역 *없이* 편집기에서 **Ctrl**+**Enter**를 사용하면 **대화형** 창에서 현재 코드 줄이 실행되고 자동으로 다음 줄에 캐럿이 배치됩니다. 이 기능을 사용하면 **Ctrl**+**Enter**를 반복적으로 눌러 Python 명령줄만으로 가능하지 않은 단계별 코드 실행을 편리하게 수행할 수 있습니다. 또한 디버거를 실행하지 않으며 시작 부분에서 프로그램을 반드시 시작하지 않고 코드를 단계별로 실행할 수 있도록 합니다.

1. 아래 코드 조각과 같이 임의 소스에서 여러 줄의 코드를 복사하고 **대화형** 창에 붙여넣을 수도 있습니다. Python 명령줄 REPL에서는 이러한 작업을 수행하기 어렵습니다. 붙여넣으면 입력한 것처럼 **대화형** 창에서 해당 코드가 실행됩니다.

    ```python
    for i in range(360):
        s = make_dot_string(i)
        print(s)
    ```

    ![Interactive로 보내기를 사용하여 여러 줄의 코드 붙여넣기](media/vs-getting-started-python-15-interactive5.png)

1. 볼 수 있듯이 이 코드는 제대로 작동하지만 해당 출력을 권장하지 않습니다. `for` 루프의 다른 단계 값은 코사인 웨이브로 표시됩니다. 다행히 전체 `for` 루프는 REPL 기록에 단일 단위로 존재하기 때문에 손쉽게 다시 돌아가서 원하는 부분을 변경한 후 함수를 다시 테스트할 수 있습니다. 위쪽 화살표 키를 눌러 먼저 `for` 루프를 회수합니다. 그런 다음 왼쪽 또는 오른쪽 화살표 키를 눌러 코드에서 탐색을 시작합니다(이렇게 할 때까지 위쪽 및 아래쪽 화살표는 기록을 통해 계속해서 순환함). 탐색하고 `range` 사양을 `range(0, 360, 12)`로 변경합니다. 그런 다음, 코드의 아무 곳에서나 **Ctrl**+**Enter**를 눌러 전체 문을 다시 실행합니다.

    ![대화형 창에서 이전 문 편집](media/vs-getting-started-python-16-interactive6.png)

1. 프로세스를 반복하여 가장 마음에 드는 값을 찾을 때까지 다른 단계 설정으로 실험합니다. 범위를 늘려(예: `range(0, 1800, 12)`) 웨이브 반복을 만들 수도 있습니다.

1. **대화형** 창으로 작성한 코드가 만족스럽다면 코드를 선택합니다. 다음으로 코드를 마우스 오른쪽 단추로 클릭하고 **코드 복사**를 선택합니다(**Ctrl**+**Shift**+**C**). 마지막으로 선택한 코드를 편집기에 붙여 넣습니다. Visual Studio의 이 특별한 기능이 모든 출력과 `>>>` 및 `...` 프롬프트를 자동으로 생략하는 방식을 확인합니다. 예를 들어 아래 이미지는 프롬프트 및 출력을 포함하는 선택 영역에서 **코드 복사** 명령을 사용하는 것을 보여 줍니다.

    ![프롬프트 및 출력이 있는 선택 영역에서 대화형 창 코드 복사 명령](media/vs-getting-started-python-17-interactive7.png)

    편집기에 붙여넣을 때 다음 코드만을 가져옵니다.

    ```python
    for i in range(0, 1800, 12):
        s = make_dot_string(i)
        print(s)
    ```

    프롬프트 및 출력을 포함하여 **대화형** 창의 정확한 내용을 복사하려는 경우 표준 **복사** 명령을 사용합니다.

1. 방금 수행한 작업은 **대화형** 창의 신속한 REPL 환경을 사용하여 작은 코드 부분의 세부 정보를 파악한 다음, 프로젝트의 소스 파일에 해당 코드를 편리하게 추가한 것입니다. 이제 **Ctrl**+**F5**(또는 **디버그** > **디버깅하지 않고 시작**)를 사용하여 코드를 다시 실행하면 원하는 정확한 결과가 표시됩니다.

## <a name="next-step"></a>다음 단계

> [!div class="nextstepaction"]
> [디버거에서 코드 실행](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)

## <a name="go-deeper"></a>자세히 알아보기

- [대화형 창 사용](python-interactive-repl-in-visual-studio.md)
- [IPython REPL 사용](interactive-repl-ipython.md)