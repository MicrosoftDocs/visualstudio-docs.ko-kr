---
title: 솔루션용 상위 컨테이너 폴더 만들기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e5481e20a12fc05ccba97eef55173e5ce9b30d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709095"
---
# <a name="create-parent-container-folders-for-solutions"></a>솔루션에 대한 상위 컨테이너 폴더 만들기
소스 제어 플러그인 API 버전 1.2에서 사용자는 솔루션 내의 모든 웹 프로젝트에 대해 단일 루트 소스 제어 대상을 지정할 수 있습니다. 이 단일 루트를 수퍼 통합 루트(SUR)라고 합니다.

 소스 제어 플러그인 API 버전 1.1에서 사용자가 소스 제어에 다중 프로젝트 솔루션을 추가한 경우 사용자는 각 웹 프로젝트에 대해 하나의 소스 제어 대상을 지정하라는 메시지가 표시됩니다.

## <a name="new-capability-flags"></a>새 기능 플래그
 `SCC_CAP_CREATESUBPROJECT`

 `SCC_CAP_GETPARENTPROJECT`

## <a name="new-functions"></a>새로운 함수
- [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)

- [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)

 IDE는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 소스 제어에 솔루션을 추가할 때 거의 항상 SUR 폴더를 만듭니다. 특히 다음과 같은 경우에는 다음과 같은 경우에 수행합니다.

- 프로젝트가 파일 공유 웹 프로젝트입니다.

- 프로젝트 및 솔루션 파일에 는 다른 드라이브가 있습니다.

- 프로젝트 및 솔루션 파일에 대해 서로 다른 공유가 있습니다.

- 프로젝트는 소스 제어 솔루션에서 별도로 추가되었습니다.

에서 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]SUR 폴더의 이름은 확장이 없는 솔루션 이름과 동일합니다. 다음 표에서는 두 버전의 동작을 요약합니다.

|기능|소스 제어 플러그인 API 버전 1.1|소스 제어 플러그인 API 버전 1.2|
|-------------| - | - |
|SCC에 솔루션 추가|Scc초기화()<br /><br /> 스겟프로이패스()<br /><br /> 스겟프로이패스()<br /><br /> SccOpen프로젝트()|Scc초기화()<br /><br /> 스겟프로이패스()<br /><br /> SccCreate서브프로젝트()<br /><br /> SccCreate서브프로젝트()<br /><br /> SccOpen프로젝트()|
|소스 제어 솔루션에 프로젝트 추가|스겟프로이패스()<br /><br /> 오픈 프로젝트()|SccGet부모프로젝트패스()<br /><br /> SccOpen프로젝트()<br /><br />  **참고:**  Visual Studio는 솔루션이 SUR의 직접 자식이라고 가정합니다.|

## <a name="examples"></a>예
 다음 표에는 두 가지 예제가 나열되어 있습니다. 두 경우 모두 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] *user_choice* 대상으로 지정될 때까지 소스 제어하에 있는 솔루션의 대상 위치에 대한 메시지가 표시됩니다. user_choice 지정하면 소스 제어 대상에 대한 메시지를 표시하지 않고 솔루션과 두 프로젝트가 추가됩니다.

|솔루션에는|디스크 위치에서|데이터베이스 기본 구조|
|-----------------------|-----------------------|--------------------------------|
|*sln1.sln*<br /><br /> Web1<br /><br /> 웹 2|*C:\솔루션\sln1*<br /><br /> *C:\Inetpub\wwwroot\Web1*<br /><br /> \\\서버\wwwroot$\Web2|$/<user_choice>/sln1<br /><br /> $/<user_choice>/C/Web1<br /><br /> $/<user_choice>/웹2|
|*sln1.sln*<br /><br /> Web1<br /><br /> 승리 1|*C:\솔루션\sln1*<br /><br /> *D:\Inetpub\wwwroot\Web1*<br /><br /> *C:\솔루션\sln1\Win1*|$/<user_choice>/sln1<br /><br /> $/<user_choice>/D/web1<br /><br /> $/<user_choice>/sln1/win1|

 SUR 폴더와 하위 폴더는 오류로 인해 작업이 취소되거나 실패하는지 여부에 관계없이 만들어집니다. 취소 또는 오류 조건에서 자동으로 제거되지 는 않습니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]기본값은 소스 제어 플러그인이 반환되지 `SCC_CAP_CREATESUBPROJECT` 않고 `SCC_CAP_GETPARENTPROJECT` 기능 플래그가 있는 경우 버전 1.1 동작으로 설정됩니다. 또한 사용자는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 다음 키값을 *dword:00000001로*설정하여 버전 1.1 동작으로 되돌릴 수 있습니다.

 **[HKEY_CURRENT_USER\소프트웨어\마이크로소프트\비주얼 스튜디오\8.0\소스 컨트롤] ** = *DoNotCreate솔루션루트폴더인소스제어검:00000001*

## <a name="see-also"></a>참조
- [소스 제어 플러그인 API 버전 1.2의 새로운 소식](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
