---
title: SccEndBatch 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 85d49fcd9920c442aa1736f1fb0f3e46ccd4eba0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943051"
---
# <a name="sccendbatch-function"></a>SccEndBatch 함수
이 함수는 소스 제어 작업의 일괄 처리를 끝냅니다. 이러한 일괄 처리는 중첩 될 수 없습니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>매개 변수
 없음

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|작업 일괄 처리를 완료 했습니다.|
|SCC_E_UNKNOWNERROR|일반 오류입니다.|

## <a name="remarks"></a>설명
 원본 제어 일괄 처리는 여러 프로젝트 또는 여러 컨텍스트에서 동일한 소스 제어 작업을 실행 하는 데 사용 됩니다. 일괄 처리는 일괄 처리 작업을 수행 하는 동안 사용자 환경에서 중복 된 대화 상자를 제거 하는 데 사용할 수 있습니다. [Sccbeginbatch](../extensibility/sccbeginbatch-function.md) 및 함수는 `SccEndBatch` 작업의 시작과 끝을 나타내는 쌍으로 사용 됩니다. 중첩 될 수 없습니다.

## <a name="see-also"></a>참고 항목
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
