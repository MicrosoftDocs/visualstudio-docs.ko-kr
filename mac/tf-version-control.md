---
title: TFVC(Team Foundation 버전 제어)
description: TFVC 및 macOS에 대한 문제 해결 가이드
author: jmatthiesen
ms.author: jomatthi
ms.date: 09/02/2019
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.topic: troubleshooting
ms.openlocfilehash: c51f3cd50598cd0c33b019c09f95554cc5f9058b
ms.sourcegitcommit: 5335a9864d5747bc917ed28d4ebeade3076b10e7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85950492"
---
# <a name="does-visual-studio-for-mac-support-team-foundation-version-control"></a>Mac용 Visual Studio는 Team Foundation 버전 제어를 지원하나요?

> [!CAUTION]
> Mac용 Visual Studio의 TFVC 확장 미리 보기는 Mac용 Visual Studio 2019에서 더 이상 지원되지 않습니다.


## <a name="alternative-version-control-options-in-visual-studio-for-mac"></a>Mac용 Visual Studio의 대체 버전 제어 옵션

macOS에 가장 적합한 버전 제어 환경의 경우 TFVC(Team Foundation 버전 제어) 대신 **Git**을 사용하는 것이 좋습니다. 

Git은 Mac용 Visual Studio에서 지원되고 TFS(Team Foundation Server)/Azure DevOps에서 호스트되는 리포지토리의 기본 옵션입니다. TFS/Azure DevOps와 함께 Git을 사용하는 방법을 자세히 알아보려면 [Git 리포지토리 설정](/visualstudio/mac/set-up-git-repository) 가이드를 참조하세요.

## <a name="unsupported-workarounds-for-tfvc"></a>TFVC에 대해 지원되지 않는 해결 방법

Mac용 Visual Studio는 TFVC를 공식적으로 지원하지 않지만 이 가이드의 나머지 부분에서는 macOS에서 TFVC를 사용할 몇 가지 해결 방법을 제공합니다. 현재 버전 제어에 TFVC를 사용하고 있는 경우 TFVC에서 호스트되는 소스 코드에 액세스하는 데 사용할 수 있는 몇 가지 솔루션은 다음과 같습니다.

* 옵션 1. [ 그래픽 UI에 Visual Studio Code 및 Azure Repos 확장 사용](#use-visual-studio-code-and-the-azure-repos-extension)
* 옵션 2. [TEE-CLC(Team Explorer Everywhere 명령줄 클라이언트)를 사용하여 리포지토리에 연결](#connecting-using-the-team-explorer-everywhere-command-line-client)

### <a name="option-1--use-visual-studio-code-and-the-azure-repos-extension"></a>옵션 1. <a id="use-visual-studio-code-and-the-azure-repos-extension"></a> Visual Studio Code 및 Azure Repos 확장 사용

그래픽 인터페이스를 사용하여 버전 제어에서 파일을 관리하려는 경우 Visual Studio Code용 Azure Repos 확장이 Microsoft에서 지원되는 솔루션을 제공합니다. 시작하려면 [Visual Studio Code](https://code.visualstudio.com)를 다운로드한 다음, [Azure Repos 확장을 구성](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team)하는 방법을 알아봅니다.

### <a name="option-2--connecting-using-the-team-explorer-everywhere-command-line-client"></a>옵션 2. <a id="connecting-using-the-team-explorer-everywhere-command-line-client"></a> Team Explorer Everywhere 명령줄 클라이언트를 사용하여 연결

> [!IMPORTANT]
> Team Explorer Everywhere 추가 정보에 따라 이 프로젝트는 [더 이상 유지 관리](https://github.com/microsoft/team-explorer-everywhere)되지 않습니다.

macOS 터미널을 능숙하게 사용할 수 있는 경우 TEE-CLC(Team Explorer Everywhere 명령줄 클라이언트)에서는 TFVC에서 소스에 연결하는 지원 방법을 제공합니다.

아래 단계에 따라 TFVC에 대한 연결을 설정하고 변경 내용을 커밋할 수 있습니다.

#### <a name="setting-up-the-tee-clc"></a>TEE-CLC 설정

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

#### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>TEE-CLC를 사용하여 리포지토리에 연결

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

#### <a name="committing-changes-using-the-tee-clc"></a>TEE-CLC를 사용하여 변경 내용 커밋

Mac용 Visual Studio에서 파일을 변경한 후에는 터미널로 다시 전환하여 편집 내용을 체크 인할 수 있습니다. `tf add` 명령은 체크 인할 보류 중인 변경 사항 목록에 파일을 추가하는 데 사용되고 `tf checkin` 명령은 서버에 대한 실제 체크 인을 수행합니다. `checkin` 명령은 주석을 추가하거나 관련 작업 항목을 연결하는 매개 변수를 포함합니다. 다음 코드 조각에서 `WebApp.Services` 폴더의 모든 파일이 체크 인에 재귀적으로 추가됩니다. 그런 다음, 코드가 주석으로 체크 인되고 ID가 “42”인 작업 항목과 연결됩니다.

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

여기에 언급된 명령에 대해 자세히 알아보려면 터미널에서 다음 명령을 사용하면 됩니다.

`tf help`

## <a name="see-also"></a>참조

- [Visual Studio를 사용하여 TFVC에서 코드 개발 및 공유(Windows에서)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)