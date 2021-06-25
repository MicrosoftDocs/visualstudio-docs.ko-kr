---
description: 이 함수는 소스 제어 작업의 일괄 처리 시퀀스를 시작합니다.
title: SccBeginBatch 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 08b9199b98e566a71bfeb95124ebd85781e69950
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904762"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch 함수
이 함수는 소스 제어 작업의 일괄 처리 시퀀스를 시작합니다. 일괄 처리를 종료하기 위해 [SccEndBatch가](../extensibility/sccendbatch-function.md) 호출됩니다. 이러한 일괄 처리는 중첩되지 않을 수 있습니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>매개 변수
 없음

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|작업 일괄 처리가 성공적으로 시작되었습니다.|
|SCC_E_UNKNOWNERROR|지정되지 않은 오류입니다.|

## <a name="remarks"></a>설명
 소스 제어 일괄 처리는 여러 프로젝트 또는 여러 컨텍스트에서 동일한 작업을 실행하는 데 사용됩니다. 일괄 처리를 사용하여 일괄 처리 작업 중에 사용자 환경의 중복 프로젝트별 대화 상자를 제거할 수 있습니다. `SccBeginBatch`함수와 [SccEndBatch는](../extensibility/sccendbatch-function.md) 작업의 시작과 끝을 나타내는 함수 쌍으로 사용됩니다. 중첩할 수 없습니다. `SccBeginBatch` 는 일괄 처리 작업이 진행 중임을 나타내는 플래그를 설정합니다.

 일괄 처리 작업이 적용되는 동안 소스 제어 플러그 인은 사용자에게 질문에 대한 최대 하나의 대화 상자를 표시하고 모든 후속 작업에 해당 대화 상자의 응답을 적용해야 합니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)
