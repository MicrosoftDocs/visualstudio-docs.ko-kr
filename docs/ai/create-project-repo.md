---
title: 리포지토리 복제
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 9bb3aa4a7aa9818f42f99860956e0e2ae73b2b7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85371588"
---
# <a name="clone-a-repository-of-python-code-in-visual-studio"></a>Visual Studio에서 Python 코드의 리포지토리 복제

[Visual Studio Tools for AI를 설치](installation.md)하면 Python 코드의 리포지토리를 쉽게 복제하고 여기에서 프로젝트를 만들 수 있습니다.

1. GitHub 리포지토리에 연결하려면 Visual Studio 설치 관리자를 실행하고 **수정**을 선택하고 **개별 구성 요소** 탭을 선택합니다. **코드 도구** 섹션으로 아래로 스크롤하고 **Visual Studio용 GitHub 확장**을 선택하고 **수정**을 선택합니다.

    ![Visual Studio 설치 관리자에서 GitHub 확장 선택](media/create-project-repo/installation-github-extension.png)

2. Visual Studio를 실행합니다.

3. **보기 > 팀 탐색기**를 선택하여 GitHub 또는 Azure DevOps에 연결하거나 리포지토리를 복제할 수 있는 **팀 탐색기** 창을 엽니다.

    ![Azure DevOps, GitHub를 표시하고 리포지토리를 복제하는 팀 탐색기 창](media/create-project-repo/team-explorer-devops.png)

4. **로컬 Git 리포지토리** 아래의 URL 필드에 `https://github.com/Microsoft/samples-for-ai`를 입력하고, 복제된 파일에 대한 폴더를 입력하고, **복제**를 선택합니다.

    > [!Tip]
    > 팀 탐색기에서 지정하는 폴더는 복제된 파일을 받을 특정 폴더입니다. `git clone` 명령과 달리 팀 탐색기에서 복제본을 만드는 것은 리포지토리의 이름으로 하위 폴더를 자동으로 만들지 않습니다.

5. 복제가 완료되면 팀 탐색기의 맨 아래에 있는 리포지토리 폴더를 두 번 클릭하여 리포지토리 대시보드로 이동합니다. **솔루션** 아래에서 **새로 만들기**를 선택합니다.

    ![팀 탐색기 창, 복제에서 새 프로젝트 만들기](media/create-project-repo/team-explorer-new-project.png)

6. 나타나는 **새 프로젝트** 대화 상자에서 "**기존 Python 코드에서**"를 선택하고, 프로젝트에 대한 이름을 지정하고, **위치**를 리포지토리와 같은 폴더로 설정하고, **확인**을 선택합니다. 표시되는 마법사에서 **마침**을 선택합니다.

7. 메뉴에서 **보기 > 솔루션 탐색기**를 선택합니다.

8. 솔루션 탐색기에서 `TensorFlow Examples> MNIST` 노드를 확장하고, `convolutional.py`를 마우스 오른쪽 단추로 클릭하고, **시작 파일로 설정**을 선택합니다. 이 단계는 Visual Studio에서 프로젝트를 실행할 때 사용해야 하는 파일을 지정합니다.

9. **Ctrl**+**F5**를 누르거나 **디버그 > 디버깅하지 않고 시작**을 선택하여 프로그램을 실행합니다. 오류가 표시되면 이전 단계에서 작업 디렉터리 설정을 다시 확인합니다.

10. 프로그램이 성공적으로 실행되면 학습 및 테스트 데이터 세트를 다운로드하기 시작한 다음, 모델을 학습하고 오류 비율을 출력합니다. 시간이 지나면 오류 비율이 감소합니다.

    ![Python MNIST 프로그램의 첫 번째 출력](media/create-project-repo/tensorflow-mnist-running.png)

   > [!NOTE]
   > Anaconda를 사용하고 누락된 numpy에 대한 오류가 발생하는 경우 [Anaconda를 사용하도록 Python 환경을 변경](../python/selecting-a-python-environment-for-a-project.md)해야 할 수 있습니다.

11. TensorBoard를 사용하여 진행률을 시각화할 수 있습니다. 프로젝트를 마우스 오른쪽 단추로 클릭하고 **TensorBoard 실행**을 클릭한 다음 출력 TensorBoard 로그의 디렉터리를 선택합니다.

   ![run tensorboard](media/create-project-repo/run-tensorboard.png)

12. 시간이 지나면 오류가 감소합니다. 즉, 성능이 개선됩니다.

   ![run tensorboard](media/create-project-repo/tensorboard.png)
