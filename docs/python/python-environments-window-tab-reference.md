---
title: Python 환경 창 참조
description: Visual Studio의 [Python 환경] 창에 나타나는 각 탭에 대한 세부 정보입니다.
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 578f73aabfb8b5a4c8336c8611f634b8947c8885
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79307120"
---
# <a name="python-environments-window-tabs-reference"></a>Python 환경 창 탭 참조

**Python 환경** 창을 열려면:

- **보기** > **다른 창** > **Python 환경** 메뉴 명령을 선택합니다.
- **솔루션 탐색기**에서 프로젝트의 **Python 환경** 노드를 마우스 오른쪽 단추로 클릭하고 **모든 Python 환경 보기**를 선택합니다.

**Python 환경** 창을 적당히 넓게 확장하면 이러한 옵션이 탭으로 표시되어 작업하기가 더 편리할 수 있습니다. 이해를 돕기 위해 이 문서의 탭이 확장 보기에 표시됩니다.

::: moniker range="vs-2017"
![Python 환경 창 확장된 보기](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python 환경 창 확장된 보기](media/environments/environments-expanded-view-2019.png)
::: moniker-end

## <a name="overview-tab"></a>개요 탭

환경에 대한 기본 정보와 명령을 제공합니다.

::: moniker range="vs-2017"
![Python 환경 개요 탭](media/environments/environments-overview-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python 환경 개요 탭](media/environments/environments-overview-tab-2019.png)
::: moniker-end

| 명령 | 설명 |
| --- | --- |
| **이 환경을 새 프로젝트에 대한 기본값으로 설정** | 활성 환경을 설정합니다. 이 경우 IntelliSense 데이터베이스가 로드되는 동안 Visual Studio(2017 버전 15.5 및 그 이전)가 잠시 응답하지 않을 수 있습니다. 많은 패키지가 있는 환경에서는 더 오랫동안 응답하지 않을 수 있습니다. |
| **배포자 웹 사이트 방문** | Python 배포에서 제공된 URL로 브라우저를 엽니다. 예를 들어 Python 3.x는 python.org로 이동합니다. |
| **대화형 창 열기** | Visual Studio 내에서 이 환경에 대한 [대화형(REPL) 창](python-interactive-repl-in-visual-studio.md)을 열고 [시작 스크립트(아래 참조)](#startup-scripts)를 적용합니다. |
| **대화형 스크립트 탐색** | [시작 스크립트](#startup-scripts)를 참조하세요. |
| **IPython 대화형 모드 사용** | 설정하면 기본적으로 IPython을 사용하여 **대화형** 창을 엽니다. 여기서 인라인 플롯과 확장된 IPython 구문을 사용할 수 있습니다. 예를 들어 도움말을 보려면 `name?`를 사용하고, 셸 명령을 실행하려면 `!command`를 사용합니다. 이 옵션은 추가 패키지를 요구하는 Anaconda 배포를 사용할 때 권장됩니다. 자세한 내용은 [대화형 창에서 IPython 사용](interactive-repl-ipython.md)을 참조하세요. |
| **PowerShell에서 열기** | PowerShell 명령 창에서 인터프리터를 시작합니다. |
| (폴더 및 프로그램 링크) | 환경 설치 폴더, *python.exe* 인터프리터, *pythonw.exe* 인터프리터에 대한 빠른 액세스를 제공합니다. 첫 번째 링크는 Windows 탐색기에서 열리고, 나머지 링크는 콘솔 창을 엽니다. |

### <a name="startup-scripts"></a>시작 스크립트

일상적인 워크플로에 대화형 창을 사용하면서 정기적으로 사용하는 도우미 함수를 개발할 가능성이 큽니다. 예를 들어 Excel에서 데이터 프레임을 여는 함수를 만든 다음, **대화형** 창에서 항상 사용할 수 있도록 해당 코드를 시작 스크립트로 저장할 수 있습니다.

시작 스크립트에는 가져오기, 함수 정의 등을 포함하여 **대화형** 창에서 자동으로 로드하고 실행하는 코드가 포함됩니다. 이러한 스크립트는 다음 두 가지 방법으로 참조됩니다.

1. 환경을 설치할 때 Visual Studio는 *Documents\Visual Studio \<version>\Python Scripts\\\<environment>* 폴더를 만듭니다. 여기서 &lt;version&gt;은 Visual Studio 버전(예: 2017 또는 2019)이고 &lt;environment&gt;는 환경 이름과 일치합니다. **대화형 스크립트 탐색** 명령을 사용하여 환경 관련 폴더를 쉽게 탐색할 수 있습니다. 해당 환경에 대한 **대화형** 창을 시작하면 여기서 발견된 *.py* 파일이 사전순으로 로드 및 실행됩니다.

1. **도구** > **옵션** > **Python** > **대화형 창** 탭([대화형 창 옵션](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options) 참조)의 **스크립트** 컨트롤은 모든 환경에서 로드 및 실행되는 시작 스크립트에 대한 추가 폴더를 지정하기 위한 것입니다. 그러나 이 기능은 현재 작동하지 않습니다.

## <a name="configure-tab"></a>구성 탭

사용 가능한 경우 **구성** 탭에는 아래 표에 설명된 세부 정보가 포함됩니다. 이 탭이 없는 경우 Visual Studio에서 모든 세부 정보를 자동으로 관리하는 것입니다.

::: moniker range="vs-2017"
![Python 환경 구성 탭](media/environments/environments-configure-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python 환경 구성 탭](media/environments/environments-configure-tab-2019.png)
::: moniker-end

| 필드 | 설명 |
| --- | --- |
| **설명** | 환경에 지정할 이름입니다. |
| **접두사 경로** | 인터프리터의 기본 폴더 위치입니다. 이 값을 입력하고 **자동 검색**을 클릭하면 Visual Studio에서 다른 필드를 채우려고 시도합니다. |
| **인터프리터 경로** | 인터프리터 실행 파일의 경로이며, 일반적으로 접두사 경로 다음에 **python.exe**가 나옵니다. |
| **창 인터프리터** | 비콘솔 실행 파일의 경로이며, 보통 접두사 경로 다음에 **pythonw.exe**가 나옵니다. |
| **라이브러리 경로**<br/>(사용 가능한 경우) | 표준 라이브러리의 루트를 지정하지만 Visual Studio에서 인터프리터로부터 더 정확한 경로를 요청할 수 있는 경우 이 값은 무시될 수 있습니다. |
| **언어 버전** | 드롭다운 메뉴에서 선택합니다. |
| **아키텍처** | 일반적으로 검색되어 자동으로 채워지며 그렇지 않으면 **32비트** 또는 **64비트**가 지정됩니다. |
| **경로 환경 변수** | 인터프리터에서 검색 경로를 찾는 데 사용하는 환경 변수입니다. Visual Studio는 Python을 시작할 때 변수 값을 변경하여 프로젝트의 검색 경로를 포함하도록 합니다. 일반적으로 이 속성은 **PYTHONPATH**로 설정해야 하지만 일부 인터프리터에서는 다른 값을 사용합니다. |

## <a name="packages-tab"></a>패키지 탭

또한 이전 버전에서 “pip”로 레이블이 지정됩니다. 

환경에 설치된 패키지는 PIP(**패키지(PyPI)** 탭) 또는 Conda(**패키지(Conda)** 탭, Visual Studio 2017 버전 15.7 이상의 Conda 환경인 경우)를 사용하여 관리합니다. 이러한 탭에서는 종속성을 포함하여 새 패키지를 검색하고 설치할 수도 있습니다.

이미 설치된 패키지는 패키지 업데이트(위쪽 화살표) 및 제거(원 안의 X) 컨트롤과 함께 표시됩니다.

![Python 환경 패키지 탭](media/environments/environments-pip-tab-controls.png)

검색 용어를 입력하면 설치된 패키지 및 PyPI에서 설치할 수 있는 패키지 목록이 필터링됩니다.

::: moniker range="vs-2017"
![“num” 검색이 있는 Python 환경 패키지 탭](media/environments/environments-pip-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![“num” 검색이 있는 Python 환경 패키지 탭](media/environments/environments-pip-tab-2019.png)
::: moniker-end

위의 이미지에서 볼 수 있듯이 검색 결과에는 검색어와 일치하는 여러 패키지가 표시되지만 목록의 첫 번째 항목은 **pip install \<name>** 을 직접 실행하는 명령입니다. **패키지(Conda)** 탭에 있는 경우 대신 **conda install \<name>** 을 참조하세요.

::: moniker range="vs-2017"
![conda 설치 명령을 표시하는 conda 패키지 탭](media/environments/environments-conda-tab-install.png)
::: moniker-end
::: moniker range=">=vs-2019"
![conda 설치 명령을 표시하는 conda 패키지 탭](media/environments/environments-conda-tab-install-2019.png)
::: moniker-end

두 경우 모두 패키지 이름 뒤에 있는 검색 상자에서 인수를 추가하여 설치를 사용자 지정할 수 있습니다. 인수를 포함하면 검색 결과에 **pip install** 또는 **conda install**이 표시되고, 그다음에 검색 상자의 콘텐츠가 표시됩니다.

::: moniker range="vs-2017"
![pip 및 conda 설치 명령에 인수 사용](media/environments/environments-pip-tab-arguments.png)
::: moniker-end
::: moniker range=">=vs-2019"
![pip 및 conda 설치 명령에 인수 사용](media/environments/environments-pip-tab-arguments-2019.png)
::: moniker-end

패키지를 설치하면 파일 시스템에서 환경의 *Lib* 폴더 안에 하위 폴더가 생성됩니다. 예를 들어 *c:\Python36*에 Python 3.6을 설치한 경우 패키지는 *c:\Python36\Lib*에 설치됩니다. *c:\Program Files\Anaconda3*에 Anaconda3를 설치한 경우 패키지는 *c:\Program Files\Anaconda3\Lib*에 설치됩니다. Conda 환경의 경우 패키지는 해당 환경의 폴더에 설치됩니다.

### <a name="grant-administrator-privileges-for-package-install"></a>패키지 설치에 대한 관리자 권한 부여

*c:\Program Files\Anaconda3\Lib*와 같이 파일 시스템의 보호된 영역에 있는 환경에 패키지를 설치할 때, Visual Studio에서 패키지 하위 폴더를 만들 수 있도록 권한이 상승된 `pip install`을 실행해야 합니다. 권한 상승이 요구되는 경우 Visual Studio에서 **이 환경에 대해 패키지를 설치, 업데이트 또는 제거하려면 관리자 권한이 필요할 수 있습니다.** 프롬프트가 표시됩니다.

![패키지 설치를 위한 권한 상승 프롬프트](media/environments/environments-pip-elevate.png)

**지금 권한 상승**은 단일 작업에 대한 관리 권한을 pip에 부여하며, 사용 권한에 대한 운영 체제 프롬프트에도 적용됩니다. **관리자 권한 없이 계속**을 선택하면 패키지 설치가 시도되지만, pip에서 폴더를 만들려고 할 때 실패하고 **오류: ‘C:\Program Files\Anaconda3\Lib\site-packages\png.py’를 만들 수 없음: 사용 권한이 거부되었습니다.** 등의 출력이 표시됩니다.

**패키지를 설치하거나 제거할 때 항상 권한 상승**을 선택하면 해당 환경에 대해 대화 상자가 표시되지 않습니다. 대화 상자를 다시 표시하려면 **도구** > **옵션** > **Python** > **일반**으로 이동하여 **영구적으로 숨겨진 모든 대화 상자 다시 설정** 단추를 선택합니다.

동일한 **옵션** 탭에서 **항상 관리자로 pip 실행**을 선택하여 모든 환경에 대해 대화 상자를 표시하지 않을 수도 있습니다. [옵션 - 일반 탭](python-support-options-and-settings-in-visual-studio.md#general-options)을 참조하세요.

### <a name="security-restrictions-with-older-versions-of-python"></a>이전 버전의 Python으로 보안 제한

Python 2.6, 3.1 및 3.2를 사용하는 경우 Visual Studio에서 **새 보안 제한으로 인해 이 버전의 Python에서 인터넷에서 설치가 작동하지 않을 수 있습니다.** 라는 경고가 표시됩니다.

![이전 버전의 Python을 사용한 pip 설치 제한에 대한 메시지](media/environments/environments-old-version-restriction.png)

이 경고가 표시되는 이유는 이전 버전의 Python에서 `pip install`은 패키지 소스인 pypi.org에서 패키지를 다운로드하는 데 필요한 전송 계층 보안(TLS) 1.2를 지원하지 않기 때문입니다. 사용자 지정 Python 빌드는 TLS 1.2를 지원할 수 있습니다. 이 경우 `pip install`이 작동할 수 있습니다.

[bootstrap.pypa.io](https://bootstrap.pypa.io/)에서 패키지의 적절한 *get-pip.py*를 다운로드하고 [pypi.org](https://pypi.org/)에서 수동으로 패키지를 다운로드한 다음, 해당 로컬 복사본에서 패키지를 설치할 수 있습니다.

그러나 권장 사항은 단순히 Python 2.7 또는 3.3+로 업그레이드하는 것입니다. 이 경우 경고는 표시되지 않습니다.

::: moniker range="vs-2017"
## <a name="intellisense-tab"></a>IntelliSense 탭

IntelliSense 완성 데이터베이스의 현재 상태를 보여 줍니다.

![Python 환경 IntelliSense 탭](media/environments/environments-intellisense-tab.png)

- Visual Studio 2017 버전 15.5 및 이전 버전에서 IntelliSense 완성은 해당 라이브러리에 대해 컴파일된 데이터베이스에 따라 달라집니다. 데이터베이스 빌드는 라이브러리를 설치할 때 백그라운드에서 수행되지만 시간이 걸릴 수 있으며, 코드 작성을 시작할 때 완료되지 않았을 수도 있습니다.
- Visual Studio 2017 버전 15.6 이상에서는 기본적으로 데이터베이스에 종속되지 않는 완료를 제공합니다. 이 때문에 탭 레이블이 **IntelliSense [데이터베이스 사용 안 함]** 입니다. **도구** > **옵션** > **Python** > **실험** > **환경에 새 스타일 IntelliSense 사용** 옵션을 취소하여 데이터베이스를 사용하도록 설정할 수 있습니다.

Visual Studio에서 새 환경을 검색하거나 사용자가 환경을 추가하면 라이브러리 소스 파일을 분석하여 데이터베이스 컴파일을 자동으로 시작합니다. 이 프로세스는 설치된 항목에 따라 1분에서 1시간 또는 그 이상이 소요될 수 있습니다. (예를 들어 Anaconda에는 많은 라이브러리가 함께 제공되며 데이터베이스를 컴파일하는 데 다소 시간이 소요됩니다.) 완료되면 자세한 IntelliSense를 얻게 되며 더 많은 라이브러리를 설치할 때까지 데이터베이스를 다시 새로 고치지 않아도 됩니다(**DB 새로 고침** 단추 사용).

컴파일되지 않은 데이터에 대한 라이브러리는 **!** 로 표시되며 환경의 데이터베이스가 완료되지 않은 경우 주 환경 목록에서 데이터베이스 옆에도 **!** 가 표시됩니다.

::: moniker-end

## <a name="see-also"></a>참조

- [Visual Studio에서 Python 환경 관리](managing-python-environments-in-visual-studio.md)
- [프로젝트의 인터프리터 선택](selecting-a-python-environment-for-a-project.md)
- [종속성에 대해 requirements.txt 사용](managing-required-packages-with-requirements-txt.md)
- [검색 경로](search-paths.md)
