---
title: Python 설치 지원
description: 옵션 및 설치 위치를 포함하여 Visual Studio 2017, 2015, 2013, 2012 및 2010에서 PTVS(Visual Studio용 Python 도구)를 설치하는 방법입니다.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 15869119ea867e41d3b91a1f046d1ffb995cd4e4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75398429"
---
# <a name="how-to-install-python-support-in-visual-studio-on-windows"></a>Windows의 Visual Studio에서 Python 지원 설치 방법

Visual Studio용 Python 지원(Visual Studio용 Python 도구 또는 PTVS라고도 함)을 설치하려면 Visual Studio 버전과 일치하는 섹션의 지침을 따릅니다.

- [Visual Studio 2017 및 Visual Studio 2019](#visual-studio-2017-and-2019)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 및 이전 버전](#visual-studio-2013-and-earlier)

설치 단계를 따른 후 Python 지원을 신속하게 테스트하려면 **Alt**+**I**를 누르고 `2+2`를 입력하여 **Python 대화형** 창을 엽니다. `4`의 출력이 표시되지 않으면 수행한 단계를 다시 확인합니다.

> [!Tip]
> Python 작업에는 템플릿을 검색하고, 템플릿 옵션을 입력하고, 프로젝트와 파일을 만들 수 있는 그래픽 사용자 인터페이스를 제공하는 유용한 Cookiecutter 확장 프로그램이 포함되어 있습니다. 자세한 내용은 [Cookiecutter 확장 사용](using-python-cookiecutter-templates.md)을 참조하세요.

> [!Note]
> Python 지원은 현재 Mac용 Visual Studio에서 사용할 수 없으며 Visual Studio Code를 통해 Mac 및 Linux에서 사용할 수 있습니다. [질문과 대답](overview-of-python-tools-for-visual-studio.md#questions-and-answers)을 참조하세요.

<a name="visual-studio-2017-and-2019"></a>
## <a name="visual-studio-2019-and-visual-studio-2017"></a>Visual Studio 2019 및 Visual Studio 2017

1. 최신 Visual Studio 설치 관리자를 다운로드하고 실행합니다. Visual Studio가 이미 설치되어 있는 경우 Visual Studio 설치 관리자를 실행하고 **수정** 옵션([Visual Studio 수정](../install/modify-visual-studio.md) 참조)을 선택하고 2단계로 이동합니다.

    > [!div class="nextstepaction"]
    > [Visual Studio 2019 Community 설치](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > 커뮤니티 에디션은 개인 개발자, 교실 학습, 학술 연구 및 오픈 소스 개발용입니다. 다른 용도의 경우 [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) 또는 [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)를 설치합니다.

1. 설치 관리자는 특정 개발 영역에 대한 관련 옵션의 그룹인 워크로드 목록을 제공합니다. Python의 경우 **Python 개발** 워크로드를 선택합니다.

    ![Visual Studio 설치 관리자의 Python 개발 작업](media/installation-python-workload.png)

    ::: moniker range="vs-2017"
    선택 사항: 데이터 과학을 사용하는 경우 **데이터 과학 및 분석 애플리케이션** 워크로드도 고려합니다. 이 워크로드는 Python, R 및 F# 언어에 대한 지원을 포함합니다. 자세한 내용은 [데이터 과학 및 분석 애플리케이션 워크로드](data-science-and-analytical-applications-workload.md)를 참조하세요.

    > [!Note]
    > Python 및 데이터 과학 워크로드는 Visual Studio 2017 버전 15.2 이상에서만 사용할 수 있습니다.

    ::: moniker-end

    ::: moniker range=">=vs-2019"
    선택 사항: 데이터 과학을 사용하는 경우 **데이터 과학 및 분석 애플리케이션** 워크로드도 고려합니다. 이 워크로드는 Python 및 F# 언어에 대한 지원을 포함합니다. 자세한 내용은 [데이터 과학 및 분석 애플리케이션 워크로드](data-science-and-analytical-applications-workload.md)를 참조하세요.
    ::: moniker-end

1. 설치 관리자의 오른쪽에서 필요한 경우 추가 옵션을 선택합니다. 기본 옵션을 적용하려면 이 단계를 건너뜁니다.

    ::: moniker range="vs-2017"
    ![Visual Studio 설치 관리자의 Python 개발 옵션](media/installation-python-options.png)
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    ![Visual Studio 2019 설치 관리자의 Python 개발 옵션](media/installation-python-options-2019.png)
    ::: moniker-end

    ::: moniker range="<=vs-2017"
    | 옵션 | 설명 |
    | --- | --- |
    | Python 배포 | 작업하려는 Python 2, Python 3, Miniconda, Anaconda2 및 Anaconda3 분배의 32비트 및 64비트 변형과 같은 사용 가능한 옵션 조합을 선택합니다. 각각은 배포의 인터프리터, 런타임 및 라이브러리를 포함합니다. 특히 Anaconda는 다양한 미리 설치된 패키지를 포함하는 개방형 데이터 과학 플랫폼입니다. (배포를 추가하거나 제거하기 위해 언제든지 Visual Studio 설치 관리자로 돌아갈 수 있습니다.)  **참고**: Visual Studio 설치 관리자 외부에서 배포를 설치한 경우 여기서 해당 옵션을 선택할 필요가 없습니다. Visual Studio에서 기존 Python 설치를 자동으로 검색합니다. [Python 환경 창](managing-python-environments-in-visual-studio.md#the-python-environments-window)을 참조하세요. 또한 설치 관리자에 표시된 버전보다 최신 버전의 Python을 사용할 수 있는 경우 해당 버전을 별도로 설치할 수 있으며, Visual Studio에서 이를 검색합니다. |
    | **Cookiecutter 템플릿 지원** | Cookiecutter 그래픽 UI를 설치하여 템플릿을 검색하고, 템플릿 옵션을 입력하고, 프로젝트 및 파일을 만듭니다. [Cookiecutter 확장 사용](using-python-cookiecutter-templates.md)을 참조하세요. |
    | **Python 웹 지원** | Bottle, Flask 및 Django 프레임워크를 사용하는 프로젝트에 대한 템플릿과 함께 HTML, CSS 및 JavaScript 편집 지원을 포함하는 웹 개발용 도구를 설치합니다. [Python 웹 프로젝트 템플릿](python-web-application-project-templates.md)을 참조하세요. |
    | **Python IoT 지원** | Python을 사용하여 Windows IoT Core 개발을 지원합니다. |
    | **Python 네이티브 개발 도구** | C++ 컴파일러 및 Python에 대한 기본 확장을 개발하는 데 필요한 기타 구성 요소를 설치합니다. [Python용 C++ 확장 만들기](working-with-c-cpp-python-in-visual-studio.md)를 참조하세요. 또한 전체 C++ 지원을 사용하려면 **C++를 사용한 데스크톱 개발** 워크로드를 설치하세요. |
    | **Azure Cloud Services 핵심 도구** | Python에서 개발자 Azure Cloud Services에 대한 추가 지원을 제공합니다. [Azure Cloud Service 프로젝트](python-azure-cloud-service-project-template.md)를 참조하세요. |
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    | 옵션 | 설명 |
    | --- | --- |
    | Python 배포 | 작업하려는 Python 2, Python 3, Miniconda, Anaconda2 및 Anaconda3 분배의 32비트 및 64비트 변형과 같은 사용 가능한 옵션 조합을 선택합니다. 각각은 배포의 인터프리터, 런타임 및 라이브러리를 포함합니다. 특히 Anaconda는 다양한 미리 설치된 패키지를 포함하는 개방형 데이터 과학 플랫폼입니다. (배포를 추가하거나 제거하기 위해 언제든지 Visual Studio 설치 관리자로 돌아갈 수 있습니다.)  **참고**: Visual Studio 설치 관리자 외부에서 배포를 설치한 경우 여기서 해당 옵션을 선택할 필요가 없습니다. Visual Studio에서 기존 Python 설치를 자동으로 검색합니다. [Python 환경 창](managing-python-environments-in-visual-studio.md#the-python-environments-window)을 참조하세요. 또한 설치 관리자에 표시된 버전보다 최신 버전의 Python을 사용할 수 있는 경우 해당 버전을 별도로 설치할 수 있으며, Visual Studio에서 이를 검색합니다. |
    | **Cookiecutter 템플릿 지원** | Cookiecutter 그래픽 UI를 설치하여 템플릿을 검색하고, 템플릿 옵션을 입력하고, 프로젝트 및 파일을 만듭니다. [Cookiecutter 확장 사용](using-python-cookiecutter-templates.md)을 참조하세요. |
    | **Python 웹 지원** | Bottle, Flask 및 Django 프레임워크를 사용하는 프로젝트에 대한 템플릿과 함께 HTML, CSS 및 JavaScript 편집 지원을 포함하는 웹 개발용 도구를 설치합니다. [Python 웹 프로젝트 템플릿](python-web-application-project-templates.md)을 참조하세요. |
    | **Python 네이티브 개발 도구** | C++ 컴파일러 및 Python에 대한 기본 확장을 개발하는 데 필요한 기타 구성 요소를 설치합니다. [Python용 C++ 확장 만들기](working-with-c-cpp-python-in-visual-studio.md)를 참조하세요. 또한 전체 C++ 지원을 사용하려면 **C++를 사용한 데스크톱 개발** 워크로드를 설치하세요. |
    | **Azure Cloud Services 핵심 도구** | Python에서 개발자 Azure Cloud Services에 대한 추가 지원을 제공합니다. [Azure Cloud Service 프로젝트](python-azure-cloud-service-project-template.md)를 참조하세요. |
    ::: moniker-end

1. 설치가 끝나면 설치 관리자는 Visual Studio를 수정, 실행, 복구 또는 제거하는 옵션을 제공합니다. **수정** 단추는 설치된 구성 요소의 Visual Studio에 대한 업데이트를 사용할 수 있으면 **업데이트**로 변경됩니다. (**수정** 옵션은 드롭다운 메뉴에서 사용할 수 있습니다.) "Visual Studio"를 검색하여 Windows **시작** 메뉴에서 Visual Studio 및 설치 관리자를 시작할 수도 있습니다.

    ![설치 관리자에서 Visual Studio 시작, 수정 또는 제거](media/installation-vs-launch.png)

### <a name="troubleshooting"></a>문제 해결

Visual Studio에서 Python 설치 또는 실행 문제가 발생하는 경우 다음을 시도합니다.

- Python CLI를 사용하여 동일한 오류가 발생했는지 확인합니다. 즉, 명령 프롬프트에서 *python.exe*를 실행합니다.
- Visual Studio 설치 관리자의 [**복구**](../install/repair-visual-studio.md) 옵션을 사용합니다.
- Windows의 **설정** > **앱 및 기능**을 통해 Python을 복구하거나 다시 설치합니다.

**오류 예제**: 대화형 프로세스를 시작하지 못했습니다. System.ComponentModel.Win32Exception (0x80004005): Microsoft.PythonTools.Repl.PythonInteractiveEvaluator.d__43.MoveNext()에서 알 수 없는 오류(0xc0000135)입니다.

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. **제어판 > 프로그램 및 기능**에서 **Microsoft Visual Studio 2015**, **변경**을 차례로 선택하여 Visual Studio 설치 관리자를 실행합니다.

1. 설치 관리자에서 **수정**을 선택합니다.

1. **프로그래밍 언어** > **Visual Studio용 Python 도구**를 선택하고 **다음**을 선택합니다.

    ![Visual Studio 2015 설치 관리자의 PTVS 옵션](media/installation-vs2015.png)

1. Visual Studio 설치가 완료되면 [원하는 Python 인터프리터를 설치](installing-python-interpreters.md)합니다. Visual Studio 2015는 Python 3.5 이하만 지원합니다. 이후 버전에서는 **지원되지 않는 Python 버전 3.6**과 같은 메시지를 생성합니다. 이미 인터프리터가 설치되어 있고 Visual Studio에서 이를 자동으로 검색하지 않는 경우 [기존 환경 수동 식별](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)을 참조하세요.

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 및 이전 버전

1. 사용 중인 Visual Studio 버전에 맞는 적절한 버전의 Visual Studio용 Python 도구를 설치합니다.

    - Visual Studio 2013: [Visual Studio 2013용 PTVS 2.2.2](https://github.com/Microsoft/PTVS/releases/v2.2.2) Visual Studio 2013에서 **파일** > **새 프로젝트** 대화 상자는 이 프로세스에 대한 바로 가기를 제공합니다.
    - Visual Studio 2010 및 2012: [Visual Studio 2010 및 2012용 PTVS 2.1.1](https://github.com/Microsoft/PTVS/releases/v2.1.1)

1. [원하는 Python 인터프리터를 설치합니다](installing-python-interpreters.md). 이미 인터프리터가 설치되어 있고 Visual Studio에서 이를 자동으로 검색하지 않는 경우 [기존 환경 수동 식별](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)을 참조하세요.

## <a name="install-locations"></a>설치 위치

기본적으로 Python 지원은 컴퓨터의 모든 사용자를 위해 설치됩니다.

Visual Studio 2019 및 Visual Studio 2017에서 Python 워크로드는 *%ProgramFiles(x86)%\Microsoft Visual Studio\\<VS_version>\\<VS_edition>Common7\IDE\Extensions\Microsoft\Python*에 설치됩니다. 여기서 &lt;VS_version&gt;은 2019 또는 2017이고 &lt;VS_edition&gt;은 Community, Professional 또는 Enterprise입니다.

Visual Studio 2015 및 이전 버전에서 설치 경로는 다음과 같습니다.

- 32비트:
  - 경로: *%Program Files(x86)%\Microsoft Visual Studio \<VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\\<PTVS_ver>*
  - 경로의 레지스트리 위치: **HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\\<VS_ver>\InstallDir**
- 64비트:
  - 경로: *%Program Files%\Microsoft Visual Studio \<VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\\<PTVS_ver>*
  - 경로의 레지스트리 위치: **HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\\<VS_ver>\InstallDir**

다음은 각 문자에 대한 설명입니다.

- &lt;VS_ver&gt;는 다음과 같습니다.
  - Visual Studio 2015의 경우 14.0
  - Visual Studio 2013의 경우 12.0
  - Visual Studio 2012의 경우 11.0
  - Visual Studio 2010의 경우 10.0
- &lt;PTVS_ver&gt;는 2.2.2, 2.1.1, 2.0, 1.5, 1.1, 1.0과 같은 버전 번호입니다.

### <a name="user-specific-installations-15-and-earlier"></a>사용자 고유의 설치(1.5 및 이전 버전)

Visual Studio용 Python 도구 1.5 이하에서는 현재 사용자에 대한 설치만 허용했습니다. 이 경우 설치 경로는 *%LocalAppData%\Microsoft\VisualStudio\\<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio\\<PTVS_ver>* 이고, 여기서 &lt;VS_ver&gt; 및 &lt;PTVS_ver&gt;는 위에 설명된 것과 같습니다.
