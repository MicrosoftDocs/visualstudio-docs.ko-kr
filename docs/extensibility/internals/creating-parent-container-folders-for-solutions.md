---
title: 솔루션용 부모 컨테이너 폴더 만들기 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709095"
---
# <a name="create-parent-container-folders-for-solutions"></a>솔루션용 부모 컨테이너 폴더 만들기
소스 제어 플러그 인 API 버전 1.2에서 사용자는 솔루션 내의 모든 웹 프로젝트에 대 한 단일 루트 소스 제어 대상을 지정할 수 있습니다. 이 단일 루트를 성 (Super 단일화 Root) 라고 합니다.

 소스 제어 플러그 인 API 버전 1.1에서 사용자가 소스 제어에 다중 프로젝트 솔루션을 추가한 경우 각 웹 프로젝트에 대해 하나의 소스 제어 대상을 지정 하 라는 메시지가 표시 됩니다.

## <a name="new-capability-flags"></a>새 기능 플래그
 `SCC_CAP_CREATESUBPROJECT`

 `SCC_CAP_GETPARENTPROJECT`

## <a name="new-functions"></a>새로운 함수
- [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)

- [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE는 솔루션을 소스 제어에 추가할 때 거의 항상 성 폴더를 만듭니다. 특히 다음과 같은 경우에이 작업을 수행 합니다.

- 프로젝트는 파일 공유 웹 프로젝트입니다.

- 프로젝트와 솔루션 파일에는 서로 다른 드라이브가 있습니다.

- 프로젝트와 솔루션 파일에 대해 서로 다른 공유가 있습니다.

- 소스 제어 솔루션에서 프로젝트를 개별적으로 추가 했습니다.

에서 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 성 폴더의 이름은 확장명이 없는 솔루션 이름과 동일 하 게 사용 하는 것이 좋습니다. 다음 표에는 두 버전의 동작이 요약 되어 있습니다.

|기능|소스 제어 플러그 인 API 버전 1.1|소스 제어 플러그 인 API 버전 1.2|
|-------------| - | - |
|SCC에 솔루션 추가|SccInitialize ()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject ()|SccInitialize ()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject ()|
|소스 제어 솔루션에 프로젝트 추가|SccGetProjPath()<br /><br /> OpenProject ()|SccGetParentProjectPath()<br /><br /> SccOpenProject ()<br /><br />  **참고:**  Visual Studio에서는 솔루션이 성의 직계 자식인 것으로 가정 합니다.|

## <a name="examples"></a>예제
 다음 표에서는 두 가지 예를 보여 줍니다. 두 경우 모두 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]  *user_choice* 대상으로 지정 될 때까지 소스 제어에서 솔루션의 대상 위치를 묻는 메시지가 사용자에 게 표시 됩니다. User_choice 지정 하면 사용자에 게 소스 제어 대상에 대 한 메시지를 표시 하지 않고 솔루션과 두 개의 프로젝트가 추가 됩니다.

|솔루션 포함|디스크 위치|데이터베이스 기본 구조|
|-----------------------|-----------------------|--------------------------------|
|*sln1*<br /><br /> Web1<br /><br /> Web2|*C:\Solutions\sln1*<br /><br /> *C:\Inetpub\wwwroot\Web1*<br /><br /> \\\server\wwwroot $ \Web2|$/<user_choice>/sln 1<br /><br /> $/<user_choice>/C/Web1<br /><br /> $/<user_choice>/Web2|
|*sln1*<br /><br /> Web1<br /><br /> Win1|*C:\Solutions\sln1*<br /><br /> *D:\Inetpub\wwwroot\Web1*<br /><br /> *C:\s\s\sln1\win1*|$/<user_choice>/sln 1<br /><br /> $/<user_choice>/D/web1<br /><br /> $/<user_choice>/sln1/win1|

 성 폴더와 하위 폴더는 오류로 인해 작업이 취소 되거나 실패 하는지 여부에 관계 없이 생성 됩니다. 이러한 오류는 취소 또는 오류 조건에서 자동으로 제거 되지 않습니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 소스 제어 플러그 인에서 `SCC_CAP_CREATESUBPROJECT` 및 기능 플래그를 반환 하지 않는 경우 기본값은 버전 1.1 동작입니다 `SCC_CAP_GETPARENTPROJECT` . 또한 사용자는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 다음 키의 값을 *dword: 00000001*로 설정 하 여 버전 1.1 동작으로 되돌릴 수 있습니다.

 **[HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0\sourcecontrol] DoNotCreateSolutionRootFolderInSourceControl**  =  *dword: 00000001*

## <a name="see-also"></a>참고 항목
- [소스 제어 플러그 인 API 버전 1.2의 새로운 기능](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
