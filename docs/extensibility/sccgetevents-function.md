---
title: SccGetEvents 기능 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700813"
---
# <a name="sccgetevents-function"></a>SccGetEvents 기능
이 함수는 큐에 대기된 상태 이벤트를 검색합니다.

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

【인】 소스 제어 플러그인 컨텍스트 구조입니다.

 lpFileName

【인, 아웃】 소스 제어 플러그인이 반환된 파일 이름을 넣는 버퍼(최대 _MAX_PATH 문자).

 lpStatus

【인, 아웃】 상태 코드를 반환합니다(가능한 값에 대한 [파일 상태 코드](../extensibility/file-status-code-enumerator.md) 참조).

 pn이벤트잔류

【인, 아웃】 이 호출 후 큐에 남아 있는 항목 수를 반환합니다. 이 번호가 큰 경우 호출자는 [SccQueryInfo를](../extensibility/sccqueryinfo-function.md) 호출하여 모든 정보를 한 번에 가져옵니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|이벤트를 성공으로 가져옵니다.|
|SCC_E_OPNOTSUPPORTED|이 함수는 지원되지 않습니다.|
|SCC_E_NONSPECIFICERROR|비특정 오류입니다.|

## <a name="remarks"></a>설명
 이 함수는 유휴 처리 중에 호출되어 소스 제어하에 있는 파일에 대한 상태 업데이트가 있는지 확인합니다. 소스 제어 플러그인은 알고 있는 모든 파일의 상태를 유지하며, 플러그인에 의해 상태 변경이 기록될 때마다 상태와 관련 파일이 큐에 저장됩니다. `SccGetEvents` 호출되면 큐의 맨 위 요소가 검색되고 반환됩니다. 이 함수는 이전에 캐시된 정보만 반환하도록 제한되며 매우 빠른 처리 가 있어야 합니다(즉, 디스크를 읽거나 소스 제어 시스템에 상태를 요청하지 않습니다). 그렇지 않으면 IDE의 성능이 저하되기 시작할 수 있습니다.

 보고할 상태 업데이트가 없는 경우 소스 제어 플러그인은 에 의해 `lpFileName`가리키는 버퍼에 빈 문자열을 저장합니다. 그렇지 않으면 플러그인은 상태 정보가 변경된 파일의 전체 경로 이름을 저장하고 적절한 상태 코드(파일 상태 코드에 설명된 값 중 하나)를 [반환합니다.](../extensibility/file-status-code-enumerator.md)

## <a name="see-also"></a>참조
- [소스 제어 플러그인 API 기능](../extensibility/source-control-plug-in-api-functions.md)
- [파일 상태 코드](../extensibility/file-status-code-enumerator.md)
