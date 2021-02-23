---
title: '자습서: Visual Studio 2019의 리포지토리에서 프로젝트 열기'
description: Visual Studio 2019를 사용하여 Git 또는 Azure DevOps 리포지토리에서 프로젝트를 여는 방법을 알아봅니다.
ms.custom: get-started
ms.date: 02/11/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
monikerRange: vs-2019
ms.openlocfilehash: 5a637b2536c05e8f5678989f47dba61cd6ec7381
ms.sourcegitcommit: 15109ead7991f52092502518a6f4d9061cc22cd2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2021
ms.locfileid: "100335474"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>자습서: 리포지토리에서 프로젝트 열기

이 자습서에서는 처음으로 Visual Studio를 사용하여 리포지토리에 연결한 후 리포지토리에서 프로젝트를 엽니다.

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads) 페이지로 이동하여 체험용으로 설치합니다.

## <a name="open-a-project-from-a-github-repo"></a>GitHub 리포지토리에서 프로젝트 열기

Visual Studio 2019를 사용하여 GitHub 리포지토리에서 프로젝트를 여는 방법은 사용하는 버전에 따라 달라집니다. 특히 [**버전 16.8**](/visualstudio/releases/2019/release-notes/) 이상을 설치한 경우 더욱 완전히 통합된 새로운 [Visual Studio의 Git 환경](../ide/git-with-visual-studio.md)을 사용할 수 있습니다.

그러나 설치한 버전과 관계없이 언제든지 Visual Studio를 사용하여 GitHub 리포지토리에서 프로젝트를 열 수 있습니다.

#### <a name="168-and-later"></a>[16.8 이상](#tab/vs168later)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>GitHub 리포지토리를 복제하고 프로젝트 열기

1. Visual Studio 2019를 엽니다.

1. 시작 창에서 **리포지토리 복제** 를 선택합니다.

   ![Visual Studio 2019 버전 16.8 이상의 리포지토리 복제 대화 상자 스크린샷](../ide/media/vs-2019/clone-repository.png)

1. 리포지토리 위치를 입력한 다음, **복제** 를 선택합니다.

   ![Visual Studio 2019 버전 16.8 이상에서 Git 리포지토리 URL을 입력하는 리포지토리 복제 대화 상자 스크린샷](../ide/media/vs-2019/clone-repository-enter-location.png)

1. **Git 사용자 정보** 대화 상자에서 사용자 로그인 정보를 묻는 메시지가 표시될 수 있습니다. 정보를 추가하거나 제공된 기본 정보를 편집할 수 있습니다.

   ![Visual Studio 2019 버전 16.8 이상에서 계정 정보를 입력하거나 편집하는 Git 사용자 정보 대화 상자 스크린샷](../ide/media/vs-2019/git-user-information-dialog.png)

    **저장** 을 선택하여 전역 .gitconfig 파일에 정보를 추가합니다. 또는 **취소** 를 선택하여 나중에 이 작업을 수행하도록 선택할 수 있습니다.

    그런 다음, Visual Studio가 리포지토리에서 솔루션을 자동으로 로드하고 엽니다.

   ![Visual Studio 2019 버전 16.8 이상에서 솔루션 탐색기에 열려 있는 Git의 프로젝트 스크린샷](../ide/media/vs-2019/git-solution-explorer.png )

1. 리포지토리에 여러 솔루션이 포함된 경우 솔루션 탐색기에 표시됩니다. 솔루션 탐색기에서 **보기 전환** 단추를 선택하여 솔루션 목록을 볼 수 있습니다.

   ![Visual Studio 2019 버전 16.8 이상에서 보기 전환 단추가 강조 표시되고 솔루션 탐색기에 열려 있는 Git의 프로젝트 스크린샷](../ide/media/vs-2019/git-solution-explorer-switch-views.png)

   솔루션 탐색기는 **폴더 보기** 에서 루트 폴더를 열거나 열려는 솔루션 파일을 선택할 수 있는 옵션을 제공합니다.

   ![Visual Studio 2019 버전 16.8 이상에서 보기 전환 단추를 선택한 후 솔루션 탐색기에 열려 있는 Git의 .sln 파일 스크린샷](../ide/media/vs-2019/git-solution-explorer-view-solution.png)

    보기를 전환하려면 **보기 전환** 단추를 다시 선택합니다.

    > [!TIP]
    > Visual Studio IDE의 **Git** 메뉴를 사용하여 리포지토리를 복제하고 프로젝트를 열 수도 있습니다.
    >
    > ![Visual Studio 2019 버전 16.8 이상의 Git 메뉴 스크린샷](../ide/media/vs-2019/git-menu-clone-create-git-repository.png)

#### <a name="open-a-project-locally-from-a-previously-cloned-github-repo"></a>이전에 복제된 GitHub 리포지토리에서 프로젝트를 로컬에서 열기

1. Visual Studio 2019를 엽니다.

1. 시작 창에서 **프로젝트 또는 솔루션 열기** 를 선택합니다.

    Visual Studio에서 파일 탐색기 인스턴스를 열며, 여기에서 솔루션이나 프로젝트로 이동하고 이를 선택하여 열 수 있습니다.

   ![Visual Studio 2019 버전 16.8 이상의 ‘프로젝트 또는 솔루션 열기’ 창 스크린샷](../ide/media/vs-2019/open-local-project-from-cloned-repo.png)

    최근에 프로젝트 또는 솔루션을 연 경우 **최근 파일 열기** 섹션에서 선택하여 신속하게 다시 엽니다.

    > [!TIP]
    > Visual Studio IDE의 **Git** 메뉴를 사용하여 이전에 복제한 리포지토리에서 로컬 폴더 및 파일을 열 수도 있습니다.
    >
    > ![로컬 리포지토리 옵션이 확장된 Visual Studio 2019 버전 16.8 이상의 Git 메뉴 스크린샷](../ide/media/vs-2019/git-menu-local-repositories.png)

    코딩을 시작합니다.

#### <a name="167-and-earlier"></a>[16.7 이전](#tab/vs167earlier)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>GitHub 리포지토리를 복제하고 프로젝트 열기

1. Visual Studio 2019를 엽니다.

1. 시작 창에서 **코드 복제 또는 체크 아웃** 을 선택합니다.

   ![Visual Studio 2019 버전 16.7 이전의 ‘새 프로젝트 만들기’ 창 스크린샷](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. 리포지토리 위치를 입력한 다음, **복제** 를 선택합니다.

   ![Visual Studio 2019 버전 16.7 이전의 ‘코드 복제 또는 체크 아웃’ 창 스크린샷](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio는 리포지토리에서 프로젝트를 엽니다.

1. 사용 가능한 솔루션 파일이 있는 경우 “솔루션 및 폴더” 플라이아웃 메뉴에 표시됩니다. 솔루션을 선택하면 Visual Studio에서 열립니다.

   ![Visual Studio 2019 버전 16.7 이전의 솔루션 탐색기 드롭다운 목록 스크린샷](./media/open-proj-repo-github-solutions-folders-picker.png)

   리포지토리에 솔루션 파일(특히 .sln 파일)이 없는 경우 플라이아웃 메뉴에 “솔루션을 찾을 수 없음”이 표시됩니다. 하지만 폴더 메뉴의 어떤 파일이든 두 번 클릭하면 Visual Studio 코드 편집기에서 열 수 있습니다.

    코딩을 시작합니다.

---

> [!NOTE]
> Visual Studio 2017과 관련된 정보는 [Visual Studio 2017의 리포지토리에서 프로젝트 열기](tutorial-open-project-from-repo-visual-studio-2017.md) 페이지를 참조하세요.

## <a name="connect-to-an-azure-devops-server"></a>Azure DevOps 서버에 연결

Visual Studio 2019를 사용하여 Azure DevOps 서버에 연결할 때 표시되는 항목은 사용하는 버전에 따라 달라집니다. 특히 [**버전 16.8**](/visualstudio/releases/2019/release-notes/) 이상을 설치한 경우 더욱 완전히 통합된 새로운 [Visual Studio의 Git 환경](../ide/git-with-visual-studio.md)을 Visual Studio에서 사용할 수 있도록 UI가 변경되었습니다.

그러나 설치한 버전과 관계없이 언제든지 Visual Studio를 사용하여 Azure DevOps 서버에 연결할 수 있습니다.

#### <a name="168-and-later"></a>[16.8 이상](#tab/vs168later)

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

#### <a name="167-and-earlier"></a>[16.7 이전](#tab/vs167earlier)

1. Visual Studio 2019를 엽니다.

1. 시작 창에서 **코드 복제 또는 체크 아웃** 을 선택합니다.

   ![Visual Studio 2019 버전 16.7 이전의 ‘새 프로젝트 만들기’ 창 스크린샷](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. **리포지토리 찾아보기** 섹션에서 **Azure DevOps** 를 선택합니다.

   ![Visual Studio 2019 버전 16.7 이전에서 Azure DevOps를 나열하는 ‘리포지토리 찾아보기’ 섹션이 있는 ‘코드 복제 또는 체크 아웃’ 창 스크린샷](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   로그인 창이 표시되면 계정에 로그인합니다.

1. **프로젝트에 연결** 대화 상자에서 연결할 리포지토리를 선택한 후 **복제** 를 선택합니다.

      ![Visual Studio 2019 버전 16.7 이전에서 생성된 ‘프로젝트에 연결’ 대화 상자 스크린샷](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > 목록 상자에 표시되는 내용은 액세스 권한이 있는 Azure DevOps 리포지토리에 따라 달라집니다.

   Visual Studio는 **팀 탐색기** 를 열고 복제가 완료되면 알림을 표시합니다.

     ![복제가 완료된 후 Visual Studio 2019 버전 16.7 이전의 팀 탐색기 창 솔루션 섹션](./media/vs-2019/clone-complete-azure-devops.png)

1. 폴더 및 파일을 보려면 **폴더 뷰 표시** 링크를 선택합니다.

     ![복제가 완료된 후 Visual Studio 2019 버전 16.7 이전에서 팀 탐색기 창의 솔루션 섹션 스크린샷](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio에서 **솔루션 탐색기** 를 엽니다.

1. **솔루션 및 폴더** 링크를 선택하여 열려는 솔루션 파일(특히 .sln 파일)을 검색합니다.

      ![Visual Studio 2019 버전 16.7 이전에서 팀 탐색기의 ‘솔루션 및 폴더’ 알림 스크린샷](./media/open-proj-repo-solutions-folders.png)

   리포지토리에 솔루션 파일이 없는 경우 ‘솔루션을 찾을 수 없음’ 메시지가 나타납니다. 하지만 폴더 메뉴의 어떤 파일이든 두 번 클릭하면 Visual Studio 코드 편집기에서 열 수 있습니다.

---

## <a name="next-steps"></a>다음 단계

Visual Studio로 코딩할 준비가 되면 다음 언어별 자습서를 자세히 살펴보세요.

- [Visual Studio 자습서 | **C#**](./csharp/index.yml)
- [Visual Studio 자습서 | **Visual Basic**](./visual-basic/index.yml)
- [Visual Studio 자습서 | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Visual Studio 자습서 | **Python**](../python/index.yml)
- [Visual Studio 자습서 | **JavaScript**, **TypeScript** 및 **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>참조

- [Visual Studio 2017의 리포지토리에서 프로젝트 열기](tutorial-open-project-from-repo-visual-studio-2017.md)
- [Visual Studio 2019의 새로운 Git 환경](../ide/git-with-visual-studio.md)
- [Azure DevOps Services: Get started with Azure Repos and Visual Studio](/azure/devops/repos/git/gitquickstart/)(Azure DevOps Services: Azure Repos 및 Visual Studio 시작하기)
- [Microsoft Learn: Azure DevOps 시작하기](/learn/modules/get-started-with-devops/)