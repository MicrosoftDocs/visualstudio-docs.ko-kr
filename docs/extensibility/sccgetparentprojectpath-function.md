---
description: 이 함수는 지정된 프로젝트의 부모 프로젝트 경로를 결정합니다.
title: SccGetParentProjectPath 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 13a0a77808004c7bc8f408bbf34a3ed4f0715b36
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900137"
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath 함수
이 함수는 지정된 프로젝트의 부모 프로젝트 경로를 결정합니다. 이 함수는 사용자가 소스 제어에 Visual Studio 프로젝트를 추가할 때 호출됩니다.

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

[in] 소스 제어 플러그 인 컨텍스트 포인터입니다.

 Hwnd

[in] 소스 제어 플러그 인이 제공하는 모든 대화 상자의 부모로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 lpUser

[in, out] 사용자 이름(NULL 종결자를 포함하여 최대 SCC_USER_SIZE)입니다.

 lpProjPath

[in] 프로젝트 경로를 식별하는 문자열입니다(NULL 종결자를 포함하여 최대 SCC_PRJPATH_SIZE).

 lpAuxProjPath

[in, out] 프로젝트를 식별하는 보조 문자열입니다(NULL 종결자를 포함하여 최대 SCC_PRJPATH_SIZE).

 lpParentProjPath

[in, out] 부모 프로젝트 경로를 식별하는 출력 문자열입니다(NULL 종결자를 포함하여 최대 SCC_PRJPATH_SIZE).

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|부모 프로젝트 경로를 성공적으로 얻었습니다.|
|SCC_E_INITIALIZEFAILED|프로젝트를 초기화할 수 없습니다.|
|SCC_E_INVALIDUSER|사용자가 소스 제어 플러그 인에 로그인할 수 없습니다.|
|SCC_E_UNKNOWNPROJECT|프로젝트는 소스 제어 플러그 인에서 알 수 없습니다.|
|SCC_E_INVALIDFILEPATH|잘못되었거나 사용할 수 없는 파일 경로입니다.|
|SCC_E_NOTAUTHORIZED|사용자가 이 작업을 수행할 수 없습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 소스 제어 시스템에 액세스하는 데 문제가 있었습니다. 다시 시도 하는 것이 좋습니다.|
|SCC_E_PROJSYNTAXERR|프로젝트 구문이 잘못되었습니다.|
|SCC_E_CONNECTIONFAILURE|연결 문제를 저장합니다.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|지정되지 않은 오류입니다.|

## <a name="remarks"></a>설명
 이 함수는 성공 또는 실패 코드를 반환하고 성공하면 `lpParentProjPath` 변수를 지정된 프로젝트의 전체 프로젝트 경로로 채웁니다.

 이 함수는 기존 프로젝트의 부모 프로젝트 경로를 반환합니다. 루트 프로젝트의 경우 함수는 전달된 프로젝트 경로(즉, 동일한 루트 프로젝트 경로)를 반환합니다. 프로젝트 경로는 소스 제어 플러그 인에만 의미가 있는 문자열입니다.

 IDE는 및 매개 변수에 대한 변경 내용을 수락할 준비가 되어 `lpUser` `lpAuxProjPath` 있습니다. IDE는 이러한 문자열을 유지하며 사용자가 나중에 이 프로젝트를 열 때 [SccOpenProject에](../extensibility/sccopenproject-function.md) 전달합니다. 따라서 이러한 문자열은 소스 제어 플러그 인이 프로젝트와 연결하는 데 필요한 정보를 추적하는 방법을 제공합니다.

 이 함수는 사용자에게 프로젝트를 선택하라는 메시지가 표시되지 않는다는 점을 제외하고 [SccGetProjPath와](../extensibility/sccgetprojpath-function.md)비슷합니다. 또한 새 프로젝트를 만들 수는 없지만 기존 프로젝트에서만 작동합니다.

 가 호출될 때 `SccGetParentProjectPath` 및 는 비어 있지 않으며 유효한 프로젝트에 `lpProjPath` `lpAuxProjPath` 해당합니다. 이러한 문자열은 일반적으로 함수에 대한 이전 호출에서 IDE에 의해 `SccGetProjPath` 수신됩니다.

 `lpUser`인수는 사용자 이름입니다. IDE는 이전에 함수에서 받은 것과 동일한 사용자 이름을 `SccGetProjPath` 전달하며 소스 제어 플러그 인은 이름을 기본값으로 사용해야 합니다. 사용자가 이미 플러그 인과 연결된 경우 플러그 인은 함수가 자동으로 작동하는지 확인하기 위해 프롬프트를 제거해야 합니다. 그러나 로그인에 실패하면 플러그 인에서 사용자에게 로그인을 요청하는 메시지를 표시하고 유효한 로그인을 받으면 이름을 에 다시 전달해야 `lpUser` 합니다. 플러그 인이 이 문자열을 변경할 수 있으므로 IDE는 항상 크기( `SCC_USER_LEN` +1)의 버퍼를 할당합니다. 문자열이 변경된 경우 새 문자열은 유효한 로그인 이름(적어도 이전 문자열만큼 유효)이어야 합니다.

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>SccCreateSubProject 및 SccGetParentProjectPath에 대한 기술 정보
 소스 제어에 솔루션 및 프로젝트 추가는 Visual Studio 사용자가 소스 제어 시스템에서 위치를 선택하라는 메시지가 표시되는 횟수를 최소화하기 위해 간소화되었습니다. 이러한 변경 내용은 소스 제어 플러그 인이 새 함수인 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) 및 함수를 모두 지원하는 경우 Visual Studio 의해 `SccGetParentProjectPath` 활성화됩니다. 그러나 다음 레지스트리 항목을 사용하여 이러한 변경 내용을 사용하지 않도록 설정하고 이전 Visual Studio(소스 제어 플러그 인 API 버전 1.1) 동작으로 되돌릴 수 있습니다.

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001**

 이 레지스트리 항목이 없거나 dword:000000000으로 설정된 경우 Visual Studio 새 함수 및 를 사용하려고 `SccCreateSubProject` `SccGetParentProjectPath` 시도합니다.

 레지스트리 항목이 dword:00000001로 설정된 경우 Visual Studio 이러한 새 함수를 사용하지 않으며 소스 제어에 를 추가하는 작업은 이전 버전의 Visual Studio 작동합니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
