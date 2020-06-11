---
title: Git 리포지토리 설정
description: Mac용 Visual Studio에서 Git 및 Subversion 사용
author: therealjohn
ms.author: johmil
ms.date: 05/13/2020
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.openlocfilehash: 7e9dc8728a3115368f1772287362b2a9f21a4309
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173375"
---
# <a name="set-up-a-git-repository"></a>Git 리포지토리 설정

Git은 모든 팀원이 동일한 문서를 동시에 작업할 수 있는 분산형 버전 제어 시스템입니다. 즉, 모든 파일을 포함하는 단일 서버가 있더라도 이 중앙 소스에서 리포지토리를 체크 아웃할 때마다 리포지토리 전체가 로컬 컴퓨터에 복제됩니다.

Git을 사용한 버전 제어를 제공하는 원격 호스트는 많지만 가장 일반적인 호스트는 GitHub입니다. 다음 예제에서는 GitHub 호스트를 사용하지만, Mac용 Visual Studio에서 어떤 Git 호스트를 사용해도 버전 제어를 수행할 수 있습니다.

GitHub를 사용하려면 계정을 만들고 구성한 다음, 이 문서의 단계를 수행하세요.

## <a name="creating-a-remote-repo-on-github"></a>GitHub에서 원격 리포지토리 만들기

다음 예제에서는 GitHub 호스트를 사용하지만, Mac용 Visual Studio에서 어떤 Git 호스트를 사용해도 버전 제어를 수행할 수 있습니다.

Git 리포지토리를 설정하려면 다음 단계를 수행하세요.

1. github.com에서 새 Git 리포지토리를 만듭니다.

    ![새 Git 리포지토리 만들기](media/version-control-git1-sml.png)

2. 리포지토리 이름, 설명, 개인 정보 보호를 설정합니다. 리포지토리를 초기화하지 **마세요.** .gitignore 및 라이선스를 [없음]으로 설정합니다.

    ![Git 리포지토리 세부 사항 설정](media/version-control-git2.png)

3. 다음 페이지에서는 직접 만든 리포지토리에 대한 HTTPS 또는 SSH 주소를 표시하고 복사하는 옵션을 제공합니다.

    ![주소 보기 및 복사](media/version-control-git3.png)

   Mac용 Visual Studio에서 이 리포지토리를 가리키려면 HTTPS 주소가 필요합니다.

## <a name="publishing-an-existing-project"></a>기존 프로젝트 게시

기존 프로젝트가 버전 제어에 아직 _존재하지 않는_ 경우 다음 단계를 사용해 Git에서 이를 설정합니다.

1. Mac용 Visual Studio의 Solution Pad에서 솔루션 이름을 선택합니다.

2. 메뉴 모음에서 **버전 제어 > 버전 제어에서 게시**를 선택하여 **리포지토리 복제** 대화 상자를 표시합니다.

    ![Mac용 Visual Studio에서 체크 아웃 시작](media/version-control-git4.png)

    이 메뉴 항목이 메뉴에 표시되지 않으면 솔루션 이름을 선택했는지 확인합니다.

3. **등록된 항목에서 선택** 탭을 선택하고 **추가** 단추를 누릅니다.

    ![](media/version-control-git5.png)

4. 로컬에 표시하고 싶은 리포지토리 이름을 입력하고 3단계에서 복사한 URL을 붙여넣습니다. [리포지토리 구성] 대화 상자가 다음과 같이 표시됩니다. [확인]을 누릅니다.

    ![Git 세부 사항 입력 대화 상자](media/version-control-git6.png)

    SSH를 사용하여 Git에 연결할 수도 있습니다.

5. Git에 앱을 게시하려면 리포지토리를 선택하고 **모듈 이름** 및 **메시지** 텍스트 필드가 둘 다 입력되었는지 확인합니다.

    ![Git에 프로젝트 게시](media/version-control-git7.png)

6. **확인**을 클릭한 다음 경고 대화 상자에서 **게시**를 클릭합니다.

7. **Git 자격 증명** 창에 GitHub 사용자 이름 및 암호를 입력합니다. 

> [!NOTE]
> 계정에 2단계 인증(2FA)이 사용 설정된 경우 암호 대신 사용되는 액세스 토큰을 만들어야 합니다. 액세스 토큰을 만들지 않은 경우에는 Git [액세스 토큰](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) 설명서의 단계를 따르세요.

8. 사용자 이름과 개인용 액세스 토큰을 입력하고 **확인**을 누릅니다.

    ![Git에 대한 사용자 이름 및 암호 입력](media/version-control-git9-sml.png)

9. 몇 초 후에 솔루션이 초기 커밋과 함께 게시됩니다. [버전 제어] 메뉴 항목을 찾아 게시되었는지 확인합니다. 이제 [버전 제어] 메뉴 항목이 다음과 같이 다양한 옵션으로 채워져 있어야 합니다.

    ![버전 제어 메뉴](media/version-control-git10.png)

10. 추가 변경을 시작하면 먼저 **버전 제어 > 검토 및 커밋** 메뉴를 사용하여 상태 보기를 엽니다. 변경 내용을 선택하여 커밋한 후 **푸시**를 선택하여 변경 내용을 원격 리포지토리로 푸시합니다. 이렇게 하면 github.com에서 해당하는 모든 사용자가 변경 사항을 볼 수 있습니다.

    ![원격 리포지토리에 변경 사항 푸시](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>새 프로젝트 게시

새 프로젝트 대화 상자를 사용하여 로컬 git 리포지토리로 새 프로젝트를 만들 수 있습니다. 활성화하려면 다음 스크린샷에 표시된 대로 **버전 제어에 git 사용** 확인란을 선택합니다. 이렇게 하면 리포지토리가 초기화되고 선택적 .gitignore 파일이 추가됩니다.

![git 지원으로 새 프로젝트 만들기](media/version-control-git-publish-new1.png)

새 GitHub 리포지토리로 새 로컬 리포지토리를 푸시하려면 다음 단계를 수행합니다.

> [!NOTE]
> GitHub 리포지토리를 아직 만들지 않은 경우 [GitHub에서 원격 리포지토리 만들기](#creating-a-remote-repo-on-github) 섹션을 참조하세요.

1. 메뉴 모음에서 **버전 제어 > 검토 및 커밋**으로 이동하여 첫 번째 커밋을 만듭니다.

2. 상태 탭에서 왼쪽 상단에 있는 **커밋**을 선택합니다.

3. 커밋 메시지(예: "첫 번째" 커밋)를 작성한 다음, **커밋**을 클릭합니다.

    ![git 리포지토리에 초기 변경 사항 커밋](media/version-control-git-publish-new2.png)

4. 그런 다음, 메뉴 모음에서 **버전 제어 > 분기 및 원격 관리**로 이동합니다.

5. **원격 원본** 탭으로 이동한 다음, **추가**를 클릭합니다.

6. **원격 원본** 창에서 이전에 만든 GitHub 리포지토리의 세부 정보를 추가하고 **확인**을 클릭합니다.

    ![git 리포지토리용 원격 원본 구성](media/version-control-git-publish-new3.png)

7. **Git 리포지토리 구성** 창을 닫은 다음, 메뉴 모음에서 **버전 제어 > 변경 내용 푸시**로 이동합니다.

8. **리포지토리에 푸시** 창에서 **변경 내용 푸시** 단추를 클릭합니다.

    ![원격 리포지토리에 변경 내용 푸시](media/version-control-git-publish-new4.png)

9. 메시지가 표시되면 GitHub 사용자 이름과 암호를 입력합니다.

> [!NOTE]
> 계정에 2단계 인증(2FA)이 사용 설정된 경우 암호 대신 사용되는 액세스 토큰을 만들어야 합니다. 액세스 토큰을 만들지 않은 경우에는 Git [액세스 토큰](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) 설명서의 단계를 따르세요.

Mac용 visual Studio는 이제 원격 GitHub 리포지토리에 변경 내용을 푸시합니다.

![푸시 작업이 성공적으로 완료되었습니다.](media/version-control-git11.png)

## <a name="clone-an-existing-repository"></a>기존 리포지토리 복제

로컬 머신에는 없고 원격에만 존재하는 GitHub 리포지토리로 작업해야 하는 경우가 있습니다. Mac용 Visual Studio를 사용하면 이 리포지토리를 신속하게 복제할 수 있습니다. 다음 단계를 수행하여 컴퓨터로 복제합니다.

1. 메뉴 모음에서 **버전 제어 > 리포지토리 복제**를 선택합니다.

2. **URL에 연결** 탭이 표시됩니다.

    ![세부 정보가 입력된 URL에 연결 탭](media/version-control-git13.png)

3. 원격 리포지토리의 GitHub 페이지에서 **복제 또는 다운로드** 단추를 누르고 제공된 URL을 복사합니다.

    ![표시된 GitHub URL](media/version-control-git14.png)

4. **URL에 연결** 탭에서 **URL** 입력 필드의 모든 텍스트를 바꿉니다. 그러면 2단계의 이미지에 나와 있는 것처럼 이 탭의 다른 대부분의 필드가 사용자에 맞게 채워집니다.

5. 리포지토리를 복제할 디렉터리를 입력하고 **복제**를 누릅니다.

> [!NOTE]
> 리포지토리 크기가 4GB 이상인 경우 문제가 발생할 수 있습니다.

## <a name="troubleshooting"></a>문제 해결

빈 원격 리포지토리로 프로젝트를 초기화하는 데 문제가 있을 경우 다음 단계를 시도하세요.

1. 솔루션 폴더로 이동합니다.
1. **Command + Shift + .** 키를 눌러 숨겨진 파일과 폴더를 표시합니다.
1. **.git** 폴더가 있으면 삭제합니다.
1. **gitignore** 파일이 있으면 삭제합니다.
1. **Command + Shift + .** 키를 눌러 파일과 폴더를 숨깁니다.
1. 솔루션을 Mac용 VS에서 엽니다.
1. Solution Pad에서 솔루션 노드를 선택합니다.
1. [버전 제어] 메뉴를 찾아 **버전 제어에서 게시**를 선택합니다.
1. 위의 연습 단계를 6단계부터 따라 수행합니다.

## <a name="see-also"></a>참조

- [Visual Studio의 버전 제어(Windows에서)](/visualstudio/version-control/)
