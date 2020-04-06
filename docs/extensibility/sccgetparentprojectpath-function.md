---
title: SccGetParent프로젝트패스 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f258558207f86ff76746d18aa432fe4c5850290
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700707"
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParent프로젝트패스 기능
이 함수는 지정된 프로젝트의 상위 프로젝트 경로를 결정합니다. 이 함수는 사용자가 소스 컨트롤에 Visual Studio 프로젝트를 추가할 때 호출됩니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccGetParentProjectPath(
   LPVOID pContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPCSTR lpProjPath,
   LPSTR  lpAuxProjPath,
   LPSTR  lpParentProjPath
);
```

### <a name="parameters"></a>매개 변수
 pContext

【인】 소스 제어 플러그인 컨텍스트 포인터입니다.

 Hwnd

【인】 소스 제어 플러그인이 제공하는 모든 대화 상자에 대한 상위로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 lpUser

【인, 아웃】 사용자 이름(NULL 종사 포함 SCC_USER_SIZE).

 lpProjPath

【인】 프로젝트 경로를 식별하는 문자열(NULL 종기 포함 SCC_PRJPATH_SIZE).

 lpAuxProjPath

【인, 아웃】 프로젝트를 식별하는 보조 문자열(NULL 종기 포함 최대 SCC_PRJPATH_SIZE).

 lpParentProjPath

【인, 아웃】 상위 프로젝트 경로를 식별하는 출력 문자열(NULL 종기 포함 SCC_PRJPATH_SIZE).

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|상위 프로젝트 경로를 성공적으로 얻었습니다.|
|SCC_E_INITIALIZEFAILED|프로젝트를 초기화할 수 없습니다.|
|SCC_E_INVALIDUSER|사용자가 소스 제어 플러그인에 로그인할 수 없습니다.|
|SCC_E_UNKNOWNPROJECT|프로젝트는 소스 제어 플러그인에 알 수 없습니다.|
|SCC_E_INVALIDFILEPATH|잘못되었거나 사용할 수 없는 파일 경로입니다.|
|SCC_E_NOTAUTHORIZED|사용자는 이 작업을 수행할 수 없습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 소스 제어 시스템에 액세스하는 데 문제가 있었습니다. 다시 시도하는 것이 좋습니다.|
|SCC_E_PROJSYNTAXERR|잘못된 프로젝트 구문입니다.|
|SCC_E_CONNECTIONFAILURE|저장소 연결 문제.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|비특정 오류입니다.|

## <a name="remarks"></a>설명
 이 함수는 성공 또는 실패 코드를 반환하고 성공하면 지정된 프로젝트에 대한 전체 프로젝트 경로로 변수를 `lpParentProjPath` 채웁니다.

 이 함수는 기존 프로젝트의 상위 프로젝트 경로를 반환합니다. 루트 프로젝트의 경우 함수는 전달된 프로젝트 경로(즉, 동일한 루트 프로젝트 경로)를 반환합니다. 프로젝트 경로는 소스 제어 플러그인에만 의미 있는 문자열입니다.

 IDE는 `lpUser` 및 `lpAuxProjPath` 매개 변수에 대한 변경 내용도 수락할 준비가 되어 있습니다. IDE는 이러한 문자열을 유지 하 고 사용자가 나중에이 프로젝트를 열 때 [SccOpenProject에](../extensibility/sccopenproject-function.md) 전달 합니다. 따라서 이러한 문자열은 소스 제어 플러그인이 프로젝트와 연결하는 데 필요한 정보를 추적할 수 있는 방법을 제공합니다.

 이 함수는 사용자에게 프로젝트를 선택하라는 메시지를 표시하지 않는다는 점을 제외하면 [SccGetProjPath와](../extensibility/sccgetprojpath-function.md)유사합니다. 또한 새 프로젝트를 생성하지 않지만 기존 프로젝트에서만 작동합니다.

 호출될 `SccGetParentProjectPath` 때 `lpProjPath` `lpAuxProjPath` 비어 있지 않으며 유효한 프로젝트에 해당합니다. 이러한 문자열은 일반적으로 `SccGetProjPath` 함수에 대한 이전 호출에서 IDE에 의해 수신됩니다.

 인수는 `lpUser` 사용자 이름입니다. IDE는 `SccGetProjPath` 함수에서 이전에 받은 것과 동일한 사용자 이름으로 전달되며 소스 제어 플러그인은 이름을 기본값으로 사용해야 합니다. 사용자가 이미 플러그인과 열린 연결을 가지고 있는 경우 플러그인은 함수가 자동으로 작동하는지 확인하기 위해 프롬프트를 제거해야 합니다. 그러나 로그인에 실패하면 플러그인은 사용자에게 로그인하라는 메시지를 표시하고 유효한 로그인을 받으면 에 이름을 다시 `lpUser`전달해야 합니다. 플러그인이 이 문자열을 변경할 수 있으므로 IDE는 항상 크기`SCC_USER_LEN`버퍼(+1)를 할당합니다. 문자열이 변경되면 새 문자열은 유효한 로그인 이름이어야 합니다(적어도 이전 문자열만큼 유효).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>SccCreate서브프로젝트 및 SccGetParentProjectPath에 대한 기술 노트
 소스 제어에 솔루션 및 프로젝트를 추가하는 것이 Visual Studio에서 단순화되어 사용자가 소스 제어 시스템의 위치를 선택하라는 메시지가 표시되는 횟수를 최소화했습니다. 소스 제어 플러그인이 새 기능인 [SccCreateSubProject와](../extensibility/scccreatesubproject-function.md) 함수를 모두 지원하는 경우 이러한 `SccGetParentProjectPath` 변경 내용은 Visual Studio에서 활성화됩니다. 그러나 다음 레지스트리 항목을 사용하여 이러한 변경 내용을 사용하지 않도록 설정하고 이전 Visual Studio(소스 제어 플러그인 API 버전 1.1) 동작으로 되돌릴 수 있습니다.

 **[HKEY_CURRENT_USER\소프트웨어\마이크로소프트\비주얼 스튜디오\8.0\소스 컨트롤] "DoNotCreate솔루션루트폴더인소스제어"=워드:00000001**

 이 레지스트리 항목이 없거나 dword:0000000으로 설정된 경우 Visual Studio는 새 `SccCreateSubProject`함수를`SccGetParentProjectPath`사용하려고 시도합니다.

 레지스트리 항목d:00000001로 설정된 경우 Visual Studio는 이러한 새 함수를 사용하려고 시도하지 않으며 이전 버전의 Visual Studio에서와 마찬가지로 소스 제어 작업에 추가하는 작업을 시도하지 않습니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그인 API 기능](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
