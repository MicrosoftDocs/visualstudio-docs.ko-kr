---
title: SccGet확장 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5247f2de7ffc63db7235f915c72b3274b8fee5f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700730"
---
# <a name="sccgetextendedcapabilities-function"></a>SccGet확장기능 기능
이 함수는 소스 제어 플러그인에서 지원하는 추가 기능을 반환합니다.

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

【인】 소스 제어 플러그인 컨텍스트 포인터입니다.

 lSccExCaps

【인】 테스트할 확장 기능을 지정하는 플래그입니다(가능한 플래그에 대한 [기능 플래그의](../extensibility/capability-flags.md) 확장 기능 코드 테이블 참조).

 pb지원

【아웃】 지정된 기능이 지원되는 경우 0이 아닌 ()`TRUE`반환합니다. 그렇지 않으면 0`FALSE`()을 반환합니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|get 기능 작업이 성공적으로 완료되었습니다.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|알 수 없거나 지정되지 않은 오류가 발생했습니다.|

## <a name="remarks"></a>설명
 이 메서드는 요청 시 호출됩니다. 즉, 기능을 테스트해야 하는 경우 해당 기능이 지원되는지 확인하기 위해 이 메서드가 호출됩니다. 한 번에 하나의 플래그만 지정됩니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그인 API 기능](../extensibility/source-control-plug-in-api-functions.md)
- [오류 코드](../extensibility/error-codes.md)
- [기능 플래그](../extensibility/capability-flags.md)
