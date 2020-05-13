---
title: 빠른 시작 - Python 코드 폴더 열기
description: 이 빠른 시작에서는 Visual Studio 프로젝트를 사용하지 않고 폴더에서 Python 코드를 열어 실행합니다(Visual Studio 2019만 해당).
ms.date: 03/12/2019
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
monikerRange: '>= vs-2019'
ms.openlocfilehash: ab234d9482cf9cbab49c15167ea45aff9ac2c7e6
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "62431160"
---
# <a name="quickstart-open-and-run-python-code-in-a-folder"></a>빠른 시작: 폴더에서 Python 코드 열기 및 실행

[Visual Studio 2019에서 Python 지원을 설치](installing-python-support-in-visual-studio.md)하면 Visual Studio 프로젝트를 만들지 않고도 Visual Studio 2019에서 기존 Python 코드를 쉽게 실행할 수 있습니다.

> [!Note]
> Visual Studio 2017 및 이전 버전에서는 Visual Studio 프로젝트를 만들어야 Python 코드를 실행할 수 있으며, 이러한 작업은 기본 제공 프로젝트 템플릿을 사용하여 쉽게 수행할 수 있습니다. [빠른 시작: 기존 코드에서 Python 프로젝트 만들기](quickstart-01-python-in-visual-studio-project-from-existing-code.md)를 참조하세요.

1. 이 연습에서는 원하는 Python 코드가 있는 폴더를 사용할 수 있습니다. 여기에 나와 있는 예제를 계속 진행하려면 적합한 폴더에서 `git clone https://github.com/gregmalcolm/python_koans` 명령을 사용하여 gregmalcolm/python_koans GitHub 리포지토리를 컴퓨터에 복제하세요.

1. Visual Studio 2019를 시작하고 시작 창에서 **시작** 열 아래에 있는 **열기**를 선택합니다. 또는 이미 Visual Studio를 실행하고 있는 경우 **파일** > **열기** > **폴더** 명령을 선택합니다.

    ![Visual Studio 시작 화면](media/quickstart-open-folder/01-open-local-folder.png)

1. Python 코드가 있는 폴더로 이동하여 **폴더 선택**을 선택합니다. python_koans 코드를 사용하고 있는 경우 클론 폴더 내에서 `python3` 폴더를 선택해야 합니다.

    ![폴더 열기 명령의 폴더 선택 대화 상자](media/quickstart-open-folder/02-select-folder.png)

1. Visual Studio는 **폴더 뷰**라는 **솔루션 탐색기**에 폴더를 표시합니다. 폴더 이름 왼쪽 가장자리에 있는 화살표를 사용하여 폴더를 확장 및 축소할 수 있습니다.

    ![솔루션 탐색기에서 폴더를 확장 및 축소하는 컨트롤](media/quickstart-open-folder/03-expand-collapse-folders.png)

1. Python 폴더를 열면 Visual Studio는 프로젝트와 관련된 설정을 관리하는 여러 숨겨진 폴더를 만듭니다. 이러한 폴더와 다른 모든 숨겨진 파일 및 폴더(예: *.git* 폴더)를 보려면 **모든 파일 표시** 도구 모음 단추를 선택합니다.

    ![솔루션 탐색기의 숨겨진 폴더 뷰](media/quickstart-open-folder/05-view-hidden-folders.png)

1. 코드를 실행하려면 먼저 시작 또는 기본 프로그램 파일을 파악해야 합니다. 여기에 표시된 예제에서는 시작 파일 *contemplate-koans.py*입니다. 해당 파일을 마우스 오른쪽 단추로 클릭하고 **시작 항목으로 설정**을 선택합니다.

    ![솔루션 탐색기에서 시작 항목 설정](media/quickstart-open-folder/06-set-as-startup-item-command.png)

    > [!Important]
    > 열린 폴더의 루트에 시작 항목이 없는 경우에도 [작업 디렉터리 설정](#set-a-working-directory) 섹션에 설명된 대로 실행 구성 JSON 파일에 줄을 추가해야 합니다.

1. **Ctrl**+**F5**를 누르거나 **디버그** > **디버깅 없이 시작**을 선택하여 코드를 실행합니다. Visual Studio 디버거에서 코드를 실행하는 시작 항목을 재생 단추와 함께 표시하는 도구 모음 단추를 선택할 수도 있습니다. 모든 경우에서 Visual Studio가 시작 항목이 Python 파일임을 감지하므로 자동으로 기본 Python 환경에서 코드를 실행합니다. (해당 환경은 도구 모음의 시작 항목 오른쪽에 표시됩니다.)

    ![디버거 시작 도구 모음 단추](media/quickstart-open-folder/07-start-debug-toolbar.png)

1. 프로그램 출력이 별도의 명령 창에 표시됩니다.

    ![Python 코드 실행 출력 창](media/quickstart-open-folder/08-result-window.png)

1. 다른 환경에서 코드를 실행하려면 도구 모음의 드롭다운 컨트롤에서 해당 환경을 선택하고 시작 항목을 다시 시작합니다.

1. Visual Studio에서 폴더를 닫으려면 **파일** > **폴더 닫기** 메뉴 명령을 선택합니다.

## <a name="set-a-working-directory"></a>작업 디렉터리 설정

기본적으로 Visual Studio는 해당 폴더의 루트에 폴더로 열린 Python 프로젝트를 실행합니다. 하지만 프로젝트의 코드는 Python이 하위 폴더에서 실행되고 있다고 가정할 수 있습니다. 예를 들어 python_koans 리포지토리의 루트 폴더를 열고 *python3/contemplate-koans.py* 파일을 시작 항목으로 설정한다고 가정해보겠습니다. 그런 다음, 코드를 실행하면 *koans.txt* 파일을 찾을 수 없다는 오류가 표시됩니다. 이 오류는 *contemplate-koans.py*에서 Python이 리포지토리 루트가 아닌 *python3* 폴더에서 실행되고 있다고 가정하기 때문에 발생합니다.

이런 경우도 시작 구성 JSON 파일에 줄을 추가하여 작업 디렉터리를 지정해야 합니다.

1. **솔루션 탐색기**에서 Python( *.py*) 시작 파일을 마우스 오른쪽 단추로 클릭하고 **디버그 및 시작 설정**을 선택합니다.

    ![Python 파일의 디버그 및 시작 설정 명령](media/quickstart-open-folder/09-debug-launch-settings-menu-command.png)

1. 표시되는 **디버거 선택** 대화 상자에서 **기본값**, **선택**을 차례로 누릅니다.

    ![Python 파일의 디버그 및 시작 설정 명령](media/quickstart-open-folder/10-select-debugger.png)

    > [!Note]
    > 선택 항목으로 **기본값**이 표시되지 않는 경우 **디버그 및 시작 설정** 명령을 선택할 때 Python *.py* 파일을 마우스 오른쪽 단추로 클릭했는지 확인하세요. Visual Studio는 파일 형식을 사용하여 표시할 디버거 옵션을 결정합니다.

1. Visual Studio는 숨겨진 *.vs* 폴더에 있는 *launch.vs.json* 파일을 엽니다. 이 파일은 프로젝트의 디버깅 컨텍스트를 설명합니다. 작업 디렉터리를 지정하려면 python-koans 예제의 `"workingDirectory": "python3"`와 같이 `"workingDirectory"`에 대한 값을 추가하세요.

    ```json
    {
      "version": "0.2.1",
      "defaults": {},
      "configurations": [
        {
          "type": "python",
          "interpreter": "(default)",
          "interpreterArguments": "",
          "scriptArguments": "",
          "env": {},
          "nativeDebug": false,
          "webBrowserUrl": "",
          "project": "python3\\contemplate_koans.py",
          "name": "contemplate_koans.py",
          "workingDirectory": "python3"
        }
      ]
    }
    ```

1. 파일을 저장하고 프로그램을 다시 시작하면 이제 지정된 폴더에서 프로그램이 실행됩니다.

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [자습서: Visual Studio에서 Python 작업](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>참조

- [빠른 시작: 기존 코드에서 Python 프로젝트 만들기](quickstart-01-python-in-visual-studio-project-from-existing-code.md)
- [빠른 시작: 리포지토리에서 Python 프로젝트를 만들기](quickstart-03-python-in-visual-studio-project-from-repository.md)
- [기존 Python 인터프리터 수동 식별](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
