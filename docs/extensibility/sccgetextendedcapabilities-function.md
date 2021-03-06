---
description: 이 함수는 소스 제어 플러그 인에서 지 원하는 추가 기능을 반환 합니다.
title: SccGetExtendedCapabilities 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e1409753559088c0f8129ebacd17387bfb7d111e
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220783"
---
# <a name="sccgetextendedcapabilities-function"></a>SccGetExtendedCapabilities 함수
이 함수는 소스 제어 플러그 인에서 지 원하는 추가 기능을 반환 합니다.

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

진행 소스 제어 플러그 인 컨텍스트 포인터입니다.

 lSccExCaps

진행 테스트할 확장 기능을 지정 하는 플래그입니다 (가능한 플래그의 [기능 플래그](../extensibility/capability-flags.md) 에서 확장 된 기능 코드 테이블 참조).

 Psupported

제한이 `TRUE`지정 된 기능이 지원 되 면 0이 아닌 값을 반환 하 고, 그렇지 않으면 0 ()을 반환 `FALSE` 합니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|기능 가져오기 작업을 완료 했습니다.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|알 수 없거나 지정 되지 않은 오류가 발생 했습니다.|

## <a name="remarks"></a>설명
 이 메서드는 요청 시 호출 됩니다. 즉, 기능을 테스트 해야 하는 경우이 메서드를 호출 하 여 해당 기능이 지원 되는지 확인 합니다. 한 번에 하나의 플래그만 지정 됩니다.

## <a name="see-also"></a>참고 항목
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [오류 코드](../extensibility/error-codes.md)
- [기능 플래그](../extensibility/capability-flags.md)
