---
description: 이 함수는 클라이언트 디스크의 현재 로컬 디렉터리와 소스 제어에 있는 해당 프로젝트 간의 차이점을 표시합니다.
title: SccDirDiff 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e938cdaedf8541d787673371cfce3d07e005711f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904645"
---
# <a name="sccdirdiff-function"></a>SccDirDiff 함수
이 함수는 클라이언트 디스크의 현재 로컬 디렉터리와 소스 제어에 있는 해당 프로젝트 간의 차이점을 표시합니다.

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

[in] 소스 제어 플러그 인 컨텍스트 구조입니다.

 Hwnd

[in] 소스 제어 플러그 인이 제공하는 모든 대화 상자의 부모로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 lpDirName

[in] 시각적 차이를 표시할 로컬 디렉터리에 대한 정규화된 경로입니다.

 dwFlags

[in] 명령 플래그(주의 섹션 참조).

 pvOptions

[in] 소스 제어 플러그 인 관련 옵션입니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|디스크의 디렉터리 는 소스 코드 제어의 프로젝트와 동일합니다.|
|SCC_I_FILESDIFFER|디스크의 디렉터리 소스 코드 제어의 프로젝트와 다릅니다.|
|SCC_I_RELOADFILE|파일 또는 프로젝트를 다시 로드해야 합니다.|
|SCC_E_FILENOTCONTROLLED|디렉터리에 소스 코드 제어가 없습니다.|
|SCC_E_NOTAUTHORIZED|사용자가 이 작업을 수행할 수 없습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 소스 제어 시스템에 액세스하는 데 문제가 있었습니다. 다시 시도 하는 것이 좋습니다.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|지정되지 않은 오류입니다.|
|SCC_E_FILENOTEXIST|로컬 디렉터리를 찾을 수 없습니다.|

## <a name="remarks"></a>설명
 이 함수는 소스 제어 플러그 인에 지정된 디렉터리에 대한 변경 내용 목록을 사용자에게 표시하도록 지시하는 데 사용됩니다. 플러그 인은 디스크의 사용자 디렉터리와 버전 제어의 해당 프로젝트 간의 차이점을 표시하기 위해 선택한 형식으로 자체 창을 엽니다.

 플러그 인이 디렉터리 비교를 지원하는 경우 "quick-diff" 옵션이 지원되지 않는 경우에도 파일 이름별로 디렉터리 비교를 지원해야 합니다.

|`dwFlags`|해석|
|---------------|--------------------|
|SCC_DIFF_IGNORECASE|대/소문자를 구분하지 않는 비교(빠른 diff 또는 시각적 개체에 사용할 수 있음).|
|SCC_DIFF_IGNORESPACE|공백을 무시합니다(빠른 diff 또는 시각적 개체에 사용할 수 있음).|
|SCC_DIFF_QD_CONTENTS|소스 제어 플러그 인에서 지원되는 경우 는 디렉터리 바이트 바이트를 자동으로 비교합니다.|
|SCC_DIFF_QD_CHECKSUM|플러그 인에서 지원되는 경우 체크섬을 통해 디렉터리를 자동으로 비교하거나, 지원되지 않는 경우 SCC_DIFF_QD_CONTENTS 돌아갑니다.|
|SCC_DIFF_QD_TIME|플러그 인에서 지원되는 경우 는 해당 타임스탬프를 통해 디렉터리를 자동으로 비교하거나, 지원되지 않는 경우 SCC_DIFF_QD_CHECKSUM 또는 SCC_DIFF_QD_CONTENTS 대신합니다.|

> [!NOTE]
> 이 함수는 [SccDiff와](../extensibility/sccdiff-function.md)동일한 명령 플래그를 사용합니다. 그러나 소스 제어 플러그 인은 디렉터리에 대한 "빠른 diff" 작업을 지원하지 않도록 선택할 수 있습니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
