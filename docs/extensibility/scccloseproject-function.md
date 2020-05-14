---
title: SccClose프로젝트 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71df385bc0cf42c2437abfd117c2f84bda5b5432
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701054"
---
# <a name="scccloseproject-function"></a>SccClose프로젝트 기능
이 함수는 프로젝트를 닫아 특정 세션의 끝을 표시합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>매개 변수
 pvContext 소스 제어 플러그인 컨텍스트 구조입니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|프로젝트가 성공적으로 종료되었습니다.|
|SCC_E_PROJNOTOPEN|현재 열려 있는 프로젝트가 없습니다.|
|SCC_E_NOTAUTHORIZED|사용자는 이 작업을 수행할 수 없습니다.|
|SCC_E_NONSPECIFICERROR|비특정 오류입니다.|

## <a name="remarks"></a>설명
 [SccOpenProject는](../extensibility/sccopenproject-function.md) 항상 이 함수 앞에 호출됩니다. 그런 다음 이 함수에 대한 호출 다음에 `SccOpenProject` 함수 또는 [SccUninitialize에](../extensibility/sccuninitialize-function.md)대한 호출이 수행되어 소스 제어 시스템에 대한 연결이 완전히 종료됩니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그인 API 기능](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
