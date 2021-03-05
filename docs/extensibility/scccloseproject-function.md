---
description: 이 함수는 특정 세션의 끝을 표시 하는 프로젝트를 닫습니다.
title: SccCloseProject 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f3fb9208619639a8f1c767cbf12a2de0ed24768f
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220874"
---
# <a name="scccloseproject-function"></a>SccCloseProject 함수
이 함수는 특정 세션의 끝을 표시 하는 프로젝트를 닫습니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>매개 변수
 소스 제어 플러그 인 컨텍스트 구조를 pvContext 합니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|프로젝트를 닫았습니다.|
|SCC_E_PROJNOTOPEN|현재 열려 있는 프로젝트가 없습니다.|
|SCC_E_NOTAUTHORIZED|사용자가이 작업을 수행할 수 없습니다.|
|SCC_E_NONSPECIFICERROR|일반 오류입니다.|

## <a name="remarks"></a>설명
 [Sccopenproject](../extensibility/sccopenproject-function.md) 는 항상이 함수 이전에 호출 됩니다. 그런 다음이 함수를 호출 하 고 그 다음에 `SccOpenProject` 함수 또는 [SccUninitialize](../extensibility/sccuninitialize-function.md)를 호출 하 여 소스 제어 시스템에 대 한 연결을 완전히 종료 합니다.

## <a name="see-also"></a>참고 항목
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
