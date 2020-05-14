---
title: Visual Studio IDE 둘러보기
titleSuffix: ''
ms.date: 02/21/2019
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 490d3edddd35ad5d72733824e3af41888839e946
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75596972"
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>빠른 시작: 먼저 Visual Studio IDE 살펴보기

이 5~10분이 걸리는 Visual Studio IDE(통합 개발 환경) 소개 내용에서는 창, 메뉴 및 기타 UI 기능 일부를 살펴보겠습니다.

::: moniker range="vs-2017"

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 페이지로 이동하여 평가판을 설치합니다.

::: moniker-end

::: moniker range=">=vs-2019"

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads) 페이지로 이동하여 평가판을 설치합니다.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>시작 페이지

Visual Studio를 열면 맨 처음 표시되는 것은 대부분 **시작 페이지**입니다. **시작 페이지**는 필요한 명령과 프로젝트 파일을 빠르게 찾아볼 수 있는 “허브”로 디자인되었습니다. **최근 항목** 섹션에는 최근에 작업한 프로젝트 및 폴더가 표시됩니다. **새 프로젝트**에서 링크를 클릭하여 **새 프로젝트** 대화 상자를 표시하거나, **열기**에서 기존 코드 프로젝트 또는 폴더를 열 수 있습니다. 오른쪽에는 최신 개발자 뉴스 피드가 있습니다.

![Visual Studio의 시작 페이지](media/start-page.png)

**시작 페이지**를 닫았다가 다시 보려면 **파일** 메뉴에서 다시 열 수 있습니다.

![Visual Studio의 파일 메뉴](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a>시작 창

Visual Studio를 열면 맨 처음 표시되는 것은 시작 창입니다. 시작 창은 "코드 가져오기"를 더 빨리 할 수 있도록 설계되었습니다. 코드를 복제 또는 체크 아웃하거나, 기존 프로젝트 또는 솔루션을 열거나, 새 프로젝트를 만들거나, 일부 코드 파일이 포함된 폴더를 열 수 있는 옵션이 있습니다.

[![Visual Studio 2019의 시작 창](media/vs-2019/start-window-labeled.png)](media/vs-2019/start-window-labeled.png#lightbox)

Visual Studio를 처음 사용하는 경우 최근 프로젝트 목록이 비어 있습니다.

비 MSBuild 기반 코드베이스로 작업하는 경우 **로컬 폴더 열기** 옵션을 사용하여 Visual Studio에서 코드를 엽니다. 자세한 내용은 [프로젝트 또는 솔루션 없이 Visual Studio에서 코드 개발](develop-code-in-visual-studio-without-projects-or-solutions.md)을 참조하세요. 그렇지 않으면 새 프로젝트를 만들거나 GitHub 또는 Azure DevOps와 같은 원본 공급자에서 프로젝트를 복제할 수 있습니다.

**코드 없이 계속** 옵션은 특정 프로젝트나 코드를 로드하지 않고 Visual Studio 개발 환경을 열면 됩니다. 이 옵션을 선택하면 [Live Share](/visualstudio/liveshare/) 세션에 조인하거나 디버깅을 위해 프로세스에 연결할 수 있습니다. **Esc**를 눌러 시작 창을 닫고 IDE를 열 수도 있습니다.

::: moniker-end

## <a name="create-a-project"></a>프로젝트 만들기

Visual Studio의 기능을 계속 탐색하기 위해 새 프로젝트를 만들어 보겠습니다.

::: moniker range="vs-2017"

1. **시작 페이지**의 **새 프로젝트**에 있는 검색 상자에 **console**을 입력하여 프로젝트 형식 목록을 이름에 “console”이 포함된 항목으로 필터링합니다.

   ![Visual Studio 시작 페이지에서 프로젝트 템플릿 검색](media/start-page-search-templates.png)

   Visual Studio에서는 신속하게 코딩을 시작하는 데 도움이 되는 다양한 종류의 프로젝트 템플릿을 제공합니다. C# **콘솔 앱(.NET Core)** 프로젝트 템플릿을 선택합니다. (또는 Visual Basic, C++, Javascript나 기타 언어 개발자인 경우 해당 언어 중 하나로 프로젝트를 만들 수 있습니다. 표시되는 UI는 모든 프로그래밍 언어에서 비슷합니다.)

1. 표시되는 **새 프로젝트** 대화 상자에서 기본 프로젝트 이름을 그대로 사용하고 **확인**을 선택합니다.

::: moniker-end

::: moniker range=">=vs-2019"

1. 시작 창에서 **새 프로젝트 만들기**를 선택합니다.

   **새 프로젝트 만들기**라고 표시된 대화 상자가 열립니다. 여기서 프로젝트 템플릿을 검색, 필터링 및 선택할 수 있습니다. 최근에 사용한 프로젝트 템플릿 목록도 보여줍니다.

1. 맨 위에 있는 검색 상자에 **console**을 입력하여 프로젝트 유형 목록을 이름에 “console”이 포함된 프로젝트 유형으로 필터링합니다. **언어** 선택기에서 **C#**(또는 선택한 다른 언어)를 선택하여 검색 결과를 더 구체화합니다.

   ![Visual Studio 2019의 새 프로젝트 대화 상자](media/vs-2019/create-a-new-project.png)

1. C#, Visual Basic 또는 F#를 언어로 선택한 경우 **콘솔 앱(.NET Core)** 템플릿을 선택하고 **다음**을 선택합니다. (다른 언어를 선택한 경우에는 임의로 템플릿을 선택하면 됩니다. 표시되는 UI는 모든 프로그래밍 언어에서 비슷합니다.)

1. **새 프로젝트 구성** 페이지에서 기본 프로젝트 이름 및 위치를 그대로 사용하고 **만들기**를 선택합니다.

::: moniker-end

   프로젝트가 만들어지고 *편집기* 창에 **Program.cs**라는 파일이 열립니다. **편집기**에는 파일 내용이 표시되며, 여기서 Visual Studio에서 하는 코딩 작업 대부분을 수행합니다.

   ![Visual Studio의 편집기](media/editor.png)

## <a name="solution-explorer"></a>솔루션 탐색기

일반적으로 Visual Studio의 오른쪽에 있는 **솔루션 탐색기**에는 프로젝트, 솔루션 또는 코드 폴더에 있는 파일 및 폴더의 계층 구조가 그래픽으로 표시됩니다. **솔루션 탐색기**에서 계층 구조를 탐색하고 파일로 이동할 수 있습니다.

![Visual Studio의 솔루션 탐색기](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>메뉴

Visual Studio의 위쪽에 있는 메뉴 모음은 명령을 범주로 그룹화합니다. 예를 들어 **프로젝트** 메뉴에는 작업 중인 프로젝트와 관련된 명령이 포함되어 있습니다. **도구** 메뉴에서 **옵션**을 선택하여 Visual Studio 동작 방법을 사용자 지정하거나, **도구 및 기능 가져오기**를 선택하여 설치에 기능을 추가할 수 있습니다.

::: moniker range="vs-2017"

![Visual Studio 2017의 메뉴 모음](media/quickstart-IDE-menu-bar.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Visual Studio 2019의 메뉴 모음](media/vs-2019/menu-bar.png)

::: moniker-end

## <a name="error-list"></a>오류 목록

**보기** 메뉴, **오류 목록**을 차례로 선택하여 **오류 목록** 창을 엽니다.

**오류 목록**에는 오류, 경고 및 코드의 현재 상태에 대한 메시지가 표시됩니다. 파일 또는 프로젝트 어딘가에 오류(예: 괄호 또는 세미콜론 누락)가 있는 경우 여기에 나열됩니다.

![Visual Studio의 오류 목록](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>출력 창

**출력** 창에는 프로젝트 및 원본 제어 공급자에서 빌드한 출력 메시지가 표시됩니다.

프로젝트를 빌드하여 일부 빌드 출력을 확인하겠습니다. **빌드** 메뉴에서 **솔루션 빌드**를 선택합니다. **출력** 창에는 자동으로 포커스가 표시되고 빌드 성공 메시지가 표시됩니다.

![Visual Studio의 출력 창](media/build-output-minimal.png)

## <a name="search-box"></a>검색 상자

검색 상자를 사용하면 Visual Studio의 거의 모든 항목으로 빠르고 쉽게 이동할 수 있습니다. 수행하려는 작업과 관련된 일부 텍스트를 입력하면 해당 텍스트와 관련된 옵션 목록이 표시됩니다. 예를 들어 빌드가 정확하게 수행하는 작업에 대한 추가 세부 정보를 표시하기 위해 빌드 출력의 세부 정보 표시를 증가시킨다고 가정해 보겠습니다. 수행할 수 있는 방법은 다음과 같습니다.

::: moniker range="vs-2017"

1. IDE의 오른쪽 위에 있는 **빠른 실행** 검색 상자를 찾습니다. (또는 **Ctrl**+**Q**를 눌러 액세스하세요.)

2. 검색 상자에 **자세한 정도**를 입력합니다. 표시된 결과에서 **옵션** 범주에 있는 **프로젝트 및 솔루션 -> 빌드 및 실행**을 선택합니다.

   ![Visual Studio 2017의 빠른 실행 검색 상자](media/quickstart-IDE-quick-launch.png)

   **옵션** 대화 상자가 열려 **빌드 및 실행** 옵션 페이지가 표시됩니다.

::: moniker-end

::: moniker range=">=vs-2019"

1. **Ctrl**+**Q**를 눌러 IDE의 위쪽 부분에 있는 검색 상자를 활성화합니다.

2. 검색 상자에 **자세한 정도**를 입력합니다. 표시된 결과에서 **MSBuild의 자세한 정도 변경**을 선택합니다.

   ![Visual Studio 2019의 검색 상자](media/vs-2019/quick-launch-verbosity.png)

   **옵션** 대화 상자가 열려 **빌드 및 실행** 옵션 페이지가 표시됩니다.

::: moniker-end

3. **MSBuild 프로젝트 빌드 출력의 자세한 정도** 아래에서 **보통**을 선택한 다음 **확인**을 클릭합니다.

4. **솔루션 탐색기**에서 **ConsoleApp1** 프로젝트를 마우스 오른쪽 단추로 클릭하고 팝업 메뉴에서 **다시 빌드**를 선택하여 프로젝트를 다시 빌드합니다.

   이번에는 **출력** 창에 어떤 파일이 어디에 복사되었는지를 비롯하여 빌드 프로세스의 더 자세한 정보 로깅이 표시됩니다.

   ![Visual Studio의 세부 정보 표시 빌드 출력](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>사용자 의견 보내기 메뉴

Visual Studio를 사용하는 동안 문제가 발생하거나 제품을 개선하는 방법에 대한 제안이 있는 경우 Visual Studio 창의 위쪽에 있는 **사용자 의견 보내기** 메뉴를 사용할 수 있습니다.

::: moniker range="vs-2017"

![Visual Studio 2017의 사용자 의견 보내기 메뉴](media/quickstart-IDE-send-feedback.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Visual Studio 2019의 사용자 의견 보내기 메뉴](media/vs-2019/send-feedback-menu.png)

::: moniker-end

## <a name="next-steps"></a>다음 단계

사용자 인터페이스에 익숙해지도록 Visual Studio의 몇 가지 기능에 대해 살펴보았습니다. 더 살펴보려면:

> [!div class="nextstepaction"]
> [코드 편집기에 대한 자세한 정보](../get-started/tutorial-editor.md)

> [!div class="nextstepaction"]
> [프로젝트 및 솔루션에 대한 자세한 정보](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>참고 항목

- [Visual Studio IDE 개요](../get-started/visual-studio-ide.md)
- [Visual Studio의 추가 기능](../ide/advanced-feature-overview.md)
- [테마 및 글꼴 색 변경](../ide/quickstart-personalize-the-ide.md)
