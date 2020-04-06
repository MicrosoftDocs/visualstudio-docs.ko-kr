---
title: SccGetProjPath 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 281787da3499c081fbbe6f59b7b8175a4dbf24d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700699"
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath 함수
이 함수는 소스 제어 플러그인에만 의미 있는 문자열인 프로젝트 경로에 대 한 사용자를 묻는 메시지를 표시 합니다. 사용자가 다음과 같은 경우 호출됩니다.

- 새 프로젝트 만들기

- 버전 컨트롤에 기존 프로젝트 추가

- 기존 버전 제어 프로젝트를 찾으려고 시도

## <a name="syntax"></a>구문

```cpp
SCCRTN SccGetProjPath (
   LPVOID pvContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPSTR  lpProjName,
   LPSTR  lpLocalPath,
   LPSTR  lpAuxProjPath,
   BOOL   bAllowChangePath,
   LPBOOL pbNew
);
```

### <a name="parameters"></a>매개 변수
 pvContext

【인】 소스 제어 플러그인 컨텍스트 구조입니다.

 Hwnd

【인】 소스 제어 플러그인이 제공하는 모든 대화 상자에 대한 상위로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 lpUser

【인, 아웃】 사용자 이름(NULL 터미네이터를 포함하여 SCC_USER_SIZE 초과하지 않음)

 lpProjName

【인, 아웃】 IDE 프로젝트, 프로젝트 작업 영역 또는 makefile의 이름(NULL 종기 등 SCC_PRJPATH_SIZE 초과하지 않음).

 lp로컬패스

【인, 아웃】 프로젝트의 작업 경로입니다. `TRUE`이 경우 `bAllowChangePath` 소스 제어 플러그인은 이 문자열을 수정할 수 있습니다(null-terminator를 포함하여 _MAX_PATH 초과하지 않음).

 lpAuxProjPath

【인, 아웃】 반환된 프로젝트 경로에 대한 버퍼(NULL 종사 포함 SCC_PRJPATH_SIZE 초과하지 않음).

 bAllow변경경로

【인】 이 `TRUE`경우 소스 제어 플러그인에 대한 프롬프트를 표시하고 문자열을 수정할 `lpLocalPath` 수 있습니다.

 pbNew

【인, 아웃】 들어오는 값은 새 프로젝트를 만들지 여부를 나타냅니다. 반환된 값은 프로젝트를 만드는 데 성공했음을 나타냅니다.

|수신|해석|
|--------------|--------------------|
|TRUE|사용자는 새 프로젝트를 만들 수 있습니다.|
|FALSE|사용자가 새 프로젝트를 만들 수 없습니다.|

|발신|해석|
|--------------|--------------------|
|TRUE|새 프로젝트가 만들어졌습니다.|
|FALSE|기존 프로젝트가 선택되었습니다.|

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|프로젝트가 성공적으로 만들어지거나 검색되었습니다.|
|SCC_I_OPERATIONCANCELED|작업이 취소되었습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 소스 제어 시스템에 액세스하는 데 문제가 있었습니다.|
|SCC_E_CONNECTIONFAILURE|소스 제어 시스템에 연결하려고 하는 데 문제가 있습니다.|
|SCC_E_NONSPECIFICERROR|지정되지 않은 오류가 발생했습니다.|

## <a name="remarks"></a>설명
 이 함수의 목적은 IDE가 매개 변수 `lpProjName` `lpAuxProjPath`및 을 획득하는 것입니다. 소스 제어 플러그인이 사용자에게 이 정보를 묻는 메시지가 표시되면 이 두 문자열을 IDE로 다시 전달합니다. IDE는 솔루션 파일에 이러한 문자열을 유지 하 고 사용자가이 프로젝트를 열 때마다 [SccOpenProject에](../extensibility/sccopenproject-function.md) 전달 합니다. 이러한 문자열을 사용하면 플러그인을 사용하여 프로젝트와 관련된 정보를 추적할 수 있습니다.

 함수가 처음 호출되면 `lpAuxProjPath` 빈 문자열로 설정됩니다. `lProjName`비어 있거나 소스 제어 플러그인이 사용하거나 무시할 수 있는 IDE 프로젝트 이름이 포함될 수도 있습니다. 함수가 성공적으로 반환되면 플러그인은 두 개의 해당 문자열을 반환합니다. IDE는 이러한 문자열에 대해 가정을 하지 않으며, 문자열을 사용하지 않으며, 사용자가 해당 문자열을 수정할 수 없습니다. 사용자가 설정을 변경하려는 경우 IDE는 이전 `SccGetProjPath` 시간에 받은 것과 동일한 값을 전달하여 다시 호출합니다. 이렇게 하면 플러그인이 이 두 문자열을 완벽하게 제어할 수 있습니다.

 의 `lpUser`경우 IDE는 사용자 이름으로 전달되거나 포인터를 빈 문자열로 전달할 수 있습니다. 사용자 이름이 있는 경우 소스 제어 플러그인을 기본값으로 사용해야 합니다. 그러나 이름이 전달되지 않았거나 지정된 이름으로 로그인에 실패한 경우 플러그인은 사용자에게 로그인을 요청하고 유효한 로그인을 `lpUser` 받을 때 이름을 다시 전달해야 합니다. 플러그인이 이 문자열을 변경할 수 있으므로 IDE는 항상 크기`SCC_USER_LEN`버퍼(+1)를 할당합니다.

> [!NOTE]
> IDE가 수행하는 첫 번째 작업은 `SccOpenProject` 함수 또는 `SccGetProjPath` 함수에 대한 호출일 수 있습니다. 따라서 둘 다 동일한 `lpUser` 매개 변수를 가지므로 소스 제어 플러그인이 어느 한 번에 사용자를 로그인할 수 있습니다. 함수에서 반환하는 것이 실패를 나타내는 경우에도 플러그인은 이 문자열을 유효한 로그인 이름으로 채워야 합니다.

 `lpLocalPath`은 사용자가 프로젝트를 유지하는 디렉터리입니다. 빈 문자열일 수 있습니다. 현재 정의된 디렉터리(소스 제어 시스템에서 프로젝트를 다운로드하려는 사용자의 경우)가 없고 있는 경우 `bAllowChangePath` `TRUE`소스 제어 플러그인은 사용자에게 입력을 요청하거나 다른 메서드를 사용하여 자신의 `lpLocalPath`문자열을 에 배치할 수 있습니다. `FALSE`사용자가 `bAllowChangePath` 지정된 디렉터리에서 이미 작업 중이기 때문에 플러그인은 문자열을 변경하지 않아야 합니다.

 사용자가 소스 제어하에 놓을 새 프로젝트를 만드는 경우 소스 제어 플러그인이 호출될 때 `SccGetProjPath` 소스 제어 시스템에서 실제로 생성되지 않을 수 있습니다. 대신, 프로젝트가 소스 제어 시스템에서 생성될 `pbNew`것임을 나타내는 비영값과 함께 문자열을 다시 전달합니다.

 예를 들어 Visual Studio의 **새 프로젝트** 마법사에서 사용자가 자신의 프로젝트를 소스 제어에 추가하는 경우 Visual Studio는 이 함수를 호출하고 플러그인은 소스 제어 시스템에서 Visual Studio 프로젝트를 포함하도록 새 프로젝트를 만드는 것이 괜찮은지 결정합니다. 사용자가 마법사를 완료하기 전에 **취소를** 클릭하면 프로젝트가 만들어지지 않습니다. 사용자가 **확인을**클릭하면 Visual `SccOpenProject`Studio가 `SCC_OPT_CREATEIFNEW`호출하고 을 전달하면 소스 제어 프로젝트가 만들어집니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그인 API 기능](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
