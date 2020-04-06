---
title: 스크디르Diff 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1bb592a1174a91480ed76ef818733c288c5273c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701010"
---
# <a name="sccdirdiff-function"></a>SccDirDiff 기능
이 함수는 클라이언트 디스크의 현재 로컬 디렉터리와 소스 제어하에 있는 해당 프로젝트 간의 차이점을 표시합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccDirDiff(
   LPVOID    pContext,
   HWND      hWnd,
   LPCSTR    lpDirName,
   LONG      dwFlags,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>매개 변수
 pContext

【인】 소스 제어 플러그인 컨텍스트 구조입니다.

 Hwnd

【인】 소스 제어 플러그인이 제공하는 모든 대화 상자에 대한 상위로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 lpDirName

【인】 시각적 차이를 표시하는 로컬 디렉터리로 의한 정규화된 경로입니다.

 dwFlags

【인】 명령 플래그(비고 섹션 참조).

 pv옵션

【인】 소스 제어 플러그인 관련 옵션.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|디스크의 디렉터리도 소스 코드 제어의 프로젝트와 동일합니다.|
|SCC_I_FILESDIFFER|디스크의 디렉터리소스 코드 제어의 프로젝트와 다릅니다.|
|SCC_I_RELOADFILE|파일 또는 프로젝트를 다시 로드해야 합니다.|
|SCC_E_FILENOTCONTROLLED|디렉터리소스 코드 제어하에 있지 않습니다.|
|SCC_E_NOTAUTHORIZED|사용자는 이 작업을 수행할 수 없습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 소스 제어 시스템에 액세스하는 데 문제가 있었습니다. 다시 시도하는 것이 좋습니다.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|비특정 오류입니다.|
|SCC_E_FILENOTEXIST|로컬 디렉터리를 찾을 수 없습니다.|

## <a name="remarks"></a>설명
 이 함수는 소스 제어 플러그인이 사용자에게 지정된 디렉터리변경 사항 목록을 표시하도록 지시하는 데 사용됩니다. 플러그인은 디스크의 사용자 디렉토리와 버전 제어하에 있는 해당 프로젝트 간의 차이점을 표시하기 위해 선택한 형식으로 자체 창을 엽니다.

 플러그인이 디렉터리 비교를 전혀 지원하는 경우 "quick-diff" 옵션이 지원되지 않더라도 파일 이름 기준으로 디렉터리 비교를 지원해야 합니다.

|`dwFlags`|해석|
|---------------|--------------------|
|SCC_DIFF_IGNORECASE|대/소문자 구분 되지 않는 비교 (빠른 diff 또는 시각적에 대 한 사용할 수 있습니다).|
|SCC_DIFF_IGNORESPACE|공백을 무시합니다(빠른 diff 또는 시각적 개체에 사용할 수 있음).|
|SCC_DIFF_QD_CONTENTS|소스 제어 플러그인에서 지원하는 경우 디렉토리바이트바이트를 바이트별로 자동으로 비교합니다.|
|SCC_DIFF_QD_CHECKSUM|플러그인에서 지원되는 경우 체크섬을 통해 디렉토리를 자동으로 비교하거나 지원되지 않으면 SCC_DIFF_QD_CONTENTS 돌아갑니다.|
|SCC_DIFF_QD_TIME|플러그인에서 지원되는 경우 타임스탬프를 통해 디렉토리를 자동으로 비교하거나 지원되지 않으면 SCC_DIFF_QD_CHECKSUM 또는 SCC_DIFF_QD_CONTENTS 다시 떨어집니다.|

> [!NOTE]
> 이 함수는 [SccDiff](../extensibility/sccdiff-function.md)와 동일한 명령 플래그를 사용합니다. 그러나 소스 제어 플러그인은 디렉터리에 대한 "빠른 diff" 작업을 지원하지 않도록 선택할 수 있습니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그인 API 기능](../extensibility/source-control-plug-in-api-functions.md)
