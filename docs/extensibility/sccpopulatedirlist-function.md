---
title: SccPopulateDirList 함수 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700561"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList 함수
이 함수는 검사할 디렉터리 목록이 지정 된 경우 소스 제어에 저장 되는 디렉터리 및 파일 (옵션)을 결정 합니다.

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

진행 소스 제어 플러그 인 컨텍스트 포인터입니다.

 nDirs

진행 배열의 디렉터리 경로 수 `lpDirPaths` 입니다.

 lpDirPaths

진행 검사할 디렉터리 경로 배열입니다.

 pfnPopulate

진행 각 디렉터리 경로 및 (선택 사항)의 파일 이름에 대해 호출할 콜백 함수 `lpDirPaths` (자세한 내용은 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) 참조).

 pvCallerData

진행 변경 되지 않은 상태로 콜백 함수로 전달 되는 값입니다.

 fOptions

진행 디렉터리 처리 방법을 제어 하는 값의 조합입니다. 가능한 값에 대 한 [특정 명령에서 사용 하는 bitflags](../extensibility/bitflags-used-by-specific-commands.md) 의 "PopulateDirList flags" 섹션을 참조 하세요.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|작업을 완료 했습니다.|
|SCC_E_UNKNOWNERROR|오류가 발생했습니다.|

## <a name="remarks"></a>설명
 소스 제어 리포지토리에 실제로 있는 디렉터리 및 파일 이름 (선택 사항)만 콜백 함수에 전달 됩니다.

## <a name="see-also"></a>추가 정보
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [특정 명령에 사용되는 Bitflag](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [오류 코드](../extensibility/error-codes.md)
