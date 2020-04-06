---
title: 쿼리변경스FUNC | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30864cae95672f4026084a94c5474d165b124cba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701640"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
이 콜백 함수는 [SccQueryChanges](../extensibility/sccquerychanges-function.md) 작업에서 파일 이름 컬렉션을 등록하고 각 파일의 상태를 확인하는 데 사용됩니다.

 함수에는 `SccQueryChanges` 파일 목록과 콜백에 대한 `QUERYCHANGESFUNC` 포인터가 제공됩니다. 소스 제어 플러그인은 지정된 목록을 열거하고 목록의 각 파일에 대해 (이 콜백을 통해) 상태를 제공합니다.

## <a name="signature"></a>서명

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>매개 변수
 pvCallerData

【인】 `pvCallerData` 호출자(IDE)를 통해 [SccQueryChanges로](../extensibility/sccquerychanges-function.md)전달된 매개 변수입니다. 소스 제어 플러그인은 이 값의 내용에 대해 가정하지 않아야 합니다.

 p변경데이터

【인】 파일의 변경 내용을 설명하는 [QUERYCHANGESDATA 구조에](#LinkQUERYCHANGESDATA) 대한 포인터입니다.

## <a name="return-value"></a>반환 값
 IDE는 적절한 오류 코드를 반환합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|처리를 계속합니다.|
|SCC_I_OPERATIONCANCELED|처리를 중지합니다.|
|SCC_E_xxx|적절한 SCC 오류는 처리를 중지해야 합니다.|

## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a>쿼리 변경데이터 구조
 각 파일에 대해 전달된 구조는 다음과 같습니다.

```cpp
struct QUERYCHANGESDATA_A
{
    DWORD  dwSize;
    LPCSTR lpFileName;
    DWORD  dwChangeType;
    LPCSTR lpLatestName;
};

typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA;

struct QUERYCHANGESDATA_W
{
    DWORD   dwSize;
    LPCWSTR lpFileName;
    DWORD   dwChangeType;
    LPCWSTR lpLatestName;
};
```

 dwSize 이 구조의 크기(바이트)입니다.

 lpFileName 이 항목의 원래 파일 이름입니다.

 dwChangeType 코드 파일의 상태를 나타내는:

|코드|설명|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|변경된 내용을 알 수 없습니다.|
|`SCC_CHANGE_UNCHANGED`|이 파일의 이름이 변경되지 않습니다.|
|`SCC_CHANGE_DIFFERENT`|ID가 다르지만 이름이 같은 파일이 데이터베이스에 있습니다.|
|`SCC_CHANGE_NONEXISTENT`|파일이 데이터베이스 또는 로컬에 존재하지 않습니다.|
|`SCC_CHANGE_DATABASE_DELETED`|데이터베이스에서 삭제된 파일입니다.|
|`SCC_CHANGE_LOCAL_DELETED`|파일은 로컬로 삭제되었지만 파일은 데이터베이스에 여전히 존재합니다. 이 것을 확인할 수 `SCC_CHANGE_DATABASE_ADDED`없는 경우 을 반환합니다.|
|`SCC_CHANGE_DATABASE_ADDED`|데이터베이스에 추가되었지만 로컬로 존재하지 않는 파일입니다.|
|`SCC_CHANGE_LOCAL_ADDED`|파일이 데이터베이스에 없고 새 로컬 파일입니다.|
|`SCC_CHANGE_RENAMED_TO`|파일 이름이 바뀌거나 데이터베이스에서 로 `lpLatestName`이동했습니다.|
|`SCC_CHANGE_RENAMED_FROM`|에서 데이터베이스에서 `lpLatestName`이름이 바뀌거나 이동된 파일입니다. 추적하기에 너무 비쌀 경우 와 같은 `SCC_CHANGE_DATABASE_ADDED`다른 플래그를 반환합니다.|

 lpLatestName 이 항목의 현재 파일 이름입니다.

## <a name="see-also"></a>참조
- [IDE에서 구현한 콜백 함수](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [오류 코드](../extensibility/error-codes.md)
