---
description: 이 함수는 검사할 디렉터리 목록이 지정된 경우 소스 제어에 저장되는 디렉터리 및 파일(선택 사항)을 결정합니다.
title: SccPopulateDirList 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bf2620ff42106be7c858c5104dbf9cb2521252ab
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902360"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList 함수
이 함수는 검사할 디렉터리 목록이 지정된 경우 소스 제어에 저장되는 디렉터리 및 파일(선택 사항)을 결정합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccPopulateDirList(
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

[in] 소스 제어 플러그 인 컨텍스트 포인터입니다.

 nDirs

[in] 배열의 디렉터리 경로 `lpDirPaths` 수입니다.

 lpDirPaths

[in] 검사할 디렉터리 경로의 배열입니다.

 pfnPopulate

[in] 의 각 디렉터리 경로 및 파일 이름(선택 사항)에 대해 를 호출하는 콜백 `lpDirPaths` 함수입니다(자세한 내용은 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) 참조).

 pvCallerData

[in] 콜백 함수에 변경되지 않고 전달할 값입니다.

 fOptions

[in] 디렉터리 처리 방법을 제어하는 값의 조합입니다(가능한 값은 [특정 명령에서 사용되는 Bitflags의](../extensibility/bitflags-used-by-specific-commands.md) "PopulateDirList 플래그" 섹션 참조).

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|‘작업이 성공적으로 완료되었습니다.’|
|SCC_E_UNKNOWNERROR|오류가 발생했습니다.|

## <a name="remarks"></a>설명
 소스 제어 리포지토리에 실제로 있는 디렉터리 및 파일 이름(선택 사항)만 콜백 함수에 전달됩니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [특정 명령에 사용되는 Bitflag](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [오류 코드](../extensibility/error-codes.md)
