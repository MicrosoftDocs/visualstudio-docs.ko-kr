---
description: 이 함수는 소스 제어 작업의 일괄 처리를 완료합니다.
title: SccEndBatch 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 11ff596f19d3a98b929f9346bbf579e0ad1258c5
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904593"
---
# <a name="sccendbatch-function"></a>SccEndBatch 함수
이 함수는 소스 제어 작업의 일괄 처리를 완료합니다. 이러한 일괄 처리는 중첩되지 않을 수 있습니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>매개 변수
 없음

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|작업 일괄 처리가 성공적으로 완료되었습니다.|
|SCC_E_UNKNOWNERROR|지정되지 않은 오류입니다.|

## <a name="remarks"></a>설명
 소스 제어 일괄 처리는 여러 프로젝트 또는 여러 컨텍스트에서 동일한 소스 제어 작업을 실행하는 데 사용됩니다. 일괄 처리를 사용하여 일괄 처리 작업 중에 사용자 환경의 중복 대화 상자를 제거할 수 있습니다. [SccBeginBatch](../extensibility/sccbeginbatch-function.md) 및 `SccEndBatch` 함수는 작업의 시작과 끝을 나타내는 쌍으로 사용됩니다. 중첩할 수 없습니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
