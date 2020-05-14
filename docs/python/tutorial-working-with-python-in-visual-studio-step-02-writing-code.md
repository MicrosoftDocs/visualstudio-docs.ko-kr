---
title: Visual Studio 자습서 2단계에서 Python 코드 작성 및 실행
titleSuffix: ''
description: Visual Studio의 Python 기능에 대한 핵심 연습의 2단계로, 코드 편집 및 프로젝트 실행을 포함합니다.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: fda68b9e5bffbd1afab3389a0d8d624312a8de3f
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "62430074"
---
# <a name="step-2-write-and-run-code"></a>2단계: 작성 및 코드 실행

**이전 단계: [새 Python 프로젝트 만들기](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)**

프로젝트 파일은 **솔루션 탐색기**에서 관리하더라도 일반적으로 소스 코드와 같은 파일의 ‘콘텐츠’는 ‘편집기’ 창에서 작업합니다. 편집기는 컨텍스트에 따라 프로그래밍 언어(파일 확장명에 따라)를 포함한 편집 중인 파일의 유형을 파악하고, IntelliSense를 사용한 구문 색 지정 및 자동 완성과 같이 해당 언어에 적절한 기능을 제공합니다.

1. 새로운 “Python 애플리케이션” 프로젝트를 만들면 Visual Studio 편집기에 *PythonApplication1.py*라는 기본 빈 파일이 열립니다.

1. 편집기에서 `print("Hello, Visual Studio")`를 입력하기 시작하면 Visual Studio IntelliSense가 입력 도중에 자동 완성 옵션을 어떻게 표시하는지 알 수 있습니다. 드롭다운 목록에서 윤곽선이 있는 옵션은 **Tab** 키를 누르면 사용되는 기본 완성입니다. 완성 기능은 더 긴 문이나 식별자가 포함된 경우에 가장 유용합니다.

    ![IntelliSense 자동 완성 팝업](media/vs-getting-started-python-04-IntelliSense1b.png)

1. IntelliSense는 사용자가 사용하는 문, 호출하는 함수 등에 따라 다른 정보를 표시합니다. 함수 호출을 표시하도록 `print` 뒤에 `(`를 입력하여 `print` 함수를 사용하면 해당 함수에 대한 전체 사용 정보가 표시됩니다. 또한 IntelliSense는 현재 인수를 굵은 글꼴로 표시합니다(다음에 표시된 것처럼 **value**).

    ![IntelliSense 함수 자동 완성 팝업](media/vs-getting-started-python-05-IntelliSense2b.png)

1. 다음과 일치하도록 문을 완성하세요.

    ```python
    print("Hello, Visual Studio")
    ```

1. 구문 색 지정은 `print` 문을 `"Hello Visual Studio"` 인수와 구분합니다. 또한 문자열에서 마지막 `"`를 일시적으로 삭제하여 Visual Studio에서 구문 오류가 포함된 코드에 빨간색 밑줄이 어떻게 표시되는지 확인합니다. 그런 다음 `"`를 다시 입력하여 코드를 수정합니다.

    ![IntelliSense 구문 색 지정 및 오류 강조 표시](media/vs-getting-started-python-06-IntelliSense3b.png)

    > [!Tip]
    > 개발 환경은 매우 개인적인 문제이기 때문에 Visual Studio는 사용자가 Visual Studio의 모양 및 동작을 완벽히 제어할 수 있는 기능을 제공합니다. **도구** > **옵션** 메뉴 명령을 선택하고 **환경** 및 **텍스트 편집기** 탭 아래에 있는 설정을 탐색합니다. 기본적으로 제한된 개수의 옵션만 표시됩니다. 모든 프로그래밍 언어에 대한 옵션을 모두 보려면 대화 상자의 맨 아래에 있는 **모든 설정 표시**를 선택합니다.

1. **Ctrl**+**F5**를 누르거나 **디버그** > **디버깅하지 않고 시작** 메뉴 항목을 선택하여 이 지점까지 작성한 코드를 실행합니다. 코드에 여전히 오류가 있는 경우 Visual Studio에서 경고 메시지를 표시합니다.

1. 프로그램을 실행하면 명령줄에서 *PythonApplication1.py*를 사용하여 Python 인터프리터를 실행했을 때와 마찬가지로 결과가 표시된 콘솔 창이 나타납니다. 아무 키나 눌러서 창을 닫고 Visual Studio 편집기로 돌아갑니다.

    ![프로그램의 첫 번째 실행에 대한 출력](media/vs-getting-started-python-07-output.png)

1. IntelliSense는 명령문 및 함수 완성 외에 Python `import` 및 `from` 문 완성 기능도 제공합니다. 이러한 완성 기능을 사용하면 사용자 환경에서 사용할 수 있는 모듈과 해당 모듈의 멤버를 손쉽게 확인할 수 있습니다. 편집기에서 `print` 줄을 삭제하고 `import` 입력을 시작합니다. 공백을 입력하면 모듈의 목록이 표시됩니다.

    ![import 문에 사용할 수 있는 모듈을 보여 주는 IntellSense](media/vs-getting-started-python-08-import1.png)

1. `sys`를 입력하거나 선택하여 줄을 완성합니다.

1. 다음 줄에 `from`을 입력하면 모듈 목록을 다시 볼 수 있습니다.

    ![from 문에 사용할 수 있는 모듈을 보여 주는 IntellSense](media/vs-getting-started-python-09-import2.png)

1. `math`를 선택하거나 입력한 후 계속해서 공백과 `import`를 입력하면 모듈 멤버가 표시됩니다.

    ![모듈 멤버를 보여 주는 IntellSense](media/vs-getting-started-python-10-import3.png)

1. `sin`, `cos` 및 `radians` 멤버를 가져오고 각각에 사용 가능한 자동 완성을 확인하여 완료합니다. 완료되면 코드가 다음과 같이 표시됩니다.

    ```python
    import sys
    from math import cos, radians
    ```

    > [!Tip]
    > 완성 기능은 사용자가 입력하는 하위 문자열, 단어와 일치하는 부분, 단어 시작 부분의 글자, 생략된 문자에 작동합니다. 자세한 내용은 [코드 편집 - 완성](editing-python-code-in-visual-studio.md#completions)을 참조하세요.

1. 360도 코사인 값을 인쇄하려면 코드를 조금 더 추가합니다.

    ```python
    for i in range(360):
        print(cos(radians(i)))
    ```

1. **Ctrl**+**F5** 또는 **디버그** > **디버깅하지 않고 시작**을 사용하여 프로그램을 다시 실행합니다. 완료되면 출력 창을 닫습니다.

## <a name="next-step"></a>다음 단계

> [!div class="nextstepaction"]
> [대화형 REPL 창 사용](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)

## <a name="go-deeper"></a>자세히 알아보기

- [코드 편집](editing-python-code-in-visual-studio.md)
- [코드 형식](formatting-python-code.md)
- [코드 리팩터링](refactoring-python-code.md)
- [PyLint 사용](linting-python-code.md)
