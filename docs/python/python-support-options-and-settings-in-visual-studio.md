---
title: Python에서 옵션 및 설정
description: Python 코드 및 프로젝트와 관련된 Visual Studio의 다양한 설정에 대한 참조입니다.
ms.date: 03/13/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Python_Tools
- VS.ToolsOptionsPages.Python_Tools.General
- VS.ToolsOptionsPages.Python_Tools.Debugging
- VS.ToolsOptionsPages.Python_Tools.Diagnostics
- VS.ToolsOptionsPages.Python_Tools.Experimental
- VS.ToolsOptionsPages.Python_Tools.Interactive_Windows
- VS.ToolsOptionsPages.Text_Editor.Python.Advanced
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 08501d71400a0df139022f04e68573d0dd1449d1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79307102"
---
# <a name="options-for-python-in-visual-studio"></a>Visual Studio의 Python 옵션

Python 옵션을 보려면 **도구** > **옵션** 메뉴 명령을 사용하고 **모든 설정 표시**가 선택되었는지 확인한 다음, **Python**으로 이동합니다.

::: moniker range="vs-2017"
![Python 옵션 대화 상자, 일반 탭](media/options-general.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python 옵션 대화 상자, 일반 탭](media/options-general-2019.png)
::: moniker-end

**텍스트 편집기** > **Python** > **고급** 탭과 **환경** > **글꼴 및 색** 탭의 **텍스트 편집기** 그룹 내에 추가 Python 관련 옵션이 있습니다.

> [!Note]
> **실험적** 그룹은 아직 개발 중인 기능에 대한 옵션을 포함하며 여기서는 설명하지 않습니다. 종종 [Microsoft 블로그의 Python 엔지니어링](https://devblogs.microsoft.com/python/)의 포스트에 논의됩니다.

## <a name="general-options"></a>일반 옵션

(**도구** > **옵션** > **Python** 탭)

| 옵션 | 기본값 | 설명 |
| --- | --- | --- |
| **가상 환경을 만들 때 출력 창 표시**| 켜기 | **출력** 창이 표시되지 않도록 하려면 선택 취소합니다. |
| **패키지를 설치하거나 제거할 때 출력 창 표시** | 켜기 | **출력** 창이 표시되지 않도록 하려면 선택 취소합니다. |
| **환경 만들기에 대한 알림 표시줄 표시** | 켜기 | ‘Visual Studio 2019만’ 해당합니다.  이 옵션이 설정되어 있는 경우 사용자가 *requirements.txt* 또는 *environment.yml* 파일이 포함된 프로젝트를 열면 Visual Studio는 기본 전역 환경을 사용하지 않고 가상 환경 또는 Conda 환경을 만들기 위한 각각의 제안이 포함되어 있는 알림 표시줄을 보여 줍니다. |
| **패키지 설치에 대한 알림 표시줄 표시** | 켜기 | ‘Visual Studio 2019만’ 해당합니다.  이 옵션이 설정되어 있는 경우 사용자가 *requirements.txt* 파일이 포함된 프로젝트를 열면(기본 전역 환경을 사용하지 않음), Visual Studio가 해당 요구 사항을 현재 환경에 설치된 패키지와 비교합니다. 패키지가 누락된 경우에는 Visual Studio에서 해당 종속성을 설치하라는 메시지를 표시합니다. |
| **항상 관리자로 패키지 관리자 실행** | 끄기 | 항상 모든 환경에서 `pip install` 및 유사한 패키지 관리자 작업 권한을 상승합니다. 패키지를 설치할 때 환경이 *c:\Program Files*와 같은 파일 시스템의 보호된 영역에 있을 경우 Visual Studio에서 관리자 권한을 확인하는 메시지를 표시합니다. 해당 메시지에서 하나의 환경에 대해서만 항상 설치 명령 권한을 상승하도록 선택할 수 있습니다. [패키지 탭](python-environments-window-tab-reference.md#packages-tab)을 참조하세요. |
| **처음 사용할 때 완성 DB 자동 생성** | 켜기 | Visual Studio 2017 버전 15.5 및 이전 버전과 IntelliSense 데이터베이스를 사용하는 경우 이후 버전에 적용됩니다.  데이터베이스를 사용하는 코드를 작성할 때 라이브러리에 대한 데이터베이스 완성에 우선 순위를 지정합니다. 자세한 내용은 [IntelliSense 탭](python-environments-window-tab-reference.md?view=vs-2017#intellisense-tab)을 참조하세요. |
| **시스템 전체 PYTHONPATH 변수 무시** | 켜기 | Visual Studio에서 환경 및 프로젝트에 검색 경로를 지정하는 보다 직접적인 수단을 제공하기 때문에 PYTHONPATH는 기본적으로 무시됩니다. 자세한 내용은 [검색 경로](search-paths.md)를 참조하세요. |
| **연결된 파일을 추가할 때 검색 경로 업데이트** | 켜기 | 설정된 경우 [연결된 파일](managing-python-projects-in-visual-studio.md#linked-files)을 프로젝트에 추가하면 IntelliSense가 연결된 파일의 폴더 내용을 완성 데이터베이스에 포함할 수 있도록 [검색 경로](search-paths.md)가 업데이트됩니다. 이러한 내용을 완성 데이터베이스에서 제외하려면 이 옵션의 선택을 취소합니다. |
| **가져온 모듈을 찾을 수 없으면 경고 표시** | 켜기 | 가져온 모듈을 현재 사용할 수 없지만 달리 코드 작업에 영향을 주지 않음을 알고 있는 경우 경고를 무시하려면 이 옵션의 선택을 취소합니다. |
| **일치하지 않는 들여쓰기를 보고할 형식** | **경고** | Python 인터프리터는 적절한 들여쓰기를 사용하여 범위를 확인하기 때문에 Visual Studio는 기본적으로, 코딩 오류를 나타낼 수 있는 일관성 없는 들여쓰기가 검색될 경우 경고를 실행합니다. **오류**로 설정하면 훨씬 더 엄격하게 적용되어, 프로그램이 종료됩니다. 이 동작을 사용하지 않으려면 **사용 안 함**을 선택합니다. |
| **설문 조사/뉴스 확인** | **한 주에 한 번** | ‘Visual Studio 2017 및 이전 버전’에 제공됩니다.  Visual Studio에서 사용 가능한 경우 Python 관련 설문 조사 및 뉴스 항목이 표시된 웹 페이지를 포함하는 창을 열 수 있는 빈도를 설정합니다. 옵션은 **안 함**, **하루에 한 번**, **한 주에 한 번**, **한 달에 한 번**입니다. |
| **영구적으로 숨겨진 모든 대화 상자 다시 설정** 단추 | N/A | 여러 대화 상자에서 **이 대화 상자를 다시 표시 안 함** 등의 옵션을 제공합니다. 이러한 옵션의 선택을 취소하고 대화 상자를 다시 표시하려면 이 단추를 사용합니다. |

::: moniker range="vs-2017"
![Python 옵션 대화 상자, 일반 탭](media/options-general.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python 옵션 대화 상자, 일반 탭](media/options-general-2019.png)
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="conda-options"></a>Conda 옵션

(**도구** > **옵션** > **Python** > **Conda** 탭)

| 옵션 | 기본값 | 설명 |
| --- | --- | --- |
| **Conda 실행 파일 경로** | (비어 있음) | Python 워크로드에 포함된 기본 Miniconda 설치를 사용하지 않고 *conda.exe* 실행 파일에 대한 정확한 경로를 지정합니다. 여기에 다른 경로가 지정되면 기본 설치 및 레지스트리에 지정된 기타 모든 conda.exe 실행 파일보다 이 경로가 먼저 적용됩니다. 최신 버전의 Anaconda 또는 Miniconda를 수동으로 설치하거나 기본 64비트 배포판이 아닌 32비트 배포판을 사용하려는 경우 이 설정을 변경할 수 있습니다. |

![Python 옵션 대화 상자, 언어 서버 탭](media/options-conda.png)

::: moniker-end

## <a name="debugging-options"></a>디버깅 옵션

(**도구** > **옵션** > **Python** > **디버깅** 탭)

| 옵션 | 기본값 | 설명 |
| --- | --- | --- |
| **오류가 있으면 실행 전에 묻기** | 켜기 | 설정하면 오류가 포함된 코드를 실행할 것인지 확인하는 메시지가 표시됩니다. 경고를 사용하지 않으려면 이 옵션의 선택을 취소합니다. |
| **프로세스가 비정상적으로 종료되면 입력 대기**<br/><br/>**프로세스가 정상적으로 종료되면 입력 대기** | 켜짐(모두) | Visual Studio에서 시작된 Python 프로그램은 자체 콘솔 창에서 실행됩니다. 기본적으로 프로그램 종료 방법과 관계없이 창을 닫기 전에 사용자가 키를 누를 때까지 대기합니다. 프롬프트를 제거하고 창을 자동으로 닫으려면 이러한 옵션 중 하나 또는 둘 다의 선택을 취소합니다. |
| **디버그 출력 창에 Tee 프로그램 출력** | 켜기 | 별도 콘솔 창과 Visual Studio **출력** 창에 프로그램 출력을 표시합니다. 별도 콘솔 창에만 출력을 표시하려면 이 옵션의 선택을 취소합니다. |
| **SystemExit 예외에서 중단하고 종료 코드로 0 출력** | 끄기 | 설정하면 이 예외에서 디버거를 중지합니다. 선택 취소하면 디버거가 중단되지 않고 종료됩니다. |
| **Python 표준 라이브러리 디버깅 사용** | 끄기 | 디버깅하는 동안 표준 라이브러리 소스 코드를 한 단계씩 실행할 수 있지만 디버거를 시작하는 데 걸리는 시간이 증가합니다.|
| **함수 반환 값 표시** | 켜기 | ‘Visual Studio 2019만’ 해당합니다.  **지역** 창에 함수 반환 값을 표시한 후 디버거(F10)의 함수 호출을 건너뜁니다. |
| **레거시 디버거 사용** | 끄기 | ‘Visual Studio 2019만’ 해당합니다.  Visual Studio에서 기본적으로 레거시 디버거를 사용하도록 지시합니다. 자세한 내용은 [디버깅 - 레거시 디버거 사용](debugging-python-in-visual-studio.md#use-the-legacy-debugger)을 참조하세요. |

::: moniker range="vs-2017"
![Python 옵션 대화 상자, 디버깅 탭](media/options-debugging.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python 옵션 대화 상자, 디버깅 탭](media/options-debugging-2019.png)
::: moniker-end

## <a name="diagnostics-options"></a>진단 옵션

(**도구** > **옵션** > **Python** > **진단** 탭)

| 옵션 | 기본값 | 설명 |
| --- | --- | --- |
| **분석 로그 포함** | 켜기 | 진단을 파일에 저장하거나 단추를 사용하여 클립보드에 복사할 경우 설치된 Python 환경의 분석과 관련된 세부 로그를 포함합니다. 이 옵션으로 생성된 파일의 크기가 늘어나고 IntelliSense 문제를 자주 진단해야 합니다. |
| **파일에 진단 저장** 단추 | N/A | 파일 이름을 묻는 메시지를 표시한 다음 텍스트 파일에 로그를 저장합니다. |
| **클립보드에 진단 복사** 단추 | N/A | 로그 전체를 클립보드에 넣습니다. 이 작업은 로그 크기에 따라 시간이 걸릴 수 있습니다. |

![Python 옵션 대화 상자, 진단 탭](media/options-diagnostics.png)

## <a name="interactive-windows-options"></a>대화형 Windows 옵션

(**도구** > **옵션** > **Python** > **대화형 창** 탭)

| 옵션 | 기본값 | 설명 |
| --- | --- | --- |
| **스크립트** | N/A | 모든 환경에 대한 **대화형** 창에 적용할 시작 스크립트에 대한 일반 폴더를 지정합니다. [시작 스크립트](python-environments-window-tab-reference.md#startup-scripts)를 참조하세요. 그러나 이 기능은 현재 작동하지 않습니다. |
| **위쪽/아래쪽 화살표로 기록 탐색** | 켜기 | 화살표 키를 사용하여 **대화형** 창의 기록을 탐색합니다. 화살표 키를 사용하여 **대화형** 창의 출력 내에서 탐색하려면 이 설정의 선택을 취소합니다. |
| **완료 모드** | **함수 호출이 없는 식만 평가** | **대화형** 창에서 식에 사용 가능한 멤버를 확인하는 프로세스를 수행하려면 현재 완료되지 않은 식을 평가해야 할 수 있으며, 이로 인해 부작용이 발생하거나 함수가 여러 번 호출될 수 있습니다. 기본 설정인 **함수 호출이 없는 식만 평가**는 함수를 호출하는 것으로 보이는 식을 제외하지만 다른 식은 평가합니다. 예를 들어 `a.b`는 평가하지만 `a().b`는 평가하지 않습니다.  **식 평가 안 함**은 일반적인 IntelliSense 엔진만 제안에 사용하여 모든 부작용을 방지합니다. **모든 식 평가**는 부작용과 관계없이 전체 식을 평가하여 제안을 가져옵니다. |
| **정적 분석 제안 숨기기** | 끄기 | 설정하면 식을 평가하여 얻은 제안만 표시합니다. **완료 모드** 값 **식 평가 안 함**과 함께 사용할 경우 **대화형** 창에 유용한 완료가 나타나지 않습니다. |

![Python 옵션 대화 상자, 대화형 창 탭](media/options-interactive-windows.png)

::: moniker range=">=vs-2019"
## <a name="language-server-options"></a>언어 서버 옵션

(**도구** > **옵션** > **Python** > **언어 서버** 탭)

| 옵션 | 기본값 | 설명 |
| --- | --- | --- |
| **Typeshed의 완성 사용 안 함** | 끄기 | Visual Studio IntelliSense는 일반적으로 번들 버전의 Typeshed( *.pyi* 파일 집합)를 사용하여 Python 2 및 Python 3 둘 다에 대해 표준 라이브러리 및 타사 라이브러리의 형식 힌트를 찾습니다. 이 옵션을 설정하면 번들 TypeShed 동작을 사용하지 않도록 설정합니다. |
| **사용자 지정 Typeshed 경로** | (비어 있음) | 이 옵션을 설정하면 Visual Studio가 이 경로에서는 해당 번들 버전이 아닌 Typeshed 파일을 사용합니다. **Typeshed의 완성 사용 안 함**이 설정된 경우에는 무시합니다. |

![Python 옵션 대화 상자, 언어 서버 탭](media/options-language-server.png)

::: moniker-end

## <a name="advanced-python-editor-options"></a>고급 Python 편집기 옵션

(**도구** > **옵션** > **텍스트 편집기** > **Python** > **고급** 탭)

### <a name="completion-results"></a>완료 결과

| 옵션 | 기본값 | 설명 |
| --- | --- | --- |
| **멤버 완료 시 멤버 교집합 표시** | 끄기 | 설정하면 가능한 모든 형식에서 지원되는 완료만 표시됩니다. |
| **검색 문자열에 따라 목록 필터링** | 켜기 | 입력할 때 완료 제안 필터링을 적용합니다(기본값이 선택됨). |
| **모든 식별자에 대해 완료 자동 표시** | 켜기 | 편집기와 **대화형** 창 둘 다에서 완료를 사용하지 않으려면 이 옵션의 선택을 취소합니다. |

### <a name="selection-in-completion-list"></a>완성 목록의 선택

| 옵션 | 기본값 | 설명 |
| --- | --- | --- |
| **다음 문자를 입력하면 커밋됨** | **{}\[\]().,:;+-*/%&&#124;^~=<>#@\\** | 일반적으로 이러한 문자는 완성 목록에서 선택할 수 있는 식별자 다음에 오므로 문자를 입력해서 완료를 커밋하는 것이 편리합니다. 필요에 따라 목록에 특정 문자를 추가하거나 제거할 수 있습니다.  |
| **Enter 키를 눌러 현재 완료 커밋** | 켜기 | 설정하면 **Enter** 키를 누를 때 위의 문자와 마찬가지로 현재 선택한 완료가 선택 및 적용됩니다. 물론, **Enter** 키에 대한 문자는 없으므로 해당 목록에 직접 포함할 수는 없습니다. |
| **단어를 모두 입력한 후 Enter 키를 누르면 새 줄 추가** | 끄기 | 기본적으로 완성 팝업에 표시되는 전체 단어를 입력하고 **Enter** 키를 누르면 해당 완료가 커밋됩니다. 이 옵션을 설정하면 식별자 입력을 마칠 때 실제로 완료가 커밋되고 **Enter** 키를 누를 때 새 줄이 삽입되도록 합니다. |

### <a name="miscellaneous-options"></a>기타 옵션

| 옵션 | 기본값 | 설명 |
| --- | --- | --- |
| **개요 모드로 파일 열기** | 켜기 | Python 코드 파일을 열 때 편집기에서 Visual Studio의 개요 기능을 자동으로 켭니다. |
| **붙여넣으면 REPL 프롬프트가 제거됨** | 켜기 | 붙여넣은 텍스트에서 **>>>** 및 **...** 을 제거하여 **대화형** 창에서 편집기로 코드를 쉽게 전송할 수 있도록 합니다. 다른 소스에서 붙여넣을 때 해당 문자를 유지해야 하는 경우 이 옵션의 선택을 취소합니다. |
| **형식에 따라 이름에 색 지정** | 켜기 | Python 코드에서 구문 색 지정을 사용하도록 설정합니다. |

![Python 편집기 옵션 대화 상자, 고급 탭](media/options-editor-advanced.png)

## <a name="fonts-and-colors-options"></a>글꼴 및 색 옵션

(**환경** > **글꼴 및 색** 탭의 **텍스트 편집기** 그룹 내)

Python 옵션의 이름은 모두 **Python**으로 시작하며 이해하기 쉽습니다. 모든 Visual Studio 색 테마의 기본 글꼴은 10pt Consolas 보통 글꼴(굵은 글꼴 아님)입니다. 기본 색은 테마에 따라 다릅니다. 일반적으로 기본 설정으로 텍스트를 읽기 어려운 경우 글꼴 또는 색을 변경합니다.

![Python 글꼴 및 색 옵션](media/options-fonts-and-colors.png)
