---
title: 명령줄 매개 변수를 사용 하 여 Visual Studio 2015 | 설치 Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
caps.latest.revision: 10
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a3fe0233f08f33535be4b02cc06c29d919d75169
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180257"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>명령줄 매개 변수를 사용하여 Visual Studio 설치
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에 대 한 최신 설명서는 [명령줄 매개 변수를 사용 하 여 Visual studio 설치를](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)참조 하세요.

명령 프롬프트에서 Visual Studio 2015를 설치하는 경우 다음 명령줄 매개 변수(스위치라고도 함)를 사용할 수 있습니다.

> [!NOTE]
> 부트스트래퍼 파일이 아니라 실제 설치 관리자를 사용 하는지 확인 합니다. 예를 들어 **`vs_enterprise.exe`** *GUID*.exe vs_enterprise_ 대신를 사용 해야 합니다. [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015)에서 설치 관리자를 다운로드할 수 있습니다.

## <a name="list-of-command-line-parameters"></a>명령줄 매개 변수 목록

Visual Studio 명령줄 매개 변수는 대/소문자를 구분하지 않습니다.

|매개 변수|설명|
|---------------|-----------------|
|**/?**<br /><br /> **/help**<br /><br /> **/h**|명령줄 매개 변수를 표시합니다.|
|**/AddRemoveFeatures**|설치된 제품에서 추가하거나 제거할 기능을 지정합니다.|
|**/AdminFile** *AdminDeployment.xml*|관리 설치용으로 지정한 데이터 파일을 사용하여 Visual Studio를 설치합니다.|
|**/ChainingPackage** *BundleName*|이 번들을 연결하는 번들을 지정합니다. 고객 환경 개선 프로그램 cohort를 지정할 수도 있습니다.|
|**/CreateAdminFile \<filename>**|/AdminFile로 사용할 수 있는 제어 파일을 만들 위치를 지정합니다.|
|**/CustomInstallPath** *InstallationDirectory*|지정한 디렉터리에 대상 변경 가능 패키지를 모두 설치합니다.|
|**/ForceRestart**|설치 후 항상 컴퓨터를 다시 시작합니다.|
|**/full**|모든 제품 기능을 설치합니다.|
|**/InstallSelectableItems \<item name 1> [; \<item name 2> ]**|설치 마법사의 선택 화면에서 선택할 선택 트리 항목의 목록입니다.|
|**/l**<br /><br /> **/Log** *파일 이름*|로그 파일의 위치를 지정합니다.|
|**/layout** *디렉터리*|설치 미디어에 있는 파일을 지정한 디렉터리로 복사합니다.|
|**/NoCacheOnlyMode**|패키지 캐시 미리 채우기를 방지합니다.|
|**/NoRefresh**|필수 또는 권장 업데이트 버전에 대해 이 제품의 최신 버전을 선택할 수 없게 합니다.|
|**/norestart**|설치 애플리케이션에서 설치 중 또는 설치 후 컴퓨터를 다시 시작하지 않습니다. 찾으려는 반환 코드에 대한 [Visual Studio 관리자 가이드](../install/visual-studio-administrator-guide.md)의 반환 코드 섹션을 참조하세요.|
|**/noweb**|인터넷에서 설치하지 않습니다.|
|**/OverrideFeedUri \<path to feed file>**|소프트웨어 항목을 설명하는 로컬 외부 피드에 대한 경로|
|**/ProductKey**<br /><br /> *ProductKey*|대시를 포함하지 않고 24자 이하로 이루어진 사용자 지정 제품 키를 설정합니다.|
|**/PromptRestart**|컴퓨터를 다시 시작하기 전에 사용자에게 메시지를 표시합니다.|
|**/q**<br /><br /> **/quiet**<br /><br /> **/s**<br /><br /> **/silent**|설치 애플리케이션의 UI(사용자 인터페이스)를 표시하지 않습니다. Visual Studio가 이미 설치되어 있는 경우 이 매개 변수 외에 다른 매개 변수를 지정하지 않으면 설치 애플리케이션이 유지 관리 모드로 실행됩니다.|
|**/qb**<br /><br /> **/passive**|진행률이 표시되지만 사용자 입력을 기다리지 않습니다.|
|**/repair**|Visual Studio를 복구합니다.|
|**/SuppressRefreshPrompt**|설치 마법사에 업데이트 사용 가능 대화 상자가 표시되지 않도록 하므로 설치 마법사가 필수 또는 권장 업데이트 버전을 자동으로 수락합니다.|
|**/u**<br /><br /> **/Uninstall**|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 제거합니다.|
|**/Uninstall/Force**<br /><br /> **/u /force**|Visual Studio 및 다른 제품과 공유하는 모든 기능을 제거합니다. **경고:**  이 매개 변수를 사용 하는 경우 같은 컴퓨터에 설치 된 다른 제품이 제대로 작동 하지 않을 수 있습니다.|

## <a name="see-also"></a>관련 항목

- [Visual Studio 관리자 가이드](../install/visual-studio-administrator-guide.md)