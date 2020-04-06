---
title: SccGetUser옵션 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc7b68df3331c1240ad833048940e656da034ccf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700683"
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption 함수
이 함수는 다양한 사용자 별 옵션을 검색합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccGetUserOption(
   LPVOID pContext,
   LONG nOption,
   LPLONG lpVal
);
```

#### <a name="parameters"></a>매개 변수
 pContext

【인】 소스 제어 플러그인 컨텍스트 포인터입니다.

 n옵션

【인】 검색 옵션(가능한 옵션에 대한 비고 참조).

 lpVal

【아웃】 옵션과 연결된 값입니다.

## <a name="return-value"></a>Return Value
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|옵션을 성공적으로 검색했습니다.|
|SCC_E_OPNOTSUPPORTED|옵션은 지원되지 않습니다.|
|SCC_E_NONSPECIFICERROR|지정되지 않은 오류가 발생했습니다.|

## <a name="remarks"></a>설명
 다음 옵션은 이 명령에서 지원됩니다.

|사용자 옵션|설명|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|사용자가 파일의 로컬 버전을 체크 아웃할지 여부를 결정합니다. `lpVal`할당된(사용자가 `SCC_USEROPT_COLV_YES` 로컬 파일을 체크 아웃하려고) 또는 `SCC_USEROPT_COLV_NO`.|

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [오류 코드](../extensibility/error-codes.md)
