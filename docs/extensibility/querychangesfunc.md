---
title: QUERYCHANGESFUNC | Microsoft Docs
description: QUERYCHANGESFUNC 콜백 함수는 파일 이름 컬렉션을 열거하고 각 파일의 상태를 확인하는 데 사용됩니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b061fbfb6644f77348574020c0a5cb614691ae6b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899136"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
[SccQueryChanges](../extensibility/sccquerychanges-function.md) 작업에서 파일 이름 컬렉션을 열거하고 각 파일의 상태를 확인하는 데 사용하는 콜백 함수입니다.

 `SccQueryChanges`함수에는 파일 목록과 콜백에 대한 포인터가 `QUERYCHANGESFUNC` 제공됩니다. 소스 제어 플러그 인은 지정된 목록을 열거하고 목록의 각 파일에 대한 상태를 제공합니다(이 콜백을 통해).

## <a name="signature"></a>서명

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>매개 변수
 pvCallerData

[in] `pvCallerData` 호출자(IDE)가 [SccQueryChanges](../extensibility/sccquerychanges-function.md)에 전달한 매개 변수입니다. 소스 제어 플러그 인은 이 값의 내용을 가정하지 않아야 합니다.

 pChangesData

[in] 파일의 변경 내용을 설명하는 [QUERYCHANGESDATA 구조체에](#LinkQUERYCHANGESDATA) 대한 포인터입니다.

## <a name="return-value"></a>반환 값
 IDE는 적절한 오류 코드를 반환합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|처리를 계속합니다.|
|SCC_I_OPERATIONCANCELED|처리를 중지합니다.|
|SCC_E_xxx|적절한 SCC 오류는 처리를 중지해야 합니다.|

## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a> QUERYCHANGESDATA 구조체
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

 dwSize 이 구조체의 크기(바이트)입니다.

 lpFileName 이 항목의 원래 파일 이름입니다.

 파일의 상태를 나타내는 dwChangeType 코드:

|코드|Description|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|변경된 내용을 알 수 없습니다.|
|`SCC_CHANGE_UNCHANGED`|이 파일의 이름은 변경되지 않습니다.|
|`SCC_CHANGE_DIFFERENT`|ID가 다르지만 이름이 같은 파일이 데이터베이스에 있습니다.|
|`SCC_CHANGE_NONEXISTENT`|파일이 데이터베이스에 없거나 로컬로 존재하지 않습니다.|
|`SCC_CHANGE_DATABASE_DELETED`|데이터베이스에서 삭제된 파일입니다.|
|`SCC_CHANGE_LOCAL_DELETED`|파일이 로컬로 삭제되었지만 파일이 여전히 데이터베이스에 있습니다. 확인할 수 없는 경우 를 `SCC_CHANGE_DATABASE_ADDED` 반환합니다.|
|`SCC_CHANGE_DATABASE_ADDED`|데이터베이스에 추가되었지만 로컬에 존재하지 않는 파일입니다.|
|`SCC_CHANGE_LOCAL_ADDED`|파일이 데이터베이스에 없으며 새 로컬 파일입니다.|
|`SCC_CHANGE_RENAMED_TO`|파일 이름이 변경되거나 데이터베이스에서 로 `lpLatestName` 이동되었습니다.|
|`SCC_CHANGE_RENAMED_FROM`|파일 이름이 변경되거나 데이터베이스에서 에서 이동되었습니다. `lpLatestName` 추적하기에 비용이 너무 많이 들면 와 같은 다른 플래그를 반환합니다. `SCC_CHANGE_DATABASE_ADDED`|

 lpLatestName 이 항목의 현재 파일 이름입니다.

## <a name="see-also"></a>참조
- [IDE에서 구현하는 콜백 함수](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [오류 코드](../extensibility/error-codes.md)
