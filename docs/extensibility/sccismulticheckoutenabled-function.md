---
title: SccIsMultiCheckout활성화 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e91eb566a820f4fe11ceb629643e1815dcb87a8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700578"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled 함수
이 함수는 소스 제어 플러그인이 파일에 여러 체크 아웃을 허용하는지 여부를 확인합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccIsMultiCheckoutEnabled(
   LPVOID pContext,
   LPBOOL pbMultiCheckout
);
```

#### <a name="parameters"></a>매개 변수
 pContext

【인】 소스 제어 플러그인 컨텍스트 구조입니다.

 pbMulti체크아웃

【아웃】 이 프로젝트에 대해 여러 체크 아웃이 활성화되어 있는지 여부를 지정합니다(0이 아닌 것은 여러 체크 아웃이 지원된다는 의미).

## <a name="return-value"></a>Return Value
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|검사가 성공했습니다.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|비특정 오류입니다.|

## <a name="remarks"></a>설명
 IDE는 두 명 이상의 사용자가 파일을 동시에 체크 아웃할 수 있는지 여부를 확인하기 위해 두 가지 검사를 수행합니다. 첫째, 소스 제어 시스템은 여러 체크 아웃을 지원해야 합니다. 소스 제어 플러그인은 을 지정하여 초기화 중에 `SCC_CAP_MULTICHECKOUT`이 기능을 지정할 수 있습니다. 그런 다음 두 번째 검사로 IDE는 이 함수를 호출하여 현재 프로젝트가 여러 체크 아웃을 지원하는지 여부를 결정합니다. 선택한 프로젝트에 대해 여러 체크 아웃이 지원되는 경우 플러그인은 성공 `pbMultiCheckout` 코드를 반환하고 0이 아닌 ()`TRUE`또는 `FALSE`.로 설정합니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
