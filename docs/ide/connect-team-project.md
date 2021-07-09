---
title: 팀 탐색기의 프로젝트에 연결
description: Visual Studio에서 팀 탐색기를 사용하여 팀 구성원과 함께 프로젝트를 개발하고 관리하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 06/11/2021
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
monikerRange: <=vs-2019
ms.openlocfilehash: b45399f7a4115ce5946a67caca22ca92148e7434
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308248"
---
# <a name="connect-to-projects-in-team-explorer"></a>팀 탐색기의 프로젝트에 연결

::: moniker range="vs-2017"

**팀 탐색기** 도구 창을 사용하여 프로젝트를 개발하고 사용자, 팀 또는 프로젝트에 할당된 작업을 관리하기 위해 다른 팀 구성원과 코드 작업을 조정합니다. **팀 탐색기** 는 Visual Studio를 Git 및 GitHub 리포지토리, TFVC(Team Foundation 버전 제어) 리포지토리 및 [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) 또는 온-프레미스 [Azure DevOps 서버](/azure/devops/index-all)(이전의 TFS로 알려짐)에 호스팅된 프로젝트와 연결합니다. 소스 코드, 작업 항목 및 빌드를 관리할 수 있습니다.

::: moniker-end

::: moniker range="vs-2019"

팀 탐색기는 Visual Studio를 TFVC(Team Foundation 버전 제어) 리포지토리에 연결하고 [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) 또는 온-프레미스 [Azure DevOps 서버](/azure/devops/user-guide/about-azure-devops-services-tfs?view=azure-devops&preserve-view=true)(이전에는 TFS로 알려짐)에 호스트된 프로젝트에 연결합니다. 소스 코드, 작업 항목 및 빌드를 관리할 수 있습니다.

> [!IMPORTANT]
> Visual Studio 2019 [**버전 16.8**](/visualstudio/releases/2019/release-notes-history) 릴리스에서는 Git 버전 제어 환경이 기본적으로 설정되어 있습니다. 팀 탐색기와 어떤 차이가 있는 자세히 알아보려면 [**Git와 팀 탐색기 비교**](../version-control/git-team-explorer-feature-comparison.md) 페이지를 참조하세요.
>
> 하지만 팀 탐색기를 계속 사용하려면 **도구** > **옵션** > **환경** > **미리 보기 기능** 으로 이동한 다음 **새 Git 사용자 환경** 확인란을 토글합니다.

팀 탐색기 사용하여 프로젝트에 연결하는 방법은 사용 중인 Visual Studio 2019의 버전에 따라 다릅니다.

## <a name="in-version-168-and-later"></a>버전 16.8 이상

1. Visual Studio 2019를 엽니다.

1. 시작 창에서 **리포지토리 복제** 를 선택합니다.

   ![Visual Studio 2019 버전 16.8 이상에서 Azure DevOps의 리포지토리 복제 대화 상자 스크린샷](../ide/media/vs-2019/clone-repository.png)

1. **리포지토리 찾아보기** 섹션에서 **Azure DevOps** 를 선택합니다.

    ![Visual Studio 2019 버전 16.8 이상에서 ‘프로젝트에 연결’ 대화 상자의 ‘리포지토리 찾아보기’ 섹션 스크린샷](../ide/media/vs-2019/browse-repository-azure-devops.png)

1. 로그인 창이 표시되면 계정에 로그인합니다.

1. **프로젝트에 연결** 대화 상자에서 연결할 리포지토리를 선택한 후 **복제** 를 선택합니다.

      ![Visual Studio 2019 버전 16.8 이상에서 생성된 ‘프로젝트에 연결’ 대화 상자 스크린샷](../ide/media/vs-2019/connect-project-azure-devops.png)

      > [!TIP]
      > 연결할 리포지토리의 미리 채워진 목록이 표시되지 않으면 **Azure DevOps Server 추가** 를 선택하여 서버 URL을 입력합니다. 또는 기존 Azure DevOps Server를 추가하거나 Azure DevOps 계정을 만들 수 있는 링크를 포함하는 “서버를 찾을 수 없음” 프롬프트가 표시될 수 있습니다.

   그런 다음, Visual Studio에서 폴더 및 파일을 표시하는 **솔루션 탐색기** 를 엽니다.

1. **팀 탐색기** 탭을 선택하여 Azure DevOps 작업을 확인합니다.

      ![Visual Studio 2019 버전 16.8 이상에서 생성된 ‘팀 탐색기’ 대화 상자 스크린샷](../ide/media/vs-2019/team-explorer-azure-devops.png)

## <a name="in-version-167-and-earlier"></a>버전 16.7 이하

1. Visual Studio 2019를 엽니다.

1. 시작 창에서 **코드 복제 또는 체크 아웃** 을 선택합니다.

   ![Visual Studio 2019 버전 16.7 이전의 ‘새 프로젝트 만들기’ 창 스크린샷](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. **리포지토리 찾아보기** 섹션에서 **Azure DevOps** 를 선택합니다.

   ![Visual Studio 2019 버전 16.7 이전에서 Azure DevOps를 나열하는 ‘리포지토리 찾아보기’ 섹션이 있는 ‘코드 복제 또는 체크 아웃’ 창 스크린샷](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   로그인 창이 표시되면 계정에 로그인합니다.

1. **프로젝트에 연결** 대화 상자에서 연결할 리포지토리를 선택한 후 **복제** 를 선택합니다.

      ![Visual Studio 2019 버전 16.7 이전에서 생성된 ‘프로젝트에 연결’ 대화 상자 스크린샷](../get-started/media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > 목록 상자에 표시되는 내용은 액세스 권한이 있는 Azure DevOps 리포지토리에 따라 달라집니다.

   Visual Studio는 **팀 탐색기** 를 열고 복제가 완료되면 알림을 표시합니다.

     ![복제가 완료된 후 Visual Studio 2019 버전 16.7 이전의 팀 탐색기 창 솔루션 섹션](../get-started/media/vs-2019/clone-complete-azure-devops.png)

1. 폴더 및 파일을 보려면 **폴더 뷰 표시** 링크를 선택합니다.

     ![복제가 완료된 후 Visual Studio 2019 버전 16.7 이전에서 팀 탐색기 창의 솔루션 섹션 스크린샷](../get-started/media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio에서 **솔루션 탐색기** 를 엽니다.

1. **솔루션 및 폴더** 링크를 선택하여 열려는 솔루션 파일(특히 .sln 파일)을 검색합니다.

      ![Visual Studio 2019 버전 16.7 이전에서 팀 탐색기의 ‘솔루션 및 폴더’ 알림 스크린샷](../get-started/media/open-proj-repo-solutions-folders.png)

   리포지토리에 솔루션 파일이 없는 경우 ‘솔루션을 찾을 수 없음’ 메시지가 나타납니다. 하지만 폴더 메뉴의 어떤 파일이든 두 번 클릭하면 Visual Studio 코드 편집기에서 열 수 있습니다.

::: moniker-end

::: moniker range="vs-2017&quot;

![Visual Studio의 팀 탐색기 홈 페이지](media/team-explorer/team-explorer.png &quot;팀 탐색기 - Visual Studio의 홈 페이지.")

> [!TIP]
> Visual Studio를 열었지만 **팀 탐색기** 가 나타나지 않으면 메뉴 모음에서 **보기** > **팀 탐색기** 를 선택하거나 **Ctrl**+ **&#92;** , **Ctrl**+**M** 을 눌러 엽니다.

## <a name="connect-to-a-project-or-repository"></a>프로젝트 또는 리포지토리에 연결

**연결** 페이지에서 프로젝트 또는 리포지토리에 연결합니다.

![팀 탐색기에서 페이지 연결](media/team-explorer/connect.png "팀 탐색기 - Visual Studio의 연결 페이지.")

프로젝트에 연결하려면:

1. **연결 관리** 아이콘을 선택하여 **연결** 페이지를 엽니다.

   ![팀 탐색기에서 연결 단추 관리](media/team-explorer/manage-connections.png "팀 탐색기 - Visual Studio의 연결 관리 단추.")

1. **연결** 페이지에서 **연결 관리** > **프로젝트에 연결** 을 선택합니다.

   ![팀 탐색기의 프로젝트에 연결](media/team-explorer/connect-project.png "팀 탐색기 - Visual Studio의 프로젝트에 연결 옵션.")

> [!TIP]
> 리포지토리에서 프로젝트를 열려면 [리포지토리에서 프로젝트 열기](../get-started/tutorial-open-project-from-repo-visual-studio-2017.md)를 참조하세요. 새 프로젝트를 만들거나 프로젝트에 사용자를 추가하려면 [프로젝트 만들기(Azure DevOps)](/azure/devops/organizations/projects/create-project) 및 [프로젝트 또는 팀에 사용자 추가(Azure DevOps)](/azure/devops/organizations/security/add-users-team-project)를 참조하세요.

::: moniker-end

## <a name="see-also"></a>참조

- [Git와 팀 탐색기 나란히 비교](git-team-explorer-feature-comparison.md)
- [Visual Studio의 새로운 Git 환경](git-with-visual-studio.md)
- [팀 탐색기 참조](reference/team-explorer-reference.md)
- [프로젝트(Azure DevOps)에 연결](/azure/devops/organizations/projects/connect-to-projects)
- [Troubleshoot connecting to a project](/azure/devops/user-guide/troubleshoot-connection?view=azure-devops&preserve-view=true)(프로젝트 연결 문제 해결)
