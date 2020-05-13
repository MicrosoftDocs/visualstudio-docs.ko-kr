---
title: SccOpen프로젝트 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fbf566e593bb1ddbc31c70de1570d746a14fbdcf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700574"
---
# <a name="sccopenproject-function"></a>SccOpenProject 함수
이 함수는 기존 소스 제어 프로젝트를 열거나 새 소스를 만듭니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccOpenProject (
   LPVOID        pvContext,
   HWND          hWnd,
   LPSTR         lpUser,
   LPCSTR        lpProjName,
   LPCSTR        lpLocalProjPath,
   LPSTR         lpAuxProjPath,
   LPCSTR        lpComment,
   LPTEXTOUTPROC lpTextOutProc,
   LONG          dwFlags
);
```

#### <a name="parameters"></a>매개 변수
 pvContext

【인】 소스 제어 플러그인 컨텍스트 구조입니다.

 Hwnd

【인】 소스 제어 플러그인이 제공하는 모든 대화 상자에 대한 상위로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 lpUser

【인, 아웃】 사용자의 이름(null 종사 포함 SCC_USER_SIZE 초과하지 않음).

 lpProjName

【인】 프로젝트 이름을 식별하는 문자열입니다.

 lp로컬프로지패스

【인】 프로젝트의 작업 폴더에 대한 경로입니다.

 lpAuxProjPath

【인, 아웃】 프로젝트를 식별하는 선택적 보조 문자열(NULL 종단을 포함하여 SCC_AUXPATH_SIZE 초과하지 않음).

 lpComment

【인】 생성중인 새 프로젝트에 주석을 달 수 있습니다.

 lpTextOutProc

【인】 소스 제어 플러그인의 텍스트 출력을 표시하는 선택적 콜백 기능입니다.

 dwFlags

【인】 소스 제어 플러그인에 프로젝트를 알 수 없는 경우 새 프로젝트를 만들어야 하는지 여부를 알 수 있습니다. 값은 `SCC_OP_CREATEIFNEW``SCC_OP_SILENTOPEN.`

## <a name="return-value"></a>Return Value
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|프로젝트 열기성공.|
|SCC_E_INITIALIZEFAILED|프로젝트를 초기화할 수 없습니다.|
|SCC_E_INVALIDUSER|사용자가 소스 제어 시스템에 로그인할 수 없습니다.|
|SCC_E_COULDNOTCREATEPROJECT|호출 이전에 프로젝트가 존재하지 않았습니다.  플래그가 `SCC_OPT_CREATEIFNEW` 설정되었지만 프로젝트를 만들 수 없습니다.|
|SCC_E_PROJSYNTAXERR|잘못된 프로젝트 구문입니다.|
|SCC_E_UNKNOWNPROJECT|프로젝트는 소스 제어 플러그인에 알 수 없으며 `SCC_OPT_CREATEIFNEW` 플래그가 설정되지 않았습니다.|
|SCC_E_INVALIDFILEPATH|잘못되었거나 사용할 수 없는 파일 경로입니다.|
|SCC_E_NOTAUTHORIZED|사용자는 이 작업을 수행할 수 없습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 소스 제어 시스템에 액세스하는 데 문제가 있었습니다. 다시 시도하는 것이 좋습니다.|
|SCC_E_NONSPECFICERROR|비특이적 오류; 소스 제어 시스템이 초기화되지 않았습니다.|

## <a name="remarks"></a>설명
 IDE는 사용자 이름()으로`lpUser`전달되거나 포인터를 빈 문자열로 전달할 수 있습니다. 사용자 이름이 있는 경우 소스 제어 플러그인을 기본값으로 사용해야 합니다. 그러나 이름이 전달되지 않았거나 지정된 이름으로 로그인에 실패한 경우 플러그인은 사용자에게 로그인하라는 메시지를 표시하고 유효한 SCC_USER_SIZE `lpUser` 로그인을`.` `SCC_USER_LEN`받을 때 유효한 이름을 반환해야 합니다.

> [!NOTE]
> IDE가 수행해야 할 첫 번째 작업은 `SccOpenProject` 함수 또는 [SccGetProjPath에](../extensibility/sccgetprojpath-function.md)대한 호출일 수 있습니다. 이러한 이유로 둘 다 동일한 `lpUser` 매개 변수를 갖습니다.

 `lpAuxProjPath`솔루션`lpProjName` 파일에서 읽거나 `SccGetProjPath` 함수에 대한 호출에서 반환됩니다. 이러한 매개 변수에는 소스 제어 플러그인이 프로젝트와 연결되고 플러그인에만 의미가 있는 문자열이 포함됩니다. 이러한 문자열이 솔루션 파일에 없고 사용자가 찾아보라는 메시지가 표시되지 않은 `SccGetProjPath` 경우(함수를 통해 문자열을 반환하는) IDE는 빈 문자열을 모두 `lpAuxProjPath` `lpProjName`전달하고 이 함수가 반환될 때 플러그인에서 이러한 값을 업데이트할 것으로 예상합니다.

 `lpTextOutProc`는 명령 결과 출력을 표시하기 위해 소스 제어 플러그인에 IDE에서 제공하는 콜백 함수에 대한 포인터입니다. 이 콜백 함수는 [LPTEXTOUTPROC에](../extensibility/lptextoutproc.md)자세히 설명되어 있습니다.

> [!NOTE]
> 소스 제어 플러그인이 이를 활용하려는 경우 `SCC_CAP_TEXTOUT` [SccInitialize에서](../extensibility/sccinitialize-function.md)플래그를 설정해야 합니다. 해당 플래그가 설정되지 않았거나 IDE가 이 기능을 `lpTextOutProc` 지원하지 `NULL`않는 경우 .

 매개 `dwFlags` 변수는 열려 있는 프로젝트가 현재 존재하지 않는 경우 결과를 제어합니다. 두 개의 비트 `SCC_OP_CREATEIFNEW` 플래그와 `SCC_OP_SILENTOPEN`. 열려 있는 프로젝트가 이미 있는 경우 함수는 프로젝트를 `SCC_OK`열고 반환합니다. 프로젝트가 존재하지 않고 플래그가 `SCC_OP_CREATEIFNEW` 있는 경우 소스 제어 플러그인은 소스 제어 시스템에서 프로젝트를 만들고 열어 반환할 `SCC_OK`수 있습니다. 프로젝트가 존재하지 않고 플래그가 `SCC_OP_CREATEIFNEW` 꺼져 있으면 플러그인에서 플래그를 `SCC_OP_SILENTOPEN` 확인해야 합니다. 해당 플래그가 켜지지 않은 경우 플러그인은 사용자에게 프로젝트 이름을 묻는 메시지를 표시할 수 있습니다. 해당 플래그가 켜지면 플러그인이 단순히 `SCC_E_UNKNOWNPROJECT`반환됩니다.

## <a name="calling-order"></a>통화 순서
 일반적인 이벤트 과정에서 [SccInitialize는](../extensibility/sccinitialize-function.md) 소스 제어 세션을 열기 위해 먼저 호출됩니다. 세션은 에 대한 `SccOpenProject`호출로 구성될 수 있으며, 다음에 다른 소스 제어 플러그인 API 함수 호출이 있을 수 있으며 [SccCloseProject](../extensibility/scccloseproject-function.md)에 대한 호출로 종료됩니다. 이러한 세션은 [SccUninitialize가](../extensibility/sccuninitialize-function.md) 호출되기 전에 여러 번 반복될 수 있습니다.

 소스 제어 플러그인이 `SCC_CAP_REENTRANT` 비트를 설정하는 `SccInitialize`경우, 위의 세션 시퀀스는 병렬로 여러 번 반복될 수 있다. 서로 `pvContext` 다른 구조는 서로 다른 `pvContext` 세션을 추적하며, 각 세션은 한 번에 하나의 열린 프로젝트와 연결됩니다. 매개 변수에`pvContext` 따라 플러그인은 특정 호출에서 참조되는 프로젝트를 결정할 수 있습니다. 기능 비트가 `SCC_CAP_REENTRANT` 설정되지 않은 경우 비재원 소스 제어 플러그인은 여러 프로젝트에서 작업하는 기능이 제한됩니다.

> [!NOTE]
> 비트는 `SCC_CAP_REENTRANT` 소스 제어 플러그인 API의 버전 1.1에 도입되었습니다. 버전 1.0에서 설정되지 않았거나 무시되며 모든 버전 1.0 소스 제어 플러그인은 비반복으로 가정됩니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [문자열 길이에 대한 제한](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
