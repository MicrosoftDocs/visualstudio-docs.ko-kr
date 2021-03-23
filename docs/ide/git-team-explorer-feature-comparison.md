---
title: Visual Studio에서 Git 및 팀 탐색기 나란히 비교
titleSuffix: ''
description: Visual Studio에서 새 Git 환경 대비 팀 탐색기를 사용하여 소스 제어를 관리하는 방법을 비교 및 대조합니다.
ms.date: 03/12/2021
ms.topic: how-to
ms.author: tglee
author: TerryGLee
ms.manager: jmartens
monikerRange: vs-2019
ms.openlocfilehash: 4cbd5b928bb066401c2f091863ad610fbd9f23d5
ms.sourcegitcommit: 8edb1a7e3e8eee48bf0a900f00b5ee8e08de8e1d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103482646"
---
# <a name="side-by-side-comparison-of-git-and-team-explorer"></a>Git 및 팀 탐색기 나란히 비교

Visual Studio 2019 [버전 16.8](/visualstudio/releases/2019/release-notes/)에서 새로운 Git 환경의 첫 번째 버전을 시작했습니다. 이 새로운 환경에서는 일반적인 Git 작업을 포함하는 간단한 **Git 변경 내용** 창으로 컨텍스트 전환을 줄일 수 있습니다. 또한 분기 관리 및 리포지토리 탐색과 같은 고급 Git 작업을 위한 화면 전체 **Git 리포지토리** 창을 포함합니다.

팀 탐색기 사용 중인 경우 새 Git 환경을 사용하는 방법을 설명하는 단계별 가이드는 다음과 같습니다.

> [!NOTE]
> 다음 섹션에는 테이블의 열에 맞게 크기가 지정되는 스크린샷이 포함됩니다. 각 스크린샷을 클릭하여 더 큰 버전을 볼 수 있습니다. (터치 스크린 디바이스를 사용 중인 경우 각 스크린샷을 탭하여 더 큰 버전을 볼 수 있습니다.)

## <a name="get-started"></a>시작

|         |팀 탐색기  |새로운 Git 환경 |
|---------|---------|---------|
|**리포지토리 복제** | :::image type="content" source="media/vs-2019/clone-repo-team-explorer-sml.png" alt-text="Visual Studio 2019에서 ‘리포지토리 복제’ 프로시저 오버레이가 포함된 팀 탐색기, 연결 창의 스크린샷" lightbox="media/vs-2019/clone-repo-team-explorer-lrg.png":::  </p>1. **연결** 페이지를 엽니다. <br> 2. **연결 관리** 를 확장합니다. <br> 3. **프로젝트에 연결** 을 선택합니다. | :::image type="content" source="media/vs-2019/clone-repo-new-git-sml.png" alt-text="Visual Studio 2019에서 ‘리포지토리 복제’ 프로시저 오버레이가 포함된 Git 메뉴의 스크린샷" lightbox="media/vs-2019/clone-repo-new-git-lrg.png":::  </p> 1. **Git** 메뉴를 엽니다. <br>2. **리포지토리 복제** 를 선택합니다. <br><br> |
|**리포지토리 간 전환**  | :::image type="content" source="media/vs-2019/switch-repos-team-explorer-sml.png" alt-text="Visual Studio 2019에서 ‘리포지토리 간 전환’ 프로시저 오버레이가 포함된 팀 탐색기, 연결 창의 스크린샷" lightbox="media/vs-2019/switch-repos-team-explorer-lrg.png":::  </p>1. **연결** 페이지를 엽니다. <br>2. **로컬 리포지토리** 목록에서 리포지토리를 선택합니다. | :::image type="content" source="media/vs-2019/switch-repos-new-git-sml.png" alt-text="Visual Studio 2019에서 ‘리포지토리 복제’ 프로시저 오버레이가 포함된 로컬 리포지토리 메뉴 항목의 스크린샷" lightbox="media/vs-2019/switch-repos-new-git-lrg.png"::: </p> 1. **Git** 메뉴를 엽니다. <br>2. **로컬 리포지토리** 목록에서 리포지토리를 선택합니다.  |
|**솔루션 열기**  |  :::image type="content" source="media/vs-2019/open-solution-team-explorer-sml.png" alt-text="Visual Studio 2019에서 ‘솔루션 열기’ 프로시저 오버레이가 포함된 팀 탐색기, 홈 창의 스크린샷" lightbox="media/vs-2019/open-solution-team-explorer-lrg.png":::</p>1. **팀 탐색기** 에서 **홈** 페이지를 엽니다. <br>2. 솔루션 목록에서 솔루션을 선택합니다.  |  :::image type="content" source="media/vs-2019/open-solution-new-git-sml.png" alt-text="Visual Studio 2019에서 ‘솔루션 열기’ 프로시저 오버레이가 포함된 솔루션 탐색기의 스크린샷" lightbox="media/vs-2019/open-solution-new-git-lrg.png":::</p>1. **솔루션 탐색기** 에서 **보기 전환** 페이지를 엽니다. <br>2. 솔루션 목록에서 솔루션을 선택합니다.  |
|**소스 제어에 솔루션 추가 및 새 리포지토리 만들기**  | :::image type="content" source="media/vs-2019/source-control-team-explorer-sml.png" alt-text="Visual Studio 2019에서 소스 제어에 추가 - 리포지토리 만들기 프로시저 오버레이가 포함된 팀 탐색기 옵션의 스크린샷 콜라주" lightbox="media/vs-2019/source-control-team-explorer-lrg.png":::</p>1. **소스 제어에 추가** 상태 표시줄 메뉴에서 **Git** 을 선택합니다. <br>2. **게시** 를 선택합니다.  | :::image type="content" source="media/vs-2019/source-control-new-git-sml.png" alt-text="Visual Studio 2019에서 ‘소스 제어에 추가 - 리포지토리 만들기’ 프로시저 오버레이가 포함된 Git 옵션의 스크린샷 콜라주" lightbox="media/vs-2019/source-control-new-git-lrg.png":::</p>1. **소스 제어에 추가** 상태 표시줄 메뉴에서 **Git** 을 선택하거나, 최상위 Visual Studio 메뉴 모음에서 **Git** > **Git 리포지토리 만들기** 를 선택합니다. <br>2. **만들기 및 푸시** 를 선택합니다. </p> **참고**: Azure DevOps에 코드를 추가하려면 기존 원격 옵션을 사용합니다. 이 경우 먼저 Azure DevOps 리포지토리를 만들어야 합니다. |
> [!TIP]
> [새 Git 환경](git-with-visual-studio.md)은 사용자가 연 리포지토리 또는 솔루션에 따라 올바른 Azure DevOps 리포지토리에 자동으로 연결되어야 합니다. 그러나 리포지토리에 수동으로 연결해야 하는 경우에도 팀 탐색기를 사용하여 연결할 수 있습니다. Visual Studio 메뉴 모음에서 **보기** > **팀 탐색기** > **연결 관리** > **연결** 을 선택합니다.

## <a name="git-changes"></a>Git 변경 내용

|         |팀 탐색기  |새로운 Git 환경 |
|---------|---------|---------|
|**커밋 및 스테이지** | :::image type="content" source="media/vs-2019/commit-stage-team-explorer-sml.png" alt-text="Visual Studio 2019에서 ‘커밋 및 스테이지’ 프로시저 오버레이가 포함된 팀 탐색기, 변경 내용 창의 스크린샷" lightbox="media/vs-2019/commit-stage-team-explorer-lrg.png":::  </p>1. 커밋 메시지를 입력합니다. <br>2. **모두 커밋** 을 선택합니다. <br>3. 특정 파일을 스테이징하려면 해당 파일을 마우스 오른쪽 단추로 클릭한 다음, **스테이지** 를 선택합니다.  | :::image type="content" source="media/vs-2019/commit-stage-new-git-sml.png" alt-text="Visual Studio 2019에서 ‘커밋 및 스테이지’ 프로시저 오버레이가 포함된 Git 변경 내용 창의 스크린샷" lightbox="media/vs-2019/commit-stage-new-git-lrg.png"::: </p>1. 커밋 메시지를 입력합니다. <br>2. **모두 커밋** 을 선택합니다. <br>3. 특정 파일을 스테이징하려면 해당 파일을 마우스로 가리킨 다음, “ **+** ” 아이콘을 클릭합니다. |
|**커밋 수정** |  :::image type="content" source="media/vs-2019/amend-commit-team-explorer-sml.png" alt-text="Visual Studio 2019에서 ‘커밋 수정’ 프로시저 오버레이가 포함된 팀 탐색기, 변경 내용 창의 스크린샷" lightbox="media/vs-2019/amend-commit-team-explorer-lrg.png":::</p>1. **작업** 드롭다운을 클릭합니다. <br>2. **이전 커밋 수정** 을 선택합니다. | :::image type="content" source="media/vs-2019/amend-commit-new-git-sml.png" alt-text="Visual Studio 2019에서 ‘커밋 수정’ 프로시저 오버레이가 포함된 Git 변경 내용 창의 스크린샷" lightbox="media/vs-2019/amend-commit-new-git-lrg.png"::: </p>1. **수정** 확인란을 클릭합니다. <br>2. **모두 커밋** 을 클릭하여 업데이트를 커밋합니다.  |
|**변경 내용 스태시** | :::image type="content" source="media/vs-2019/stash-change-team-explorer-sml.png" alt-text="Visual Studio 2019에서 ‘변경 내용 스태시’ 프로시저 오버레이가 포함된 팀 탐색기, 변경 내용 창의 스크린샷" lightbox="media/vs-2019/stash-change-team-explorer-lrg.png":::</p>1. **스태시** 드롭다운을 클릭합니다. <br>2. 관련 **스태시** 옵션을 선택합니다. | :::image type="content" source="media/vs-2019/stash-change-new-git-sml.png" alt-text="Visual Studio 2019에서 ‘변경 내용 스태시’ 프로시저 오버레이가 포함된 Git 변경 내용 창의 스크린샷" lightbox="media/vs-2019/stash-change-new-git-lrg.png":::</p>1. **모두 커밋** 드롭다운을 클릭합니다. <br>2. 관련 **스태시** 옵션을 선택합니다. |

## <a name="synchronization"></a>동기화

|         |팀 탐색기  |새로운 Git 환경 |
|---------|---------|---------|
|**변경 내용 페치, 풀 및 푸시** | :::image type="content" source="media/vs-2019/fetch-pull-push-team-explorer-sml.png" alt-text="Visual Studio 2019에서 ‘페치, 풀 및 푸시’ 프로시저 오버레이가 포함된 팀 탐색기, 동기화 창의 스크린샷" lightbox="media/vs-2019/fetch-pull-push-team-explorer-lrg.png":::</p>1. **동기화** 페이지로 이동합니다. <br>2. 선택한 네트워크 작업을 클릭합니다. | :::image type="content" source="media/vs-2019/fetch-pull-push-new-git-sml.png" alt-text="Visual Studio 2019에서 ‘페치, 풀 및 푸시’ 프로시저 오버레이가 포함된 Git 변경 내용 창의 스크린샷" lightbox="media/vs-2019/fetch-pull-push-team-new-git-lrg.png"::: </p>1. **Git 변경 내용** 창에서 페치, 풀 및 푸시 단추를 찾습니다. <br>2. 선택한 네트워크 작업을 클릭합니다.|
|**들어오는 커밋 및 나가는 커밋 보기** | :::image type="content" source="media/vs-2019/view-commits-team-explorer-sml.png" alt-text="Visual Studio 2019에서 ‘들어오는 커밋 및 나가는 커밋 보기’ 프로시저 오버레이가 포함된 팀 탐색기, 동기화 창의 스크린샷" lightbox="media/vs-2019/view-commits-team-explorer-lrg.png"::: </p>1. **동기화** 페이지로 이동합니다. <br>2. 수신 및 발신 목록을 봅니다. | :::image type="content" source="media/vs-2019/view-commits-new-git-sml.png" alt-text="Visual Studio 2019에서 ‘들어오는 커밋 및 나가는 커밋 보기’ 프로시저 오버레이가 포함된 Git 변경 내용 창 및 Git 리포지토리 창의 스크린샷" lightbox="media/vs-2019/view-commits-new-git-lrg.png":::</p>1. **Git 변경 내용** 창에서 **발신/수신** 링크를 클릭합니다. <br>2. **Git 리포지토리** 창 위쪽에 있는 그래프 테이블의 아이콘을 사용하여 들어오는 커밋 및 나가는 커밋을 봅니다. |

## <a name="branches"></a>분기

|         |팀 탐색기  |새로운 Git 환경 |
|---------|---------|---------|
|**분기 만들기** |  :::image type="content" source="media/vs-2019/create-branch-team-explorer-sml.png" alt-text="Visual Studio 2019에서 ‘새 분기 만들기’ 프로시저 오버레이가 포함된 팀 탐색기, 분기 창의 스크린샷" lightbox="media/vs-2019/create-branch-team-explorer-lrg.png":::</p>1. **분기** 창으로 이동합니다. <br> 2. **새 분기** 를 클릭합니다. | :::image type="content" source="media/vs-2019/create-branch-new-git-sml.png" alt-text="Visual Studio 2019에서 ‘새 분기 만들기’ 프로시저 오버레이가 포함된 Git 변경 내용 창의 스크린샷" lightbox="media/vs-2019/create-branch-new-git-lrg.png"::: </p>1. **Git 변경 내용** 창에서 분기 드롭다운 목록을 클릭합니다. <br>2. **새 분기** 를 클릭합니다. |
|**원격 분기에서 최신 변경 내용 가져오기** | :::image type="content" source="media/vs-2019/sync-remote-team-explorer-sml.png" alt-text="Visual Studio 2019에서 ‘원격 분기에서 최근 변경 내용 가져오기’ 프로시저 오버레이가 포함된 팀 탐색기, 분기 창의 스크린샷" lightbox="media/vs-2019/sync-remote-team-explorer-lrg.png"::: </p>1. **분기 페이지** 로 이동합니다. <br>2. 원격 분기를 마우스 오른쪽 단추로 클릭하고 **병합 원본** 또는 **기준 주소 다시 지정 대상** 을 선택합니다.  | :::image type="content" source="media/vs-2019/sync-remote-new-git-sml.png" alt-text="Visual Studio 2019에서 ‘원격 분기에서 최근 변경 내용 가져오기’ 프로시저 오버레이가 포함된 Git 변경 내용 창의 스크린샷" lightbox="media/vs-2019/sync-remote-new-git-lrg.png":::</p>1. 분기 드롭다운 목록을 클릭합니다. <br>2. **원격** 탭에서 원격 분기를 클릭하고 **현재 분기로 병합** 또는 **현재 분기를 다음으로 다시 지정** 을 선택합니다.  |
|**분기 관리** | :::image type="content" source="media/vs-2019/manage-branches-team-explorer-sml.png" alt-text="Visual Studio 2019에서 ‘분기 관리’ 프로시저 오버레이가 포함된 팀 탐색기, 분기 창의 스크린샷" lightbox="media/vs-2019/manage-branches-team-explorer-lrg.png"::: </p>1. **분기** 창으로 이동합니다. <br>2. 관리하려는 분기를 마우스 오른쪽 단추로 클릭합니다. <br>3. 커밋을 관리할 분기의 **기록** 을 봅니다. | :::image type="content" source="media/vs-2019/manage-branches-new-git-sml.png" alt-text="Visual Studio 2019에서 분기를 관리하는 데 사용할 세 가지 UI 옵션의 스크린샷 콜라주" lightbox="media/vs-2019/manage-branches-new-git-lrg.png"::: </p>1. 다음 진입점 중 하나를 사용하여 Git 리포지토리 창으로 이동합니다. <br><br>a. 최상위 Visual Studio 메뉴에서 **Git** > **분기 관리** 를 선택합니다.<br> b. **Git 변경 내용** > **수신/발신** 을 선택합니다. <br>다. 오른쪽 아래 상태 표시줄 메뉴에서 **분기 관리** 를 선택합니다.<br> <br> 2. 최상위 **Git** > **분기 관리** 메뉴에서 다음 작업 중 하나를 수행합니다. <br><br>A. 분기를 마우스 오른쪽 단추로 클릭합니다.<br>B. 관리하려는 커밋을 여러 개 선택합니다. |

## <a name="conflict-resolution"></a>충돌 해결

|         |팀 탐색기  |새로운 Git 환경 |
|---------|---------|---------|
|**충돌이 포함된 파일 목록 액세스** | :::image type="content" source="media/vs-2019/resolve-conflicts-team-explorer-sml.png" alt-text="Visual Studio 2019에서 프로시저 오버레이가 포함된 팀 탐색기에 있는 변경 내용 창 및 충돌 해결 창의 스크린샷 콜라주" lightbox="media/vs-2019/resolve-conflicts-team-explorer-lrg.png":::</p>1. **충돌** 링크를 클릭하여 **충돌 해결** 창으로 이동합니다. <br> 2. **충돌** 목록을 사용하여 병합 충돌을 해결합니다. | :::image type="content" source="media/vs-2019/resolve-conflicts-new-git-sml.png" alt-text="Visual Studio 2019에서 ‘충돌 해결’ 프로시저 오버레이가 포함된 Git 변경 내용 창의 스크린샷" lightbox="media/vs-2019/resolve-conflicts-new-git-lrg.png"::: </p>1. **병합하는 중 충돌이 발생함** 이 표시되는지 확인합니다. <br>2. 병합 충돌이 있는 파일 목록이 **Git 변경 내용** 창의 **병합되지 않은 변경 내용** 섹션에 표시됩니다. <br>충돌을 해결합니다. |

## <a name="next-steps"></a>다음 단계

새 Git 환경에 관한 자세한 내용은 YouTube의 최신 동영상 [Visual Studio에서 Git 시작](https://www.youtube.com/watch?v=GCZ9x3yqkyc)을 참조하세요.

## <a name="see-also"></a>참조
- [Visual Studio의 새로운 Git 환경](git-with-visual-studio.md)
- [Visual Studio에서 GitHub 계정 작업](work-with-github-accounts.md)