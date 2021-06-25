---
description: 이 함수는 다양한 사용자별 옵션을 검색합니다.
title: SccGetUserOption 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 622abc04609edf410214af6b8acf795f969e2fbc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901112"
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption 함수
이 함수는 다양한 사용자별 옵션을 검색합니다.

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

[in] 소스 제어 플러그 인 컨텍스트 포인터입니다.

 nOption

[in] 검색할 옵션(가능한 옵션에 대한 주의 참조)

 lpVal

[out] 옵션과 연결된 값입니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|옵션이 성공적으로 검색되었습니다.|
|SCC_E_OPNOTSUPPORTED|옵션은 지원되지 않습니다.|
|SCC_E_NONSPECIFICERROR|지정되지 않은 오류가 발생했습니다.|

## <a name="remarks"></a>설명
 다음 옵션은 이 명령에서 지원됩니다.

|사용자 옵션|설명|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|사용자가 로컬 버전의 파일을 체크 아웃할지 여부를 결정합니다. `lpVal` 가 `SCC_USEROPT_COLV_YES` 할당되었습니다(사용자가 로컬 파일을 체크 아웃하려는 경우) 또는 `SCC_USEROPT_COLV_NO` .|

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [오류 코드](../extensibility/error-codes.md)
