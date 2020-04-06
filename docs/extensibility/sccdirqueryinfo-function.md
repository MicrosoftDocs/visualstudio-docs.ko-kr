---
title: SccDirQueryInfo 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 222b5d15a1e2bcd9bd3f27a5cd0e9904642d9786
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700946"
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo 함수
이 함수는 현재 상태에 대해 정규화된 디렉터리 목록을 검사합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccDirQueryInfo(
LPVOID  pContext,
LONG    nDirs,
LPCSTR* lpDirNames,
LPLONG  lpStatus
);
```

### <a name="parameters"></a>매개 변수
 pContext

【인】 소스 제어 플러그인 컨텍스트 구조입니다.

 nDirs

【인】 쿼리할 디렉터리 수입니다.

 lpDirNames

【인】 쿼리할 디렉터리 경로의 정규화된 경로 배열입니다.

 lpStatus

【인, 아웃】 상태 플래그를 반환하는 소스 제어 플러그인에 대한 배열 구조입니다(자세한 내용은 [디렉터리 상태 코드](../extensibility/directory-status-code-enumerator.md) 참조).

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|쿼리가 성공했습니다.|
|SCC_E_OPNOTSUPPORTED|소스 코드 제어 시스템은 이 작업을 지원하지 않습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 소스 제어 시스템에 액세스하는 데 문제가 있었습니다. 다시 시도하는 것이 좋습니다.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|비특정 오류입니다.|

## <a name="remarks"></a>설명
 이 함수는 반환 배열을 `SCC_DIRSTATUS` 패밀리의 비트 마스크(디렉터리 상태 [코드](../extensibility/directory-status-code-enumerator.md)참조)로 채우고, 지정된 각 디렉터리에 대해 하나의 항목을 입력합니다. 상태 배열은 호출자에 의해 할당됩니다.

 IDE는 디렉터리 이름을 바뀌기 전에 이 함수를 사용하여 해당 프로젝트가 있는지 여부를 쿼리하여 디렉터리제어가 소스 제어되고 있는지 확인합니다. 디렉터리소스 제어하에 있지 않으면 IDE는 사용자에게 적절한 경고를 제공할 수 있습니다.

> [!NOTE]
> 소스 제어 플러그인이 하나 이상의 상태 값을 구현하지 않도록 선택하는 경우 구현되지 않은 비트는 0으로 설정해야 합니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그인 API 기능](../extensibility/source-control-plug-in-api-functions.md)
- [디렉터리 상태 코드](../extensibility/directory-status-code-enumerator.md)
