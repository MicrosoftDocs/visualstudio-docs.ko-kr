---
title: SccBeginBatch 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c7982d8c8c0d71f8c79e9b808be5453d384882d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701194"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch 함수
이 함수는 소스 제어 작업의 일괄 처리 시퀀스를 시작 합니다. [Sccendbatch](../extensibility/sccendbatch-function.md) 가 호출 되어 일괄 처리가 종료 됩니다. 이러한 일괄 처리는 중첩 될 수 없습니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>매개 변수
 없음

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|작업 배치가 성공적으로 시작 되었습니다.|
|SCC_E_UNKNOWNERROR|일반 오류입니다.|

## <a name="remarks"></a>설명
 원본 제어 일괄 처리는 여러 프로젝트 또는 여러 컨텍스트에서 동일한 작업을 실행 하는 데 사용 됩니다. 일괄 처리는 일괄 처리 작업을 수행 하는 동안 사용자 환경에서 중복 프로젝트별 대화 상자를 제거 하는 데 사용할 수 있습니다. `SccBeginBatch`함수와 [Sccendbatch](../extensibility/sccendbatch-function.md) 는 작업의 시작과 끝을 나타내는 함수 쌍으로 사용 됩니다. 중첩 될 수 없습니다. `SccBeginBatch` 일괄 처리 작업이 진행 중임을 나타내는 플래그를 설정 합니다.

 일괄 처리 작업이 적용 되는 동안 소스 제어 플러그 인은 사용자에 게 모든 질문에 대 한 대화 상자를 하나 이상 표시 하 고 모든 후속 작업에 대해 해당 대화 상자에서 응답을 적용 해야 합니다.

## <a name="see-also"></a>추가 정보
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)
