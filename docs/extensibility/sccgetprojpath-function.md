---
title: SccGetProjPath 함수 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700699"
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath 함수
이 함수는 소스 제어 플러그 인에만 의미가 있는 문자열인 프로젝트 경로를 사용자에 게 묻는 메시지를 표시 합니다. 사용자가 다음과 같은 경우 호출 됩니다.

- 새 프로젝트 만들기

- 버전 제어에 기존 프로젝트 추가

- 기존 버전 제어 프로젝트를 찾으려고 시도 하는 중

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

진행 소스 제어 플러그 인 컨텍스트 구조입니다.

 hWnd

진행 소스 제어 플러그 인이 제공 하는 대화 상자의 부모로 사용할 수 있는 IDE 창에 대 한 핸들입니다.

 lpUser

[in, out] 사용자 이름 (NULL 종결자를 포함 하 여 SCC_USER_SIZE를 초과 하지 않음)

 lpProjName

[in, out] IDE 프로젝트, 프로젝트 작업 영역 또는 메이크파일의 이름입니다 (NULL 종결자를 포함 하 여 SCC_PRJPATH_SIZE를 초과 하지 않음).

 lpLocalPath

[in, out] 프로젝트의 작업 경로입니다. `bAllowChangePath`가 이면 `TRUE` 소스 제어 플러그 인에서이 문자열을 수정할 수 있습니다 (null 종결자를 포함 하 여 _MAX_PATH를 초과 하지 않음).

 lpAuxProjPath

[in, out] 반환 된 프로젝트 경로에 대 한 버퍼입니다 (NULL 종결자를 포함 하 여 SCC_PRJPATH_SIZE를 초과 하지 않음).

 bAllowChangePath

진행 이 경우 `TRUE` 소스 제어 플러그 인에서 문자열을 확인 하 고 수정할 수 있습니다 `lpLocalPath` .

 Pnew

[in, out] 에서 제공 되는 값은 새 프로젝트를 만들지 여부를 나타냅니다. 반환 된 값은 프로젝트를 만든 성공을 나타냅니다.

|수신|해석|
|--------------|--------------------|
|TRUE|사용자가 새 프로젝트를 만들 수 있습니다.|
|FALSE|사용자가 새 프로젝트를 만들 수 없습니다.|

|나가는 포트|해석|
|--------------|--------------------|
|TRUE|새 프로젝트를 만들었습니다.|
|FALSE|기존 프로젝트를 선택 했습니다.|

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|프로젝트를 만들거나 검색 했습니다.|
|SCC_I_OPERATIONCANCELED|작업이 취소되었습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 원본 제어 시스템에 액세스 하는 동안 문제가 발생 했습니다.|
|SCC_E_CONNECTIONFAILURE|원본 제어 시스템에 연결 하는 동안 문제가 발생 했습니다.|
|SCC_E_NONSPECIFICERROR|지정되지 않은 오류가 발생했습니다.|

## <a name="remarks"></a>설명
 이 함수의 목적은 IDE에서 및 매개 변수를 얻기 위한 것입니다 `lpProjName` `lpAuxProjPath` . 원본 제어 플러그 인은 사용자에 게이 정보를 입력 하 라는 메시지를 표시 한 후이 두 문자열을 다시 IDE에 전달 합니다. IDE는 이러한 문자열을 솔루션 파일에 유지 하 고 사용자가이 프로젝트를 열 때마다 [Sccopenproject](../extensibility/sccopenproject-function.md) 에 전달 합니다. 이러한 문자열을 통해 플러그 인은 프로젝트와 관련 된 정보를 추적할 수 있습니다.

 함수를 처음 호출 하면 `lpAuxProjPath` 이 빈 문자열로 설정 됩니다. `lProjName` 는 비어 있을 수도 있고, 소스 제어 플러그 인이 사용 하거나 무시할 수 있는 IDE 프로젝트 이름을 포함할 수도 있습니다. 함수가 성공적으로 반환 되 면 플러그 인은 해당 하는 두 문자열을 반환 합니다. IDE는 이러한 문자열을 가정 하지 않으며 사용 하지 않으며 사용자가 수정할 수 없도록 합니다. 사용자가 설정을 변경 하려는 경우 IDE는 `SccGetProjPath` 이전에 받은 값과 동일한 값을 전달 하 여를 다시 호출 합니다. 이를 통해 플러그 인은 이러한 두 문자열을 완벽 하 게 제어할 수 있습니다.

 의 경우 `lpUser` IDE는 사용자 이름을 전달할 수도 있고, 빈 문자열에 대 한 포인터를 전달 하기만 할 수도 있습니다. 사용자 이름이 있으면 원본 제어 플러그 인에서이를 기본값으로 사용 해야 합니다. 그러나 이름이 전달 되지 않았거나 지정 된 이름으로 로그인이 실패 한 경우 플러그 인은 사용자에 게 로그인을 요청 하 고 `lpUser` 유효한 로그인을 받을 때이 이름을 다시 전달 해야 합니다. 플러그 인이이 문자열을 변경할 수 있으므로 IDE는 항상 크기 (+ 1)의 버퍼를 할당 `SCC_USER_LEN` 합니다.

> [!NOTE]
> IDE에서 수행 하는 첫 번째 작업은 함수 또는 함수에 대 한 호출 일 수 있습니다 `SccOpenProject` `SccGetProjPath` . 따라서 둘 다 동일한 `lpUser` 매개 변수를 사용 하 여 소스 제어 플러그 인이 사용자를 어느 때에도 로그인 할 수 있도록 합니다. 함수에서 반환 된 오류를 나타내는 경우에도 플러그 인은이 문자열을 유효한 로그인 이름으로 채워야 합니다.

 `lpLocalPath` 사용자가 프로젝트를 유지 하는 디렉터리입니다. 빈 문자열일 수 있습니다. 사용자가 소스 제어 시스템에서 프로젝트를 다운로드 하려고 시도 하는 경우와 같이 현재 정의 된 디렉터리가 없는 경우에 `bAllowChangePath` 는 `TRUE` 소스 제어 플러그 인에서 사용자에 게 입력을 요청 하거나 다른 메서드를 사용 하 여 해당 문자열을에 삽입할 수 있습니다 `lpLocalPath` . `bAllowChangePath`가 이면 `FALSE` 사용자가 이미 지정 된 디렉터리에서 작업 중 이므로 플러그 인에서 문자열을 변경 하지 않아야 합니다.

 사용자가 소스 제어에서 새 프로젝트를 만드는 경우 소스 제어 플러그 인이 호출 될 때 소스 제어 시스템에서 실제로이를 만들지 않을 수 있습니다 `SccGetProjPath` . 대신,에 대 한 0이 아닌 값과 함께 문자열을 다시 전달 `pbNew` 합니다 .이 경우에는 프로젝트가 소스 제어 시스템에 생성 됩니다.

 예를 들어 Visual Studio의 **새 프로젝트** 마법사에서 사용자가 프로젝트를 소스 제어에 추가 하는 경우 visual studio는이 함수를 호출 하 고 플러그 인은 소스 제어 시스템에서 visual studio 프로젝트를 포함 하는 새 프로젝트를 만들 수 있는지 여부를 확인 합니다. 마법사를 완료 하기 전에 사용자가 **취소** 를 클릭 하면 프로젝트가 생성 되지 않습니다. 사용자가 **확인**을 클릭 하면 Visual Studio가를 호출 하 `SccOpenProject` 고를 전달 `SCC_OPT_CREATEIFNEW` 하며 소스 제어 프로젝트가 생성 됩니다.

## <a name="see-also"></a>추가 정보
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
