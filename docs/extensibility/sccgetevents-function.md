---
title: SccGetEvents 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91b3debf0e686ceece3048cf3d92b629e3359edd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700813"
---
# <a name="sccgetevents-function"></a>SccGetEvents 함수
이 함수는 대기 중인 상태 이벤트를 검색 합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccGetEvents (
   LPVOID pvContext,
   LPSTR  lpFileName,
   LPLONG lpStatus,
   LPLONG pnEventsRemaining
);
```

### <a name="parameters"></a>매개 변수
 pvContext

진행 소스 제어 플러그 인 컨텍스트 구조입니다.

 lpFileName

[in, out] 소스 제어 플러그 인에서 반환 된 파일 이름을 저장 하는 버퍼입니다 (최대 _MAX_PATH 자).

 lpStatus

[in, out] 상태 코드를 반환 합니다 (가능한 값에 대 한 [파일 상태 코드](../extensibility/file-status-code-enumerator.md) 참조).

 pnEventsRemaining

[in, out] 이 호출 후에 큐에 남아 있는 항목의 수를 반환 합니다. 이 수가 클 경우 호출자는 [Sccqueryinfo](../extensibility/sccqueryinfo-function.md) 를 호출 하 여 모든 정보를 한 번에 가져올 수 있습니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|이벤트 가져오기에 성공 했습니다.|
|SCC_E_OPNOTSUPPORTED|이 함수는 지원되지 않습니다.|
|SCC_E_NONSPECIFICERROR|일반 오류입니다.|

## <a name="remarks"></a>설명
 이 함수는 유휴 처리 중에 호출 되어 소스 제어에서 파일에 대 한 상태 업데이트가 있는지 확인 합니다. 원본 제어 플러그 인은 알고 있는 모든 파일의 상태를 유지 관리 하 고, 플러그 인에서 상태 변경이 표시 될 때마다 상태와 관련 파일이 큐에 저장 됩니다. `SccGetEvents`가 호출 되 면 큐의 최상위 요소가 검색 되어 반환 됩니다. 이 함수는 이전에 캐시 된 정보만 반환 하도록 제한 되며, 디스크를 읽거나 원본 제어 시스템에 상태를 요청 하지 않아야 합니다. 그렇지 않으면 IDE의 성능이 저하 되기 시작할 수 있습니다.

 보고할 상태 업데이트가 없는 경우 소스 제어 플러그 인은가 가리키는 버퍼에 빈 문자열을 저장 합니다 `lpFileName` . 그렇지 않으면 플러그 인은 상태 정보가 변경 된 파일의 전체 경로 이름을 저장 하 고 적절 한 상태 코드 ( [파일 상태 코드](../extensibility/file-status-code-enumerator.md)에 자세히 설명 되어 있는 값 중 하나)를 반환 합니다.

## <a name="see-also"></a>추가 정보
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [파일 상태 코드](../extensibility/file-status-code-enumerator.md)
