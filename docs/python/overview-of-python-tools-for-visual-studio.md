---
title: Windows의 Visual Studio에서 Python 지원
titleSuffix: ''
description: Windows에서 최상의 Python IDE(PTVS(Visual Studio용 Python 도구)로도 알려짐)로 만드는 Visual Studio의 Python 기능에 대한 요약입니다.
ms.date: 06/05/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: a913fa6abdcf59a64d8514f17656b8f8531d476d
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "79300866"
---
# <a name="work-with-python-in-visual-studio-on-windows"></a>Windows의 Visual Studio에서 Python 작업

Python은 안정적이고 유연하며 배우기 쉬울뿐만 아니라 모든 운영 체제에서 무료로 사용할 수 있으며, 유용한 개발자 커뮤니티와 다양한 무료 라이브러리에서 지원되며 널리 사용되는 프로그래밍 언어입니다. Python은 웹 애플리케이션, 웹 서비스, 데스크톱 앱, 스크립팅 및 과학적 컴퓨팅 등 모든 방식의 개발을 지원하며 대학, 과학자, 아마추어 개발자 및 전문 개발자 등 많은 분야에 사용됩니다. [python.org](https://www.python.org) 및 [Python for Beginners](https://www.python.org/about/gettingstarted/)(초보자를 위한 Python)에서 이 언어에 대해 자세히 알아볼 수 있습니다.

Visual Studio는 Windows에서 강력한 Python IDE입니다. Visual Studio는 **Python 개발** 및 **데이터 과학** 워크로드(Visual Studio 2017 이상)와 무료 Visual Studio용 Python 도구 확장(Visual Studio 2015 및 이전 버전)을 통해 Python 언어에 대한 [오픈 소스](https://github.com/Microsoft/ptvs) 지원을 제공합니다.

Python은 현재 Mac용 Visual Studio에서는 지원되지 않지만 Visual Studio Code를 통해 Mac 및 Linux에서 사용할 수 있습니다([질문 및 답변](#questions-and-answers) 참조).

시작하기:

- [설치 지침](installing-python-support-in-visual-studio.md)에 따라 Python 워크로드를 설치합니다.
- 이 문서의 섹션을 통해 Visual Studio의 Python 기능을 숙지합니다.
::: moniker range="vs-2017"
- 빠른 시작을 하나 이상 수행하여 프로젝트를 만듭니다. 확실하지 않은 경우 [Flask를 사용하여 웹앱 만들기](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)부터 시작합니다.
::: moniker-end
::: moniker range=">=vs-2019"
- 빠른 시작을 하나 이상 수행하여 프로젝트를 만듭니다. 확실하지 않은 경우 [빠른 시작: 폴더에서 Python 코드 열기 및 실행](quickstart-05-python-visual-studio-open-folder.md) 또는 [Flask를 사용하여 웹앱 만들기](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)로 시작합니다.
::: moniker-end
- 전체 엔드투엔드 환경을 위한 [Visual Studio에서 Python 작업](tutorial-working-with-python-in-visual-studio-step-01-create-project.md) 자습서를 수행합니다.

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio는 Python 버전 2.7과 버전 3.5부터 3.7까지를 지원합니다. Visual Studio를 사용하여 다른 버전의 Python에서 작성된 코드도 편집할 수 있지만, 해당 버전은 공식적으로 지원되지 않으며 IntelliSense, 디버깅 등의 기능이 작동하지 않을 수 있습니다. Python 버전 3.8 지원은 아직 개발 중이며, 지원에 대한 구체적인 정보는 관련 [GitHub 추적 이슈](https://github.com/microsoft/PTVS/issues/5822)에서 확인할 수 있습니다.
::: moniker-end

## <a name="support-for-multiple-interpreters"></a>다중 인터프리터 지원.

Visual Studio의 **Python 환경** 창(넓게 확장된 뷰에서 아래에 표시)은 전역 Python 환경, Conda 환경 및 가상 환경 모두를 관리하기 위한 단일 위치를 제공합니다. Visual Studio는 자동으로 기본 위치에 Python 설치를 검색하고 사용자 지정 설치를 구성할 수 있습니다. 각 환경을 사용하여 패키지를 쉽게 관리하고 해당 환경에 대한 대화형 창을 열고 환경 폴더에 액세스할 수 있습니다.

::: moniker range="vs-2017"
![Python 환경 창의 확장된 뷰](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python 환경 창의 확장된 뷰](media/environments/environments-expanded-view-2019.png)
::: moniker-end

Visual Studio의 컨텍스트 내에서 Python을 대화형으로 실행하려면 **대화형 창 열기** 명령을 사용합니다. 선택한 환경의 폴더에서 별도의 명령 창을 열려면 **PowerShell에서 열기** 명령을 사용합니다. 해당 명령 창에서 모든 Python 스크립트를 실행할 수 있습니다.

추가 정보

- [Python 환경 관리](managing-python-environments-in-visual-studio.md)
- [Python 환경 참조](python-environments-window-tab-reference.md)

## <a name="rich-editing-intellisense-and-code-comprehension"></a>다양한 편집 기능, IntelliSense 및 코드 이해

Visual Studio에서는 구문 색 지정, 모든 코드 및 라이브러리에 대한 자동 완성 기능, 코드 서식 지정, 서명 도움말, 리팩터링, linting 및 형식 힌트를 포함하는 고급 Python 편집기를 제공합니다. Visual Studio에서 클래스 뷰, **정의로 이동**, **모든 참조 찾기**, 코드 조각 등의 고유한 기능도 제공합니다. [대화형 창](#interactive-window)과 직접 통합되어 파일에 이미 저장되어 있는 Python 코드를 신속하게 개발할 수 있습니다.

![Visual Studio에서 Python 코드에 대한 코드 완성](media/code-editing-completions-simple.png)

추가 정보

- 문서: [Python 코드 편집](editing-python-code-in-visual-studio.md)
- 문서: [코드 형식](formatting-python-code.md)
- 문서: [코드 리팩터링](refactoring-python-code.md)
- 문서: [Linter 사용](linting-python-code.md)
- 일반 Visual Studio 기능 문서: [코드 편집기의 기능](../ide/writing-code-in-the-code-and-text-editor.md)

## <a name="interactive-window"></a>대화형 창

Visual Studio에 알려진 모든 Python 환경의 경우 별도 명령 프롬프트를 사용하는 대신 Visual Studio 내에서 직접 Python 인터프리터에 대한 동일한 대화형(REPL) 환경을 쉽게 열 수 있습니다. 또한 환경 간 전환을 쉽게 할 수 있습니다. (별도의 명령 프롬프트를 열려면 **Python 환경** 창에서 원하는 환경을 선택하고 앞서 [다중 인터프리터 지원](#support-for-multiple-interpreters)에서 설명한 대로 **PowerShell에서 열기** 명령을 선택합니다.)

![Visual Studio의 Python 대화형 창](media/interactive-window.png)

또한 Visual Studio는 Python 코드 편집기와 **대화형** 창 간의 긴밀한 통합을 제공합니다. **Ctrl**+**Enter** 바로 가기 키는 간편하게 편집기에서 현재 코드 줄(또는 코드 블록)을 **대화형** 창으로 보낸 후, 다음 줄(또는 블록)로 이동합니다. **Ctrl**+**Enter**를 사용하면 디버거를 실행할 필요 없이 쉽게 한 단계씩 코드를 실행할 수 있습니다. 또한 동일한 키 입력으로 선택한 코드를 **대화형** 창으로 보내고, **대화형** 창에서 편집기에 코드를 쉽게 붙여넣을 수 있습니다. 이러한 기능을 함께 사용하면 **대화형** 창에서 코드의 세그먼트에 대한 세부 정보를 파악하고 편집기에서 결과를 파일에 쉽게 저장할 수 있습니다.

또한 Visual Studio는 인라인 플롯, .NET 및 WPF(Windows Presentation Foundation)를 포함하여 REPL에서 IPython/Jupyter를 지원합니다.

추가 정보

- [대화형 창](python-interactive-repl-in-visual-studio.md)
- [Visual Studio의 IPython](interactive-repl-ipython.md)

## <a name="project-system-and-project-and-item-templates"></a>프로젝트 시스템, 프로젝트 및 항목 템플릿

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio 2019는 Visual Studio 프로젝트 및 솔루션 파일을 만들지 않고도 Python 코드가 포함된 폴더를 열어 해당 코드를 실행하도록 지원합니다. 자세한 내용은 [빠른 시작: 폴더에서 Python 코드 열기 및 실행](quickstart-05-python-visual-studio-open-folder.md)을 참조하세요. 하지만 이 섹션에서 설명한 대로 프로젝트 파일 사용을 통해 얻을 수 있는 이점이 있습니다.
::: moniker-end

Visual Studio에서는 시간이 지남에 따라 커지는 프로젝트의 복잡성을 관리할 수 있습니다. ‘Visual Studio 프로젝트’는 폴더 구조보다 훨씬 더 복잡합니다. 프로젝트에는 다른 파일이 어떻게 사용되는지 그리고 서로 어떤 관계인지에 대한 이해가 포함됩니다.  Visual Studio를 사용하면 앱 코드, 태스트 코드, 웹 페이지, JavaScript, 빌드 스크립트 등을 구분한 다음, 파일에 적합한 기능을 사용하도록 설정할 수 있습니다. 또한 Visual Studio 솔루션에서는 Python 프로젝트 및 C++ 확장 프로젝트 같은 다수의 관련 프로젝트를 관리할 수 있습니다.

![Python 및 C++ 프로젝트가 포함된 Visual Studio 솔루션](media/projects-solution-explorer-two-projects.png)

프로젝트 및 항목 템플릿은 다양한 유형의 프로젝트와 파일의 설정 프로세스를 자동화하여 소중한 시간을 절약해주고 복잡하고 오류가 발생하기 쉬운 세부 정보를 관리할 필요가 없습니다. Visual Studio는 웹, Azure, 데이터 과학, 콘솔 및 기타 유형의 프로젝트에 대한 템플릿뿐 아니라 Python 클래스, 단위 테스트, Azure 웹 구성, HTML 및 Django 앱 같은 파일에 대한 템플릿도 제공합니다.

[![Visual Studio에서 Python 프로젝트 및 항목 템플릿](media/project-and-item-templates.png)](media/project-and-item-templates.png#lightbox)

추가 정보

- 문서: [Python 프로젝트 관리](managing-python-projects-in-visual-studio.md)
- 문서: [항목 템플릿 참조](python-item-templates.md)
- 문서: [Python 프로젝트 템플릿](managing-python-projects-in-visual-studio.md#project-templates)
- 문서: [C++ 및 Python 작업](working-with-c-cpp-python-in-visual-studio.md)
- 일반 Visual Studio 기능 문서: [프로젝트 및 항목 템플릿](../ide/creating-project-and-item-templates.md#visual-studio-templates)
- 일반 Visual Studio 기능 문서: [Visual Studio의 솔루션 및 프로젝트](../ide/solutions-and-projects-in-visual-studio.md)

## <a name="full-featured-debugging"></a>완전한 기능의 디버깅

Visual Studio의 장점 중 하나는 강력한 디버거입니다. 특히 Python의 경우 Visual Studio는 Python/C++ 혼합 모드 디버깅, Linux의 원격 디버깅, **대화형** 창 내의 디버깅 및 Python 단위 테스트 디버깅을 포함합니다.

![예외 팝업을 표시하는 Python용 Visual Studio 디버거](media/debugging-exception-popup.png)

::: moniker range=">=vs-2019"
Visual Studio 2019에서 Visual Studio 프로젝트 파일 없이 코드를 실행하고 디버그할 수 있습니다. [빠른 시작: 폴더에서 Python 코드 열기 및 실행](quickstart-05-python-visual-studio-open-folder.md)의 예를 참조하세요.
::: moniker-end

추가 정보

- 문서: [Python 디버그](debugging-python-in-visual-studio.md)
- 문서: [Python/C++ 혼합 모드 디버깅](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- 문서: [Linux에서 원격 디버깅](debugging-python-code-on-remote-linux-machines.md)
- 일반 Visual Studio 기능 문서: [Visual Studio 디버거 기능 둘러보기](../debugger/debugger-feature-tour.md)

## <a name="profiling-tools-with-comprehensive-reporting"></a>포괄적인 보고를 제공하는 프로파일링 도구

프로파일링은애플리케이션 내에서 시간이 어떻게 쓰이는지를 탐색합니다. Visual Studio는 CPython 기반 인터프리터를 사용한 프로 파일링을 지원하고 다른 프로파일링 실행 간 성능을 비교하는 기능을 포함합니다.

[![Python 프로젝트에 대한 Visual Studio 프로파일러 결과](media/profiling-results.png)](media/profiling-results.png#lightbox)

추가 정보

- 문서: [Python 프로파일링 도구](profiling-python-code-in-visual-studio.md)
- 일반 Visual Studio 기능 문서: [프로파일링 기능 둘러보기](../profiling/profiling-feature-tour.md). (Python에 대해 일부 Visual Studio 프로파일링 기능만 사용할 수 있습니다).

## <a name="unit-testing-tools"></a>위 테스트 도구

Visual Studio **테스트 탐색기**에서 테스트를 검색, 실행 및 관리하고 단위 테스트를 쉽게 디버그합니다.

![Visual Studio에서 Python 단위 테스트 디버깅](media/unit-test-debugging.png)

추가 정보

- 문서: [Python용 단위 테스트 도구](unit-testing-python-in-visual-studio.md)
- 일반 Visual Studio 기능 문서: [코드 단위 테스트](../test/unit-test-your-code.md).

## <a name="azure-sdk-for-python"></a>Python용 Azure SDK

Python용 Azure 라이브러리는 Windows, Mac OS X 및 Linux 앱에서 Azure 서비스 사용을 간소화합니다. 라이브러리를 사용하여 Azure 리소스를 만들고 관리할 뿐만 아니라, Azure 서비스에 연결할 수 있습니다. 

자세한 내용은 [Python용 Azure SDK](/azure/python/) 및 [Python용 Azure 라이브러리](/azure/python/python-sdk-azure-overview)를 참조하세요.

## <a name="questions-and-answers"></a>질문과 대답

**질문: Mac용 Visual Studio에서 Python 지원을 사용할 수 있나요?**

대답: 이번에는 아니지만 [개발자 커뮤니티](https://developercommunity.visualstudio.com/content/idea/351820/python-tools-for-visual-studio-mac.html)에 대한 요청을 긍정적으로 검토할 수 있습니다. [Mac용 Visual Studio](/visualstudio/mac/) 설명서에서는 지원되는 현재 개발 유형을 확인합니다. 한편, Windows, Mac 및 Linux의 Visual Studio Code는 [사용 가능한 확장을 통해 Python에서 잘 작동](https://code.visualstudio.com/docs/languages/python)합니다.

**질문: UI를 빌드하는 데 Python과 함께 무엇을 사용할 수 있나요?**

대답: 이 영역의 기본 제품은 [Qt Project](https://www.qt.io/qt-for-application-development/), [PySide(공식 바인딩)](https://wiki.qt.io/PySide)([PySide 다운로드](https://download.qt.io/official_releases/pyside/.)도 참조)로 알려진 Python용 바인딩 및 [PyQt](https://wiki.python.org/moin/PyQt)입니다. 현재는 Visual Studio의 Python 지원에 UI 개발용 특정 도구가 포함되지 않습니다.

**질문: Python 프로젝트에서 독립 실행형 실행 파일을 생성할 수 있나요?**

대답: Python은 일반적으로 Visual Studio, 웹 서버와 같은 적합한 Python 지원 환경에서 요청 시 코드를 실행하는 데 사용되는 해석된 언어입니다. 현재는 Visual Studio 자체에서 독립 실행형 실행 파일을 만드는 방법을 제공하지 않습니다. 즉, 기본적으로 포함된 Python 인터프리터가 있는 프로그램입니다. 그러나 [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency)에 설명된 것처럼 Python 커뮤니티에서는 실행 파일을 만드는 다양한 방법을 제공합니다. 또한 CPython은 블로그 게시물 [Using CPython's embeddable zip file](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/)(CPython의 포함 가능한 zip 파일 사용)에 설명된 것처럼 네이티브 애플리케이션 내에 포함되는 기능을 지원합니다.

::: moniker range="<=vs-2017"

## <a name="feature-support"></a>기능 지원

[설치 가이드](installing-python-support-in-visual-studio.md)에 설명된 대로 Visual Studio의 다음 버전(edition)에 Python 기능을 설치할 수 있습니다.

- [Visual Studio 2019(모든 버전)](https://visualstudio.microsoft.com/vs/)
- Visual Studio 2017(모든 버전)
- Visual Studio 2015(모든 버전)
- Visual Studio 2013 Community Edition
- Visual Studio 2013 Express for Web 업데이트 2 이상
- Visual Studio 2013 Express for Desktop 업데이트 2 이상
- Visual Studio 2013(Pro 버전 이상)
- Visual Studio 2012(Pro 버전 이상)
- Visual Studio 2010 SP1(Pro 버전 이상, .NET 4.5 필요)

Visual Studio 2015 및 이전 버전은 [visualstudio.microsoft.com/vs/older-downloads/](https://visualstudio.microsoft.com/vs/older-downloads/)에서 제공됩니다.

> [!Important]
> 기능이 Visual Studio의 최신 버전에 대해서만 완전하게 지원 및 유지 관리됩니다. 기능이 이전 버전에서 사용할 수 있지만 적극적으로 유지 관리되지 않습니다.

|          Python 지원          |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|----------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|   여러 인터프리터 관리   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| 자동 검색에 자주 사용되는 인터프리터 | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     사용자 지정 인터프리터 추가      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       가상 환경       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Pip/간편 설치         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         프로젝트 시스템         |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ |      2012 Pro+       | 2010 SP1 Pro+ |
|--------------------------------|----------|----------|-----------|--------------|----------|-----------|----------------------|---------------|
| 기존 코드에서 새 프로젝트 | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         모든 파일 표시         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         소스 제어         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|        Git 통합         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;<sup>1</sup> |   &#10007;    |

<br/>

|           편집            |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     구문 강조      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        자동 완성         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        서명 도움말        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|          요약 정보          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  개체 브라우저/클래스 뷰   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        탐색 모음        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       정의로 이동       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         다음 탐색          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     모든 참조 찾기      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       자동 들여쓰기       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       코드 서식        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      리팩터링 - 이름 바꾸기       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  리팩터링 - 추출 방법   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| 리팩터링 - 가져오기 추가/제거 | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|            PyLint            | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|     대화형 창     |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|----------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     대화형 창     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| 인라인 그래프가 있는 IPython | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|               바탕 화면               |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|-------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     콘솔/Windows 애플리케이션     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| IronPython WPF(XAML 디자이너 포함) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      IronPython Windows Forms       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         웹         |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Django 웹 프로젝트  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Bottle 웹 프로젝트  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Flask 웹 프로젝트  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| 일반 웹 프로젝트 | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Azure          |   2017+   |   2015   | 2013 Comm | 2013 Desktop |       2013 Web       |      2013 Pro+       |      2012 Pro+       |    2010 SP1 Pro+     |
|------------------------|----------|----------|-----------|--------------|----------------------|----------------------|----------------------|----------------------|
|   웹 사이트에 배포   | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       |       &#10004;       | &#10004;<sup>2</sup> |
|   웹 역할에 배포   | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| 작업자 역할에 배포  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Azure 에뮬레이터에서 실행  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
|    원격 디버깅    | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> |       &#10007;       |
| 서버 탐색기 연결 | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> |       &#10007;       |       &#10007;       |

<br/>

|           Django 템플릿           |   2017+   |   2015   | 2013 Comm | 2013 Desktop |       2013 Web       |      2013 Pro+       | 2012 Pro+ | 2010 SP1 Pro+ |
|--------------------------------------|----------|----------|-----------|--------------|----------------------|----------------------|-----------|---------------|
|              디버깅               | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       | &#10004;  |   &#10004;    |
|            자동 완성             | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004;  |   &#10004;    |
| CSS 및 JavaScript 자동 완성 | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007;  |   &#10007;    |

<br/>

|                  디버깅                  |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|                  디버깅                  | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         프로젝트 없이 디버깅         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        디버깅 - 편집에 연결        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|            혼합 모드 디버깅             | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
| 원격 디버깅(Windows, Mac OS X, Linux) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|          디버그 대화형 창           | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

<a name="matrix-profiling"></a>

| 프로파일링 |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|-----------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| 프로파일링 | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|     테스트      |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| 테스트 탐색기 | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|   테스트 실행    | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|  테스트 디버깅   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |

<br/>

1. Visual Studio 2012에 대한 Git 지원은 Git용 Visual Studio Tools 확장에서 사용 가능하며 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TFSPowerToolsTeam.VisualStudioToolsforGit)에서 제공됩니다.

1. Azure 웹 사이트에 배포하려면 [.NET 2.1용 Azure SDK - Visual Studio 2010 SP1](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VS2010SP1AzurePack.2E2.2E1.appids)이 필요합니다. 이후 버전에서는 Visual Studio 2010을 지원하지 않습니다.

1. Azure 웹 역할 및 작업자 역할에 대한 지원을 사용하려면 [.NET 2.3용 Azure SDK - VS 2012](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs11AzurePack.appids) 이상이 필요합니다.

1. Azure 웹 역할 및 작업자 역할에 대한 지원을 사용하려면 [.NET 2.3용 Azure SDK - VS 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) 이상이 필요합니다.

1. Visual Studio 2013에서 Django 템플릿 편집기에는 몇 가지 알려진 문제가 있으며 Update 2를 설치하여 해결할 수 있습니다.

1. Windows 8 이상이 필요합니다. Visual Studio 2013 Express for Web에는 **프로세스에 연결** 대화 상자가 없지만, **서버 탐색기**에서 **디버거 연결(Python)** 명령을 사용하여 Azure 웹 사이트 원격 디버깅을 계속 수행할 수 있습니다. 원격 디버깅을 사용하려면 [.NET 2.3용 Azure SDK - Visual Studio 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) 이상이 필요합니다.

1. Windows 8 이상이 필요합니다. **서버 탐색기**에서 **디버거 연결(Python)** 명령을 사용하려면 [.NET 2.3용 Azure SDK - Visual Studio 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) 이상이 필요합니다.

1. Windows 8 이상이 필요합니다.
::: moniker-end
