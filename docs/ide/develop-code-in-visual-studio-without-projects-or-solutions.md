---
title: 프로젝트 또는 솔루션 없이 코드 개발
ms.date: 02/21/2018
ms.topic: conceptual
helpviewer_keywords:
- open folder [Visual Studio]
- anycode [Visual Studio]
- projects and solutions, develop code without
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7a9459868d569a7466dccf92e4b548c0500bf80
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596296"
---
# <a name="develop-code-in-visual-studio-without-projects-or-solutions"></a>프로젝트 또는 솔루션 없이 Visual Studio에서 코드 개발

솔루션이나 프로젝트 파일 없이 거의 모든 유형의 디렉터리 기반 프로젝트에서 Visual Studio로 코드를 열 수 있습니다. 예를 들어 GitHub에서 리포지토리를 복제하여 Visual Studio로 직접 열고 솔루션이나 프로젝트를 만들지 않고도 개발을 시작할 수 있습니다. 필요한 경우 간단한 JSON 파일을 통해 사용자 지정 빌드 작업을 지정하고 매개 변수를 실행할 수 있습니다.

Visual Studio에서 코드 파일을 연 후 **솔루션 탐색기**에는 폴더의 모든 파일이 표시됩니다. 파일을 클릭하여 편집을 시작할 수 있습니다. 백그라운드에서 Visual Studio는 IntelliSense, 탐색 및 리팩터링 기능을 사용할 수 있도록 파일 인덱싱을 시작합니다. 파일을 편집, 생성, 이동 또는 삭제하면 Visual Studio는 변경 내용을 자동으로 추적하고 해당 IntelliSense 인덱스를 계속해서 업데이트합니다. 코드는 구문 색 지정으로 표시되며, 대부분의 경우 기본 IntelliSense 문 완성을 포함합니다.

## <a name="open-any-code"></a>코드 열기

Visual Studio에서 다음과 같은 방법으로 코드를 열 수 있습니다.

- Visual Studio 메뉴 모음에서 **파일** > **열기** > **폴더**를 선택한 다음, 코드 위치로 이동합니다.

- 코드가 포함된 폴더의 상황에 맞는 메뉴(마우스 오른쪽 단추 클릭)에서 **Visual Studio에서 열기** 명령을 선택합니다.

::: moniker range="vs-2017"
- Visual Studio **시작 페이지**에서 **폴더 열기** 링크를 선택합니다.
::: moniker-end

::: moniker range=">=vs-2019"
- 시작 창에서 **폴더 열기** 링크를 선택합니다.
::: moniker-end

- 키보드 사용자인 경우 Visual Studio에서 **Ctrl**+**Shift**+**Alt**+**O**를 누릅니다.

- 복제된 GitHub 리포지토리에서 코드를 엽니다.

### <a name="to-open-code-from-a-cloned-github-repo"></a>복제된 GitHub 리포지토리에서 코드를 열려면

다음 예제에서는 GitHub 리포지토리를 복제한 다음 Visual Studio에서 해당 코드를 여는 방법을 보여 줍니다. 이 절차를 따르려면 GitHub 계정이 있어야 하고, 시스템에 Git for Windows가 설치되어 있어야 합니다. 자세한 내용은 [새 GitHub 계정 등록](https://help.github.com/articles/signing-up-for-a-new-github-account/)(영문) 및 [Git for Windows](https://git-for-windows.github.io/)(영문)를 참조하세요.

1. GitHub에서 복제하려는 리포지토리로 이동합니다.

1. **복제 또는 다운로드** 단추를 선택한 다음, 드롭다운 메뉴에서 **클립보드로 복사** 단추를 선택하여 GitHub 리포지토리에 대한 보안 URL을 복사합니다.

   ![GitHub 복제 단추](./media/VSIDE_Code_Clone.png)

1. Visual Studio에서 **팀 탐색기** 탭을 선택하여 **팀 탐색기**를 엽니다. 탭이 표시되지 않으면 **보기** > **팀 탐색기**에서 엽니다.

1. [팀 탐색기]의 **로컬 Git 리포지토리** 섹션에서 **복제** 명령을 선택한 다음, GitHub 페이지의 URL을 텍스트 상자에 붙여넣습니다.

   ![프로젝트 복제](./media/VSIDE_Code_Clone2.png)

1. **복제** 단추를 선택하여 프로젝트 파일을 로컬 Git 리포지토리에 복제합니다. 리포지토리의 크기에 따라 이 프로세스에는 몇 분이 걸릴 수 있습니다.

1. 시스템에 리포지토리를 복제한 후에 **팀 탐색기**에서 새로 복제된 리포지토리의 상황에 맞는 메뉴(마우스 오른쪽 단추 클릭)에서 **열기** 명령을 선택합니다.

   ![복제된 리포지토리](./media/VSIDE_Code_Clone3.png)

1. **폴더 보기 표시** 명령을 선택하여 **솔루션 탐색기**에서 파일을 봅니다.

   ![폴더 보기 표시](./media/VSIDE_Code_Clone3_show.png)

   이제 복제된 리포지토리에서 폴더와 파일을 탐색하고 Visual Studio 코드 편집기에서 구문 색 지정 및 기타 기능을 사용하여 완성된 코드를 보고 검색할 수 있습니다.

## <a name="run-and-debug-your-code"></a>코드 실행 및 디버그

Visual Studio에서 프로젝트 또는 솔루션 없이 코드를 디버그할 수 있습니다. 일부 언어를 디버그하려면 스크립트, 실행 파일 또는 프로젝트와 같은 유효한 ‘시작 파일’을 코드베이스에서 지정해야 할 수 있습니다.  도구 모음의 **시작** 단추 옆에 있는 드롭다운 목록 상자에서는 Visual Studio에서 검색한 모든 시작 항목과 특별히 지정한 항목을 나열합니다. 코드를 디버그할 때는 먼저 이 코드를 Visual Studio에서 실행합니다.

Visual Studio에서 실행되도록 코드를 구성하는 것은 해당 코드의 종류 및 빌드 도구에 따라 달라집니다.

### <a name="codebases-that-use-msbuild"></a>MSBuild를 사용하는 코드베이스

MSBuild 기반 코드베이스에는 **시작** 단추의 드롭다운 목록에 나타나는 여러 빌드 구성이 포함될 수 있습니다. 시작 항목으로 사용할 파일을 선택한 다음, **시작** 단추를 선택하여 디버깅을 시작합니다.

> [!NOTE]
> C# 및 Visual Basic 코드베이스의 경우 **.NET 데스크톱 개발** 워크로드가 설치되어 있어야 합니다. C++ 코드베이스의 경우 **C++를 사용한 데스크톱 개발** 워크로드가 설치되어 있어야 합니다.

### <a name="codebases-that-use-custom-build-tools"></a>사용자 지정 빌드 도구를 사용하는 코드베이스

코드베이스에서 사용자 지정 빌드 도구를 사용하는 경우 *.json* 파일에 정의된 ‘빌드 작업’을 사용하여 코드 빌드 방법을 Visual Studio에 알려야 합니다. 자세한 내용은 [빌드 및 디버그 작업 사용자 지정](../ide/customize-build-and-debug-tasks-in-visual-studio.md)을 참조하세요.

### <a name="codebases-that-contain-python-or-javascript-code"></a>Python 또는 JavaScript 코드를 포함하는 코드베이스

코드베이스에 Python 또는 JavaScript 코드가 포함된 경우에는 *.json* 파일을 구성할 필요가 없지만 해당 워크로드를 설치해야 합니다. 시작 스크립트도 구성해야 합니다.

1. **도구** > **도구 및 기능 가져오기**를 선택하거나 Visual Studio를 닫고 Visual Studio 설치 관리자를 실행하는 방법으로 [Node.js 개발](https://visualstudio.microsoft.com/vs/node-js/) 또는 [Python 개발](https://visualstudio.microsoft.com/vs/python/) 워크로드를 설치합니다.

   ![Node.js 및 Python 개발 워크로드](media/python_nodejs_workloads.png)

1. **솔루션 탐색기**의 JavaScript 또는 Python 파일의 마우스 오른쪽 단추 메뉴나 상황에 맞는 메뉴에서 **시작 항목으로 설정** 명령을 선택합니다.

1. **시작** 단추를 선택하여 디버깅을 시작합니다.

### <a name="codebases-that-contain-c-code"></a>C++ 코드를 포함하는 코드베이스

Visual Studio에서 솔루션이나 프로젝트 없이 C++ 코드를 여는 방법에 대한 자세한 내용은 [C++의 폴더 열기 프로젝트](/cpp/build/open-folder-projects-cpp)를 참조하세요.

### <a name="codebases-that-contain-a-visual-studio-project"></a>Visual Studio 프로젝트를 포함하는 코드베이스

코드 폴더에 Visual Studio 프로젝트가 포함된 경우 프로젝트를 시작 항목으로 지정할 수 있습니다.

![프로젝트를 시작 항목으로 설정](media/customize-set-project-as-startup-item.png)

프로젝트가 시작 항목임을 반영하도록 **시작** 단추의 텍스트가 변경됩니다.

![시작 단추에 대한 프로젝트](media/customize-start-button-project.png)

## <a name="see-also"></a>참조

- [빌드 및 디버그 작업 사용자 지정](../ide/customize-build-and-debug-tasks-in-visual-studio.md)
- [C++의 폴더 열기 프로젝트](/cpp/build/open-folder-projects-cpp)
- [C++의 CMake 프로젝트](/cpp/build/cmake-projects-in-visual-studio)
- [코드 및 텍스트 편집기에서 코드 작성](../ide/writing-code-in-the-code-and-text-editor.md)
