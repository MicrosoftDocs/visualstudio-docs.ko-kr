---
description: 이 함수는 특정 세션의 끝을 표시하는 프로젝트를 닫습니다.
title: SccCloseProject 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 859b1ddea99e74cc1c1dec999611e50216c3c98a
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904697"
---
# <a name="scccloseproject-function"></a>SccCloseProject 함수
이 함수는 특정 세션의 끝을 표시하는 프로젝트를 닫습니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>매개 변수
 pvContext 소스 제어 플러그 인 컨텍스트 구조입니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|프로젝트가 성공적으로 닫혔습니다.|
|SCC_E_PROJNOTOPEN|현재 열려 있는 프로젝트가 없습니다.|
|SCC_E_NOTAUTHORIZED|사용자가 이 작업을 수행할 수 없습니다.|
|SCC_E_NONSPECIFICERROR|지정되지 않은 오류입니다.|

## <a name="remarks"></a>설명
 [SccOpenProject는](../extensibility/sccopenproject-function.md) 항상 이 함수 전에 호출됩니다. 그런 다음 이 함수를 호출한 `SccOpenProject` 다음, 소스 제어 시스템에 대한 연결을 완전히 종료하는 함수 또는 [SccUninitialize](../extensibility/sccuninitialize-function.md)를 호출합니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
