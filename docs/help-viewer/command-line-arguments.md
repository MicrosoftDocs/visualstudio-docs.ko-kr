---
title: 도움말 콘텐츠 관리자에 대한 명령줄 인수
ms.date: 11/01/2017
ms.topic: reference
ms.assetid: 3aa9890a-1147-42ba-adea-17935d184038
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d9bead01c6440d5232a91a5e8fe2007b3e30340c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72631971"
---
# <a name="command-line-arguments-for-the-help-content-manager"></a>도움말 콘텐츠 관리자에 대한 명령줄 인수

*HlpCtntMgr.exe*(도움말 콘텐츠 관리자)에 대 한 명령줄 인수를 사용 하 여 로컬 도움말 콘텐츠를 배포 하 고 관리 하는 방법을 지정할 수 있습니다. 관리자 권한으로 이 명령줄 도구에 대한 스크립트를 실행해야 하며 이러한 스크립트를 서비스로 실행할 수는 없습니다. 이 도구를 사용하여 다음과 같은 작업을 수행할 수 있습니다.

- 디스크 또는 클라우드에서 로컬 도움말 콘텐츠를 추가하거나 업데이트합니다.

- 로컬 도움말 콘텐츠를 제거합니다.

- 로컬 도움말 콘텐츠 저장소를 이동합니다.

- 로컬 도움말 콘텐츠를 자동으로 추가, 업데이트, 제거 또는 이동합니다.

구문

```cmd
HlpCtntmgr.exe /operation Value /catalogname CatalogName /locale Locale /sourceuri InstallationPoint
```

예를 들면 다음과 같습니다.

```cmd
hlpctntmgr.exe /operation install /catalogname VisualStudio15 /locale en-us /sourceuri d:\productDocumentation\HelpContentSetup.msha
```

>[!NOTE]
> 카탈로그 이름은 Visual Studio 2017 및 Visual Studio 2019 모두에 대해 VisualStudio15입니다. 이는 예기치 않은 일 수 있지만 Visual Studio 버전에 동일한 도움말 뷰어를 모두 사용 하기 때문입니다.

## <a name="switches-and-arguments"></a>스위치 및 인수

다음 표에는 도움말 콘텐츠 관리자용 명령줄 도구에 사용할 수 있는 스위치와 인수가 정의되어 있습니다.

|스위치|필수 여부|인수|
|------------|---------------|---------------|
|/operation|예|-   **Install**--지정된 설치 소스의 책을 로컬 콘텐츠 저장소에 추가합니다.<br />     이 스위치에는 /booklist 인수 또는 /sourceURI 인수가 필요하거나 두 인수가 모두 필요합니다. /sourceURI 인수를 지정하지 않는 경우 기본 Visual Studio URI가 설치 소스로 사용됩니다. /booklist 인수를 지정하지 않는 경우 /sourceUri의 모든 책이 설치됩니다.<br />-   **Uninstall**--지정하는 책을 로컬 콘텐츠 저장소에서 제거합니다.<br />     이 스위치에는 /booklist 인수 또는 /sourceURI 인수가 필요합니다.  /sourceURI 인수를 지정하는 경우 모든 책이 제거되고 /booklist 인수가 무시됩니다.<br />-   **Move**--지정하는 경로로 로컬 저장소를 이동합니다. 기본 로컬 저장소 경로는 *% ProgramData%* 아래에 디렉터리로 설정 됩니다.<br />     이 스위치에는 /locationPath 및 /catalogName 인수가 필요합니다. 잘못된 경로를 지정하거나 드라이브에 콘텐츠를 저장할 충분한 여유 공간이 없는 경우 오류 메시지가 이벤트 로그에 기록됩니다.<br />-   **Refresh**--설치된 이후 변경되었거나 최근에 업데이트된 항목을 업데이트합니다.<br />     이 스위치에는 /sourceURI 인수가 필요합니다.|
|/catalogName|예|콘텐츠 카탈로그의 이름을 지정합니다. Visual Studio 2017 및 Visual Studio 2019의 경우 VisualStudio15입니다.|
|/locale|예|도움말 뷰어의 현재 인스턴스에 대한 콘텐츠를 보고 관리하는 데 사용되는 제품 로캘을 지정합니다. 예를 들어 영어-미국의 경우 `EN-US`를 지정합니다.<br /><br /> 로캘을 지정하지 않는 경우 운영 체제의 로캘이 사용됩니다. 로캘을 확인할 수 없는 경우에는 `EN-US`가 사용됩니다.<br /><br /> 잘못된 로캘을 지정하면 오류 메시지가 이벤트 로그에 기록됩니다.|
|/e|예|현재 사용자에게 관리자 자격 증명이 있는 경우 도움말 콘텐츠 관리자를 관리자 권한으로 승격합니다.|
|/sourceURI|예|콘텐츠가 설치 되는 URL (서비스 API) 또는 콘텐츠 설치 파일 (*. msha*)의 경로를 지정 합니다. URL은 Visual Studio 2010 스타일 엔드포인트에서 제품 그룹(최상위 노드) 또는 제품 책(리프 수준 노드)을 가리킬 수 있습니다. URL 끝에 슬래시(/)를 포함할 필요가 없습니다. 끝에 슬래시를 포함하는 경우 적절하게 처리됩니다.<br /><br /> 찾을 수 없거나, 잘못되거나, 액세스할 수 없는 파일을 지정하는 경우나 콘텐츠를 관리하는 동안 인터넷 연결을 사용할 수 없거나 중단된 경우 오류 메시지가 이벤트 로그에 기록됩니다.|
|/vendor|예|제거될 제품 콘텐츠의 공급업체를 지정합니다(예: `Microsoft`). 이 스위치의 기본 인수는 Microsoft입니다.|
|/productName|예|제거될 책의 제품 이름을 지정합니다. 제품 이름은 콘텐츠와 함께 제공 된 *helpcontentsetup. msha* 또는 *books.html* 파일에서 식별 됩니다. 한 번에 한 제품에서만 책을 제거할 수 있습니다. 여러 제품에서 책을 제거하려면 여러 설치를 수행해야 합니다.|
|/booklist|예|관리할 책의 이름을 공백으로 구분하여 지정합니다. 값은 설치 미디어에 표시된 책 이름과 일치해야 합니다.<br /><br /> 이 인수를 지정하지 않는 경우 /sourceURI에 지정된 제품의 모든 권장되는 책이 설치됩니다.<br /><br /> 책의 이름에 공백이 하나 이상 포함되어 있으면 목록이 적절하게 구분되도록 큰따옴표(")로 묶습니다.<br /><br /> 잘못되거나 연결될 수 없는 /sourceURI를 지정하는 경우 오류 메시지가 기록됩니다.|
|/skuId|예|설치 원본에서 제품의 SKU(Stock Keeping Unit)를 지정하고 /SourceURI 스위치로 식별되는 책을 필터링합니다.|
|/membership|예|-   **Minimum**--/skuId 스위치를 사용하여 지정한 SKU를 기반으로 도움말 콘텐츠의 최소 집합을 설치합니다. SKU와 콘텐츠 집합 간의 매핑은 서비스 API에서 노출됩니다.<br />-   **Recommended**--/skuId 인수를 사용하여 지정한 SKU에 대한 권장되는 책의 집합을 설치합니다. 설치 원본은 서비스 API 또는 *입니다. MSHA*.<br />-   **Full**--/skuId 인수를 사용하여 지정한 SKU에 대한 책의 전체 집합을 설치합니다. 설치 원본은 서비스 API 또는 *입니다. MSHA*.|
|/locationpath|예|로컬 도움말 콘텐츠의 기본 폴더를 지정합니다. 이 스위치는 콘텐츠를 설치하거나 이동하는 데만 사용해야 합니다. 이 스위치를 지정하는 경우 /silent 스위치도 지정해야 합니다.|
|/silent|예|사용자에게 메시지를 표시하거나 상태 알림 영역의 아이콘을 비롯한 UI를 표시하지 않고 도움말 콘텐츠를 설치하거나 제거합니다. 출력은 *% Temp%* 디렉터리의 파일에 기록 됩니다. **중요:**  콘텐츠를 자동으로 설치 하려면 *.mshc* 파일을 사용 하지 않고 디지털 서명 된 *.cab* 파일을 사용 해야 합니다.|
|/launchingApp|예|도움말 뷰어가 부모 애플리케이션 없이 시작될 때 애플리케이션 및 카탈로그 컨텍스트를 정의합니다. 이 스위치의 인수는 *CompanyName*, *ProductName* 및 *VersionNumber*(예: `/launchingApp Microsoft,VisualStudio,16.0`)입니다.<br /><br /> 이 스위치는 /silent 매개 변수를 사용하여 콘텐츠를 설치하는 데 필요합니다.|
|/wait *Seconds*|예|설치, 제거 및 새로 고침 작업을 일시 중지합니다. 작업이 이미 카탈로그에 대해 진행 중인 경우 프로세스는 지정된 기간(초)까지 대기한 다음 계속됩니다. 무기한 대기하려면 0을 사용합니다.|
|/?|예|도움말 콘텐츠 관리자용 명령줄 도구에 대한 스위치와 해당 설명을 나열합니다.|

### <a name="exit-codes"></a>종료 코드

도움말 콘텐츠 관리자용 명령줄 도구를 자동 모드에서 실행하면 다음과 같은 종료 코드가 반환됩니다.

```
Success = 0,

FailureToElevate = 100
InvalidCmdArgs = 101,
FailOnFetchingOnlineContent = 110,
FailOnFetchingContentFromDisk = 120,
FailOnFetchingInstalledBooks = 130,
NoBooksToUninstall = 200,
NoBooksToInstall = 300,
FailOnUninstall = 400,
FailOnInstall = 500,
FailOnMove = 600,
FailOnUpdate = 700,
FailOnRefresh = 800,
Cancelled = 900,
Others = 999,
ContentManagementDisabled = 1200,
OnlineHelpPreferenceDisabled = 1201
UpdateAlreadyRunning = 1300 - (Signals that the update didn't run because another was in progress.)
```

## <a name="see-also"></a>추가 정보

- [도움말 뷰어 관리자 가이드](../help-viewer/administrator-guide.md)
- [도움말 콘텐츠 관리자 재정의](../help-viewer/behavior-overrides.md)
- [Microsoft 도움말 뷰어](../help-viewer/overview.md)