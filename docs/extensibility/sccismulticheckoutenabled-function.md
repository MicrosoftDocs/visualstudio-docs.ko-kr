---
description: 이 함수는 소스 제어 플러그 인이 파일에 대해 여러 체크 아웃을 허용하는지 여부를 확인합니다.
title: SccIsMultiCheckoutEnabled 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7b9fc81a20e3a8078a2d4cebbc6a8db10c2e2e49
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902516"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled 함수
이 함수는 소스 제어 플러그 인이 파일에 대해 여러 체크 아웃을 허용하는지 여부를 확인합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccIsMultiCheckoutEnabled(
   LPVOID pContext,
   LPBOOL pbMultiCheckout
);
```

#### <a name="parameters"></a>매개 변수
 pContext

[in] 소스 제어 플러그 인 컨텍스트 구조입니다.

 pbMultiCheckout

[out] 이 프로젝트에 대해 여러 체크 아웃을 사용할지 여부를 지정합니다(0이 아닌 경우 여러 체크 아웃이 지원됨을 의미함).

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|확인에 성공했습니다.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|지정되지 않은 오류입니다.|

## <a name="remarks"></a>설명
 IDE는 두 개 이상의 사용자가 동시에 파일을 체크 아웃할 수 있는지 확인하는 두 가지 검사를 수행합니다. 먼저 소스 제어 시스템에서 여러 체크 아웃을 지원해야 합니다. 소스 제어 플러그 인은 를 지정하여 초기화하는 동안 이 기능을 지정할 수 `SCC_CAP_MULTICHECKOUT` 있습니다. 그 후 두 번째 검사로서 IDE는 이 함수를 호출하여 현재 프로젝트에서 여러 체크 아웃을 지원하는지 여부를 확인합니다. 선택한 프로젝트에 대해 여러 체크 아웃이 지원되는 경우 플러그 인은 성공 코드를 반환하고 `pbMultiCheckout` 를 0이 아닌 ( ) 또는 로 `TRUE` `FALSE` 설정합니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
