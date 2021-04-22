---
title: 명령줄 매개 변수를 사용하여 Visual Studio 설치
titleSuffix: ''
description: 명령줄 매개 변수를 사용하여 Visual Studio 설치를 제어하거나 사용자 지정하는 방법을 알아봅니다.
ms.date: 4/16/2021
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 23c83611e7663d35b229517f1e0224eb4ae7bb57
ms.sourcegitcommit: 367a2d9df789aa617abaa09b0cd0a18db7357d0c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107800821"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>명령줄 매개 변수를 사용하여 Visual Studio 설치

프로그래밍 방식으로 또는 명령 프롬프트에서 Visual Studio를 설치할 때 다양한 명령줄 매개 변수를 사용하여 다음 작업을 수행하도록 설치를 제어하거나 사용자 지정할 수 있습니다.

- 특정 옵션 및 동작이 미리 선택된 상태로 클라이언트에서 설치를 시작합니다.
- 설치 프로세스를 자동화합니다.
- 클라이언트 머신을 설치하거나 업데이트하기 위한 제품 파일의 네트워크 레이아웃을 만들거나 유지 관리합니다.

명령줄 옵션은 다운로드 프로세스를 시작하는 작은(1MB 이하) 파일인 설치 부트스트래퍼 또는 [Microsoft 업데이트 카탈로그](https://catalog.update.microsoft.com)에 배포된 관리자 업데이트 패키지와 함께 사용할 수 있습니다. 

::: moniker range="vs-2017"

Visual Studio 2017 버전 15.9용 부트스트래퍼를 다운로드하려면 [**Visual Studio 이전 버전**](https://visualstudio.microsoft.com/vs/older-downloads/) 페이지로 이동하여 다음 부트스트래퍼 파일 중 하나를 다운로드합니다.

| 버전 | 파일 이름 |
|-------------|-----------------------|
|Visual Studio Enterprise 2017 버전 15.9 | vs_enterprise.exe |
|Visual Studio Professional 2017 버전 15.9 | vs_professional.exe |
|Visual Studio Build Tools 2017 버전 15.9  | vs_buildtools.exe |

::: moniker-end

::: moniker range="vs-2019"

[Visual Studio 다운로드 페이지](https://visualstudio.microsoft.com/downloads)나 선택한 Visual Studio 버전 및 에디션의 [Visual Studio 2019 릴리스](https://docs.microsoft.com/visualstudio/releases/2019/history#installing-an-earlier-release) 페이지에서 Visual Studio 2019 부트스트래퍼를 다운로드할 수 있습니다. 설치 파일(또는 부트스트래퍼)은 다음 중 하나와 일치하거나 비슷합니다.

| 버전                    | 파일                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio 2019 Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019)     |
| Visual Studio 2019 Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019) |
| Visual Studio 2019 Build Tools   | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019)     |
| Visual Studio 2019 Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019)  |

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>이전에 다운로드한 부트스트래퍼 파일의 버전을 확인하려는 경우에는 다음을 참조하세요. Windows에서 파일 탐색기를 열고 부트스트래퍼 파일을 마우스 오른쪽 단추로 클릭한 다음, **속성** 을 선택하고 **세부 정보** 탭을 선택한 다음, **제품 버전** 번호를 확인합니다. 이 번호가 Visual Studio 릴리스와 일치하는지 확인하려면 [Visual Studio 빌드 번호 및 릴리스 날짜](visual-studio-build-numbers-and-release-dates.md) 페이지를 참조하세요.

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>이전에 부트스트래퍼 파일을 다운로드했으며 해당 버전을 확인하려는 경우에는 다음을 참조하세요. Windows에서 파일 탐색기를 열고 부트스트래퍼 파일을 마우스 오른쪽 단추로 클릭한 다음, **속성** 을 선택하고 **세부 정보** 탭을 선택한 다음, **제품 버전** 번호를 확인합니다. 이 번호가 Visual Studio 릴리스와 일치하는지 확인하려면 [Visual Studio 2019 릴리스](https://docs.microsoft.com/visualstudio/releases/2019/history) 페이지를 참조하세요.

::: moniker-end

[Microsoft 업데이트 카탈로그](https://catalog.update.microsoft.com)로 이동하여 설치하려는 업데이트를 검색하고 다운로드 단추를 눌러 관리자 업데이트를 다운로드할 수 있습니다. 관리자 업데이트는 컴퓨터에 Visual Studio가 이미 설치되어 있다고 가정합니다. 관리자 업데이트를 적용해도 새 설치가 시작되지는 않습니다.

## <a name="bootstrapper-commands-and-command-line-parameters"></a>부트스트래퍼 명령 및 명령줄 매개 변수

Visual Studio 부트스트래퍼를 프로그래밍 방식으로 호출하여 제품을 설치하거나 레이아웃을 유지 관리하는 경우 첫 번째 매개 변수는 수행할 작업을 설명하는 명령(동사)입니다. 모두 두 개의 대시(--)로 접두사가 지정된 후속 선택적 명령줄 매개 변수는 해당 작업이 수행되는 방식을 추가로 정의합니다. 모든 Visual Studio 명령줄 매개 변수는 대/소문자를 구분하지 않으며, [명령줄 매개 변수 예제](command-line-parameter-examples.md) 페이지에서 추가 예제를 확인할 수 있습니다.

구문 예제: `vs_enterprise.exe [command] <optional parameters>...`

| **Command** | **설명** |
| ----------------------- | --------------- |
| (비어 있음) | 기본 명령은 모두 제품을 설치하며, 모든 레이아웃 유지 관리 작업에 사용됩니다. |
| `modify` | 설치된 제품을 수정합니다. |
| `update` | 설치된 제품을 업데이트합니다. |
| `repair` | 설치된 제품을 복구합니다. |
| `uninstall` | 설치된 제품을 제거합니다. |
| `export` | 설치 선택 항목을 설치 구성 파일로 내보냅니다. **참고**: vs_installer.exe와 함께만 사용할 수 있습니다. |


| **매개 변수** | **설명** |
| ----------------------- | --------------- |
| `--installPath <dir>` | 기본 설치 명령의 경우 이 매개 변수는 **선택 사항** 이며 클라이언트 머신에서 인스턴스가 설치되는 위치를 설명합니다. 업데이트 또는 수정과 같은 다른 명령의 경우 이 매개 변수는 **필수** 이며 인스턴스가 작업을 수행할 설치 디렉터리를 나타냅니다. |
| `--add <one or more workload or component IDs>` | **선택 사항**: 설치 또는 수정 명령 중에 이 반복 가능한 매개 변수는 추가할 하나 이상의 워크로드 또는 구성 요소 ID를 지정합니다. 아티팩트의 필수 구성 요소가 설치되지만 권장 또는 선택적 구성 요소는 설치되지 않습니다. `--includeRecommended` 및/또는 `--includeOptional` 매개 변수를 사용하여 추가 구성 요소를 전역적으로 제어할 수 있습니다. 여러 워크로드 또는 구성 요소를 포함하려면 `--add` 명령(예:`--add Workload1 --add Workload2`)을 반복합니다. 더 세부적으로 제어하기 위해 `;includeRecommended` 또는 `;includeOptional`을 ID에 추가할 수 있습니다(예: `--add Workload1;includeRecommended` 또는 `--add Workload2;includeRecommended;includeOptional`). 자세한 내용은 [작업 및 구성 요소 ID](workload-and-component-ids.md) 페이지를 참조하세요. |
| `--remove <one or more workload or component IDs>` | **선택 사항**: 수정 명령 중에 이 반복 가능한 매개 변수는 제거할 하나 이상의 워크로드 또는 구성 요소 ID를 지정합니다. `--add` 매개 변수를 보완하고 이 매개 변수와 유사하게 동작합니다. |
| `--addProductLang <language-locale>` | **선택 사항**: 설치 또는 수정 명령 중에 이 반복 가능한 매개 변수는 제품과 함께 설치해야 하는 UI 언어 팩을 지정합니다. 이 매개 변수가 없으면 설치에서 머신 로캘에 해당하는 언어 팩을 사용합니다. 자세한 내용은 이 페이지의 [언어 로캘 목록](#list-of-language-locales) 섹션을 참조하세요.|
| `--removeProductLang <language-locale>` | **선택 사항**: 설치 또는 수정 명령 중에 이 반복 가능한 매개 변수는 제품에서 제거해야 하는 UI 언어 팩을 결정합니다.  `--addProductLang` 매개 변수를 보완하고 이 매개 변수와 유사하게 동작합니다. |
| `--in <path>` | **선택 사항**: 구성 설정을 포함할 수 있는 [지시 파일](automated-installation-with-response-file.md)의 URI 또는 경로입니다. |
| `--all` | **선택 사항**: 설치 또는 수정 명령 중에 이 매개 변수는 제품의 모든 워크로드 및 구성 요소가 설치되도록 합니다. |
| `--allWorkloads` | **선택 사항**: 설치 또는 수정 명령 중에 이 매개 변수는 모든 워크로드 및 구성 요소를 설치하지만, 권장 또는 선택적 구성 요소는 설치하지 않습니다. |
| `--includeRecommended` | **선택 사항**: 설치 또는 수정 명령 중에 이 매개 변수는 설치된 모든 워크로드의 권장 구성 요소를 포함하지만, 선택적 구성 요소는 포함하지 않습니다. 워크로드는 `--allWorkloads` 또는 `--add`를 사용하여 지정됩니다. |
| `--includeOptional` | **선택 사항**: 설치 또는 수정 명령 중에 이 매개 변수는 설치된 모든 워크로드의 선택적 구성 요소를 포함하지만, 권장 구성 요소는 포함하지 않습니다. 워크로드는 `--allWorkloads` 또는 `--add`를 사용하여 지정됩니다.  |
| `--quiet, -q` | **선택 사항**: 모든 명령과 함께 사용되며, 이 매개 변수는 명령이 실행되는 동안 사용자 인터페이스가 표시되지 않도록 합니다. |
| `--passive, -p` | **선택 사항**: 이 매개 변수는 비대화형 방식으로 사용자 인터페이스가 표시되도록 합니다. 이 매개 변수는 `--quiet` 매개 변수와 함께 사용할 수 없으며, 사실 이 매개 변수를 재정의합니다.  |
| `--norestart` | **선택 사항**: 이 매개 변수는 `--passive` 또는 `--quiet` 매개 변수와 쌍을 이루어야 합니다.  설치, 업데이트 또는 수정 명령 중에 `--norestart` 매개 변수를 추가하면 필요한 다시 시작이 연기됩니다. |
| `--force` | **선택 사항**: 이 매개 변수는 Visual Studio 프로세스가 사용 중인 경우에도 Visual Studio를 강제로 닫습니다. |
| `--installWhileDownloading` | **선택 사항**: 설치, 업데이트 또는 수정 명령 중에 이 매개 변수를 사용하면 Visual Studio에서 제품을 병렬로 다운로드 및 설치할 수 있습니다. 기본 환경입니다. |
| `--downloadThenInstall` | **선택 사항**: 설치, 업데이트 또는 수정 명령 중에 이 매개 변수는 강제로 Visual Studio가 모든 파일을 다운로드한 후 설치하도록 합니다. `--installWhileDownloading` 매개 변수와 함께 사용할 수 없습니다. |
| `--nickname <name>` | **선택 사항**: 설치 명령 중에 이 매개 변수는 설치된 제품에 할당할 닉네임을 정의합니다. 애칭은 10자를 초과할 수 없습니다.  |
| `--productKey` | **선택 사항**: 설치 명령 중에 이 매개 변수는 설치된 제품에 사용할 제품 키를 정의합니다. 제품 키는 `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` 또는 `xxxxxxxxxxxxxxxxxxxxxxxxx` 형식의 영숫자 25자로 구성됩니다. |
| `--help, --?, -h, -?` | 이 페이지의 오프라인 버전을 표시합니다. |
| `--config <path>` | **선택 사항**: 설치 또는 수정 작업 중에 이 매개 변수는 이전에 저장한 설치 구성 파일을 기반으로 추가할 워크로드 및 구성 요소를 결정합니다. 이 작업은 추가 작업이며 파일에 없는 워크로드나 구성 요소를 제거하지 않습니다. 또한 제품에 적용되지 않는 항목은 추가되지 않습니다. 내보내기 작업 중에 설치 구성 파일을 저장할 위치가 결정됩니다. |


> [!IMPORTANT]
> 고유한 여러 워크로드 또는 구성 요소나 언어를 지정할 경우 각 항목에 대해 `--add` 또는 `--remove` 명령줄 스위치를 반복해야 합니다.

## <a name="layout-command-and-command-line-parameters"></a>레이아웃 명령 및 명령줄 매개 변수
모든 레이아웃 관리 작업에서는 명령이 기본 설치(비어 있음)라고 가정합니다. 따라서 모든 레이아웃 관리 작업은 초기 필수 `--layout` 매개 변수로 시작해야 합니다.  다음 표에는 명령줄을 사용하여 레이아웃을 만들거나 업데이트하는 데 사용할 수 있는 다른 매개 변수가 설명되어 있습니다.

| **레이아웃 매개 변수** | **설명** |
| ----------------------- | --------------- |
| `--layout <dir>` | 오프라인 설치 캐시를 만들거나 업데이트할 디렉터리를 지정합니다. 자세한 내용은 [Visual Studio의 네트워크 기반 설치 만들기](create-a-network-installation-of-visual-studio.md)를 참조하세요.|
| `--lang <one or more language-locales>` | **선택 사항**: `--layout`과 함께 사용하여 지정된 언어의 리소스 패키지와 함께 오프라인 설치 캐시를 준비합니다. 자세한 내용은 이 페이지의 [언어 로캘 목록](#list-of-language-locales) 섹션을 참조하세요.|
| `--add <one or more workload or component IDs>` | **선택 사항**: 추가할 하나 이상의 작업 또는 구성 요소 ID입니다. 아티팩트의 필수 구성 요소가 설치되지만 권장 또는 선택적 구성 요소는 설치되지 않습니다. `--includeRecommended` 및/또는 `--includeOptional`을 사용하여 추가 구성 요소를 전체적으로 제어할 수 있습니다. 더 세부적으로 제어하기 위해 `;includeRecommended` 또는 `;includeOptional`을 ID에 추가할 수 있습니다(예: `--add Workload1;includeRecommended` 또는 `--add Workload2;includeOptional`). 자세한 내용은 [작업 및 구성 요소 ID](workload-and-component-ids.md) 페이지를 참조하세요. <br/>**참고**: `--add`를 사용하면 지정된 워크로드 및 구성 요소와 해당 종속성이 다운로드됩니다. `--add`가 지정되지 않으면 모든 워크로드 및 구성 요소가 레이아웃에 다운로드됩니다.|
| `--includeRecommended` | **선택 사항**: 설치된 모든 작업에 대한 권장 구성 요소를 포함하지만, 선택적 구성 요소는 포함하지 않습니다. 워크로드는 `--allWorkloads` 또는 `--add`를 사용하여 지정됩니다. |
| `--includeOptional` | **선택 사항**: 레이아웃에 포함되는 모든 워크로드에 대한 권장 *및* 선택적 명령을 포함합니다. 워크로드는 `--add`를 사용하여 지정됩니다.  |
| `--keepLayoutVersion` | **선택 사항**: 레이아웃의 버전을 업데이트하지 않고 레이아웃에 변경 내용을 적용합니다. |
| `--verify` | **선택 사항**: 레이아웃의 콘텐츠를 확인합니다. 손상되거나 누락된 파일이 모두 나열됩니다. |
| `--fix` | **선택 사항**: 레이아웃의 콘텐츠를 확인합니다.  손상되거나 누락된 파일은 다시 다운로드됩니다. 레이아웃을 수정하려면 인터넷 액세스가 필요합니다. |
| `--clean <one or more paths to catalogs>` | **선택 사항**: 최신 버전으로 업데이트된 레이아웃에서 이전 버전의 구성 요소를 제거합니다. |

| **고급 레이아웃 매개 변수** | **설명** |
| ----------------------- | --------------- |
| `--channelId <id>` | **선택 사항**: 설치할 인스턴스의 채널 ID입니다. 설치 명령에 필요하며, `--installPath`가 지정된 경우 다른 명령에서는 무시됩니다. |
| `--channelUri <uri>` | **선택 사항**: 채널 매니페스트의 URI입니다. 업데이트를 원하지 않는 경우 `--channelUri`는 존재하지 않는 파일(예: --channelUri C:\doesntExist.chman)을 가리킬 수 있습니다. 설치 명령에 사용할 수 있습니다. 다른 명령에서는 무시됩니다. |
| `--installChannelUri <uri>` | **선택 사항**: 설치에 사용할 채널 매니페스트의 URI입니다. `--channelUri`(`--installChannelUri`가 지정된 경우 지정해야 함)로 지정된 URI는 업데이트를 검색하는 데 사용됩니다. 설치 명령에 사용할 수 있습니다. 다른 명령에서는 무시됩니다. |
| `--installCatalogUri <uri>` | **선택 사항**: 설치에 사용할 카탈로그 매니페스트의 URI입니다. 지정된 경우 채널 관리자는 설치 채널 매니페스트의 URI를 사용하기 전에 이 URI에서 카탈로그 매니페스트를 다운로드하려고 합니다. 이 매개 변수는 이미 다운로드한 제품 카탈로그를 사용하여 레이아웃 캐시가 생성되는 오프라인 설치를 지원하는 데 사용됩니다. 설치 명령에 사용할 수 있습니다. 다른 명령에서는 무시됩니다. |
| `--productId <id>` | **선택 사항**: 설치할 인스턴스의 제품 ID입니다. 일반적인 설치 조건에서는 미리 채워져 있습니다. |
| `--wait` | **선택 사항**: 프로세스에서 설치가 완료될 때까지 기다린 후에 종료 코드를 반환합니다. 이 기능은 설치의 반환 코드를 처리하기 위해 설치가 완료할 때까지 기다려야 하는 설치를 자동화할 경우 유용합니다. |
| `--locale <language-locale>` | **선택 사항**: 설치 관리자의 사용자 인터페이스 표시 언어를 변경합니다. 설정은 유지됩니다. 자세한 내용은 이 페이지의 [언어 로캘 목록](#list-of-language-locales) 섹션을 참조하세요.|
| `--cache` | **선택 사항**: 이 매개 변수가 있으면 패키지가 이후 복구를 위해 설치된 후에도 유지됩니다. 이는 이후 설치, 복구 또는 수정에 사용할 전역 정책 설정을 재정의합니다. 기본 정책은 패키지를 캐시하는 것입니다. 제거 명령의 경우 무시됩니다. 자세한 내용은 [패키지 캐시를 사용하지 않도록 설정 또는 이동](disable-or-move-the-package-cache.md)하는 방법을 참조하세요. |
| `--nocache` | **선택 사항**: 이 매개 변수가 있으면 패키지가 설치 또는 복구된 후에 삭제됩니다. 필요한 경우에만 다시 다운로드되고 사용한 후 다시 삭제됩니다. 이는 이후 설치, 복구 또는 수정에 사용할 전역 정책 설정을 재정의합니다. 기본 정책은 패키지를 캐시하는 것입니다. 제거 명령의 경우 무시됩니다. 자세한 내용은 [패키지 캐시를 사용하지 않도록 설정 또는 이동](disable-or-move-the-package-cache.md)하는 방법을 참조하세요. |
| `--noUpdateInstaller` | **선택 사항**: 이 매개 변수가 있으면 quiet가 지정된 경우 설치 관리자가 자기 자신을 업데이트하지 않습니다. quiet와 함께 noUpdateInstaller가 지정되었는데 설치 프로그램 업데이트가 필요한 경우 설치 프로그램에서 명령을 실패로 처리하고 0이 아닌 종료 코드를 반환합니다. |
| `--noWeb` | **선택 사항**: 이 매개 변수가 있으면 Visual Studio 설치 프로그램에서 레이아웃 디렉터리에 있는 파일을 사용하여 Visual Studio를 설치합니다. 사용자가 레이아웃에 없는 구성 요소를 설치하려고 시도하면 설치에 실패합니다.  자세한 내용은 [네트워크 설치에서 배포](create-a-network-installation-of-visual-studio.md)를 참조하세요. <br/><br/> **중요**: 이 스위치는 Visual Studio 설치 프로그램에서 업데이트를 확인하는 작업을 중지하지 않습니다. 자세한 내용은 [네트워크 기반 Visual Studio 배포에 대한 업데이트 제어](controlling-updates-to-visual-studio-deployments.md)를 참조하세요. |
| `--path <name>=<path>` | **선택 사항**: 설치에 대해 사용자 지정 설치 경로를 지정하는 데 사용합니다. 지원되는 경로 이름은 공유, 캐시 및 설치입니다. |
| `--path cache=<path>` | **선택 사항**: 설치 파일을 다운로드하는 데 사용자가 지정한 위치를 사용합니다. 이 위치는 처음 Visual Studio를 설치할 때만 설정할 수 있습니다. 예: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **선택 사항**: Visual Studio 병렬 설치를 위한 공유 파일을 포함합니다. 일부 도구 및 SDK가 이 드라이브의 위치에 설치되지만 나머지는 이 설정을 재정의하고 다른 드라이브에 설치될 수 있습니다. 예: `--path shared="C:\VS\shared"` <br/><br/>**중요**: 이 매개 변수는 Visual Studio를 처음 설치할 때 한 번만 설정하면 됩니다. |
| `--path install=<path>` | **선택 사항**: `–-installPath`에 해당합니다. 특히 `--installPath "C:\VS"`와 `--path install="C:\VS"`는 같습니다. 한 번에 이 명령 중 하나만 사용할 수 있습니다. |

## <a name="administrator-update-command-and-command-line-parameters"></a>관리자 업데이트 명령 및 명령줄 매개 변수
[Microsoft 업데이트 카탈로그](https://catalog.update.microsoft.com)에서 클라이언트 머신의 설치 디렉터리로 관리자 업데이트를 다운로드하는 경우 해당 파일을 두 번 클릭하기만 하면 업데이트가 적용됩니다. 명령 창을 열고 아래의 몇 가지 매개 변수를 전달하여 기본 동작을 변경할 수도 있습니다. 

Microsoft Endpoint Manager(SCCM)를 통해 관리자 업데이트를 배포하는 경우 아래 매개 변수를 사용하여 동작을 조정하도록 패키지를 수정할 수 있습니다. 클라이언트 머신의 구성 파일을 통해 매개 변수를 제어할 수도 있습니다. 자세한 내용은 [관리자 업데이트를 구성하는 방법](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update)을 참조하세요.

모든 관리자 업데이트 매개 변수는 “업데이트” 컨텍스트에서 실행됩니다.

| **관리자 업데이트 매개 변수** | **설명** |
| ----------------------- | --------------- |
| `--installerUpdateArgs [optional parameters]` | 이 매개 변수는 관리자 업데이트 시나리오와 관련된 특정 매개 변수의 “통과 배열”로 작동합니다. 이 용도로 사용할 수 있는 선택적 매개 변수는 다음과 같습니다. <br/><br/> `--quiet`: 관리자 업데이트의 기본 환경이며 완전성을 위해 여기에 나열되어 있습니다. <br/> `--passive`: 이 매개 변수는 `--quiet` 매개 변수를 재정의합니다.  이 매개 변수는 UI가 비대화형 방식으로 표시되도록 합니다. <br/>`--norestart`: 이 매개 변수는 `--quiet` 또는 `--passive`와 함께 사용해야 하며 필요한 다시 시작이 연기되도록 합니다. <br/>`--noWeb`: 이 매개 변수는 Visual Studio가 인터넷에서 제품의 업데이트를 확인하지 못하도록 합니다. <br/>`--force`: 이 매개 변수는 Visual Studio가 사용 중인 경우에도 Visual Studio를 강제로 닫습니다. 그러면 작업이 손실될 수 있으므로 이 매개 변수는 주의해서 사용하세요. 이 매개 변수는 사용자 컨텍스트에서 사용해야 합니다. <br/>`--installWhileDownloading`: 이 매개 변수를 사용하면 Visual Studio에서 제품을 병렬로 다운로드 및 설치할 수 있습니다. 관리자 업데이트의 기본 환경이며 완전성을 위해 여기에 나열되어 있습니다. <br/>`--downloadThenInstall`: 이 매개 변수는 강제로 Visual Studio가 모든 파일을 다운로드한 후 설치하도록 합니다. `--installWhileDownloading` 매개 변수와 함께 사용할 수 없습니다. |
| `--checkPendingReboot` | 원인이 되는 애플리케이션이 무엇인지와 관계없이 머신에 보류 중인 다시 시작이 있으면 업데이트가 중단됩니다. 기본값은 보류 중인 다시 시작을 확인하지 않는 것입니다. |


구문 예제: `visualstudioupdate-16.9.0to16.9.4.exe --installerUpdateArgs=--force,--noWeb --checkPendingReboot`

## <a name="list-of-workload-ids-and-component-ids"></a>작업 ID 및 구성 요소 ID 목록

Visual Studio 제품별로 정렬된 워크로드 및 구성 요소 ID 목록은 [Visual Studio 워크로드 및 구성 요소 ID](workload-and-component-ids.md) 페이지를 참조하세요.

## <a name="list-of-language-locales"></a>언어 로캘 목록

| **언어 로캘** | **언어** |
| ----------------------- | --------------- |
| Cs-cz | 체코어 |
| De-de | 독일어 |
| En-us | 영어 |
| Es-es | 스페인어 |
| Fr-fr | 프랑스어 |
| It-it | 이탈리아어 |
| Ja-jp | 일본어 |
| Ko-kr | 한국어 |
| Pl-pl | 폴란드어 |
| Pt-br | 포르투갈어 - 브라질 |
| Ru-ru | 러시아어 |
| Tr-tr | 터키어 |
| Zh-cn | 중국어 - 간체 |
| Zh-tw | 중국어 - 번체 |

## <a name="error-codes"></a>오류 코드

작업 결과에 따라 `%ERRORLEVEL%` 환경 변수는 다음 값 중 하나로 설정됩니다.

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

각 작업은 `%TEMP%` 디렉터리에 설치 진행률을 나타내는 여러 로그 파일을 생성합니다. 폴더를 날짜별로 정렬하고 부트스트래퍼, 설치 관리자 앱 및 설치 엔진 각각에 대해 `dd_bootstrapper`, `dd_client` 및 `dd_setup`으로 시작하는 파일을 찾습니다.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참조

- [Visual Studio 설치에 대한 명령줄 매개 변수 예](command-line-parameter-examples.md)
- [Visual Studio의 오프라인 설치 만들기](create-an-offline-installation-of-visual-studio.md)
- [지시 파일을 사용하여 Visual Studio 설치 자동화](automated-installation-with-response-file.md)
- [Visual Studio 작업 및 구성 요소 ID](workload-and-component-ids.md)
