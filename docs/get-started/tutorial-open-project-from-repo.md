---
title: '자습서: 리포지토리에서 프로젝트 열기'
description: Visual Studio를 사용하여 Git 또는 Azure DevOps 리포지토리에서 프로젝트를 여는 방법을 알아봅니다.
ms.custom: get-started
ms.date: 03/30/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3af54d663cee1ad2b2dd4e8241678b88c635d376
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "70180433"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>자습서: 리포지토리에서 프로젝트 열기

이 자습서에서는 처음으로 Visual Studio를 사용하여 리포지토리에 연결한 후 리포지토리에서 프로젝트를 엽니다.

::: moniker range="vs-2017"

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 페이지로 이동하여 체험용으로 설치합니다.

::: moniker-end

::: moniker range="vs-2019"

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads) 페이지로 이동하여 체험용으로 설치합니다.

::: moniker-end

## <a name="open-a-project-from-a-github-repo"></a>GitHub 리포지토리에서 프로젝트 열기

::: moniker range="vs-2017"

1. Visual Studio 2017을 엽니다.

1. 상단 메뉴 모음에서 **파일** > **열기** > **소스 제어에서 열기**를 선택합니다.

   **팀 탐색기 - 연결** 창이 열립니다.

    ![Visual Studio IDE 내의 팀 탐색기 창](./media/open-proj-repo-team-explorer.png)

1. **로컬 Git 리포지토리** 섹션에서 **복제**를 선택합니다.

    ![로컬 Git 리포지토리 섹션에서 복제 선택](./media/open-proj-repo-local-git-repo-clone.png)

1. ***복제할 Git 리포지토리의 URL 입력*** 상자에서 리포지토리의 URL을 입력하거나 붙여넣고 **Enter** 키를 누릅니다. (GitHub에 로그인하라는 메시지가 표시될 수 있습니다. 이 경우 GitHub에 로그인합니다.)

   Visual Studio가 리포지토리를 복제한 후에는 팀 탐색기가 닫히고 솔루션 탐색기가 열립니다. *Click on Solutions and Folders above to view a list of Solutions*(위에서 솔루션 목록을 표시할 솔루션 및 폴더를 클릭하세요.) 메시지가 표시됩니다. **솔루션 및 폴더**를 선택합니다.

   ![솔루션 탐색기에서 “솔루션 및 폴더” 선택](./media/open-proj-repo-github-solutions-folders.png)

1. 사용 가능한 솔루션 파일이 있는 경우 “솔루션 및 폴더” 플라이아웃 메뉴에 표시됩니다. 해당 파일을 선택하면 Visual Studio에서 솔루션을 엽니다.

   ![솔루션 탐색기 드롭다운 목록에서 열려는 항목 선택](./media/open-proj-repo-github-solutions-folders-picker.png)

   리포지토리에 솔루션 파일(특히 .sln 파일)이 없는 경우 플라이아웃 메뉴에 “솔루션을 찾을 수 없음”이 표시됩니다. 하지만 폴더 메뉴의 어떤 파일이든 두 번 클릭하면 Visual Studio 코드 편집기에서 열 수 있습니다.

### <a name="review-your-work"></a>작업 검토

다음 애니메이션을 보고 이전 섹션에서 완료한 작업을 확인합니다.

   ![Visual Studio를 사용하여 GitHub 리포지토리에서 프로젝트를 여는 애니메이션](./media/open-project-from-github.gif)

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio 2019를 엽니다.

1. 시작 창에서 **코드 복제 또는 체크 아웃**을 선택합니다.

   !['새 프로젝트 만들기' 창 보기](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. 리토지토리 위치를 입력한 다음, **복제**를 선택합니다.

   !['코드 복제 또는 체크 아웃' 창 보기](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio는 리포지토리에서 프로젝트를 엽니다.

1. 사용 가능한 솔루션 파일이 있는 경우 “솔루션 및 폴더” 플라이아웃 메뉴에 표시됩니다. 해당 파일을 선택하면 Visual Studio에서 솔루션을 엽니다.

   ![솔루션 탐색기 드롭다운 목록에서 열려는 항목 선택](./media/open-proj-repo-github-solutions-folders-picker.png)

   리포지토리에 솔루션 파일(특히 .sln 파일)이 없는 경우 플라이아웃 메뉴에 “솔루션을 찾을 수 없음”이 표시됩니다. 하지만 폴더 메뉴의 어떤 파일이든 두 번 클릭하면 Visual Studio 코드 편집기에서 열 수 있습니다.

::: moniker-end

## <a name="open-a-project-from-an-azure-devops-repo"></a>Azure DevOps 리포지토리에서 프로젝트 열기

::: moniker range="vs-2017"

1. Visual Studio 2017을 엽니다.

1. 상단 메뉴 모음에서 **파일** > **열기** > **소스 제어에서 열기**를 선택합니다.

   **팀 탐색기 - 연결** 창이 열립니다.

    ![Visual Studio IDE 내의 팀 탐색기 창](./media/open-proj-repo-team-explorer.png)

1. Azure DevOps 리포지토리에 연결하는 방법은 다음 두 가지입니다.

      - **호스티드 서비스 공급자** 섹션에서 **연결...** 을 선택합니다.

        ![Visual Studio IDE 내에 있는 팀 탐색기 창의 호스티드 서비스 공급자 섹션](./media/open-proj-repo-azure-devops.png)

      - **연결 관리** 드롭다운 목록에서 **프로젝트에 연결...** 을 선택합니다.

        ![Visual Studio IDE 내에 있는 팀 탐색기 창의 연결 관리 섹션](./media/open-proj-repo-azuredevops-manage-connections.png)

1. **프로젝트에 연결** 대화 상자에서 연결할 리포지토리를 선택한 후 **복제**를 선택합니다.

      ![Visual Studio에서 생성된 “프로젝트에 연결” 대화 상자](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > 목록 상자에 표시되는 내용은 액세스 권한이 있는 Azure DevOps 리포지토리에 따라 달라집니다.

1. Visual Studio가 리포지토리를 복제한 후에는 팀 탐색기가 닫히고 솔루션 탐색기가 열립니다. *Click on Solutions and Folders above to view a list of Solutions*(위에서 솔루션 목록을 표시할 솔루션 및 폴더를 클릭하세요.) 메시지가 표시됩니다. **솔루션 및 폴더**를 선택합니다.

      ![Visual Studio에 있는 팀 탐색기의 “솔루션 및 폴더” 알림](./media/open-proj-repo-solutions-folders.png)

   솔루션 파일(특히 .sln 파일)은 “솔루션 및 폴더” 플라이아웃 메뉴에 표시됩니다. 해당 파일을 선택하면 Visual Studio에서 솔루션을 엽니다.

   리포지토리에 솔루션 파일이 없는 경우 플라이아웃 메뉴에 “솔루션을 찾을 수 없음”이 표시됩니다. 하지만 폴더 메뉴의 어떤 파일이든 두 번 클릭하면 Visual Studio 코드 편집기에서 열 수 있습니다.

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio 2019를 엽니다.

1. 시작 창에서 **코드 복제 또는 체크 아웃**을 선택합니다.

   !['새 프로젝트 만들기' 창 보기](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. **리포지토리 찾아보기** 섹션에서 **Azure DevOps**를 선택합니다.

   !['코드 복제 또는 체크 아웃' 창 보기](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   로그인 창이 표시되면 계정에 로그인합니다.

1. **프로젝트에 연결** 대화 상자에서 연결할 리포지토리를 선택한 후 **복제**를 선택합니다.

      ![Visual Studio에서 생성된 “프로젝트에 연결” 대화 상자](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > 목록 상자에 표시되는 내용은 액세스 권한이 있는 Azure DevOps 리포지토리에 따라 달라집니다.

   Visual Studio는 **팀 탐색기**를 열고 복제가 완료되면 알림을 표시합니다.

     ![복제가 완료된 후 Visual Studio의 팀 탐색기 창](./media/vs-2019/clone-complete-azure-devops.png)

1. 폴더 및 파일을 보려면 **폴더 보기 표시** 링크를 선택합니다.

     ![복제가 완료된 후 Visual Studio의 팀 탐색기 창 솔루션 섹션](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio에서 **솔루션 탐색기**를 엽니다.

1. 열려는 솔루션 파일(특히 .sln 파일)을 검색하려면 **솔루션 및 폴더** 링크를 선택합니다.

      ![Visual Studio에 있는 팀 탐색기의 “솔루션 및 폴더” 알림](./media/open-proj-repo-solutions-folders.png)

   리포지토리에 솔루션 파일이 없는 경우 "솔루션을 찾을 수 없음" 메시지가 나타납니다. 하지만 폴더 메뉴의 어떤 파일이든 두 번 클릭하면 Visual Studio 코드 편집기에서 열 수 있습니다.

::: moniker-end

## <a name="next-steps"></a>다음 단계

Visual Studio로 코딩할 준비가 되면 다음 언어별 자습서를 자세히 살펴보세요.

- [Visual Studio 자습서 | **C#** ](./csharp/index.yml)
- [Visual Studio 자습서 | **Visual Basic**](./visual-basic/index.yml)
- [Visual Studio 자습서 | **C++** ](/cpp/get-started/tutorial-console-cpp)
- [Visual Studio 자습서 | **Python**](/visualstudio/python/)
- [Visual Studio 자습서 | **JavaScript**, **TypeScript** 및 **Node.js**](/visualstudio/javascript/)

## <a name="see-also"></a>참조

- [Azure DevOps Services: Get started with Azure Repos and Visual Studio](/azure/devops/repos/git/gitquickstart/)(Azure DevOps Services: Azure Repos 및 Visual Studio 시작하기)
- [Microsoft Learn: Azure DevOps 시작하기](/learn/modules/get-started-with-devops/)