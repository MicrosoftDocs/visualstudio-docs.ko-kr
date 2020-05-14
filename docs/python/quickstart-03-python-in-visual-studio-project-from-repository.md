---
title: 빠른 시작 - Python 코드의 리포지토리 복제
description: 이 빠른 시작에서는 Visual Studio 팀 탐색기를 사용하는 Python koans 리포지토리를 복제하여 Visual Studio에서 Python 프로젝트를 만듭니다.
ms.date: 12/06/2018
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5d0363626748588b6f4058e197f0d6796ece51ee
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "64543146"
---
# <a name="quickstart-clone-a-repository-of-python-code-in-visual-studio"></a>빠른 시작: Visual Studio에서 Python 코드의 리포지토리 복제

[Visual Studio에 Python 지원을 설치](installing-python-support-in-visual-studio.md)하면 Visual Studio용 GitHub 확장을 추가할 수 있습니다. 확장 기능을 사용하면 Python 코드의 리포지토리를 쉽게 복제하고 IDE 내에서 프로젝트를 만들 수 있습니다. 명령줄에서 항상 리포지토리를 복제한 다음, Visual Studio에서 작업할 수 있습니다.

## <a name="install-the-github-extension-for-visual-studio"></a>Visual Studio용 GitHub 확장 설치

[!INCLUDE[install-github-extension](includes/install-github-extension.md)]

## <a name="work-with-github-in-visual-studio"></a>Visual Studio에서 GitHub 작업

1. Visual Studio를 실행합니다.

1. **보기** > **팀 탐색기**를 선택하여 GitHub 또는 Azure Repos에 연결하거나 리포지토리를 복제할 수 있는 **팀 탐색기** 창을 엽니다. (**연결** 페이지가 아래에 표시되지 않으면 해당 페이지로 이동시키는 맨 위의 도구 모음에 있는 플러그 아이콘을 선택합니다.)

    ![Azure Repos, GitHub를 표시하고 리포지토리를 복제하는 팀 탐색기 창](media/team-explorer.png)

1. **로컬 Git 리포지토리** 아래에서 **복제**를 선택한 다음, URL 필드에 `https://github.com/gregmalcolm/python_koans`를 입력하고, 복제된 파일에 대한 폴더를 입력하고, **복제** 단추를 선택합니다.

    > [!Tip]
    > **팀 탐색기**에서 지정한 폴더는 복제된 파일을 수신하는 정확한 폴더입니다. `git clone` 명령과 달리 **팀 탐색기**에서 복제본을 만드는 작업은 리포지토리의 이름으로 하위 폴더를 자동으로 만들지 않습니다.

1. 복제가 완료되면 리포지토리가 **로컬 Git 리포지토리** 목록에 나타납니다. 해당 이름을 두 번 클릭하여 **팀 탐색기**의 리포지토리 대시보드로 이동합니다.

1. **솔루션** 아래에서 **새로 만들기**를 선택합니다.

    ![팀 탐색기 창, 복제에서 새 프로젝트 만들기](media/team-explorer-new-project.png)

1. 나타나는 **새 프로젝트** 대화 상자에서 **Python** 언어로 이동(또는 “Python” 검색)하고 **기존 Python 코드에서**를 선택한 다음, 프로젝트의 이름을 지정하고 **위치**를 리포지토리와 동일한 폴더로 설정한 후 **확인**을 선택합니다. 표시되는 마법사에서 **마침**을 선택합니다.

1. 메뉴에서 **보기** > **솔루션 탐색기**를 선택합니다.

1. **솔루션 탐색기**에서 **python3** 노드를 확장하고 **contemplate_koans.py**를 마우스 오른쪽 단추로 클릭한 다음, **시작 파일로 설정**을 선택합니다. 이 단계는 Visual Studio에서 프로젝트를 실행할 때 사용해야 하는 파일을 지정합니다.

1. 메뉴에서 **프로젝트** > **Koans 속성**을 선택하고 **일반** 탭을 선택한 다음, **작업 디렉터리**를 “python3”으로 설정합니다. 기본적으로 Visual Studio는 작업 디렉터리를 시작 파일의 위치 대신 프로젝트 루트(*python3\contemplate_koans.py*, 프로젝트 속성에도 표시됨)로 설정하기 때문에 이 단계가 필요합니다. 프로그램 코드는 작업 폴더에서 *koans.txt* 파일을 찾기 때문에 이 값을 변경하지 않으면 런타임 오류가 표시됩니다.

    ![Python 프로젝트에 대한 작업 디렉터리 설정](media/projects-set-working-directory.png)

1. **Ctrl**+**F5**를 누르거나 **디버그** > **디버깅하지 않고 시작**을 선택하여 프로그램을 실행합니다. *koans.txt*에 대한 **FileNotFoundError**가 표시되면 이전 단계에서 설명한 작업 디렉터리 설정을 확인합니다.

1. 프로그램이 성공적으로 실행되면 *python3/koans/about_asserts.py*의 줄 17에 어설션 오류를 표시합니다. 이것은 의도적입니다. 프로그램은 모든 의도적인 오류를 수정하여 Python을 가르치도록 설계되었습니다. (자세한 내용은 Python Koans에 영감을 준 [Ruby Koans](https://rubykoans.com/)에 있습니다.)

    ![Python koans 프로그램의 첫 번째 출력](media/koans-output.png)

1. **솔루션 탐색기**에서 파일로 이동한 다음, 두 번 클릭하여 *python3/koans/about_asserts.py*를 엽니다. 기본적으로 줄 번호는 편집기에 표시되지 않습니다. 이를 변경하려면 **도구** > **옵션**을 선택하고 대화 상자의 맨 아래에서 **모든 설정 표시**를 선택한 다음, **텍스트 편집기** > **Python** > **일반**으로 이동하고 **줄 번호**를 선택합니다.

    ![Python 파일에 대한 줄 번호 설정](media/options-general-line-numbers.png)

1. 줄 17의 `False` 인수를 `True`로 변경하여 오류를 수정합니다. 줄은 다음과 같습니다.

    ```python
    self.assertTrue(True) # This should be True
    ```

1. 프로그램을 다시 실행합니다. Visual Studio가 오류에 대해 경고하는 경우 **예**를 사용하여 응답하고 코드를 계속 실행합니다. 그런 다음, 첫 번째 검사가 통과하고 프로그램이 다음 koan에서 중단하는지 확인합니다. 계속해서 원하는 대로 오류 및 프로그램를 수정합니다.

> [!Important]
> 이 빠른 시작에서는 GitHub에서 *python_koans* 리포지토리의 직접 복제본을 만들었습니다. 이러한 리포지토리는 직접 변경된 내용에서 해당 작성자에 의해 보호되므로 리포지토리에 대한 변경 내용을 커밋하려는 시도는 실패합니다. 실제로 개발자는 대신 고유한 GitHub 계정에 이러한 리포지토리를 포크하고, 거기에서 변경한 다음, 끌어오기 요청을 만들어 해당 변경 내용을 원래 리포지토리에 제출합니다. 고유한 포크가 있는 경우 이전에 사용된 원래 리포지토리 URL 대신 해당 URL을 사용합니다.

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [자습서: Visual Studio에서 Python 작업](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>참조

- [기존 Python 인터프리터 수동 식별](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Windows의 Visual Studio에서 Python 지원 설치 방법](installing-python-support-in-visual-studio.md)
- [설치 위치](installing-python-support-in-visual-studio.md#install-locations)
