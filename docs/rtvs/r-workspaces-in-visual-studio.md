---
title: R 작업 영역
description: Visual Studio에서 작업 영역을 사용하여 R 코드가 실행되는 위치를 제어하는 방법입니다.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 3627a8944941fc77bb9b19fe3dd0a1549f41892a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961588"
---
# <a name="control-where-r-code-runs-with-workspaces"></a>작업 영역에서 R 코드가 실행되는 위치 제어

RTVS(Visual Studio용 R 도구)의 작업 영역에서는 R 세션이 실행되는 위치를 구성할 수 있고 이 구성은 로컬 및 원격 컴퓨터에서 둘 다 수행할 수 있습니다. 목적은 잠재적으로 더 강력한 클라우드 기반 컴퓨터를 활용하는 기능을 제공하는 비슷한 사용자 환경이 있는 한쪽 컴퓨터에서 작업하도록 허용하는 것입니다.

**작업 영역** 창을 열려면 **R 도구** > **창** > **작업 영역** 명령을 사용하거나 **Ctrl**+**9** 를 누릅니다.

![Visual Studio용 R 도구(VS2017)의 작업 영역 창](media/workspaces-window.png)

이 창에서 녹색 확인 표시는 RTVS가 바인딩된 활성 작업 영역을 나타냅니다. 녹색 화살표를 선택하면 활성 작업 영역이 설정됩니다. 각 작업 영역의 오른쪽에 있는 설정(기어) 아이콘을 사용하여 이름, 위치 및 명령줄 인수를 변경할 수 있습니다. 빨간색 X를 선택하면 수동으로 추가된 작업 영역이 제거됩니다.

## <a name="save-and-reset-a-workspace"></a>작업 영역 저장 및 다시 설정

기본적으로 RTVS에서는 프로젝트를 닫고 다시 열 때 작업 영역 상태를 저장하지 않습니다. 하지만 [작업 영역 옵션](options-for-r-tools-in-visual-studio.md#workspace)을 통해 이 동작을 변경할 수 있습니다.

**R 도구** > **세션** > **다시 설정** 명령 및 대화형 창의 [다시 설정] 도구 모음 단추를 선택하면 언제든지 작업 영역 상태를 다시 설정할 수 있습니다. 원격 작업 영역에서 다시 설정은 원격 서버에 처음 연결할 때 생성된 사용자 프로필을 삭제하므로 누적되어 있는 모든 파일이 효과적으로 삭제됩니다.

## <a name="local-workspaces"></a>로컬 작업 영역

로컬 작업 영역 목록에는 컴퓨터에 설치한 모든 R 인터프리터가 표시됩니다.

Visual Studio는 시작될 때 **HKEY_LOCAL_MACHINE\Software\R-Core\\** 레지스트리 키를 검색하여 설치한 R 버전을 모두 자동으로 탐지하려고 합니다. 이 확인은 시작 시에만 수행되므로 새 R 인터프리터를 설치할 경우 Visual Studio를 다시 시작해야 합니다.

RTVS에서는 비표준 방법으로 설치된 R 인터프리터를 검색할 수 없습니다(예를 들어 설치 관리자를 실행하지 않고 단순히 파일을 폴더에 복사할 경우). 이 경우 다음과 같이 새 로컬 R 작업 영역을 수동으로 만듭니다.

1. [작업 영역] 창에서 **추가** 단추를 선택합니다.
1. 새 작업 영역의 이름을 입력합니다.
1. RTVS에서 인터프리터를 시작할 때 인터프리터에 전달할 모든 선택적 명령줄 인수와 함께 인터프리터가 있는 *bin* 폴더가 포함된 폴더인 R 루트 폴더의 경로를 입력합니다.
1. 완료되면 **저장** 을 선택합니다.

![새 작업 영역 추가](media/workspaces-add-new.png)

## <a name="remote-workspaces"></a>원격 작업 영역

원격 작업 영역을 통해 원격 컴퓨터의 R 세션에 연결할 수 있습니다. 이 목적으로 컴퓨터를 구성하는 방법에 대해서는 [원격 작업 영역 설정](setting-up-remote-r-workspaces.md)을 참조하세요.

Visual Studio는 원격 작업 영역을 자동으로 검색하지 않으므로 이전 섹션의 설명대로 [작업 영역] 창에서 **추가** 단추를 사용하여 수동으로 추가해야 합니다. 이 경우 로컬 경로가 아닌 원격 컴퓨터의 URI를 입력합니다.

> [!Important]
> 원격 작업 영역은 원격 컴퓨터와의 통신에 대한 개인 정보 및 무결성을 보장하기 위해 *HTTPS 프로토콜을 사용해야 하는* URI로 식별됩니다. Visual Studio는 HTTPS를 지원하지 않는 원격 컴퓨터에 연결할 수 없습니다.

> [!Note]
> 원격 작업 영역은 미리 보기에 효과적입니다. 향후 릴리스에서 파일 동기화 문제 구현을 개선하기 위한 작업이 진행 중이며 귀하의 아이디어와 피드백을 기다리고 있습니다.

## <a name="remote-workspace-logon"></a>원격 작업 영역 로그온

원격 작업 영역에 로그온하려면 사용자 이름 및 암호를 사용해야 합니다.

### <a name="logon-to-windows-workspace"></a>Windows 작업 영역에 로그온

원격 컴퓨터가 도메인 계정을 사용하도록 설정되어 있는 경우 도메인 로그온을 사용하여 원격 작업 영역에 액세스할 수 있습니다. 그렇지 않을 경우 `machine-name\username` 형식을 사용하여 원격 컴퓨터에서 컴퓨터 계정을 사용하여 로그온해야 합니다.

### <a name="logon-to-linux-workspace"></a>Linux 작업 영역으로 로그온

Linux 계정에 로그온하려면 `<<unix>>\username` 형식을 사용합니다. 예를 들어 이름이 `ruser`인 계정이 있는 경우 사용자 이름을 `<<unix>>\ruser`로 입력해야 합니다.

## <a name="switch-between-workspaces"></a>작업 영역 간 전환

RTVS는 한 번에 하나의 작업 영역에만 바인딩됩니다. 바인딩된 작업 영역은 [작업 영역] 창의 작은 녹색 확인 표시로 표시됩니다. 기본적으로 RTVS는 이전 세션의 마지막 로컬 작업 영역에 바인딩됩니다.

활성 작업 영역을 변경하려면 원하는 작업 영역 옆에 있는 파란색 화살표를 선택합니다. 이렇게 하면 세션을 저장할지 묻는 메시지가 표시되고, 현재 작업 영역이 종료되고, 새 작업 영역으로 전환됩니다.

> [!Tip]
> 저장 프롬프트를 사용하지 않으려면 **R 도구** > **옵션** 명령을 선택하고 **작업 영역을 전환하기 전에 확인 대화 상자를 표시합니다.** 옵션을 `No`로 설정합니다. [작업 영역 옵션](options-for-r-tools-in-visual-studio.md#workspace)을 참조하세요.

제거된 로컬 작업 영역 또는 사용할 수 없는 원격 작업 영역으로 전환하려고 하면 RTVS가 작업 영역에 바인딩되지 않을 수 있습니다. 따라서 대화형 창에 코드를 입력하거나 코드를 실행하려고 할 때 오류가 나타날 수 있습니다.

![작업 영역이 RTVS에 바인딩되지 않은 경우 오류](media/workspaces-disconnected-interactive-window.png)

이 문제를 수정하려면 [작업 영역] 창에서 다른 작업 영역으로 전환합니다. 작업 영역을 사용할 수 없으면 R 인터프리터를 설치해야 합니다. Visual Studio를 실행하는 동안 인터프리터를 설치한 경우 Visual Studio를 다시 시작해 볼 수 있습니다.

### <a name="switch-to-a-remote-workspace"></a>원격 작업 영역으로 전환

RTVS에서는 원격 작업 영역에 처음 연결할 때 자격 증명을 묻는 메시지를 표시하고 이후 세션을 위해 해당 자격 증명을 캐시합니다(안전한 Windows 자격 증명 보관 사용). 원격 서버 통신은 HTTPS(필수)를 통해 안전하게 수행됩니다.

서버 구성에 따라서는, 연결할 때 “원격 R Services를 통해 제공된 보안 인증서에서는 사용자가 컴퓨터(이름)에 연결되어 있음을 입증하도록 허용하지 않습니다.”라고 표시된 인증서 경고를 확인할 수 있습니다.

![원격 작업 영역에 연결할 때 자체 서명된 인증서 경고 대화 상자](media/workspaces-remote-self-signed-certificate-warning.png)

인증서는 연결하려는 컴퓨터에서 RTVS에 제공하는 문서입니다. 인증서는 해당 컴퓨터의 URI를 식별하는 필드를 포함합니다. RTVS에서 인증서 URI와 컴퓨터에 연결하는 데 사용된 URI 간에 불일치를 발견하면 서버의 보안이 손상되었을 수 있음을 나타내는 경고가 표시됩니다.

그러나 원격 컴퓨터에서 HTTPS를 사용하도록 설정하는 데 신뢰할 수 있는 공급자의 인증서를 사용하는 대신 *자체 서명된 인증서* 를 사용한 경우에도 이 경고가 나타납니다. 자세한 내용은 [원격 작업 영역 설정](setting-up-remote-r-workspaces.md)을 참조하세요.

## <a name="directories-on-local-and-remote-computers"></a>로컬 및 원격 컴퓨터의 디렉터리

기본적으로 새 R 인터프리터를 로컬 작업 영역에서 시작하면 현재 작업 디렉터리는 *%userprofile%\Documents* 입니다. **R 도구** > **작업 디렉터리** 명령을 사용하거나 Visual Studio 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **여기에 작업 디렉터리 설정** 같은 명령을 선택하여 언제든지 디렉터리를 변경할 수 있습니다.

원격 컴퓨터에 처음 연결할 때 RTVS가 자격 증명에 따라 사용자 프로필을 자동으로 생성하므로 작업 디렉터리는 해당 프로필 아래 *문서* 폴더로 설정됩니다. 이 폴더는 같은 자격 증명을 사용하는 모든 후속 원격 세션에 사용됩니다.

따라서 코드가 실행되는 정확한 위치는 로컬 및 원격 작업 영역 간에 다를 수 있습니다. 코드에서는 항상 데이터 파일의 상태 경로를 사용하세요. 이렇게 하면 여러 작업 영역에 걸쳐 코드를 이식할 수 있습니다.

원격 작업 영역에서는 작업 디렉터리의 모든 파일이 같은 사용자 프로필에 대한 여러 세션에 걸쳐 그대로 유지됩니다. 앞의 설명대로 원격 작업 영역을 사용할 경우 **R 도구** > **세션** > **다시 설정** 명령(또는 대화형 창의 [다시 설정] 단추)을 사용하여 이러한 파일을 삭제할 수 있습니다. 이 명령을 통해 다시 연결할 때 다시 생성된 사용자 프로필도 서버에서 삭제됩니다.

## <a name="copy-project-files-to-remote-workspaces"></a>원격 작업 영역으로 프로젝트 파일 복사

Visual Studio에서 R 프로젝트를 사용할 경우 원격 작업 영역을 사용 중인 경우에도 로컬 컴퓨터에는 항상 최신 프로젝트 파일이 포함됩니다. 즉, Visual Studio에서 프로젝트를 열 경우(일반적으로 해당 프로젝트가 포함된 솔루션을 열 경우) RTVS에서는 프로젝트 콘텐츠가 완전히 로컬 컴퓨터에 상주한다고 간주합니다. 원격 작업 영역은 실제로 프로젝트 파일 및 코드의 모든 출력에 대한 임시 호스트입니다. 이는 예를 들어 대화형 창에서 `source`를 사용하여 파일을 로드할 경우 해당 파일이 직접 제공한 경로의 원격 컴퓨터에 있어야 하거나 `setwd()` 함수로 설정된 원격 R 인터프리터의 현재 작업 디렉터리에 있어야 함을 의미합니다.

파일은 다음과 같이 원격 서버로 복사됩니다.

- 대화형 창을 통해 원격으로 파일을 사용하려면 먼저 솔루션 탐색기에서 해당 파일(또는 프로젝트)을 마우스 오른쪽 단추로 클릭하고 **소스 선택됨** 을 선택하여 파일을 수동으로 복사해야 합니다. 개별 파일의 경우 서버의 작업 디렉터리로 복사되고, 프로젝트를 복사할 경우 RTVS에서 프로젝트에 대한 폴더를 만듭니다.

- 솔루션 탐색기에서 파일을 선택하고 **선택한 파일 원본 제공** 을 선택하여 파일을 복사할 수도 있습니다. 이 작업으로 파일이 대화형 창으로 로드되고 여기서 실행됩니다. 세션이 원격 컴퓨터에 연결되면 파일은 먼저 원격 컴퓨터로 복사됩니다.

- RTVS가 원격 작업 영역에 바인딩되고 **F5** 키를 누르고 **디버그** > **디버깅 시작** 을 선택하거나 코드 실행을 시작하면 RTVS에서는 기본적으로 프로젝트 파일을 원격 작업 영역으로 자동으로 복사합니다(이 동작을 제어하는 방법은 아래 내용 참조).

- 이미 서버에 있는 모든 파일을 덮어씁니다.

> [!Note]
> RTVS가 모든 R 함수 호출을 확실히 가로챌 수는 없으므로 대화형 창 내에서 `source()` 또는 `runApp()`(Shiny 애플리케이션의 경우) 등의 함수를 호출하면 파일이 원격 작업 영역으로 복사되지 *않습니다*.

[프로젝트 속성](r-projects-in-visual-studio.md#project-properties)은 프로젝트가 실행될 때 RTVS가 파일을 복사할지 여부, 그리고 정확히 복사되는 파일을 제어합니다. 이 페이지를 열려면 **프로젝트** >  **(이름) 속성** 메뉴 명령을 선택하거나 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성** 을 선택합니다.

![파일 전송 설정이 있는 프로젝트 속성 실행 탭](media/workspaces-remote-file-transfer-filter-settings.png)

여기서 **실행할 전송 파일** 속성은 RTVS가 프로젝트 파일을 자동으로 복사할지 여부를 결정합니다. **전송할 파일** 값은 정확히 전송되는 파일을 필터링합니다. 기본 동작은 *.R*, *.Rmd*, *.sql*, *.md* 및 *.cpp* 파일만 복사합니다. 이 동작은 실행할 때마다 큰 데이터 파일이 의도치 않게 서버로 복사되지 않도록 합니다.

## <a name="copy-files-from-a-remote-workspace"></a>원격 작업 영역에서 파일 복사

R 스크립트가 서버의 파일을 생성할 경우 `rtvs::fetch_file` 함수를 사용하여 해당 파일을 다시 클라이언트로 복사할 수 있습니다. 이 함수는 최소한 컴퓨터로 복사할 파일의 원격 경로를 허용하고 경우에 따라 컴퓨터의 대상 경로를 허용합니다. 경로를 지정하지 않으면 파일이 *%userprofile%\Downloads* 폴더로 복사됩니다.
