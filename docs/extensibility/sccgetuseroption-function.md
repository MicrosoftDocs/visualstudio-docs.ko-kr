---
description: 이 함수는 다양 한 사용자별 옵션을 검색 합니다.
title: SccGetUserOption 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 262a15069f840c048f574396d5a7ec076760d77e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063957"
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption 함수
이 함수는 다양 한 사용자별 옵션을 검색 합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccGetUserOption(
   LPVOID pContext,
   LONG nOption,
   LPLONG lpVal
);
```

#### <a name="parameters"></a>매개 변수
 pContext

진행 소스 제어 플러그 인 컨텍스트 포인터입니다.

 nOption

진행 검색할 옵션입니다 (가능한 옵션에 대 한 설명 참조).

 lpVal

제한이 옵션과 관련 된 값입니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|옵션을 검색 했습니다.|
|SCC_E_OPNOTSUPPORTED|옵션은 지원 되지 않습니다.|
|SCC_E_NONSPECIFICERROR|지정되지 않은 오류가 발생했습니다.|

## <a name="remarks"></a>설명
 다음 옵션은이 명령에서 지원 됩니다.

|사용자 옵션|Description|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|사용자가 파일의 로컬 버전을 체크 아웃 하려고 할지 여부를 결정 합니다. `lpVal` 이 할당 된 경우 `SCC_USEROPT_COLV_YES` (사용자는 로컬 파일을 체크 아웃 하려고 `SCC_USEROPT_COLV_NO` 합니다.) 또는입니다.|

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [오류 코드](../extensibility/error-codes.md)
