---
description: 이 함수는 소스 제어 플러그 인에서 지원하는 추가 기능을 반환합니다.
title: SccGetExtendedCapabilities 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cc047fee2c92f47c181aef455b8175a4e7998176
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905594"
---
# <a name="sccgetextendedcapabilities-function"></a>SccGetExtendedCapabilities 함수
이 함수는 소스 제어 플러그 인에서 지원하는 추가 기능을 반환합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccGetExtendedCapabilities(
   LPVOID pContext,
   LONG lSccExCaps,
   LPBOOL pbSupported
);
```

### <a name="parameters"></a>매개 변수
 pContext

[in] 소스 제어 플러그 인 컨텍스트 포인터입니다.

 lSccExCaps

[in] 테스트할 확장 기능을 지정하는 플래그입니다(가능한 플래그는 [기능 플래그의](../extensibility/capability-flags.md) 확장 기능 코드 표 참조).

 pbSupported

[out] 지정된 기능이 지원되면 0이 `TRUE` 아닌 ()을 반환하고, 그렇지 않으면 0( `FALSE` )을 반환합니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|기능 얻기 작업이 성공적으로 완료되었습니다.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|알 수 없거나 지정되지 않은 오류가 발생했습니다.|

## <a name="remarks"></a>설명
 이 메서드는 요청 시 호출됩니다. 즉, 기능을 테스트해야 하는 경우 이 메서드를 호출하여 해당 기능이 지원되는지 확인합니다. 한 번에 하나의 플래그만 지정됩니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [오류 코드](../extensibility/error-codes.md)
- [기능 플래그](../extensibility/capability-flags.md)
