---
title: SccPopulateDirList 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ac1c51ac694acadd2efb0cd7d1c5a3f1d66ebc1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700561"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList 함수
이 함수는 검사할 디렉터리 목록이 주어지면 소스 제어에 저장되는 디렉터리 및(선택적으로) 파일을 결정합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccPopulateDirList(
   LPVOID        pContext,
   LONG          nDirs,
   LPCSTR*       lpDirPaths,
   POPDIRLISTFUNCpfnPopulate,
   LPVOID        pvCallerData,
   LONG          fOptions
);
```

#### <a name="parameters"></a>매개 변수
 pContext

【인】 소스 제어 플러그인 컨텍스트 포인터입니다.

 nDirs

【인】 배열의 디렉터리 경로 `lpDirPaths` 수입니다.

 lpDirPaths

【인】 검사할 디렉터리 경로의 배열입니다.

 pfnPopulate

【인】 콜백 함수는 각 디렉터리 경로및 (선택적으로) `lpDirPaths` 파일 이름을 호출합니다(자세한 내용은 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) 참조).

 pvCallerData

【인】 콜백 함수에 변경되지 않고 전달될 값입니다.

 f옵션

【인】 디렉터리 처리 방법을 제어하는 값의 조합입니다(가능한 값에 대해 [특정 명령에서 사용하는 비트 플래그의](../extensibility/bitflags-used-by-specific-commands.md) "PopulateDirList 플래그" 섹션 참조).

## <a name="return-value"></a>Return Value
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|작업을 성공적으로 완료했습니다.|
|SCC_E_UNKNOWNERROR|오류가 발생했습니다.|

## <a name="remarks"></a>설명
 소스 제어 리포지토리에 실제로 있는 디렉터리 및 (선택적으로) 파일 이름만 콜백 함수에 전달됩니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [특정 명령에 사용되는 Bitflag](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [오류 코드](../extensibility/error-codes.md)
