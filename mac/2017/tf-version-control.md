---
title: TFVC(Team Foundation 버전 제어)
description: TFVC(Team Foundation 버전 제어)를 사용하여 Mac용 Visual Studio에서 Team Foundation Server/Azure DevOps에 연결.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 06/25/2019
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.topic: troubleshooting
ms.openlocfilehash: 33d00d853c7496e23cb5cd97a0b9abbe05e3accc
ms.sourcegitcommit: 5335a9864d5747bc917ed28d4ebeade3076b10e7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85950585"
---
# <a name="connecting-to-team-foundation-version-control"></a>Team Foundation 버전 제어에 연결

> [!NOTE]
> macOS의 가장 적합한 제어 환경의 경우 TFVC(Team Foundation 버전 제어) 대신 Git을 사용하는 것이 좋습니다. Git은 Mac용 Visual Studio에서 지원되고 TFS(Team Foundation Server)/Azure DevOps에서 호스트되는 리포지토리의 기본 옵션입니다. TFS/Azure DevOps와 함께 Git을 사용하는 방법을 자세히 알아보려면 [Git 리포지토리 설정](/visualstudio/mac/set-up-git-repository)을 참조하세요.
>
> 이전에 Mac용 Visual Studio의 TFVC 확장 미리 보기 릴리스를 사용했다면 Mac용 Visual Studio 2019로 업그레이드할 때는 더 이상 지원되지 않습니다.

Azure Repos에서는 다음과 같은 두 가지 버전 제어 모델을 제공합니다. 분산된 버전 제어 시스템인 [Git](/azure/devops/repos/git/?view=azure-devops) 및 중앙 집중식 제어 시스템인 TFVC([Team Foundation 버전 제어](/azure/devops/repos/tfvc/index?view=azure-devops)).

Mac용 Visual Studio에서는 Git 리포지토리에 대한 전체 지원을 제공하지만 TFVC 작업을 위한 일부 해결 방법이 필요합니다. 현재 버전 제어에 TFVC를 사용하고 있는 경우 TFVC에서 호스트되는 소스 코드에 액세스하는 데 사용할 수 있는 몇 가지 솔루션은 다음과 같습니다.

* [그래픽 UI에 Visual Studio Code 및 Azure Repos 확장 사용](#use-visual-studio-code-and-the-azure-repos-extension)
* [TEE-CLC(Team Explorer Everywhere 명령줄 클라이언트)를 사용하여 리포지토리에 연결](#connecting-using-the-team-explorer-everywhere-command-line-client)
* [Mac용 Visual Studio에 Team Foundation 버전 제어 확장(지원되지 않음)을 사용하여 TFVC에 연결](#connect-to-tfvc-using-the-team-foundation-version-control-extension)

이 문서의 나머지 부분에서는 위에 나열된 옵션을 살펴봅니다.

## <a name="requirements"></a>요구 사항

* Mac용 Visual Studio Community, Professional 또는 Enterprise 버전 7.8 이상
* Azure DevOps Services, Team Foundation Server 2013 이상 또는 Azure DevOps Server 2018 이상
* Team Foundation 버전 제어를 사용하도록 구성된 Azure DevOps Services 또는 Team Foundation Server/Azure DevOps Server의 프로젝트

## <a name="use-visual-studio-code-and-the-azure-repos-extension"></a>Visual Studio Code 및 Azure Repos 확장 사용

그래픽 인터페이스를 사용하여 버전 제어에서 파일을 관리하려는 경우 Visual Studio Code용 Azure Repos 확장이 Microsoft에서 지원되는 솔루션을 제공합니다. 시작하려면 [Visual Studio Code](https://code.visualstudio.com)를 다운로드한 다음, [Azure Repos 확장을 구성](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team)하는 방법을 알아봅니다.

## <a name="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Team Explorer Everywhere 명령줄 클라이언트를 사용하여 연결

macOS 터미널을 능숙하게 사용할 수 있는 경우 TEE-CLC(Team Explorer Everywhere 명령줄 클라이언트)에서는 TFVC에서 소스에 연결하는 지원 방법을 제공합니다.

아래 단계에 따라 TFVC에 대한 연결을 설정하고 변경 내용을 커밋할 수 있습니다.

### <a name="setting-up-the-tee-clc"></a>TEE-CLC 설정

TEE-CLC를 사용하여 설정하는 두 가지 방법이 있습니다.

* Homebrew를 사용하여 클라이언트 설치 또는
* 클라이언트를 다운로드하고 수동으로 설치

가장 쉬운 솔루션은 macOS의 패키지 관리자인 **HomeBrew 사용**입니다. 이 방법으로 설치하려면 다음을 수행합니다.

1. macOS 터미널 애플리케이션을 시작합니다.
1. 터미널 및 [Homebrew 홈페이지](https://brew.sh/)의 지침을 사용하여 Homebrew를 설치합니다.
1. Homebrew가 설치되면 터미널에서 다음 명령을 실행합니다.`brew install tee-clc`

**TEE-CLC를 수동으로 설정**하려면 다음을 수행합니다.

1. Team Explorer Everywhere GitHub 리포지토리의 릴리스 페이지에서 [최신 버전의 tee-clc를 다운로드](https://github.com/Microsoft/team-explorer-everywhere/releases)합니다(예: 이 문서 작성 시 tee-clc-14.134.0.zip).
1. .zip의 콘텐츠를 디스크의 폴더로 추출합니다.
1. macOS 터미널 앱을 열고 `cd` 명령을 사용하여 이전 단계에서 사용한 폴더로 전환합니다.
1. 폴더 내에서 `./tf` 명령을 실행하여 명령줄 클라이언트가 실행될 수 있는지 테스트합니다. 그러면 Java 또는 기타 종속성을 설치하라는 메시지가 표시될 수 있습니다.

TEE-CLC가 설치되면 `tf eula` 명령을 실행하여 클라이언트의 라이선스 계약을 보고 동의할 수 있습니다.

마지막으로 TFS/Azure DevOps 환경에서 인증하려면 서버에서 개인용 액세스 토큰을 만들어야 합니다. [개인용 액세스 토큰을 사용하여 인증](/azure/devops/integrate/get-started/authentication/pats?view=azure-devops)하는 방법을 자세히 알아봅니다. TFVC와 함께 사용할 개인용 액세스 토큰을 만들 경우 토큰을 구성할 때 전체 액세스를 제공해야 합니다.

### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>TEE-CLC를 사용하여 리포지토리에 연결

소스 코드에 연결하려면 먼저 `tf workspace` 명령을 사용하여 작업 영역을 만들어야 합니다. 예를 들어 다음 명령은 “MyOrganization”이라는 Azure DevOps Services의 조직에 연결됩니다. 

```bash
export TF_AUTO_SAVE_CREDENTIALS=1
tf workspace -new MyWorkspace -collection:https://dev.azure.com/MyOrganization
```

`TF_AUTO_SAVE_CREDENTIALS` 환경 설정이 자격 증명을 저장하는 데 사용되므로 자격 증명을 입력하라는 메시지가 여러 번 표시되지 않습니다. 사용자 이름을 입력하라는 메시지가 표시되면 이전 섹션에서 만든 개인용 액세스 토큰을 사용하고 빈 암호를 사용합니다.

로컬 폴더에 대한 소스 파일 매핑을 만들려면 `tf workfold` 명령을 사용합니다. 다음 예제에서는 “MyRepository” TFVC 프로젝트에서 “WebApp.Services” 폴더를 매핑하고 로컬 ~/Projects/ 폴더(현재 사용자의 홈 폴더에 있는 “Projects” 폴더)로 복사되도록 설정합니다.

```bash
tf workfold -map $/MyRepository/WebApp.Services -workspace:MyWorkspace ~/Projects/
```

마지막으로 다음 명령을 사용하여 서버에서 소스 파일을 가져오고 로컬로 복사합니다.

```bash
tf get
```

### <a name="committing-changes-using-the-tee-clc"></a>TEE-CLC를 사용하여 변경 내용 커밋

Mac용 Visual Studio에서 파일을 변경한 후에는 터미널로 다시 전환하여 편집 내용을 체크 인할 수 있습니다. `tf add` 명령은 체크 인할 보류 중인 변경 사항 목록에 파일을 추가하는 데 사용되고 `tf checkin` 명령은 서버에 대한 실제 체크 인을 수행합니다. `checkin` 명령은 주석을 추가하거나 관련 작업 항목을 연결하는 매개 변수를 포함합니다. 다음 코드 조각에서 `WebApp.Services` 폴더의 모든 파일이 체크 인에 재귀적으로 추가됩니다. 그런 다음, 코드가 주석으로 체크 인되고 ID가 “42”인 작업 항목과 연결됩니다.

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

여기에 언급된 명령에 대해 자세히 알아보려면 터미널에서 다음 명령을 사용하면 됩니다.

`tf help`

## <a name="connect-to-tfvc-using-the-team-foundation-version-control-extension"></a>Team Foundation 버전 제어 확장을 사용하여 TFVC에 연결

> [!NOTE]
> macOS의 가장 적합한 제어 환경의 경우 TFVC(Team Foundation 버전 제어) 대신 Git을 사용하는 것이 좋습니다. Git은 Mac용 Visual Studio에서 지원되고 TFS(Team Foundation Server)/Azure DevOps에서 호스트되는 리포지토리의 기본 옵션입니다. TFS/Azure DevOps와 함께 Git을 사용하는 방법을 자세히 알아보려면 [Git 리포지토리 설정](/visualstudio/mac/set-up-git-repository)을 참조하세요.
>
> 이전에 Mac용 Visual Studio의 TFVC 확장 미리 보기 릴리스를 사용했다면 Mac용 Visual Studio 2019로 업그레이드할 때는 더 이상 지원되지 않습니다.

Mac용 Visual Studio 확장 갤러리에는 TFVC 연결에 대한 제한된 지원을 제공하는 Team Foundation 버전 제어 확장이 있습니다. 확장은 지원되지 않으며 여러 가지 알려진 문제가 있으므로 확장을 사용할 때 환경이 달라질 수 있습니다.

확장을 설치하려면 Mac용 Visual Studio를 시작하고 **Visual Studio > 확장** 메뉴를 선택합니다. **갤러리** 탭에서 **버전 제어 > TFS 및 Azure DevOps용 Team Foundation 버전 제어**를 선택하고 **설치...** 를 클릭합니다.

![확장 관리자](media/tfvc-install.png)

표시되는 메시지에 따라 확장을 설치합니다. 설치가 완료되면 IDE를 다시 시작합니다.

### <a name="updating-the-extension"></a>확장 업데이트

TFVC 확장에 대한 업데이트는 정기적으로 이루어집니다. 업데이트에 액세스하려면 메뉴에서 **Visual Studio > 확장...** 을 선택하고 **업데이트** 탭을 선택합니다. 목록에서 확장을 선택하고 **업데이트** 단추를 누릅니다.

다음 대화 상자에서 **설치**를 눌러 이전 패키지를 제거하고 새 패키지를 설치합니다.

### <a name="using-the-extension"></a>확장 사용

확장이 설치되면 **버전 제어 > TFS/Azure DevOps > 원격 리포지토리에서 열기...** 메뉴 항목을 선택합니다.

![확장을 여는 메뉴 항목](media/tfvc-source-control-explorer-devops.png)

VSTS 또는 Team Foundation Server를 선택하여 시작하고 **계속**을 누릅니다.

![서버와 연결](media/tfvc-choose-server-type-devops.png)

#### <a name="azure-repos-authentication"></a>Azure Repos 인증

Azure Repos에서 호스팅되는 프로젝트를 선택하면 Microsoft 계정 세부 정보를 입력하라는 메시지가 표시됩니다.

![Azure Repos를 사용하여 연결](media/tfvc-vsts-login.png)

#### <a name="tfs-authentication"></a>TFS 인증

TFS에 연결하려면 서버 세부 정보와 계정 자격 증명을 입력합니다. NTLM 인증을 사용할 도메인을 입력하고 기본 인증을 사용하려면 비워 둡니다. **서버 추가**를 선택합니다.

![TFS 서버에 로그인](media/tfvc-login.png)

### <a name="selecting-a-project"></a>프로젝트 선택

인증에 성공하면 **소스 제어에서 열기** 대화 상자에서 계정과 연결된 리포지토리 목록을 볼 수 있습니다.

![표시되는 프로젝트가 있는 소스 제어 대화 상자에서 열기](media/tfvc-vsts-projects.png)

이 대화 상자는 다음 노드로 구성됩니다.

- Azure DevOps 조직 또는 컬렉션 - 로그인할 때 사용하는 Microsoft 계정에 연결된 모든 조직이 표시됩니다.
- 프로젝트 - 각 조직 또는 컬렉션에 많은 수의 프로젝트가 포함될 수 있습니다. 프로젝트는 소스 코드, 작업 항목 및 자동화된 빌드가 호스팅되는 위치입니다.

이 시점에서 프로젝트 또는 조직의 이름으로 검색하고 필터링할 수 있습니다.

#### <a name="adding-a-new-server"></a>새 서버 추가

새 서버를 목록에 추가하려면 **소스 제어에서 열기** 대화 상자에서 **호스트 추가** 단추를 누릅니다.

![새 서버를 목록에 추가하는 강조 표시된 추가 단추](media/tfvc-add-new-server.png)

목록에서 공급자를 선택하고 자격 증명을 입력합니다.

![소스 제어 공급자에 대한 옵션을 표시하는 대화 상자](media/tfvc-add-new-creds-devops.png)

### <a name="creating-a-new-workspace"></a>새 작업 영역 만들기

프로젝트를 작업을 시작하려면 _작업 영역_이 있어야 합니다. 작업 영역이 아직 없는 경우 **소스 제어에서 열기** 대화 상자의 **작업 영역** 콤보 상자에서 작업 영역을 만들 수 있습니다.

![새 작업 영역 콤보 상자 옵션 만들기](media/tfvc-create-new-workspace.png)

새 작업 영역의 로컬 경로를 설정하고 **작업 영역 만들기**를 선택합니다.

![새 작업 영역의 이름 및 로컬 경로 입력](media/tfvc-local-workspace.png)

### <a name="using-the-source-code-explorer"></a>소스 코드 탐색기 사용

작업 영역을 만들고 프로젝트를 매핑하면 _소스 코드 탐색기_를 사용하여 작업을 시작할 수 있습니다.

소스 코드 탐색기를 열려면 **버전 제어 > TFS/Azure DevOps > 소스 제어 탐색기** 메뉴 항목을 선택합니다.

소스 코드 탐색기를 사용하면 매핑된 모든 프로젝트, 해당 파일 및 폴더를 탐색할 수 있습니다. 또한 다음과 같은 모든 기본 소스 제어 작업을 수행할 수 있습니다.

- 최신 버전 가져오기
- 특정 버전 가져오기
- 파일 체크 인 및 체크 아웃
- 파일 잠금 및 잠금 해제
- 추가, 삭제 및 파일 이름 바꾸기
- 기록 보기
- 변경 내용 비교.

이러한 작업 중 대부분은 프로젝트의 컨텍스트 작업을 통해 수행할 수 있습니다.

![프로젝트에 대한 바로 가기 메뉴 작업](media/tfvc-sourcecode-actions.png)

### <a name="managing-workspaces"></a>작업 영역 관리

[작업 영역 만들기](#creating-a-new-workspace) 섹션에서 설명한 대로 작업 영역을 아직 만들지 않은 경우 소스 코드 탐색기는 비어 있습니다.

![빈 소스 코드 탐색기](media/tfvc-setup-empty-sce.png)

로컬 작업 영역으로 원격 프로젝트를 설정하려면 다음 단계를 수행합니다.

1. 콤보 상자에서 **서버**를 선택합니다.
1. "작업 공간 없음" 및 로컬 경로가 "매핑되지 않음"을 참고합니다. **매핑되지 않음** 링크를 선택하여 **새 작업 영역 만들기** 대화 상자를 표시합니다.
1. 작업 영역의 이름을 지정한 후 **작업 폴더 추가**를 클릭하여 컴퓨터의 로컬 폴더에 프로젝트를 매핑합니다.

    ![기본 옵션을 표시하는 새 작업 영역 대화 상자 만들기](media/tfvc-workspace1.png)

1. "$" 폴더를 선택하여 서버의 모든 프로젝트를 동일한 작업 영역에 매핑하거나 개별 프로젝트를 선택하고 **확인**을 클릭합니다.

    ![모든 프로젝트를 표시하는 폴더 대화 상자 찾아보기](media/tfvc-workspace2.png)

1. 프로젝트를 매핑하려는 로컬 머신의 위치를 선택하고 **폴더 선택**을 클릭합니다.
1. **확인**을 눌러 새 작업 영역의 세부 정보 확인

    ![작업 폴더가 추가된 새 작업 영역 대화 상자 만들기](media/tfvc-workspace3.png)

작업 영역이 설정되면 소스 코드 탐색기에서 **작업 영역 관리** 단추를 클릭하여 작업 영역을 변경하거나 제거할 수 있습니다.

![작업 영역 관리](media/tfvc-workspace4.png)

## <a name="troubleshooting-and-known-issues"></a>문제 해결 및 알려진 문제

#### <a name="problems-using-basic-authentication"></a>기본 인증 사용 문제

다음 옵션을 사용하여 서버를 인증할 수 있습니다.

- Oauth
- Basic
- Ntlm

기본 인증을 사용하려면 다음 단계에 따라 Azure DevOps Services에서 **대체 인증 자격 증명**을 활성화해야 합니다.

1. Azure DevOps 조직 소유자로 로그인합니다(https:\//dev.azure.com/{organization}/{project}).

2. 조직 도구 모음에서 기어 아이콘을 선택하고 **정책**을 선택합니다.

    ![선택한 정책 설정 옵션](media/tfvc-auth2.png)

3. 애플리케이션 연결 설정을 검토합니다. 보안 정책에 따라 다음 설정을 변경합니다.

    ![선택한 정책 설정 옵션](media/tfvc-auth.png)

#### <a name="i-do-not-see-anything-in-tfvc"></a>TFVC에 아무것도 표시되지 않음

개발 머신에서 TFVC(Team Foundation 버전 제어)를 설정하려면 [작업 영역 관리](#managing-workspaces) 섹션에 설명된 대로 작업 영역을 **만들어야** 합니다.

소스 제어 탐색기에서 **작업 영역 관리** 단추를 누릅니다. 프로젝트를 개발 머신의 폴더에 매핑하는 단계를 수행합니다.

#### <a name="i-do-not-see-any--all-of-my-projects"></a>내 프로젝트 중 일부/전부가 표시되지 않음

인증 후 프로젝트 목록을 확인해야 합니다. 기본적으로 TFS 프로젝트만 표시됩니다. 다른 형식의 프로젝트를 보려면 "모든 프로젝트 보기" 상자를 선택합니다.

올바른 권한이 없는 경우 서버에 있는 프로젝트가 표시되지 않습니다.

##### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>"작업 영역을 만들 수 없습니다. 다시 시도하세요."라는 오류 메시지가 나타납니다.

[새 작업 영역 만들기](#creating-a-new-workspace)를 수행할 때 다음 조건이 충족되었는지 확인해야 합니다.

- 작업 영역 이름에 잘못된 문자를 사용하지 마세요.
- 이름은 64자 미만이어야 합니다.
- 로컬 경로는 다른 작업 영역에서 사용할 수 없습니다.

### <a name="see-also"></a>참조

- [Visual Studio를 사용하여 TFVC에서 코드 개발 및 공유(Windows에서)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)