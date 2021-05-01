---
title: Visual Studio 2019의 Git 환경
titleSuffix: ''
description: Visual Studio 2019의 새로운 통합 Git 환경을 활용하여 생산성을 높일 수 있는 방법을 알아봅니다.
ms.date: 04/01/2021
ms.topic: overview
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
ms.openlocfilehash: 96018a203a6a0e5d404a818817ea4e9fb7e18551
ms.sourcegitcommit: 5fb684ff8729eb118aa91ce9f049c79eeb9747b1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2021
ms.locfileid: "107920946"
---
# <a name="git-experience-in-visual-studio"></a>Visual Studio의 Git 환경

Git은 이제 Visual Studio 2019의 기본 버전 제어 환경입니다. [버전 16.6](/visualstudio/releases/2019/release-notes-v16.6)부터 피드백에 따라 기능 집합을 구축하고 반복해 왔습니다. [버전 16.8](/visualstudio/releases/2019/release-notes/) 릴리스부터 새 Git 환경은 모든 사용자에 대해 기본적으로 설정되어 있습니다.

> [!TIP]
> Git은 가장 널리 사용되는 최신 버전 제어 시스템으로, 전문 개발자와 코딩 학습자를 비롯한 모두에게 큰 도움이 될 수 있습니다. Git을 처음 사용하는 경우 https://git-scm.com/ 웹 사이트를 먼저 참조하는 것이 좋습니다. 여기에서 참고 자료, 인기 있는 온라인 설명서 및 Git 기본 사항 비디오를 찾을 수 있습니다.

## <a name="how-to-use-git-in-visual-studio"></a>Visual Studio에서 Git을 사용하는 방법

Visual Studio 2019의 새로운 Git 환경을 사용하는 방법을 안내합니다. 핵심 사항만 빠르게 확인하고 싶다면 다음 비디오를 시청하세요. <br><br>*비디오 길이:* 5분 27초

> [!VIDEO https://www.youtube.com/embed/UHrAg3iKoe0]

Visual Studio에서 Git을 사용하여 생산성을 높일 수 있는 세 가지 방법이 있습니다.

- [기존 Git 리포지토리 열기](#open-an-existing-local-repository). 코드가 이미 머신에 있는 경우 **파일** > **열기** > **프로젝트/솔루션**(또는 **폴더**)을 사용하여 코드를 엽니다. 그러면 Visual Studio에서 코드에 초기화된 Git 리포지토리가 있는지 자동으로 검색합니다.
- [새 Git 리포지토리 만들기](#create-a-new-git-repository). 코드가 Git과 연결되지 않은 경우 새 Git 리포지토리를 만들 수 있습니다.
- [기존 Git 리포지토리 복제](#clone-an-existing-git-repository). 작업하려는 코드가 머신에 없는 경우 기존 원격 리포지토리를 복제할 수 있습니다.

> [!NOTE]
> 또한 Visual Studio 2019는 [버전 16.8](/visualstudio/releases/2019/release-notes/)부터 완전히 통합된 GitHub 계정 환경을 제공합니다. 이제 키 집합에 GitHub 및 GitHub Enterprise 계정을 모두 추가할 수 있습니다. Microsoft 계정과 같은 방법으로 추가하고 활용할 수 있어 Visual Studio에서 GitHub 리소스에 더 쉽게 액세스할 수 있습니다. 자세한 내용은 [Visual Studio에서 GitHub 계정 작업](../ide/work-with-github-accounts.md) 페이지를 참조하세요.

## <a name="create-a-new-git-repository"></a>새 Git 리포지토리 만들기

코드가 Git과 연결되지 않은 경우 새 Git 리포지토리를 만들어서 시작할 수 있습니다. 이렇게 하려면 메뉴 모음에서 **Git** > **Git 리포지토리 만들기** 를 선택합니다. 그런 다음, **Git 리포지토리 만들기** 대화 상자에서 정보를 입력합니다.

:::image type="content" source="media/git-create-repository.png" alt-text="Visual Studio의 Git 리포지토리 만들기 대화 상자.":::

**Git 리포지토리 만들기** 대화 상자에서 새 리포지토리를 GitHub에 쉽게 푸시할 수 있습니다. 기본적으로 새 리포지토리는 프라이빗입니다. 즉, 사용자 자신만 해당 리포지토리에 액세스할 수 있습니다. 이 확인란의 선택을 취소하면 리포지토리는 퍼블릭이 됩니다. 즉, GitHub의 모든 사용자가 리포지토리를 볼 수 있습니다.

> [!TIP]
> 리포지토리가 퍼블릭 또는 프라이빗인지와 관계없이 팀과 함께 작업하지 않는 경우에도 코드의 원격 백업을 GitHub에 안전하게 저장하는 것이 가장 좋습니다. 이렇게 하면 사용 중인 컴퓨터가 무엇이든 해당 코드를 사용할 수 있습니다.

**로컬 전용** 옵션을 사용하여 로컬 전용 Git 리포지토리를 만들도록 선택할 수 있습니다. 또는 **기존 원격** 옵션을 사용하여 로컬 프로젝트를 Azure DevOps 또는 다른 모든 Git 공급자의 비어 있는 기존 원격 리포지토리와 연결할 수 있습니다.

## <a name="clone-an-existing-git-repository"></a>기존 Git 리포지토리 복제

Visual Studio에는 간단한 복제 환경이 포함됩니다. 복제할 리포지토리의 URL을 알고 있는 경우 **리포지토리 위치** 섹션에 URL을 붙여넣은 다음, Visual Studio에서 복제할 디스크 위치를 선택할 수 있습니다.

:::image type="content" source="media/git-clone-repository.png" alt-text="Visual Studio의 Git 리포지토리 복제 대화 상자.":::

리포지토리 URL을 모르는 경우 Visual Studio에서 기존 GitHub 또는 Azure DevOps 리포지토리로 쉽게 이동하여 해당 리포지토리를 복제할 수 있습니다.

### <a name="open-an-existing-local-repository"></a>기존 로컬 리포지토리 열기

리포지토리를 복제하거나 만든 후 Visual Studio는 Git 리포지토리를 검색하고 Git 메뉴에서 **로컬 리포지토리** 목록에 해당 리포지토리를 추가합니다. 여기에서 Git 리포지토리 간에 신속하게 액세스하고 전환할 수 있습니다.

:::image type="content" source="media/git-local-repositories.png" alt-text="Visual Studio에 있는 Git 메뉴의 로컬 리포지토리 옵션 ":::

## <a name="view-files-in-solution-explorer"></a>솔루션 탐색기에서 파일 보기

리포지토리를 복제하거나 로컬 리포지토리를 열 때 Visual Studio는 이전에 열린 솔루션 및 프로젝트를 저장하고 닫아서 해당 Git 컨텍스트로 전환합니다. 솔루션 탐색기는 Git 리포지토리 루트에 폴더를 로드하고 디렉터리 트리에서 보기 파일을 검색합니다. 여기에는 CMakeLists.txt 같은 파일이나 .sln 파일 확장명을 사용하는 파일이 포함됩니다.

Visual Studio는 솔루션 탐색기에서 로드하는 보기 파일에 따라 보기를 조정합니다.

- 단일 .sln 파일이 포함된 리포지토리를 복제하는 경우 솔루션 탐색기는 해당 솔루션을 직접 로드합니다.
- 솔루션 탐색기는 리포지토리에서 .sln 파일을 검색하지 못하면 기본적으로 폴더 보기를 로드합니다.
- 리포지토리에 둘 이상의 .sln 파일이 있는 경우 솔루션 탐색기는 선택할 수 있는 보기 목록을 표시합니다.

솔루션 탐색기 도구 모음의 **보기 전환** 단추를 사용하여 현재 열려 있는 보기와 보기 목록 간에 토글할 수 있습니다.

:::image type="content" source="media/git-solution-explorer-views.png" alt-text="Visual Studio에서 보기 전환 단추가 선택된 솔루션 탐색기.":::

## <a name="git-changes-window"></a>Git 변경 내용 창

Git은 작업할 때 리포지토리에서 파일 변경 내용을 추적하고 리포지토리의 파일을 세 가지 범주로 구분합니다. 해당 변경 내용은 명령줄에 `git status` 명령을 입력할 때 표시되는 내용과 동일합니다.

- **수정되지 않은 파일**: 해당 파일이 마지막 커밋 이후 변경되지 않았습니다.
- **수정된 파일**: 해당 파일이 마지막 커밋 이후 변경되었지만 다음 커밋을 위해 아직 스테이징하지 않았습니다.
- **스테이징된 파일**: 해당 파일에는 다음 커밋에 추가될 변경 내용이 있습니다.

작업을 수행하는 동안 Visual Studio는 **Git 변경 내용** 창의 **변경 내용** 섹션에서 프로젝트의 파일 변경 내용을 추적합니다.

:::image type="content" source="media/git-changes-window.png" alt-text="Visual Studio의 Git 변경 내용 창.":::

변경 내용을 스테이징할 준비가 되면 스테이징할 각 파일의 **+** (더하기) 단추를 클릭하거나, 파일을 마우스 오른쪽 단추로 클릭한 후 **스테이지** 를 선택합니다. **변경 내용** 섹션 위쪽에서 모두 스테이징 **+** (더하기) 단추를 사용하여 한 번 클릭으로 모든 수정된 파일을 스테이징할 수도 있습니다.

변경을 스테이징하는 경우 Visual Studio는 **스테이징된 변경 사항** 섹션을 만듭니다. **스테이징된 변경 사항** 섹션의 변경 내용만 다음 커밋에 추가됩니다. 이 작업을 수행하려면 **스테이징된 항목 커밋** 을 선택합니다. 이 동작에 해당하는 명령은 `git commit -m "Your commit message"`입니다. **–** (빼기) 단추를 클릭하여 변경 내용을 스테이징 취소할 수도 있습니다. 이 동작에 해당하는 명령은 단일 파일을 스테이징 취소하는 `git reset <directory_path>` 또는 디렉터리에 있는 모든 파일을 스테이징 취소하는 `git reset <file_path>`입니다.

또한 스테이징 영역을 건너뛰어 수정된 파일을 스테이징하지 않도록 선택할 수 있습니다. 이 경우 Visual Studio를 사용하여 변경 내용을 스테이징하지 않고도 직접 커밋할 수 있습니다. 커밋 메시지를 입력한 다음, **모두 커밋** 을 선택합니다. 이 동작에 해당하는 명령은 `git commit -a`입니다.

또한 Visual Studio는 **모두 커밋 및 푸시** 및 **모두 커밋 및 동기화** 바로 가기를 사용하여 한 번 클릭으로 쉽게 커밋하고 동기화할 수 있습니다. **변경 내용** 및 **스테이징된 변경 사항** 섹션에 있는 파일을 두 번 클릭하면 수정되지 않은 버전의 파일과 한 줄씩 비교를 확인할 수 있습니다.

:::image type="content" source="media/git-file-version-compare.png" alt-text="Visual Studio에서 파일 버전의 한 줄씩 비교 ":::

> [!TIP]
> Azure DevOps 리포지토리에 연결된 경우 “#” 문자를 사용하여 Azure DevOps 작업 항목을 커밋에 연결할 수 있습니다. **팀 탐색기** > **연결 관리** 를 통해 Azure DevOps 리포지토리를 연결할 수 있습니다.

### <a name="select-an-existing-branch"></a>기존 분기 선택

Visual Studio는 **Git 변경 내용** 창 위쪽에 있는 선택기에 현재 분기를 표시합니다.

:::image type="content" source="media/git-changes-current-branch-selector.png" alt-text="Visual Studio의 Git 변경 내용 선택기 위쪽에 있는 선택기를 사용하여 볼 수 있는 현재 분기 ":::

현재 분기는 Visual Studio IDE의 오른쪽 아래에 있는 상태 표시줄에서도 사용할 수 있습니다.

:::image type="content" source="media/git-changes-current-branch-status-bar.png" alt-text="Visual Studio IDE의 오른쪽 아래에 있는 상태 표시줄을 사용하여 볼 수 있는 현재 분기 ":::

두 위치에서 모두 기존 분기 간에 전환할 수 있습니다.

### <a name="create-a-new-branch"></a>새 분기 만들기

새 분기를 만들 수도 있습니다. 이 동작에 해당하는 명령은 `git checkout -b <branchname>`입니다.

새 분기는 간단하게 분기 이름을 입력하고 기존 분기를 기반으로 만들면 됩니다.

:::image type="content" source="media/git-changes-create-new-branch.png" alt-text="Visual Studio의 새 분기 만들기 대화 상자 ":::

기존 로컬 또는 원격 분기를 기반으로 선택할 수 있습니다. **분기 체크 아웃** 확인란은 새로 만든 분기로 자동으로 전환됩니다. 이 동작에 해당하는 명령은 `git checkout -b <new-branch><existing-branch>`입니다.

## <a name="git-repository-window"></a>Git 리포지토리 창

Visual Studio에는 모든 분기, 원격 및 커밋 기록을 포함하여 리포지토리에 있는 모든 세부 정보의 통합된 보기인 새로운 **Git 리포지토리** 창이 있습니다. 메뉴 모음 또는 상태 표시줄의 **Git** 또는 **보기** 에서 직접 해당 창에 액세스할 수 있습니다.

### <a name="manage-branches"></a>분기 관리

**Git** 메뉴에서 **분기 관리** 를 선택하면 **Git 리포지토리** 창에 분기 트리 뷰가 표시됩니다. 왼쪽 창에서 마우스 오른쪽 단추 클릭 상황에 맞는 메뉴를 사용하여 분기를 체크 아웃하고, 새 분기를 만들고, 병합, 다시 지정, cherry-pick 등을 수행할 수 있습니다. 분기를 클릭하면 오른쪽 창에서 해당 커밋 기록의 미리 보기를 볼 수 있습니다.

### <a name="incoming-and-outgoing-commits"></a>들어오는 커밋 및 나가는 커밋

분기를 페치할 때 **Git 변경 내용** 창에는 원격 분기에서 풀하지 않은 커밋 수를 표시하는 분기 드롭다운 아래에 표시기가 있습니다. 해당 표시기는 푸시되지 않은 로컬 커밋 수도 보여 줍니다.

:::image type="content" source="media/git-repo-drop-down-indicator.png" alt-text="Visual Studio의 표시기 드롭다운 UI 요소를 보여 주는 Git 변경 내용 창 ":::

해당 표시기는 **Git 리포지토리** 창에서 해당 분기의 커밋 기록으로 이동하는 링크로도 작동합니다. 이제 기록의 맨 위에 들어오는 커밋과 나가는 커밋의 세부 정보가 표시됩니다. 여기에서 커밋을 풀 또는 푸시하도록 결정할 수도 있습니다.

:::image type="content" source="media/git-branch-commit-history.png" alt-text="Visual Studio에서 분기의 커밋 기록을 보여 주는 Git 리포지토리 창 ":::

#### <a name="commit-details"></a>커밋 정보

**커밋** 을 두 번 클릭하면 Visual Studio는 별도 도구 창에서 해당 세부 정보를 엽니다. 여기에서 커밋을 되돌리거나, 커밋을 다시 설정하거나, 커밋 메시지를 수정하거나, 커밋에 태그를 만들 수 있습니다. 커밋에서 변경된 파일을 클릭하면 Visual Studio는 커밋 및 해당 부모의 **Diff** 뷰를 나란히 엽니다.

:::image type="content" source="media/git-branch-commit-details.png" alt-text="Visual Studio의 커밋 정보 대화 상자 ":::

## <a name="handle-merge-conflicts"></a>병합 충돌 처리

두 명의 개발자가 파일에서 같은 줄을 수정하는데 Git이 어떤 것이 올바른지 자동으로 알 수 없는 경우 병합 중에 충돌이 발생할 수 있습니다. Git은 병합을 중지하고 충돌 상태에 있음을 알려 줍니다.

Visual Studio를 사용하면 병합 충돌을 쉽게 파악하고 해결할 수 있습니다. 먼저 **Git 리포지토리** 창의 위쪽에는 금색 정보 표시줄이 표시됩니다.

:::image type="content" source="media/git-merge-conflict-gold-bar.png" alt-text="Visual Studio의 '병합이 완료되었지만 충돌 발생' 메시지 ":::

**Git 변경 내용** 창에는 ‘병합이 진행 중이지만 충돌 발생’ 메시지와 그 아래 별도 섹션에 병합되지 않은 파일이 표시됩니다.

:::image type="content" source="media/git-merge-progress-conflicts-message.png" alt-text="Visual Studio의 '병합이 진행 중이지만 충돌 발생' 메시지 ":::

그러나 두 창이 모두 열려 있지 않고 병합 충돌이 있는 파일로 이동하는 경우에는 다음 텍스트를 검색할 필요가 없습니다.

```bash
    <<<<<<< HEAD
    =======
    >>>>>>> main
```

대신, Visual Studio는 열린 파일에 충돌이 있음을 나타내는 금색 정보 표시줄을 페이지 위쪽에 표시합니다. 그런 다음, 링크를 클릭하여 **병합 편집기** 를 열 수 있습니다.

:::image type="content" source="media/git-merge-conflict-gold-info-bar.png" alt-text="Visual Studio의 ‘파일에 병합 충돌이 포함됨’ 메시지 스크린샷 ":::

### <a name="the-merge-editor"></a>병합 편집기

Visual Studio의 병합 편집기는 들어오는 변경 내용, 현재 변경 내용 및 병합 결과를 표시하는 3방향 병합 도구입니다. **병합 편집기** 의 맨 위에 있는 도구 모음을 사용하여 파일에서 충돌 및 자동 병합된 차이 간에 이동할 수 있습니다.

:::image type="content" source="media/git-merge-editor.png" alt-text="Visual Studio의 병합 편집기 ":::

또한 토글을 사용하여 차이를 표시하거나 숨기고, 단어 차이를 표시하거나 숨기고, 레이아웃을 사용자 지정할 수 있습니다. 각 측면의 위쪽에는 한쪽 또는 다른 쪽의 모든 변경 내용을 가져오는 데 사용할 수 있는 확인란이 있습니다. 하지만 개별 변경 내용을 가져오려면 양쪽에서 충돌하는 줄의 왼쪽에 있는 확인란을 클릭하면 됩니다. 마지막으로, 충돌 해결을 완료하면 병합 편집기에서 **병합 수락** 단추를 선택할 수 있습니다. 그런 다음, 커밋 메시지를 작성하고 변경 내용을 커밋하여 해결을 완료합니다.

## <a name="personalize-your-git-settings"></a>Git 설정 개인 설정

전역 수준뿐만 아니라 리포지토리 수준에서 Git 설정을 개인 설정하고 사용자 지정하려면 메뉴 모음에서 **Git** > **설정** 으로 이동하거나 메뉴 모음에서 **도구** > **옵션** > **소스 제어** 로 이동합니다. 그런 다음, 원하는 옵션을 선택합니다.

:::image type="content" source="media/git-options-settings.png" alt-text="Visual Studio IDE에서 개인 설정 및 사용자 지정 설정을 선택할 수 있는 옵션 대화 상자 ":::

## <a name="how-to-use-the-full-team-explorer-experience-in-visual-studio"></a>Visual Studio에서 전체 팀 탐색기 환경을 사용하는 방법

새 Git 환경은 [버전 16.8](/visualstudio/releases/2019/release-notes/)부터 Visual Studio 2019의 기본 버전 제어 시스템입니다. 그러나 이 기능을 해제하려는 경우 해제할 수 있습니다. **도구** > **옵션** > **환경** > **미리 보기 기능** 으로 이동한 다음, **새 Git 사용자 환경** 확인란을 토글합니다. 그러면 Git용 팀 탐색기 환경으로 다시 전환됩니다.

:::image type="content" source="media/git-opt-new-user-experience.png" alt-text="Visual Studio 옵션 대화 상자의 미리 보기 기능 섹션 ":::

## <a name="whats-next"></a>다음 단계

이재 새 Git 버전 제어 환경은 Visual Studio 2019 [버전 16.8](/visualstudio/releases/2019/release-notes/)에서 기본적으로 설정되어 있지만 환경을 개선하기 위해 기능을 계속 추가하고 있습니다. 미리 보기 릴리스에서 Git 환경의 새 업데이트를 확인하려는 경우 [Visual Studio Preview](https://aka.ms/vspreview/) 페이지에서 다운로드하여 설치할 수 있습니다.

> [!IMPORTANT]
> 제안 사항이 있는 경우 알려 주세요. Microsoft는 [**Developer Community**](https://aka.ms/vs-suggest) 포털을 통해 사용자와 소통하며 디자인을 결정하는 기회를 소중하게 생각합니다.

## <a name="see-also"></a>추가 정보

- Microsoft Learn의 [Visual Studio에서 Git 및 GitHub 시작](/learn/modules/visual-studio-github-push/) 자습서
- YouTube의 [Visual Studio에서 Git 시작](https://www.youtube.com/watch?v=GCZ9x3yqkyc) 동영상
- [Visual Studio의 Git 환경 릴리스 알림](https://devblogs.microsoft.com/visualstudio/announcing-the-release-of-the-git-experience-in-visual-studio/) 블로그 포스트
- YouTube의 [새 Git 환경 출시](https://www.youtube.com/watch?v=UHrAg3iKoe0&t) 동영상
- [Visual Studio 도구 상자 시리즈에서 제공: Channel 9 및 [YouTube](https://www.youtube.com/watch?v=ZiQ2LXtAJ6I&feature=youtu.be)의 새 Git 환경](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/The-New-Git-Experience) 비디오
- [Visual Studio의 Git 환경에 대한 흥미로운 새 업데이트](https://devblogs.microsoft.com/visualstudio/exciting-new-updates-to-the-git-experience-in-visual-studio/) 블로그 게시물
- [Visual Studio 2019의 향상된 Git 환경](https://devblogs.microsoft.com/visualstudio/improved-git-experience-in-visual-studio-2019/) 블로그 게시물
- [Visual Studio에서 GitHub 계정 작업](../ide/work-with-github-accounts.md)
- [Visual Studio 2019 릴리스 정보](/visualstudio/releases/2019/release-notes)
