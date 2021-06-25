---
description: 이 함수는 지정된 파일의 기록을 표시합니다.
title: SccHistory 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1208bd0cb13661f1aa60bb9f97c9e4502e517e6d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902542"
---
# <a name="scchistory-function"></a>SccHistory 함수
이 함수는 지정된 파일의 기록을 표시합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccHistory(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>매개 변수
 `pvContext`

[in] 소스 제어 플러그 인 컨텍스트 구조입니다.

 `hWnd`

[in] 소스 제어 플러그 인이 제공하는 모든 대화 상자의 부모로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 `nFiles`

[in] 배열에 지정된 파일 `lpFileName` 수입니다.

 `lpFileName`

[in] 파일의 정규화된 이름 배열입니다.

 `fOptions`

[in] 명령 플래그(현재 사용되지 않음)

 `pvOptions`

[in] 소스 제어 플러그 인 관련 옵션입니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|버전 기록을 성공적으로 획득했습니다.|
|SCC_I_RELOADFILE|원본 제어 시스템은 기록을 가져오는 동안(예: 이전 버전의 파일을 가져와서) 디스크의 파일을 실제로 수정했으므로 IDE에서 이 파일을 다시 로드해야 합니다.|
|SCC_E_FILENOTCONTROLLED|파일이 소스 제어에 있지 않습니다.|
|SCC_E_OPNOTSUPPORTED|소스 제어 시스템에서 이 작업을 지원하지 않습니다.|
|SCC_E_NOTAUTHORIZED|사용자가 이 작업을 수행할 수 없습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 소스 제어 시스템에 액세스하는 데 문제가 있었습니다. 다시 시도 하는 것이 좋습니다.|
|SCC_E_PROJNOTOPEN|프로젝트가 열리지 않았습니다.|
|SCC_E_NONSPECIFICERROR|지정되지 않은 오류입니다. 파일 기록을 가져올 수 없습니다.|

## <a name="remarks"></a>설명
 소스 제어 플러그 인은 를 부모 창으로 사용하여 각 파일의 기록을 표시하는 자체 대화 상자를 표시할 수 `hWnd` 있습니다. 또는 지원되는 경우 [SccOpenProject에](../extensibility/sccopenproject-function.md) 제공된 선택적 텍스트 출력 콜백 함수를 사용할 수 있습니다.

 특정 상황에서는 이 호출을 실행하면서 검사 중인 파일이 변경될 수 있습니다. 예를 들어 [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] 기록 명령은 사용자에게 이전 버전의 파일을 얻을 수 있는 기회를 제공합니다. 이러한 경우 소스 제어 플러그 인은 `SCC_I_RELOAD` 파일을 다시 로드해야 한다고 IDE에 경고하기 위해 를 반환합니다.

> [!NOTE]
> 소스 제어 플러그 인이 파일 배열에 대해 이 함수를 지원하지 않는 경우 첫 번째 파일의 파일 기록만 표시할 수 있습니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
