---
title: 팀 탐색기 참조
ms.date: 12/04/2018
ms.topic: reference
ms.author: kaelli
author: KathrynEE
ms.manager: jillfra
ms.openlocfilehash: b1a956579b527de9df9d24bd09dda6ae48eff961
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74538569"
---
# <a name="team-explorer-reference"></a>팀 탐색기 참조

이 문서에서는 **팀 탐색기**의 다양한 함수에 관한 Azure DevOps 문서에 대한 링크를 제공합니다.

**팀 탐색기** 도구 창을 사용하여 프로젝트를 개발하고 사용자, 팀 또는 프로젝트에 할당된 작업을 관리하기 위해 다른 팀 구성원과 코드 작업을 조정합니다. **팀 탐색기**는 Visual Studio를 Git 및 GitHub 리포지토리, TFVC(Team Foundation 버전 제어) 리포지토리 및 [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) 또는 온-프레미스 [Azure DevOps 서버](/azure/devops/index-all)(이전의 TFS로 알려짐)에 호스팅된 프로젝트와 연결합니다. 소스 코드, 작업 항목 및 빌드를 관리할 수 있습니다.

## <a name="home-page"></a>홈 페이지

[팀 탐색기](../connect-team-project.md)에서 **프로젝트에 연결**한 후 **프로젝트** 섹션에서 다음 링크를 사용할 수 있습니다.

- [리포지토리 복제](/azure/devops/repos/git/clone)
- [웹 포털](/azure/devops/project/navigation/index)
- [작업 보드](/azure/devops/boards/sprints/task-board)

**홈** 페이지는 [Git](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio) 또는 [TFVC(Team Foundation 버전 제어)](/azure/devops/repos/tfvc/overview) 리포지토리에 연결되어 있는지 여부에 따라 기능이 다릅니다.

> [!TIP]
> 두 버전 제어 시스템을 비교하려면 [프로젝트에 대한 올바른 버전 제어 선택(Azure DevOps)](/azure/devops/repos/tfvc/comparison-git-tfvc)을 참조하세요.

| Git를 사용한 **홈** 페이지 | TFVC를 사용한 **홈** 페이지 |
| - | - |
| ![Visual Studio 2019에서 Git를 포함하는 팀 탐색기 홈 페이지](media/team-explorer-reference/team-explorer-git.png) | ![Visual Studio에서 TFVC가 있는 팀 탐색기 홈 페이지](media/team-explorer-reference/team-explorer-tfvc.png) |

## <a name="changes-page-git"></a>변경 내용 페이지(Git)

[커밋으로 작업 저장](/azure/devops/repos/git/commits)을 참조하세요.

## <a name="branches-page-git"></a>분기 페이지(Git)

[분기에서 작업 만들기](/azure/devops/repos/git/branches)를 참조하세요.

## <a name="pull-requests-page-git"></a>끌어오기 요청 페이지(Git)

[끌어오기 요청으로 코드 검토](/azure/devops/repos/git/pullrequest)를 참조하세요.

## <a name="sync-page-git"></a>동기화 페이지(Git)

[가져오기 및 끌어오기로 코드 업데이트](/azure/devops/repos/git/pulling)를 참조하세요.

## <a name="tags-page-git"></a>태그 페이지(Git)

[Git 태그 작업](/azure/devops/repos/git/git-tags)을 참조하세요.

## <a name="my-work-page-tfvc"></a>내 작업 페이지(TFVC)

[작업 일시 중단/재개](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets) 및 [코드 검토](/azure/devops/repos/tfvc/day-life-alm-developer-suspend-work-fix-bug-conduct-code-review)를 참조하세요.

## <a name="pending-changes-page-tfvc"></a>보류 중인 변경 내용 페이지(TFVC)

[보류 중인 변경 내용 관리](/azure/devops/repos/tfvc/develop-code-manage-pending-changes), [보류 집합 찾기](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets) 및 [충돌 해결](/azure/devops/repos/tfvc/resolve-team-foundation-version-control-conflicts)을 참조하세요.

## <a name="source-control-explorer-page-tfvc"></a>소스 제어 탐색기 페이지(TFVC)

[파일 및 폴더 추가/보기](/azure/devops/repos/tfvc/add-files-server)를 참조하세요.

## <a name="work-items-page"></a>작업 항목 페이지

**작업 항목** 페이지에서는 [작업 항목](/azure/devops/boards/work-items/about-work-items) 쿼리를 볼 수 있습니다. 다음을 참조하세요.

- [작업 항목 추가](/azure/devops/boards/backlogs/add-work-items)
- [쿼리 편집기를 사용하여 쿼리 나열 및 관리](/azure/devops/boards/queries/using-queries)
- [쿼리 폴더 구성 및 쿼리 권한 설정](/azure/devops/boards/queries/set-query-permissions)
- [Excel에서 쿼리 열기](/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel)
- [프로젝트에서 쿼리 열기](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)
- [Outlook을 사용하여 쿼리 결과 목록을 이메일로 보내기](/azure/devops/boards/queries/share-plans)
- [Excel에서 쿼리로 보고서 만들기](/azure/devops/report/excel/create-status-and-trend-excel-reports)(TFS에만 해당)

::: moniker range=">= vs-2019"

> [!NOTE]
> Visual Studio 2019에는 새로운 [작업 항목 환경](/azure/devops/boards/work-items/set-work-item-experience-vs)이 있습니다. Visual Studio 2019에서 작업 항목을 보는 방법에 대한 자세한 내용은 [작업 항목 보기 및 추가](/azure/devops/boards/work-items/view-add-work-items)를 참조하세요.

::: moniker-end

## <a name="builds-page"></a>빌드 페이지

**빌드** 페이지에서 프로젝트에 대한 빌드 정의를 볼 수 있습니다.

다음을 참조하세요.

- [빌드 파이프라인 만들기](/azure/devops/pipelines/tasks/index)
- [빌드 보기 및 관리](/azure/devops/pipelines/overview)
- [빌드 큐 관리](/azure/devops/pipelines/agents/pools-queues)
- [Visual Studio용 CD(지속적인 업데이트) 도구 설치](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#install-continuous-delivery-cd-tools-for-visual-studio-2017)
- [앱에 대한 CD(지속적인 업데이트) 구성 및 실행](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#configure-and-execute-continuous-delivery-cd-for-your-app)

## <a name="settings-page"></a>설정 페이지

**설정** 페이지에서 프로젝트 또는 팀 프로젝트 컬렉션에 대한 관리 기능을 구성할 수 있습니다. 다음 문서를 참조하세요.

| Project | 프로젝트 컬렉션 | 기타 |
| - | - | - |
| [보안, 그룹 멤버 자격](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[보안, 소스 제어(TFVC)](/azure/devops/organizations/security/set-git-tfvc-repository-permissions)<br/>[작업 항목 영역](/azure/devops/organizations/settings/set-area-paths)<br/>[작업 항목 반복](/azure/devops/organizations/settings/set-iteration-paths-sprints)<br/>[포털 설정](/azure/devops/report/sharepoint-dashboards/configure-or-add-a-project-portal)<br/>[프로젝트 경고](/azure/devops/notifications/howto-manage-team-notifications) | [보안, 그룹 멤버 자격](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[소스 제어(TFVC)](/azure/devops/repos/tfvc/decide-between-using-local-server-workspace)<br/>[프로세스 템플릿 관리자](/azure/devops/boards/work-items/guidance/manage-process-templates) | [Git 글로벌 설정](/azure/devops/repos/git/git-config)<br/>[Git 리포지토리 설정](/azure/devops/repos/git/git-config) |

## <a name="see-also"></a>참고 항목

- [팀 탐색기의 프로젝트에 연결](../../ide/connect-team-project.md)