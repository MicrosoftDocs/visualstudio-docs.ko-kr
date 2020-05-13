---
title: SccQueryInfo 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1efae18f15588f4dacf3409ea95e30af05397c6e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700475"
---
# <a name="sccqueryinfo-function"></a>SccQueryInfo 함수
이 함수는 소스 제어하에 선택한 파일 집합에 대한 상태 정보를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccQueryInfo(
   LPVOID  pvContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPLONG  lpStatus
);
```

#### <a name="parameters"></a>매개 변수
 pvContext

【인】 소스 제어 플러그인 컨텍스트 구조입니다.

 n파일

【인】 `lpFileNames` 배열에 지정된 파일 수및 `lpStatus` 배열의 길이입니다.

 lpFile 이름

【인】 쿼리할 파일 이름의 배열입니다.

 lpStatus

【인, 아웃】 소스 제어 플러그인이 각 파일에 대한 상태 플래그를 반환하는 배열입니다. 자세한 내용은 [파일 상태 코드](../extensibility/file-status-code-enumerator.md)를 참조하십시오.

## <a name="return-value"></a>Return Value
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|쿼리에 성공했습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 소스 제어 시스템에 액세스하는 데 문제가 있었습니다. 다시 시도하는 것이 좋습니다.|
|SCC_E_PROJNOTOPEN|프로젝트는 소스 제어하에 열려 있지 않습니다.|
|SCC_E_NONSPECIFICERROR|비특정 오류입니다.|

## <a name="remarks"></a>설명
 빈 `lpFileName` 문자열인 경우 현재 업데이트할 상태 정보가 없습니다. 그렇지 않으면 상태 정보가 변경되었을 수 있는 파일의 전체 경로 이름입니다.

 반환 배열은 비트마스크가 `SCC_STATUS_xxxx` 될 수 있습니다. 자세한 내용은 [파일 상태 코드](../extensibility/file-status-code-enumerator.md)를 참조하십시오. 소스 제어 시스템이 모든 비트 유형을 지원하지 않을 수 있습니다. 예를 들어, `SCC_STATUS_OUTOFDATE` 제공되지 않는 경우 비트는 설정되지 않습니다.

 이 함수를 사용하여 파일을 체크 아웃할 때 다음 `MSSCCI` 상태 요구 사항을 확인합니다.

- `SCC_STATUS_OUTBYUSER`는 현재 사용자가 파일을 체크 아웃했을 때 설정됩니다.

- `SCC_STATUS_CHECKEDOUT`설정하지 않으면 `SCC_STATUS_OUTBYUSER` 설정할 수 없습니다.

- `SCC_STATUS_CHECKEDOUT`는 파일이 지정된 작업 디렉토리로 체크 아웃될 때만 설정됩니다.

- 현재 사용자가 파일을 작업 디렉토리가 `SCC_STATUS_OUTBYUSER` 아닌 다른 디렉터리로 체크 아웃하면 `SCC_STATUS_CHECKEDOUT` 설정되지만 그렇지 않습니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [파일 상태 코드](../extensibility/file-status-code-enumerator.md)
