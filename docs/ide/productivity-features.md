---
title: 생산성 가이드
description: 코드를 효율적으로 작성하고 디버깅하며 오류를 처리하는 데 도움이 되는 Visual Studio의 바로 가기 키 및 생산성 기능을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 4/29/2020
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bee392ddc4e7a0d185bdcc2d0e31dbd17832c733
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/25/2020
ms.locfileid: "95870874"
---
# <a name="productivity-guide-for-visual-studio"></a>Visual Studio 생산성 가이드

코드를 작성할 때 시간을 절약하려는 사용자에게 적합한 이 생산성 가이드에는 Visual Studio 시작, 코드 작성, 코드 디버그, 오류 처리, 바로 가기 키 사용에 도움이 되는 팁이 모두 한 페이지에 포함되어 있습니다.

유용한 바로 가기 키에 대한 자세한 내용은 [생산성 바로 가기](../ide/productivity-shortcuts.md)를 참조하세요. 명령 바로 가기의 전체 목록은 [기본 바로 가기 키](../ide/default-keyboard-shortcuts-in-visual-studio.md)를 참조하세요.

## <a name="get-started"></a>시작

명령, 설정, 설명서, 설치 옵션 등 필요한 항목을 빠르게 검색함으로써 메뉴를 찾아 헤매는 시간을 절약하세요. Visual Studio의 검색 결과 내에서 명령의 바로 가기 키를 확인하여 좀 더 쉽게 기억할 수 있습니다. 

- **작업 목록을 사용하여 모의 코드 생성**. 코드 조각을 완료하기 위한 요구 사항이 부족한 경우 작업 목록을 사용하여 `TODO` 및 `HACK` 같은 토큰 또는 사용자 지정 토큰을 사용하는 코드 주석을 추적하고 코드에서 미리 정의된 위치로 직접 연결되는 바로 가기를 관리합니다. 자세한 내용은 [작업 목록 사용](../ide/using-the-task-list.md)을 참조하세요.

- **솔루션 탐색기 바로 가기 사용**. Visual Studio를 처음 사용하는 경우 이러한 바로 가기가 유용하며 새 코드베이스에 익숙해지는 시간을 줄일 수 있습니다. 바로 가기의 전체 목록은 [Visual Studio의 기본 바로 가기 키](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solutionexplorerGLOBAL)를 참조하세요.

- **[Visual Studio에서 바로 가기 키 확인 및 사용자 지정](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)** . Visual Studio 명령에 대한 바로 가기 키를 확인하고, 해당 바로 가기 키를 사용자 지정하고, 다른 사용자가 사용하도록 내보낼 수 있습니다. 언제든지 옵션 대화 상자에서 바로 가기 키를 찾아 변경할 수 있습니다.

- **Visual Studio의 접근성 향상**. Visual Studio에는 화면 판독기 및 기타 보조 기술과 호환되는 내게 필요한 옵션 기능이 있습니다. 사용 가능한 기능의 전체 목록은 [Visual Studio의 접근성 팁과 요령](../ide/reference/accessibility-tips-and-tricks.md)을 참조하세요. 

- **Visual Studio 제품 수명 주기 및 서비스 확인**. Visual studio의 업데이트를 받는 방법, Enterprise 및 Professional 고객의 지원 옵션, 이전 버전 Visual Studio 지원 및 Visual Studio 서비스가 적용되지 않는 구성 요소에 대한 자세한 내용은 [Visual Studio 제품 수명 주기 및 서비스](/visualstudio/releases/2019/servicing)를 참조하세요. 

- **Visual Studio에서 NuGet 패키지 설치 및 관리**. Windows의 Visual Studio의 NuGet 패키지 관리자 UI를 사용하여 프로젝트 및 솔루션에서 NuGet 패키지를 쉽게 설치, 제거 및 업데이트할 수 있습니다. 자세한 내용은 [Visual Studio에서 NuGet 패키지 관리자를 사용하여 패키지 설치 및 관리](/nuget/consume-packages/install-use-packages-visual-studio)를 참조하세요.

## <a name="write-code"></a>코드 작성

다음 기능을 사용하여 더욱 신속하게 코드를 작성합니다.

- **유용한 명령을 사용** 합니다. Visual Studio에는 일반적인 편집 작업을 더 빠르게 수행하는 데 도움이 되는 다양한 명령이 있습니다. 예를 들어, 코드 줄을 복사하지 않고도 쉽게 복제하여 커서 위치를 변경한 다음, 붙여넣는 명령을 선택할 수 있습니다. **편집** > **복제** 를 선택하거나 **Ctrl**+**E**,**V** 를 누릅니다. **편집** > **고급** > **선택 영역 확장** 또는 **편집** > **고급** > **선택 영역 축소** 를 선택하거나 **Shift**+**Alt**+ **=** 또는 **Shift**+**Alt**+ **-** 를 눌러 텍스트 선택 영역을 빠르게 확장하거나 축소할 수도 있습니다.

- **IntelliSense 사용** 코드 편집기에 코드를 입력하면 멤버 목록, 매개 변수 정보, 요약 정보, 시그니처 도움말 및 단어 자동 완성과 같은 IntelliSense 정보가 나타납니다. 이러한 기능은 텍스트의 퍼지 일치를 지원합니다. 예를 들어 멤버 목록의 결과 목록에는 사용자가 입력한 문자로 시작하는 항목뿐만 아니라 이름에 문자 조합이 포함된 항목도 포함됩니다. 자세한 내용은 [IntelliSense 사용](../ide/using-intellisense.md)을 참조하세요.

- **코드를 입력할 때 IntelliSense 옵션의 자동 삽입 변경** IntelliSense를 제안 모드로 전환하여 명시적으로 선택할 경우에만 IntelliSense 옵션이 삽입되도록 지정할 수 있습니다.

     제안 모드를 사용하려면 **Ctrl**+**Alt**+**스페이스바** 를 선택하거나 메뉴 모음에서 **편집**,  > IntelliSense **,**  > **완료 모드 설정/해제** 를 선택합니다.

- **코드 조각 사용** 기본 제공된 코드 조각을 사용하거나 직접 코드 조각을 만들 수 있습니다.

     코드 조각을 삽입하려면 메뉴 모음에서 **편집** > **IntelliSense** > **코드 조각 삽입** 또는 **코드 감싸기** 를 선택하거나 파일의 바로 가기 메뉴를 열고 **코드 조각** > **코드 조각 삽입** 또는 **코드 감싸기** 를 선택합니다. 자세한 내용은 [코드 조각](../ide/code-snippets.md)을 참조하세요.

- **코드 오류를 인라인으로 수정** 빠른 작업을 사용하면 단일 작업으로 쉽게 코드를 리팩터링하거나, 생성하거나, 수정할 수 있습니다. 이 작업은 스크루드라이버![스크루드라이버 아이콘](media/screwdriver-icon.png) 또는 전구![전구 아이콘](media/light-bulb-icon.png) 아이콘을 사용하거나 커서가 적절한 코드 줄에 있을 때 **Alt**+**Enter** 또는 **Ctrl**+ **.** 를 눌러 적용할 수 있습니다. 자세한 내용은 [빠른 작업](quick-actions.md)을 참조하세요.

- **코드 요소의 정의 표시 및 편집** 멤버, 변수 또는 로컬 같은 코드 요소가 정의된 모듈을 신속하게 표시하고 편집할 수 있습니다.

    팝업 창에서 정의를 열려면 요소를 강조 표시하고 **Alt**+**F12** 를 선택하거나 요소의 바로 가기 메뉴를 열고 **정의 피킹(Peeking)** 을 선택합니다. 별도의 코드 창에서 정의를 열려면 해당 요소의 바로 가기 메뉴를 열고 **정의로 이동** 을 선택합니다.

- **샘플 애플리케이션 사용** [Microsoft Developer Network](https://code.msdn.microsoft.com/)에서 애플리케이션 예제를 다운로드 및 설치하여 애플리케이션 개발 시간을 단축할 수 있습니다. 해당 영역의 샘플 팩을 다운로드 및 탐색하여 특정한 기술이나 프로그래밍 개념을 익힐 수도 있습니다.

- **서식 지정/줄 추가를 사용하여 중괄호 서식 변경**. **서식 지정** 옵션 페이지를 사용하여 새 줄을 비롯해 코드 편집기의 코드를 서식 지정하기 위한 옵션을 설정합니다. C#에 이 설정을 사용하는 방법에 대한 자세한 내용은 [옵션 대화 상자: 텍스트 편집기 > C# > 코드 스타일 > 서식 지정](../ide/reference/options-text-editor-csharp-formatting.md)을 참조하세요. C++의 경우에는 [Visual Studio에서 C++ 코딩 기본 설정 지정](/cpp/ide/how-to-set-preferences)을 참조하세요. Python의 경우 [Python 코드 서식 지정](../python/formatting-python-code.md)을 참조하세요.

- **탭으로 들여쓰기 변경**. 각 코드베이스에 맞는 사용자 지정 편집기 설정을 사용하여 여러 편집기와 IDE에서 동일한 프로젝트를 작업하는 여러 개발자를 대상으로 일관된 코딩 스타일을 적용합니다. 전체 팀이 동일한 언어 규칙, 명명 규칙 및 서식 지정 규칙을 따르도록 합니다. 이러한 사용자 지정 설정은 이식 가능하고 코드와 함께 이동하므로 Visual Studio 외부에서도 코딩 스타일을 적용할 수 있습니다. 자세한 내용은 [옵션, 텍스트 편집기, 모든 언어, 탭](../ide/reference/options-text-editor-all-languages-tabs.md#tabs)을 참조하세요.

## <a name="navigate-within-your-code-and-the-ide"></a>코드와 IDE 내에서 탐색

다양한 기술을 사용하여 코드에서 특정 위치를 신속하게 찾고 이동할 수 있습니다. 기본 설정을 기준으로 Visual Studio 창의 레이아웃도 변경할 수 있습니다. 

- **코드 줄에 책갈피 지정** 책갈피를 사용하여 파일의 특정 코드 줄로 신속하게 이동할 수 있습니다.

    책갈피를 설정하려면 메뉴 모음에서 **편집** > **책갈피** > **책갈피 설정/해제** 를 선택합니다. **책갈피** 창에서 솔루션의 모든 책갈피를 볼 수 있습니다. 자세한 내용은 [코드에서 책갈피 설정](../ide/setting-bookmarks-in-code.md)을 참조하세요.

- **파일에서 기호 정의 검색** 솔루션 안에서 기호 정의와 파일 이름을 검색할 수 있지만 검색 결과에 네임스페이스나 지역 변수는 포함되지 않습니다.

   이 기능에 액세스하려면 메뉴 모음에서 **편집** > **탐색** 을 차례로 선택합니다.

- **코드의 전체 구조 찾아보기** **솔루션 탐색기** 에서 프로젝트의 클래스와 해당 형식 및 멤버를 검색하고 찾아볼 수 있습니다. 기호를 검색하고 메서드의 호출 계층 구조를 확인하며 기호 참조를 찾아 다른 작업을 수행할 수도 있습니다. **솔루션 탐색기** 에서 코드 요소를 선택할 경우 **미리 보기** 탭에 관련 파일이 열리고 커서가 파일의 요소로 이동합니다. 자세한 내용은 [코드 구조 보기](../ide/viewing-the-structure-of-code.md)를 참조하세요.

- **지도 모드를 사용하여 파일의 특정 위치로 이동**. 지도 모드에서는 스크롤 막대에 코드 줄이 작게 표시됩니다. 이 디스플레이 모드에 대한 자세한 내용은 [방법: 스크롤 막대 사용자 지정](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md#map-mode)을 참조하세요.

- **코드 맵을 사용하여 코드 구조 이해**. 코드 맵에서는 코드 전반의 종속성을 시각화할 수 있으므로 파일 및 코드 줄을 읽지 않고도 서로 어떻게 연결되는지 확인할 수 있습니다. 자세한 내용은 [코드 맵으로 종속성 매핑](../modeling/map-dependencies-across-your-solutions.md)을 참조하세요.

- **최근 파일 편집/최근 파일로 이동을 사용하여 자주 사용하는 파일 보기**. Visual Studio의 이동 명령으로 포커스가 있는 코드 검색을 수행하여 지정한 항목을 쉽게 찾을 수 있습니다. 자세한 내용은 [이동 명령을 사용하여 코드 찾기](../ide/go-to.md)를 참조하세요.

- **[속성 창](../ide/reference/properties-window.md)을 오른쪽으로 이동**. 보다 친숙한 창 레이아웃이 필요하면 **F4** 키를 눌러 Visual Studio에서 속성 창을 이동할 수 있습니다.

## <a name="find-items-faster"></a>항목 더 빨리 찾기

현재 작업에 대한 관련 정보만 표시하도록 도구 창의 내용을 필터링하는 것 외에 IDE에서 명령, 파일 및 옵션을 검색할 수 있습니다.

- **도구 창의 내용 필터링** **도구 상자**, **속성** 창 및 **솔루션 탐색기** 같은 여러 도구 창의 내용을 검색할 수 있지만 이름에 지정된 문자가 있는 항목만 표시할 수 있습니다.

- **해결하려는 오류만 표시** **오류 목록** 도구 모음에서 **필터** 단추를 선택하면 **오류 목록** 창에 나타나는 오류 수를 줄일 수 있습니다. 편집기에서 열려 있는 파일의 오류만, 현재 파일의 오류만 또는 현재 프로젝트의 오류만 표시할 수 있습니다. 특정 오류를 찾기 위해 **오류 목록** 창 내에서 검색할 수도 있습니다.

- **대화 상자, 메뉴 명령, 옵션 등을 찾습니다**. 검색 상자에 검색하려는 항목의 키워드나 문구를 입력합니다. 예를 들어 **새 프로젝트** 를 입력하면 다음 옵션이 나타납니다.

   ::: moniker range="vs-2017"

   !['새 프로젝트'의 빠른 실행 결과](../ide/media/productivity_quicklaunch.png)

   **빠른 실행** 에는 새 프로젝트 만들기, 프로젝트에 새 항목 추가, 특히 **옵션** 대화 상자의 **프로젝트 및 솔루션** 페이지에 대한 링크가 표시됩니다. 검색 결과에는 프로젝트 파일 및 도구 창이 포함될 수도 있습니다.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![‘새 프로젝트’에 대한 검색 결과](../ide/media/vs-2019/productivity-quick-launch-new-project.png)

   ::: moniker-end

   **Ctrl**+**Q** 를 눌러 검색 상자로 바로 이동할 수 있습니다.

## <a name="debug-code"></a>코드 디버그

디버깅은 시간이 오래 걸릴 수 있지만 다음 팁을 참고하여 처리 시간을 줄일 수 있습니다.

- **Visual Studio 디버거 도구 사용**. Visual Studio 컨텍스트에서 ‘앱을 디버그’하는 경우는 일반적으로 디버거 모드에서 애플리케이션이 실행되고 있음을 의미합니다. 디버거는 실행되는 동안 코드에서 수행하는 작업을 확인할 수 있는 여러 가지 방법을 제공합니다. 시작하기 위한 가이드가 필요하면 [먼저 Visual Studio 디버거 살펴보기](../debugger/debugger-feature-tour.md)를 참조하세요. 

- **여러 브라우저에서 같은 페이지, 애플리케이션 또는 사이트 테스트** 코드를 디버그할 때 **브라우저 선택** 대화 상자를 열지 않고도 [페이지 검사기(Visual Studio)](/previous-versions/hh974728(v=vs.140)) 등의 설치된 웹 브라우저 간에 쉽게 전환할 수 있습니다. **디버깅 시작** 단추 옆에 있는 **표준** 도구 모음에서 **디버그 대상** 목록을 사용하여 디버그 또는 보기 페이지로 사용 중인 브라우저를 빠르게 확인할 수 있습니다.

    ![웹 브라우저 디버그 옵션 선택](../ide/media/webbrowserdropdowntoolbar.png)

- **임시 중단점 설정** 코드의 현재 줄에 임시 중단점을 만들고 디버거를 동시에 시작할 수 있습니다. 해당 코드 줄에 도달하면 디버거 중단 모드가 시작됩니다. 자세한 내용은 [디버거로 코드 탐색](../debugger/navigating-through-code-with-the-debugger.md)을 참조하세요.

    이 기능을 사용하려면 **Ctrl**+**F10** 키를 선택하거나 중단할 코드 줄의 바로 가기 메뉴를 열고 **커서까지 실행** 을 선택합니다.

- **디버그하는 동안 실행 지점 이동** 현재 실행 지점을 코드의 다른 섹션으로 이동하고 해당 지점에서 디버깅을 다시 시작할 수 있습니다. 이 기술은 해당 섹션에 도달하는 데 필요한 모든 단계를 다시 만들 필요 없이 코드 섹션을 디버깅하려는 경우 유용합니다. 자세한 내용은 [디버거로 코드 탐색](../debugger/navigating-through-code-with-the-debugger.md)을 참조하세요.

     실행 지점을 이동하려면 노란색 화살표를 같은 소스 파일에서 다음 명령문을 설정할 위치로 끌어온 다음 **F5** 키를 선택하여 디버깅을 계속합니다.

- **변수에 대한 정보 캡처** 디버깅이 완료된 후 변수에 대해 마지막으로 알려진 값에 액세스할 수 있도록 DataTip을 노드에 있는 변수에 추가하고 고정할 수 있습니다. 자세한 내용은 [데이터 팁의 데이터 값 보기](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)를 참조하세요.

     DataTip을 추가하려면 디버거가 중단 모드여야 합니다. 커서를 변수에 놓고 나타나는 DataTip에서 핀 단추를 선택합니다. 디버깅이 중지되면 소스 파일에서 변수가 들어 있는 코드 줄 옆에 파란색 핀 아이콘이 나타납니다. 파란색 핀을 가리키면 최근 디버깅 세션의 변수 값이 나타납니다.

- **직접 실행 창 지우기** 디자인 타임에 `>cls` 또는 `>Edit.ClearAll`를 입력하여 [직접 실행 창](../ide/reference/immediate-window.md)의 내용을 지울 수 있습니다.

     추가 명령에 대한 자세한 내용은 [Visual Studio 명령 별칭](../ide/reference/visual-studio-command-aliases.md)을 참조하세요.

- **[CodeLens에서 코드 변경 내용 및 기타 기록 찾기](../ide/find-code-changes-and-other-history-with-codelens.md)** . CodeLens를 통해 코드에 대한 정보를 찾는 동안 편집기에서 나가지 않고&mdash;계속 작업에 집중할 수 있습니다. 코드 조각 참조, 코드 변경 내용, 연결된 버그, 작업 항목, 코드 검토 및 단위 테스트를 확인할 수 있습니다.

- **Live Share를 사용하여 다른 사용자와 실시간으로 디버그**. Live Share를 사용하면 사용 중인 프로그래밍 언어나 빌드 중인 앱 유형과 관계없이 다른 사람과 공동으로 실시간 편집 및 디버깅이 가능합니다. 자세한 내용은 [Visual Studio Live Share란?](/visualstudio/liveshare/)을 참조하세요.

- **대화형 창을 사용하여 작은 코드 작성 및 테스트**. Visual Studio에서는 임의의 코드를 입력하고 즉각 결과를 볼 수 있는 대화형 REPL(read–eval–print loop) 창을 제공합니다. 이러한 방식의 코딩은 API 및 라이브러리와 관련된 내용을 배우고 실험하는 데 도움이 되고, 프로젝트에 포함할 작업 코드를 대화형으로 개발하는 데에도 유용합니다. Python의 경우 [Python 대화형 창 작업](../python/python-interactive-repl-in-visual-studio.md)을 참조하세요. C#에서도 대화형 창 기능을 사용할 수 있습니다. 

## <a name="access-visual-studio-tools"></a>Visual Studio 도구에 액세스

개발자 명령 프롬프트 또는 다른 Visual Studio 도구를 시작 화면이나 작업 표시줄에 고정하여 더욱 신속하게 액세스할 수 있습니다.

::: moniker range="vs-2017"

1. Windows 탐색기에서 *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools* 로 이동합니다.

::: moniker-end

::: moniker range=">=vs-2019"

1. Windows 탐색기에서 *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools* 로 이동합니다.

::: moniker-end

2. **개발자 명령 프롬프트** 를 마우스 오른쪽 단추로 클릭하거나 상황에 맞는 메뉴를 열고 **시작 화면에 고정** 또는 **작업 표시줄에 고정** 을 선택합니다.

## <a name="manage-files-toolbars-and-windows"></a>파일, 도구 모음 및 창 관리

애플리케이션을 개발할 때 여러 코드 파일로 작업하면서 여러 도구 창 사이를 이동하는 경우가 있습니다. 다음 팁을 사용하여 체계적으로 관리할 수 있습니다.

- **자주 사용하는 파일을 편집기에 계속 표시** 편집기에 열린 파일 수와 관계없이 파일을 탭 왼쪽에 고정하여 계속 표시할 수 있습니다.

   파일을 고정하려면 해당 파일의 탭을 선택하고 **고정 상태 설정/해제** 단추를 선택합니다.

- **문서 및 창을 다른 모니터로 이동** 애플리케이션을 개발할 때 모니터를 2개 이상 사용하는 경우 편집기에서 연 파일을 다른 모니터로 이동하면 애플리케이션 부분별로 쉽게 작업할 수 있습니다. 디버거 창 같은 도구 창을 다른 모니터로 이동하고 도킹 문서와 도구 창을 함께 탭하여 “래프트”를 만들 수도 있습니다. 자세한 내용은 [Visual Studio에서 창 레이아웃 사용자 지정](../ide/customizing-window-layouts-in-visual-studio.md)을 참조하세요.

   **솔루션 탐색기** 의 다른 인스턴스를 만들고 다른 모니터로 이동하여 파일을 더욱 쉽게 관리할 수도 있습니다. **솔루션 탐색기** 의 다른 인스턴스를 만들려면 **솔루션 탐색기** 에서 바로 가기 메뉴를 열고 **새 솔루션 탐색기 뷰** 를 선택합니다.

- **Visual Studio에 표시되는 글꼴 사용자 지정** IDE에서 텍스트에 사용되는 글꼴, 글꼴 크기 및 글꼴 색을 변경할 수 있습니다. 예를 들어, 편집기의 특정 코드 요소의 색과 도구 창 또는 IDE 전체에서 글꼴을 사용자 지정할 수 있습니다. 자세한 내용은 [방법: 글꼴 및 색 변경](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) 및 [방법: 편집기의 글꼴 및 색 변경](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)을 참조하세요.

## <a name="see-also"></a>참조

- [Visual Studio 팁과 요령 블로그 게시물](https://devblogs.microsoft.com/visualstudio/visual-studio-tips-and-tricks/)
- [자주 사용되는 명령의 기본 바로 가기 키](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)
- [방법: 메뉴 및 도구 모음 사용자 지정](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
- [연습: 간단한 애플리케이션 만들기](../get-started/csharp/tutorial-wpf.md)
- [접근성 팁과 요령](../ide/reference/accessibility-tips-and-tricks.md)