---
title: SccUncheckout 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4317133b2f215e0f9af447e5c042785561231f63
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700241"
---
# <a name="sccuncheckout-function"></a>SccUncheckout 함수
이 함수는 이전 체크 아웃 작업을 취소하여 선택한 파일 또는 파일의 내용을 체크 아웃 전에 상태로 복원합니다. 체크 아웃 이후 파일에 대한 모든 변경 내용이 손실됩니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccUncheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>매개 변수
 pvContext

【인】 소스 제어 플러그인 컨텍스트 구조입니다.

 Hwnd

【인】 소스 제어 플러그인이 제공하는 모든 대화 상자에 대한 상위로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 n파일

【인】 배열에 지정된 파일 `lpFileNames` 수입니다.

 lpFile 이름

【인】 체크 아웃을 취소할 파일의 정규화된 로컬 경로 이름 배열입니다.

 f옵션

【인】 명령 플래그(사용되지 않음).

 pv옵션

【인】 소스 제어 플러그인 관련 옵션.

## <a name="return-value"></a>Return Value
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|취소 체크 아웃이 성공했습니다.|
|SCC_E_FILENOTCONTROLLED|선택한 파일이 소스 코드 제어하에 있지 않습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 소스 제어 시스템에 액세스하는 데 문제가 있었습니다. 다시 시도하는 것이 좋습니다.|
|SCC_E_NONSPECIFICERROR|비특정 오류입니다. 취소 체크 아웃이 성공하지 못했습니다.|
|SCC_E_NOTCHECKEDOUT|사용자가 파일을 체크 아웃하지 않았습니다.|
|SCC_E_NOTAUTHORIZED|사용자는 이 작업을 수행할 수 없습니다.|
|SCC_E_PROJNOTOPEN|소스 제어에서 프로젝트가 열리지 않았습니다.|
|SCC_I_OPERATIONCANCELED|작업이 완료되기 전에 취소되었습니다.|

## <a name="remarks"></a>설명
 이 작업이 끝나면 `SCC_STATUS_CHECKEDOUT` `SCC_STATUS_MODIFIED` 취소 체크 아웃이 수행된 파일에 대해 및 플래그가 모두 지워집니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
