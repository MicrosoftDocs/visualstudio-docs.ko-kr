---
description: 이 함수는 지정 된 각 파일을 사용자 상호 작용 없이 소스 제어에서 검색 합니다.
title: SccBackgroundGet 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6d850b1f8493f3118cb4d3e49915361daa1e4837
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060460"
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet 함수
이 함수는 지정 된 각 파일을 사용자 상호 작용 없이 소스 제어에서 검색 합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccBackgroundGet(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LONG    dwFlags,
   LONG    dwBackgroundOperationID
);
```

### <a name="parameters"></a>매개 변수
 pContext

진행 소스 제어 플러그 인 컨텍스트 포인터입니다.

 n

진행 배열에 지정 된 파일 수 `lpFileNames` 입니다.

 lpFileNames 이름

[in, out] 검색할 파일의 이름 배열입니다.

> [!NOTE]
> 이름은 정규화 된 로컬 파일 이름 이어야 합니다.

 dwFlags

진행 명령 플래그 ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).

 dwBackgroundOperationID

진행 이 작업과 연결 된 고유 값입니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|작업이 완료되었습니다.|
|SCC_E_BACKGROUNDGETINPROGRESS|백그라운드 검색이 이미 진행 중입니다. (소스 제어 플러그 인은 동시 일괄 처리 작업을 지원 하지 않는 경우에만이를 반환 해야 합니다.)|
|SCC_I_OPERATIONCANCELED|작업이 완료 되기 전에 취소 되었습니다.|

## <a name="remarks"></a>설명
 이 함수는 소스 제어 플러그 인을 로드 한 스레드와 다른 스레드에서 항상 호출 됩니다. 이 함수는 완료 될 때까지 반환 될 것으로 예상 되지 않습니다. 그러나 여러 파일 목록을 동시에 사용 하 여 여러 번 호출할 수 있습니다.

 인수를 사용 하는 `dwFlags` 것은 [Sccget](../extensibility/sccget-function.md)과 동일 합니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)
