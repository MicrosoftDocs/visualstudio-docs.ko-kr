---
title: 프로젝트에 대한 Python 인터프리터 선택
description: 특정 프로젝트에 적용할 Python 환경(Anaconda 및 가상 환경 포함)을 구체적으로 선택할 수 있습니다.
ms.date: 03/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 46b0a8005ea76445a1d6205c8635963dbaedd0d4
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90097036"
---
# <a name="how-to-select-a-python-environment-for-a-project"></a>프로젝트에 대한 Python 인터프리터 선택하는 방법

Python 프로젝트의 모든 코드는 글로벌 Python 환경, Anaconda 환경, 가상 환경, conda 환경과 같은 특정 환경의 컨텍스트 내에서 실행됩니다. Visual Studio는 디버깅, 가져오기 및 멤버 완성, 구문 검사, Python 버전 및 설치된 패키지 모음에 특정된 언어 서비스가 필요한 기타 모든 작업에도 해당 환경을 사용합니다.

Visual Studio의 모든 새로운 Python 프로젝트는 초기에 **솔루션 탐색기**의 **Python 환경** 노드에 표시되는 기본 전역 환경을 사용하도록 구성됩니다.

![솔루션 탐색기에 표시된 전역 기본 Python 환경](media/environments/environments-project.png)

::: moniker range="vs-2017"
프로젝트에 대한 환경을 변경하려면 **Python 환경** 노드를 마우스 오른쪽 단추로 클릭하고 **Python 환경 추가/제거**를 선택합니다. 전역, 가상 및 Conda 환경이 포함되는 표시된 목록에서 **Python 환경** 노드 아래에 표시하려는 모든 항목을 선택합니다.

![Python 환경 추가/제거 대화 상자](media/environments/environments-add-remove.png)

**확인**을 선택하면 선택한 모든 환경이 **Python 환경** 노드 아래에 표시됩니다. 현재 활성화된 환경은 굵게 표시됩니다.

![솔루션 탐색기에 표시된 여러 Python 환경](media/environments/environments-project-multiple.png)

다른 환경을 신속하게 활성화하려면 환경 이름을 마우스 오른쪽 단추로 클릭하고 **환경 활성화**를 선택합니다. 선택 사항은 프로젝트와 함께 저장되고 나중에 프로젝트를 열 때마다 해당 환경이 활성화됩니다. **Python 환경 추가/제거** 대화 상자에서 모든 옵션을 선택 취소하면 Visual Studio에서 전역 기본 환경을 활성화합니다.

**Python 환경** 노드의 팝업 메뉴에서는 추가 명령도 제공합니다.

| 명령 | 설명 |
| --- | --- |
| **가상 환경 추가** | 프로젝트에 새 가상 환경을 만드는 프로세스를 시작합니다. [가상 환경 만들기](#create-a-virtual-environment)를 참조하세요. |
| **기존 가상 환경 추가** | 가상 환경을 포함하는 폴더를 선택하고 **Python 환경** 아래에 있는 목록에 추가하라는 메시지가 표시되지만 활성화하지는 않습니다. [기존 가상 환경 활성화](#activate-an-existing-virtual-environment)를 참조하세요. |
| **Conda 환경 만들기** | 환경에 대한 이름을 입력하고 해당 기본 인터프리터를 지정하는 **Python 환경** *창*으로 전환합니다. [Conda 환경](managing-python-environments-in-visual-studio.md#conda-environments)을 참조하세요. |
::: moniker-end

::: moniker range=">=vs-2019"
프로젝트에 대한 환경을 변경하려면 **Python 환경** 노드를 마우스 오른쪽 단추로 클릭하고 **환경 추가**를 선택합니다. Python 도구 모음의 환경 드롭다운에서 **환경 추가**를 선택할 수도 있습니다.

**환경 추가** 대화 상자에서 **기존 환경** 탭을 선택한 후 **환경** 드롭다운 목록에서 새 환경을 선택합니다.

![환경 추가 대화 상자에서 프로젝트 환경 선택](media/environments/environments-project-2019.png)

전역 기본값 이외의 환경을 프로젝트에 이미 추가한 경우 새로 추가된 환경을 활성화해야 할 수 있습니다. **Python 환경** 노드에서 해당 환경을 마우스 오른쪽 단추로 클릭하고 **환경 활성화**를 선택하세요. 프로젝트에서 환경을 제거하려면 **제거**를 선택합니다.

![프로젝트 환경 활성화 및 제거](media/environments/environments-project-add-remove-2019.png)
::: moniker-end

## <a name="use-virtual-environments"></a>가상 환경 사용

가상 환경은 기타 전역 및 conda 환경과는 다른 특정 라이브러리 집합 및 특정 Python 인터프리터의 고유한 조합입니다. 가상 환경은 프로젝트에 특정되고 프로젝트 폴더에 유지됩니다. 해당 폴더에는 파일 시스템의 다른 곳에 있는 환경의 ‘기본 인터프리터’ 경로를 지정하는 *pyvenv.cfg* 파일과 함께, 환경의 설치된 라이브러리가 포함되어 있습니다.** (즉, 가상 환경에는 링크만 포함되고 인터프리터의 복사본이 포함되지 않습니다.)

가상 환경을 사용하는 이점은 시간이 지남에 따라 프로젝트를 개발하는 경우 가상 환경이 프로젝트의 정확한 종속성을 항상 반영한다는 점입니다. 반면에 공유 전역 환경에는 프로젝트에서 사용하는지 여부에 관계없이 여러 개의 라이브러리가 포함됩니다. 가상 환경에서 쉽게 *requirements.txt* 파일을 만들 수 있습니다. 그런 다음, 다른 개발 또는 프로덕션 컴퓨터에서 해당 종속성을 다시 설치하는 데 사용합니다. 자세한 내용은 [requirements.txt를 사용하여 필수 패키지 관리](managing-required-packages-with-requirements-txt.md)를 참조하세요.

Visual Studio에서 *requirements.txt* 파일이 포함된 프로젝트를 여는 경우 가상 환경을 다시 만드는 옵션이 자동으로 제공됩니다. Visual Studio가 설치되지 않은 컴퓨터에서 `pip install -r requirements.txt`를 사용하여 패키지를 복원할 수 있습니다.

가상 환경에 하드 코드된 기본 인터프리터 경로가 포함되어 있고, *requirements.txt*를 사용하여 환경을 다시 만들 수 있기 때문에 일반적으로 소스 제어에서 전체 가상 환경 폴더를 생략합니다.

다음 섹션에서는 프로젝트에서 기존 가상 환경을 활성화하는 방법 및 새 가상 환경을 만드는 방법에 대해 설명합니다.

Visual Studio에서 가상 환경은 **솔루션 탐색기**의 **Python 환경** 노드를 통해 다른 프로젝트에서 활성화할 수 있습니다.

가상 환경을 프로젝트에 추가하면 **Python 환경** 창에 표시됩니다. 그런 다음, 다른 환경과 같이 활성화하고 해당 패키지를 관리할 수 있습니다.

::: moniker range="vs-2017"
### <a name="create-a-virtual-environment"></a>가상 환경 만들기

다음과 같이 Visual Studio에서 직접 새 가상 환경을 만들 수 있습니다.

1. **솔루션 탐색기**에서 **Python 환경**을 마우스 오른쪽 단추로 클릭하고 **가상 환경 추가**를 선택하면 다음 대화 상자가 표시됩니다.

    ![가상 환경 만들기](media/environments/environments-add-virtual-1.png)

1. **가상 환경의 위치** 필드에서 가상 환경의 경로를 지정합니다. 이름만 지정하면 가상 환경이 해당 이름의 하위 폴더에 있는 현재 프로젝트 내에서 만들어집니다.

1. 환경을 기본 인터프리터로 선택하고 **만들기**를 선택합니다. 환경을 구성하고 필요한 패키지를 다운로드하는 동안 Visual Studio에서 진행 표시줄을 표시합니다. 완료되면 포함되는 프로젝트에 대한 **Python 환경** 창에 가상 환경이 표시됩니다.

1. 가상 환경은 기본적으로 활성화되지 않습니다. 프로젝트에 대한 가상 환경을 활성화하려면 가상 환경을 마우스 오른쪽 단추로 클릭하고 **환경 활성화**를 선택합니다.

> [!Note]
> 위치 경로가 기존 가상 환경을 나타내는 경우 Visual Studio에서 기본 인터프리터를 자동으로 검색하고(환경의 *lib* 디렉터리에 있는 *orig-prefix.txt* 파일 사용), **만들기** 단추를 **추가**로 변경합니다.
>
> 새 가상 환경을 추가할 때 *requirements.txt* 파일이 있으면 **가상 환경 추가** 대화 상자에 패키지를 자동으로 설치하는 옵션이 표시되므로 다른 컴퓨터에서 환경을 쉽게 다시 만들 수 있습니다.
>
> ![requirements.txt로 가상 환경 만들기](media/environments/environments-requirements-txt.png)
>
> 어느 쪽이든 결과는 **기존 가상 환경 추가** 명령을 사용한 것과 같습니다.

### <a name="activate-an-existing-virtual-environment"></a>기존 가상 환경 활성화

다른 곳에서 가상 환경을 이미 만든 경우 다음과 같이 프로젝트에 대해 가상 환경을 활성화할 수 있습니다.

1. **솔루션 탐색기**에서 **Python 환경**을 마우스 오른쪽 단추로 클릭하고 **기존 가상 환경 추가**를 선택합니다.

1. 표시되는 **찾아보기** 대화 상자에서 가상 환경이 포함된 폴더로 이동하여 폴더를 선택하고 **확인**을 선택합니다. Visual Studio가 해당 환경에서 *requirements.txt* 파일을 검색하는 경우 이러한 패키지를 설치할지 묻는 메시지가 표시됩니다.

1. 잠시 후에 가상 환경이 **솔루션 탐색기**의 **Python 환경** 노드 아래에 표시됩니다. 가상 환경은 기본적으로 활성화되지 않으므로 가상 환경을 마우스 오른쪽 단추로 클릭하고 **환경 활성화**를 선택합니다.
::: moniker-end

::: moniker range=">=vs-2019"
### <a name="create-a-virtual-environment"></a>가상 환경 만들기

다음과 같이 Visual Studio에서 직접 새 가상 환경을 만들 수 있습니다.

1. **솔루션 탐색기**에서 **Python 환경**을 마우스 오른쪽 단추로 클릭하고 **환경 추가**를 선택하거나 Python 도구 모음의 환경 드롭다운 목록에서 **환경 추가**를 선택합니다. 표시되는 **환경 추가** 대화 상자에서 **가상 환경** 탭을 선택합니다.

    ![환경 추가 대화 상자의 가상 환경 탭](media/environments/environments-add-virtual-1-2019.png)

1. 가상 환경의 이름을 지정하고 기본 인터프리터를 선택한 후 해당 위치를 확인합니다. 원하는 경우 **파일에서 패키지 설치** 아래에 *requirements.txt* 파일의 경로를 입력합니다.

1. 대화 상자에서 다른 옵션을 검토합니다.

    | 옵션 | 설명 |
    | --- | --- |
    | 현재 환경으로 설정 | 환경이 만들어지면 선택한 프로젝트에서 새 환경을 활성화합니다. |
    | 새 프로젝트의 기본 환경으로 설정 | Visual Studio에서 만드는 모든 새 프로젝트에서 자동으로 이 가상 환경을 설정하고 활성화합니다. 이 옵션을 사용하는 경우 가상 환경을 특정 프로젝트의 외부 위치에 배치해야 합니다.  |
    | Python 환경 창에서 보기 | 환경을 만든 후 **Python 환경** 창을 열 것인지 여부를 지정합니다. |
    | 이 환경을 전역에서 사용할 수 있도록 만들기 | 가상 환경이 글로벌 환경으로도 작동하는지 여부를 지정합니다. 이 옵션을 사용하는 경우 가상 환경을 특정 프로젝트의 외부 위치에 배치해야 합니다. |

1. 가상 환경을 완료하려면 **만들기**를 선택합니다. 환경을 구성하고 필요한 패키지를 다운로드하는 동안 Visual Studio에서 진행 표시줄을 표시합니다. 완료되면 가상 환경이 활성화되어 **솔루션 탐색기**의 **Python 환경** 노드 및 포함 프로젝트의 **Python 환경** 창에 나타납니다.

### <a name="activate-an-existing-virtual-environment"></a>기존 가상 환경 활성화

다른 곳에서 가상 환경을 이미 만든 경우 다음과 같이 프로젝트에 대해 가상 환경을 활성화할 수 있습니다.

1. **솔루션 탐색기**에서 **Python 환경**을 마우스 오른쪽 단추로 클릭하고 **환경 추가**를 선택합니다.

1. 표시되는 **찾아보기** 대화 상자에서 가상 환경이 포함된 폴더로 이동하여 폴더를 선택하고 **확인**을 선택합니다. Visual Studio가 해당 환경에서 *requirements.txt* 파일을 검색하는 경우 이러한 패키지를 설치할지 묻는 메시지가 표시됩니다.

1. 잠시 후에 가상 환경이 **솔루션 탐색기**의 **Python 환경** 노드 아래에 표시됩니다. 가상 환경은 기본적으로 활성화되지 않으므로 가상 환경을 마우스 오른쪽 단추로 클릭하고 **환경 활성화**를 선택합니다.
::: moniker-end

### <a name="remove-a-virtual-environment"></a>가상 환경 제거

1. **솔루션 탐색기**에서 가상 환경을 마우스 오른쪽 단추로 클릭하고 **제거**를 선택합니다.

1. Visual Studio에서 가상 환경을 제거하거나 삭제할지 묻는 메시지를 표시합니다. **제거**를 선택하면 프로젝트에서 사용할 수 없지만 파일 시스템에는 남아 있습니다. **삭제**를 선택하면 환경이 프로젝트에서 제거되고 파일 시스템에서 삭제됩니다. 기본 인터프리터는 영향을 받지 않습니다.

## <a name="view-installed-packages"></a>설치된 패키지 보기

솔루션 탐색기에서 특정 환경 노드를 확장하여 해당 환경에 설치된 패키지를 빠르게 확인합니다(환경이 활성 상태일 때 코드에서 해당 패키지를 가져오고 사용할 수 있음을 의미함).

![솔루션 탐색기에서 환경에 대한 Python 패키지](media/environments/environments-installed-packages.png)

::: moniker range="vs-2017"
새 패키지를 설치하려면 환경을 마우스 오른쪽 단추로 클릭하고 **Python 패키지 설치**를 선택하여 **Python 환경** 창의 적절한 **패키지** 탭으로 전환합니다. 검색 용어(대개 패키지 이름)를 입력하면 Visual Studio에서 일치하는 패키지를 표시합니다.
::: moniker-end
::: moniker range=">=vs-2019"
새 패키지를 설치하려면 환경을 마우스 오른쪽 단추로 클릭하고 **Python 패키지 관리**를 선택(또는 Python 도구 모음의 패키지 단추를 사용)하여 **Python 환경** 창의 적절한 **패키지** 탭으로 전환합니다. **패키지** 탭으로 전환된 후에는 검색 용어(대개 패키지 이름)를 입력하면 Visual Studio에서 일치하는 패키지를 표시합니다.
::: moniker-end

Visual Studio 내에서는 대부분의 환경에서 패키지(및 종속성)를 [PyPI(Python 패키지 인덱스)](https://pypi.org)에서 다운로드합니다. PyPI에서 사용 가능한 패키지를 검색할 수도 있습니다. Visual Studio의 상태 표시줄 및 출력 창에 설치에 대한 정보가 표시됩니다. 패키지를 제거하려면 패키지를 마우스 오른쪽 단추로 클릭하고 **제거**를 선택합니다.

Conda 패키지 관리자는 일반적으로 `https://repo.continuum.io/pkgs/`를 기본 채널로 사용하지만 다른 채널을 사용할 수도 있습니다. 자세한 내용은 [Manage Channels](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-channels.html)(채널 관리)(docs.conda.io)를 참조하세요.

표시된 항목은 정확하지 않을 수 있으며 설치 및 설치 제거가 안정적이지 않거나 사용 가능하지 않을 수 있음에 유의하세요. Visual Studio는 pip 패키지 관리자(가능한 경우)를 사용하며 필요할 경우 다운로드하여 설치합니다. 또한 Visual Studio는 easy_install 패키지 관리자도 사용할 수 있습니다. 명령줄에서 `pip` 또는 `easy_install`을 사용하여 설치된 패키지도 표시됩니다.

또한 Visual Studio에서는 현재 conda 환경에 패키지를 설치하기 위한 `conda` 사용을 지원하지 않음에 유의하세요. 대신 명령줄에서 `conda`를 사용합니다.

> [!Tip]
> pip에서 패키지 설치에 실패하는 일반적인 상황은 패키지가 *\*.pyd* 파일에 기본 구성 요소에 대한 소스 코드를 포함하는 경우입니다. 필요한 Visual Studio 버전이 설치되어 있지 않으면 pip에서 해당 구성 요소를 컴파일할 수 없습니다. 이 경우 표시되는 오류 메시지는 **오류: vcvarsall.bat를 찾을 수 없음**입니다. 대체로 `easy_install`은 미리 컴파일된 이진 파일을 다운로드할 수 있으며, [https://www.microsoft.com/download/details.aspx?id=44266](https://www.microsoft.com/download/details.aspx?id=44266)에서 이전 버전의 Python에 적합한 컴파일러를 다운로드할 수 있습니다. 자세한 내용은 Python 도구 팀 블로그에서 ["vcvarsallbat을 찾을 수 없는" 어려움을 해결하는 방법](https://devblogs.microsoft.com/python/unable-to-find-vcvarsall-bat/)(영문)을 참조하세요.

## <a name="see-also"></a>참조

- [Visual Studio에서 Python 환경 관리](managing-python-environments-in-visual-studio.md)
- [종속성에 대해 requirements.txt 사용](managing-required-packages-with-requirements-txt.md)
- [검색 경로](search-paths.md)
- [Python 환경 창 참조](python-environments-window-tab-reference.md)
