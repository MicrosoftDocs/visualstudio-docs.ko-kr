---
title: Python 개발자용 Visual Studio 개요
titleSuffix: ''
ms.date: 03/13/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
dev_langs:
- Python
ms.workload:
- python
- data-science
ms.openlocfilehash: 943c0567e3726d014f7dae01915916864e09ed9b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88801648"
---
# <a name="welcome-to-the-visual-studio-ide--python"></a>Visual Studio IDE 시작 | Python

Visual Studio *통합 개발 환경*은 코드를 편집, 디버그 및 테스트한 다음, 앱을 게시하는 데 사용할 수 있는 Python(및 기타 언어)용 창의적인 실행 패드입니다. IDE(통합 개발 환경)는 소프트웨어 개발의 다양한 측면에서 사용할 수 있는 다양한 기능을 갖춘 프로그램입니다. 대부분의 IDE가 제공하는 표준 편집기 및 디버거 이상의 Visual Studio에는 코드 완성 도구, 대화형 REPL 환경 및 소프트웨어 개발 프로세스를 쉽게 만들어 주는 많은 기능이 포함되어 있습니다.

[![Python 프로젝트가 포함된 Visual Studio](media/tour-ide-overview.png)](media/tour-ide-overview.png#lightbox)

이 이미지는 Python 프로젝트와 사용할 만한 몇 가지 주요 도구 창이 열려 있는 Visual Studio를 보여줍니다.

- [**솔루션 탐색기**](../ide/solutions-and-projects-in-visual-studio.md)(오른쪽 위) - 코드 파일을 보고, 탐색하고, 관리할 수 있습니다. **솔루션 탐색기**에서 파일을 [솔루션 및 프로젝트](../get-started/tutorial-projects-solutions.md)로 그룹화하여 코드를 구성할 수 있습니다.
  - **솔루션 탐색기**와 함께 [**Python 환경**](managing-python-environments-in-visual-studio.md)이며, 여기에서 컴퓨터에 설치된 다양한 Python 인터프리터를 관리합니다.

  ::: moniker range=">=vs-2019"
  - Visual Studio 프로젝트 및 솔루션 파일을 만들지 않고도 폴더에서 Python 코드를 열고 실행할 수 있습니다. 자세한 내용은 [빠른 시작: 폴더에서 Python 코드 열기 및 실행](quickstart-05-python-visual-studio-open-folder.md)을 참조하세요.
  ::: moniker-end

- [편집기 창](../ide/writing-code-in-the-code-and-text-editor.md)(가운데) - 대부분 작업을 수행하는 곳으로 파일 콘텐츠가 표시됩니다. 이는 [Python 코드를 편집](editing-python-code-in-visual-studio.md)하고 코드 구조 내에서 탐색하며 디버깅 세션 중에 중단점을 설정하는 곳입니다. Python을 사용하면 코드를 선택하고 Ctrl + Enter를 눌러 [대화형 REPL 창](python-interactive-repl-in-visual-studio.md)에서 해당 코드를 실행할 수도 있습니다.

- [출력 창](../ide/reference/output-window.md)(가운데 아래)은 Visual Studio가 디버깅 및 오류 메시지, 경고, 게시 상태 메시지 등과 같은 알림을 보내는 곳입니다. 각 메시지 원본에 해당하는 탭이 있습니다.
  - [Python 대화형 REPL 창](python-interactive-repl-in-visual-studio.md)이 출력 창과 동일한 영역에 나타납니다.

- [팀 탐색기](/azure/devops/user-guide/work-team-explorer?view=vsts)(오른쪽 아래) - [Git](https://git-scm.com/), [TFVC(Team Foundation 버전 제어)](/azure/devops/repos/tfvc/overview?view=vsts) 등의 버전 제어 기술을 통해 작업 항목을 추적하고 다른 사용자와 코드를 공유할 수 있습니다.

## <a name="editions"></a>버전

Visual Studio는 Windows 및 Mac에서 사용할 수 있지만 Python 지원은 Windows용 Visual Studio에서만 사용할 수 있습니다.

Windows의 세 가지 Visual Studio 버전은 다음과 같습니다. Community, Professional 및 Enterprise. 각 버전에서 지원되는 기능에 대해 알아보려면 [Visual Studio IDE 비교](https://visualstudio.microsoft.com/vs/compare/)를 참조하세요.

## <a name="popular-productivity-features"></a>주요 생산성 향상 기능

소프트웨어를 개발할 때 생산성을 높이는 데 도움이 되는 Visual Studio에서 인기 있는 기능 몇 가지는 다음과 같습니다.

- [IntelliSense](editing-python-code-in-visual-studio.md#intellisense)

   IntelliSense는 편집기에서 직접 코드에 대한 정보를 표시하고 경우에 따라 약간의 코드를 작성하는 기능 집합에 대한 용어입니다. IntelliSense는 다른 곳에서 형식 정보를 조회할 필요가 없도록 기본 설명서를 편집기에 인라인으로 포함하는 것과 같습니다. IntelliSense 기능은 언어에 따라 다르며 [Python 코드 편집](editing-python-code-in-visual-studio.md#intellisense) 문서에는 Python에 대한 세부 정보가 있습니다. 다음 그림에서는 IntelliSense에서 형식에 대한 멤버 목록을 표시하는 방법을 보여 줍니다.

   ![Visual Studio IntelliSense를 사용한 멤버 완료](media/code-editing-completions-simple.png)

- [리팩터링](refactoring-python-code.md)

   Visual Studio는 코드 조각을 마우스 오른쪽 단추로 클릭하고 **빠른 작업 및 리팩터링**을 선택하여 변수의 지능형 이름 바꾸기, 새 메서드로 코드 줄을 하나 이상 추출, 메서드 매개 변수의 순서 변경 등과 같은 작업을 제공합니다.

   ![Visual Studio에서 리팩터링](media/tour-ide-refactor-extract-method.png)

- [Linting](refactoring-python-code.md)

   Linting은 Python 코드의 오류 및 일반적인 문제를 검사하여 적절한 Python 코딩 패턴을 장려합니다.

   ![Python 프로젝트의 상황에 맞는 메뉴에 있는 PyLint 명령](media/code-pylint-command.png)

- 검색 상자

   Visual Studio는 메뉴, 옵션 및 속성이 매우 다양하여 때때로 버거울 수도 있습니다. 검색 상자는 Visual Studio에서 필요한 항목을 빠르게 찾을 수 있는 좋은 방법입니다. 찾으려는 이름을 입력하기만 하면 Visual Studio는 원하는 곳으로 정확하게 안내하는 결과를 나열합니다. 예를 들어 다른 프로그래밍 언어를 위한 지원을 추가하도록 Visual Studio에 기능을 추가하는 경우 검색 상자를 사용하면 워크로드 또는 개별 구성 요소를 설치하도록 Visual Studio 설치 관리자가 열립니다.

   ![Visual Studio의 검색 상자](media/tour-ide-quick-launch.png)

- 오류 표시선 및 [빠른 작업](../ide/quick-actions.md)

   오류 표시선은 물결 모양의 밑줄로, 입력할 때 코드의 오류 또는 잠재적인 문제를 알려줍니다. 이러한 시각적 단서를 사용하면 빌드하는 동안이나 프로그램을 실행할 때 오류가 검색될 때까지 기다리지 않고 즉시 문제를 해결할 수 있습니다. 오류 표시선 위로 마우스를 가져가면 오류에 대한 추가 정보가 표시됩니다. 오류를 수정하기 위한 작업(빠른 작업이라고 함)과 함께 전구가 왼쪽 여백에 나타날 수도 있습니다.

   ![Visual Studio의 오류 표시선](media/tour-ide-squiggles.png)

- [이동 및 정의 피킹](../ide/go-to-and-peek-definition.md)

   **정의로 이동** 기능은 함수 또는 형식이 정의된 위치로 직접 이동합니다. **정의 피킹** 명령은 별도의 파일을 열지 않고 창에 정의를 표시합니다. 또한 **모든 참조 찾기** 명령은 지정된 식별자가 정의되고 사용되는 위치를 검색하는 유용한 방법을 제공합니다.

   ![코드 탐색 명령](media/tour-ide-navigation-commands.png)

## <a name="powerful-features-for-python"></a>Python을 위한 강력한 기능

::: moniker range=">=vs-2019"
- [프로젝트 없이 코드 실행](quickstart-05-python-visual-studio-open-folder.md)

    Visual Studio 2019부터 코드의 Visual Studio 프로젝트를 만들지 않고 IntelliSense 및 디버깅 같은 기능을 사용할 수 있도록 Python 코드가 포함된 폴더를 열 수 있습니다.
::: moniker-end

- [Visual Studio를 사용하여 공동 작업](/visualstudio/liveshare/)

    Visual Studio Live Share를 사용하면 사용 중인 프로그래밍 언어나 빌드 중인 앱 유형에 관계없이 다른 사람과 공동으로 실시간 편집 및 디버깅이 가능합니다.

- [Python 대화형 REPL](python-interactive-repl-in-visual-studio.md)

    Visual Studio는 각 Python 환경에 대화형 읽기-평가-인쇄 루프(REPL) 창을 제공하여 명령줄에서 *python.exe*와 관련한 REPL을 개선합니다. **대화형** 창에서 임의의 Python 코드를 입력하고 즉각적인 결과를 볼 수 있습니다.

    ![Python 대화형 창](media/interactive-window.png)

- [디버깅](debugging-python-in-visual-studio.md)

    Visual Studio에서는 실행 중인 프로세스에 연결하고, **조사식** 및 **직접 실행** 창에서 식을 계산하고, 지역 변수, 중단점, 단계별 실행/프로시저 나가기/프로시저 단위 실행 명령문, **다음 명령문 설정** 등을 검사하는 작업을 포함한 포괄적인 디버깅 환경을 Python에 제공합니다. Linux 컴퓨터에서 실행되는 원격 Python 코드를 디버깅할 수도 있습니다.

    ![Visual Studio의 Python 디버깅](media/remote-debugging-breakpoint-hit.png)

- [C++와 상호 작용](working-with-c-cpp-python-in-visual-studio.md)

    Python용으로 만들어진 많은 라이브러리는 최적의 성능을 위해 C++로 작성됩니다. Visual Studio는 [혼합 모드 디버깅](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)을 포함하여 C++ 확장 개발에 필요한 다양한 기능을 제공합니다.

    ![Python과 C++의 혼합 모드 디버깅](media/mixed-mode-debugging.png)

- [프로파일링](profiling-python-code-in-visual-studio.md)

    CPython 기반 인터프리터를 사용하는 경우 Visual Studio 내에서 Python 코드의 성능을 평가할 수 있습니다.

    ![프로파일링 성능 보고서](media/profiling-results.png)

- [단위 테스트](unit-testing-python-in-visual-studio.md)

    Visual Studio는 IDE의 컨텍스트에서 모든 단위 테스트의 검색, 실행 및 디버깅을 위한 통합 지원을 제공합니다.

    ![실패한 테스트 상태를 표시하는 단위 테스트](media/unit-test-A-fail.png)

## <a name="next-steps"></a>다음 단계

다음 빠른 시작 또는 자습서 중 하나를 수행하여 Visual Studio에서 Python을 자세히 살펴봅니다.

> [!div class="nextstepaction"]
> [빠른 시작: Flask를 사용하여 웹앱 만들기](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)

> [!div class="nextstepaction"]
> [Visual Studio에서 Python 작업](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

> [!div class="nextstepaction"]
> [Visual Studio에서 Django 웹 프레임워크 시작](learn-django-in-visual-studio-step-01-project-and-solution.md)

> [!div class="nextstepaction"]
> [Visual Studio에서 Flask 웹 프레임워크 시작](learn-flask-visual-studio-step-01-project-solution.md)

## <a name="see-also"></a>참조

- [Visual Studio 추가 기능](../ide/advanced-feature-overview.md)을 검색하세요.
- [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/)을 방문하세요.
- [Visual Studio 블로그](https://devblogs.microsoft.com/visualstudio/)를 참고하세요.
