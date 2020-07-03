---
title: Python 대화형 창(REPL)
description: Visual Studio에서 빠른 Python 코드 개발을 위해 대화형 창(REPL)을 사용합니다.
ms.date: 02/11/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 9608f273683865be767a44dd8f1d66106b97b7e0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533551"
---
# <a name="work-with-the-python-interactive-window"></a>Python 대화형 창 작업

Visual Studio는 각 Python 환경에 대화형 읽기-평가-인쇄 루프(REPL) 창을 제공하여 명령줄에서 *python.exe*와 관련한 REPL을 개선합니다. **대화형** 창(**보기** > **다른 창** >  **&lt;환경&gt; 대화형** 창 메뉴 명령으로 열 수 있음)을 사용하면 임의의 Python 코드를 입력하고 즉각적인 결과를 확인할 수 있습니다. 이러한 방식의 코딩은 API 및 라이브러리와 관련된 내용을 배우고 실험하는 데 도움이 되고, 프로젝트에 포함할 작업 코드를 대화형으로 개발하는 데에도 유용합니다.

![Python 대화형 창](media/interactive-window.png)

Visual Studio에는 선택 가능한 다양한 Python REPL 모드가 있습니다.

| REPL | 설명 | 편집 | 디버깅 | 이미지 |
| --- | --- | --- | --- | --- |
| 표준 | 기본 REPL, Python에 직접 명령 | 표준 편집(여러 줄 등). | 예, `$attach`를 통해 | 아니요 |
| 디버그 | 기본 REPL, 디버깅된 Python 프로세스에 명령 | 표준 편집 | 디버깅만 | 아니요 |
| IPython | REPL이 IPython 백 엔드에 명령 | IPython 명령, Pylab의 편리한 기능 | 아니요 | 예, REPL에서 인라인으로 |
| Pylab가 없는 IPython | REPL이 IPython 백 엔드에 명령 | 표준 IPython | 아니요 | 예, 별도의 창 |

이 문서에서는 **표준** 및 **디버그** REPL 모드를 설명합니다. IPython 모드에 대한 자세한 내용은 [IPython REPL 사용](interactive-repl-ipython.md)을 참조하세요.

**Ctrl**+**Enter** 등의 편집기 조작을 포함하여 예제를 사용한 자세한 연습을 보려면 [자습서 3단계: 대화형 REPL 창 사용](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)을 참조하세요.

## <a name="open-an-interactive-window"></a>대화형 창 열기

특정 환경에서 **대화형** 창을 여는 방법에는 여러 가지가 있습니다.

첫째, Python 환경 창(**보기** > **다른 창** > **Python 환경** 또는 **Ctrl**+**K** > **Ctrl**+ **`** )으로 전환하고 선택한 환경에서 **대화형 창 열기** 명령 또는 단추를 선택합니다.

![Python 환경 창의 대화형 창 링크](media/interactive-window-opening.png)

둘째, **보기** > **다른 창** 메뉴의 아래쪽에는 기본 환경에 대한 **Python 대화형 창** 명령뿐만 아니라 **환경** 창으로 전환하는 명령도 있습니다.

![보기 > 다른 창의 대화형 창 메뉴 항목](media/interactive-window-menu.png)

셋째, **디버그** > **Python 대화형 창에서 \<Project | File> 실행** 메뉴 명령(**Shift**+**Alt**+**F5**)을 선택하여 프로젝트의 시작 파일 또는 독립 실행형 파일에서 **대화형** 창을 열 수 있습니다.

![Python 대화형 창에서 프로젝트 실행 메뉴](media/interactive-execute-project.png)

마지막으로, 파일의 코드를 선택하고 아래에 설명된 [**Interactive로 보내기** 명령](#send-to-interactive-command)을 사용할 수 있습니다.

## <a name="interactive-window-options"></a>대화형 창 옵션

**도구** > **옵션** > **Python** > **대화형 창**을 통해 **대화형** 창의 다양한 측면을 제어할 수 있습니다([옵션](python-support-options-and-settings-in-visual-studio.md) 참조).

![Python 대화형 창 옵션](media/options-interactive-windows.png)

## <a name="use-the-interactive-window"></a>대화형 창 사용

**대화형** 창이 열리면 **\>\>\>** 프롬프트에서 코드를 한 줄씩 입력하기 시작할 수 있습니다. **대화형** 창은 사용자가 각 줄을 입력할 때 해당 줄을 실행합니다. 여기에는 모듈을 가져오고 변수를 정의하는 등의 과정이 포함됩니다.

![Python 대화형 창](media/interactive-window.png)

단, 위와 같이 `for` 문이 콜론으로 끝나는 경우 등 완전한 문을 만들기 위해 추가 코드 줄이 필요한 경우는 예외입니다. 이 경우 위의 그림에서 네 번째 및 다섯 번째 줄에 표시된 것처럼 줄 프롬프트가 **...** 으로 바뀌는데, 블록에 추가 줄을 입력해야 한다는 의미입니다. 빈 줄에서 **Enter** 키를 누르면 **대화형** 창이 블록을 닫고 인터프리터에서 실행합니다.

> [!Tip]
> **대화형** 창은 주변 범위에 속하는 문을 자동으로 들여쓰기하여 일반적인 Python 명령줄 REPL 환경을 개선합니다. 또한 명령줄 REPL은 단일 줄만 제공하지만 대화형 창은 위쪽 화살표로 회수할 수 있는 기록에 여러 줄 항목을 제공합니다.

<a name="meta-commands"></a>**대화형** 창은 몇 가지 메타 명령도 지원합니다. 모든 메타 명령은 `$`로 시작하고, `$help`를 입력하면 메타 명령의 목록을 가져올 수 있고, `$help <command>`를 입력하면 특정 명령의 자세한 사용법을 가져올 수 있습니다.

| 메타 명령 | 설명 |
| --- | --- |
| `$$` | 세션 전체에서 코드에 주석을 추가하는 데 도움이 되는 메모를 삽입합니다. |
| `$attach` | REPL 창 프로세스에 Visual Studio 디버거를 첨부하여 디버깅을 활성화합니다. |
| `$cls`, `$clear` | 편집기 창의 내용을 지워서 기록 및 실행 컨텍스트를 그대로 유지합니다. |
| `$help` | 명령 목록 또는 특정 명령에 대한 도움말을 표시합니다. |
| `$load` | 파일에서 명령을 로드하고 완료될 때까지 실행합니다. |
| `$mod` | 현재 범위를 지정된 모듈 이름으로 전환합니다. |
| `$reset` | 실행 환경을 초기 상태로 다시 설정하되, 기록을 유지합니다. |
| `$wait` | 지정된 기간(밀리초) 이상으로 기다립니다. |

`IInteractiveWindowCommand`를 구현하고 내보내 Visual Studio 확장에서 명령을 확장할 수도 있습니다([예제](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85)).

## <a name="switch-scopes"></a>범위 전환

기본적으로 프로젝트의 **대화형** 창은 명령 프롬프트에서 실행한 것처럼 프로젝트의 시작 파일로 범위가 지정됩니다. 독립 실행형 파일의 경우 해당 파일로 범위가 지정됩니다. 그러나 REPL 세션 중에 언제든지 **대화형** 창의 맨 위에 있는 드롭다운 메뉴를 사용하여 범위를 변경할 수 있습니다.

![대화형 창 범위](media/interactive-scopes.png)

`import importlib` 입력 등의 방법으로 모듈을 가져오면 해당 모듈의 임의 범위로 전환하기 위한 옵션이 드롭다운에 표시됩니다. 또한 **대화형** 창에 새 범위를 나타내는 메시지도 표시되므로 세션 중에 어떻게 특정 상태가 되었는지를 추적할 수 있습니다.

범위에 `dir()`을 입력하면 함수 이름, 클래스 및 변수 등 해당 범위에서 유효한 식별자가 표시됩니다. 예를 들어 `import importlib` 뒤에 `dir()`을 사용하면 다음이 표시됩니다.

![importlib 범위의 대화형 창](media/interactive-importlib-scope.png)

## <a name="send-to-interactive-command"></a>Interactive로 보내기 명령

**대화형** 창에서 직접 작업할 수 있을 뿐만 아니라 편집기에서 코드를 선택하고 마우스 오른쪽 단추를 클릭한 다음, **Interactive로 보내기**를 선택하거나 **Ctrl**+**Enter**를 누를 수 있습니다.

![Interactive로 보내기 메뉴 명령](media/interactive-send-to.png)

이 명령은 코드 개발 중 테스트를 포함하여 반복적이거나 발전적인 코드 개발에 유용합니다. 예를 들어 **대화형** 창에 코드 조각을 보내고 출력을 확인한 후 위쪽 화살표를 눌러 코드를 다시 표시하고 수정한 다음, **Ctrl**+**Enter**를 눌러 빠르게 테스트할 수 있습니다. 입력의 끝에서 **Enter** 키를 누르면 코드가 실행되지만 입력 중에 **Enter** 키를 누르면 줄 바꿈이 삽입됩니다. 원하는 코드를 만들었으면 프로젝트 파일에 다시 쉽게 복사할 수 있습니다.

> [!Tip]
> 기본적으로 Visual Studio에서 **>>>** 및 **...** REPL 프롬프트는 **대화형** 창의 코드를 편집기에 붙여넣을 때 제거됩니다. **도구** > **옵션** > **텍스트 편집기** > **Python** > **고급** 탭의 **붙여넣으면 REPL 프롬프트가 제거됨** 옵션을 사용하면 이 동작을 변경할 수 있습니다. [옵션 - 기타 옵션](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options)을 참조하세요.

<!-- After 15.3 is released, you can also press **Undo** after pasting to restore prompts. Press **Undo** a second time to remove the pasted code entirely. -->

## <a name="work-with-code-cells"></a>코드 셀 작업

코드 셀은 데이터를 분석하는 데 사용될 수 있으며 다양한 텍스트 편집기에서 지원됩니다.

예를 들어 코드 파일을 잠깐 보관함으로 사용하는 경우 작은 코드 블록을 한 번에 모두 전송하려는 경우가 많습니다. 코드를 그룹화하려면 `#%%`로 시작하는 주석을 셀의 시작 부분에 추가하여 코드를 *코드 셀*로 표시합니다. 주석을 추가하면 이전 코드 셀은 종료됩니다. 코드 셀을 축소 및 확장할 수 있으며, 코드 셀 내부에서 **Ctrl**+**Enter**를 사용하면 전체 셀이 **대화형** 창으로 전송되고 다음 셀로 이동합니다.

또한 Visual Studio는 `# In[1]:`과 같은 주석으로 시작하는 코드 셀도 검색합니다. 이 형식은 Jupyter Notebook을 Python 파일로 내보낼 때 사용되는 형식입니다. 이 검색을 통해 Python 파일로 다운로드하고 Visual Studio에서 연 다음, **Ctrl**+**Enter**로 각 셀을 실행하면 [Azure Notebook](https://notebooks.azure.com/)에서 노트북을 쉽게 실행할 수 있습니다.

![대화형 코드 셀](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>IntelliSense 동작

IntelliSense가 소스 코드 분석만을 기반으로 하는 코드 편집기와 달리 **대화형** 창에는 라이브 개체를 기반으로 한 IntelliSense가 포함되어 있습니다. 동적으로 생성된 코드의 경우 특히 **대화형** 창의 제안이 더 정확합니다. 단점은 부작용(예: 로깅 메시지)이 있는 함수가 개발 환경에 영향을 줄 수 있다는 점입니다.

이 동작이 문제가 될 경우 [옵션 - 대화형 창 옵션](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)에 설명된 대로 **도구** > **옵션** > **Python** > **대화형 창** 아래의 **완료 모드** 그룹에서 설정을 변경합니다.
