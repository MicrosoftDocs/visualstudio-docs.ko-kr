---
title: C++ 시작
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 99c73344-86ba-4b08-9e15-f6111cc04185
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 001b394d86e56b172bb1a50c335bd8ba5bcacb15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645624"
---
# <a name="getting-started-with-c-in-visual-studio"></a>Visual Studio에서 C++ 시작
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습을 완료하면 Visual Studio를 사용하여 애플리케이션을 개발할 때 사용할 수 있는 여러 도구 및 대화 상자에 익숙해집니다. 간단한 "Hello, World" 스타일 애플리케이션을 만들면서 IDE(통합 개발 환경)에서 작업하는 방법을 배워 보겠습니다.

 이 항목에는 다음과 같은 섹션이 포함되어 있습니다.

 [Visual Studio에 로그인](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_Configure)

 [간단한 응용 프로그램 만들기](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_CreateApp)

 [응용 프로그램에 코드 추가](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_AddCode)

 [응용 프로그램 디버그 및 테스트](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_DebugTest)

 [앱 릴리스 버전 빌드](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_BuildRelease)

## <a name="sign-in-to-visual-studio"></a><a name="BKMK_Configure"></a> Visual Studio에 로그인
 Visual Studio를 처음 시작하는 경우 Live 또는 Outlook 같은 Microsoft 계정을 사용하여 로그인할 수 있는 옵션이 제공됩니다. 로그인하면 모든 디바이스 간에 설정을 동기화할 수 있습니다. 자세한 내용은 [Signing in to Visual Studio](../ide/signing-in-to-visual-studio.md)을 참조하세요.

 그림 1: Visual Studio IDE

 ![Visual C&#43;&#43; 설정이 적용된 IDE](../ide/media/c-ide-defaultenvironmentlayout.png "C + + IDE_DefaultEnvironmentLayout")

 Visual Studio를 열면 IDE의 세 가지 기본 부분인 도구 창, 메뉴 및 도구 모음, 주 창 공간을 확인할 수 있습니다. **빠른 실행**, 메뉴 모음 및 상단의 표준 도구 모음이 포함된 도구 창은 앱 창 왼쪽과 오른쪽에 도킹되어 있습니다. 애플리케이션 창의 가운데에는 **시작 페이지**가 있습니다. 솔루션 또는 프로젝트를 열면 편집기와 디자이너가 이 공간에 나타납니다. 애플리케이션을 개발할 때 이 중앙 영역에서 대부분의 시간을 보냅니다.

## <a name="create-a-simple-application"></a><a name="BKMK_CreateApp"></a> 간단한 응용 프로그램 만들기
 Visual Studio에서 앱을 만들 때 먼저 프로젝트와 솔루션을 만들어야 합니다. 이 예제에서는 Windows 콘솔 애플리케이션을 만듭니다.

#### <a name="to-create-a-console-app"></a>콘솔 앱을 만들려면

1. 메뉴 모음에서 **파일**, **새로 만들기**, **프로젝트**를 차례로 선택합니다.

    ![메뉴 모음에서 [파일], [새로 만들기], [프로젝트]를 선택합니다.](../ide/media/exploreide-filenewproject.png "Exploreide-newprojectcsharp-FileNewProject")

2. **Visual C++** 범주에서 **Win32 콘솔 애플리케이션** 템플릿을 선택한 후 프로젝트 이름을 `GreetingsConsoleApp`으로 지정합니다.

    ![Win32 콘솔 애플리케이션 템플릿](../ide/media/c-ide-newprojectdlg.png "C + + IDE_NewProjectDlg")

3. Win32 애플리케이션 마법사가 나타나면 **마침** 단추를 선택합니다.

    ![Win32 콘솔 애플리케이션 마법사](../ide/media/c-ide-win32consoleappwizard.png "C + + IDE_Win32ConsoleAppWizard")

   Win32 콘솔 앱용 기본 파일과 함께 GreetingsConsoleApp 프로젝트 및 솔루션이 생성된 후 **솔루션 탐색기**에 자동으로 로드됩니다. GreetingsConsoleApp.cpp 파일이 코드 편집기에서 열립니다. 다음 항목이 **솔루션 탐색기**에 나타납니다.

   그림 4: 프로젝트 항목

   ![솔루션 탐색기의 솔루션 파일](../ide/media/c-ide-solutioncontents.png "C + + IDE_SolutionContents")

## <a name="add-code-to-the-application"></a><a name="BKMK_AddCode"></a> 애플리케이션에 코드 추가
 다음으로 콘솔 창에 "Hello"를 표시하는 코드를 추가합니다.

#### <a name="to-display-hello-in-the-console-window"></a>콘솔 창에 "Hello"를 표시하려면

1. GreetingsConsoleApp.cpp 파일에서 `return 0;` 줄 앞에 빈 줄을 입력하고 다음 코드를 입력합니다.

    ```
    cout << "Hello\n";
    ```

     `cout`아래에 빨간색 물결선이 나타납니다. 이 물결선을 가리키면 오류 메시지가 표시됩니다.

     ![cout에 대한 오류 텍스트](../ide/media/c-ide-couterror.png "C + + IDE_CoutError")

     이 오류 메시지는 **오류 목록** 창에도 나타납니다. 메뉴 모음에서 **보기**, **오류 목록**을 선택하여 이 창을 표시할 수 있습니다.

     [cout](https://msdn.microsoft.com/library/d87db6c3-e4e1-4d09-9ec5-458f55018257) 은 헤더 파일에 포함 되어 \<iostream\> 있습니다.

2. Iostream 헤더를 포함하려면 `#include "stdafx.h"`뒤에 다음 코드를 입력합니다.

    ```
    #include \<iostream\>
    using namespace std;
    ```

     코드를 입력하면 입력한 문자에 대한 추천 단어를 표시하는 상자가 나타나는 것을 확인할 수 있습니다. 이 상자는 C++ IntelliSense의 일부로, 클래스 또는 인터페이스 멤버 및 매개 변수 정보의 나열을 비롯한 코딩 프롬프트를 제공합니다. 또한 미리 정의된 코드 블록인 코드 조각을 사용할 수도 있습니다. 자세한 내용은 IntelliSense 및 [코드 조각](../ide/code-snippets.md) [사용](../ide/using-intellisense.md) 을 참조 하세요.

     `cout` 아래의 빨간색 물결선은 오류를 해결하면 사라집니다.

3. 변경 내용을 파일에 저장합니다.

     ![cout 오류 수정 코드](../ide/media/c-ide-coutfix.png "C + + IDE_CoutFix")

## <a name="debug-and-test-the-application"></a><a name="BKMK_DebugTest"></a> 응용 프로그램 디버그 및 테스트
 GreetingsConsoleApp을 디버그하여 단어 "Hello"가 콘솔 창에 표시되는지 여부를 확인할 수 있습니다.

#### <a name="to-debug-the-application"></a>애플리케이션을 디버그하려면

- 디버거를 시작합니다.

     ![디버그 메뉴의 디버깅 시작 명령](../ide/media/exploreide-startdebugging.png "Exploreide-newprojectcsharp-StartDebugging")

     디버거가 시작되고 코드가 실행됩니다. 콘솔 창(명령 프롬프트외 비슷한 별도의 창)이 몇 초간 나타나지만 디버거에서 실행이 중지되면 바로 닫힙니다. 텍스트를 보려면 중단점을 설정하여 프로그램 실행을 중지해야 합니다.

#### <a name="to-add-a-breakpoint"></a>중단점을 추가하려면

1. 메뉴 모음에서 `return 0;`줄에 중단점을 추가합니다. 왼쪽 여백을 클릭하여 중단점을 설정할 수도 있습니다.

    ![디버그 메뉴의 중단점 설정/해제 명령](../ide/media/exploreide-togglebreakpoint.png "Exploreide-newprojectcsharp-ToggleBreakpoint")

    편집기 창의 맨 왼쪽 여백 코드 줄 옆에 빨간색 원이 나타납니다.

2. F5 키를 선택하여 디버깅을 시작합니다.

    디버거가 시작되고 단어 **Hello**를 표시하는 콘솔 창이 나타납니다.

    ![Windows 명령 프롬프트 창의 Hello 텍스트](../ide/media/c-ide-hellocommandwindow.png "C + + IDE_HelloCommandWindow")

3. Shift+F5를 눌러 디버깅을 중지합니다.

   자세한 내용은 [콘솔 프로젝트](../debugger/debugging-preparation-console-projects.md)를 참조하세요.

## <a name="build-a-release-version-of-the-app"></a><a name="BKMK_BuildRelease"></a> 앱 릴리스 버전 빌드
 모든 것이 작동하는 것을 확인했으므로 애플리케이션의 릴리스 빌드를 준비할 수 있습니다.

#### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>솔루션 파일을 정리하고 릴리스 버전을 빌드하려면

1. 메뉴 모음에서 이전 빌드 중에 생성된 중간 파일 및 출력 파일을 삭제합니다.

    ![빌드 메뉴의 솔루션 정리 명령](../ide/media/exploreide-cleansolution.png "Exploreide-newprojectcsharp 솔루션")

2. GreetingsConsoleApp의 빌드 구성을 **디버그** 에서 **릴리스**로 변경합니다.

    ![애플리케이션 릴리스 버전 빌드](../ide/media/c-ide-changingbuildtorelease.png "C + + IDE_ChangingBuildtoRelease")

3. 솔루션을 빌드합니다.

    ![빌드 메뉴의 솔루션 빌드 명령](../ide/media/exploreide-buildsolution.png "Exploreide-newprojectcsharp-BuildSolution")

   이 연습을 완료한 것을 축하 드립니다! 더 많은 예제를 탐색 하려는 경우 [Visual Studio 샘플](../ide/visual-studio-samples.md)을 참조 하세요.

## <a name="see-also"></a>관련 항목
 [연습: 간단한 애플리케이션 만들기](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md) [생산성 팁](../ide/productivity-tips-for-visual-studio.md) [Visual Studio 샘플](../ide/visual-studio-samples.md) [Visual Studio를 사용한 개발 시작](../ide/get-started-developing-with-visual-studio.md)
