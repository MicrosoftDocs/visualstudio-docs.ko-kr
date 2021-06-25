---
description: 정규화된 파일 이름 목록이 제공된 경우 이 함수는 로컬 드라이브에 체크 아웃합니다.
title: SccCheckout 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 72d36ccaf5c6dcddb6730f52b0ce1c3074c605a7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904723"
---
# <a name="scccheckout-function"></a>SccCheckout 함수
정규화된 파일 이름 목록이 제공된 경우 이 함수는 로컬 드라이브에 체크 아웃합니다. 주석은 체크 아웃되는 모든 파일에 적용됩니다. comment 인수는 문자열일 수 `null` 있습니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccCheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>매개 변수
 pvContext

[in] 소스 제어 플러그 인 컨텍스트 구조입니다.

 Hwnd

[in] 소스 제어 플러그 인이 제공하는 모든 대화 상자의 부모로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 nFiles

[in] 체크 아웃할 파일 수입니다.

 lpFileNames

[in] 체크 아웃할 파일의 정규화된 로컬 경로 이름 배열입니다.

 lpComment

[in] 선택한 각 파일에 적용할 주석입니다.

 fOptions

[in] 명령 [플래그(특정 명령에 사용되는 Bitflags](../extensibility/bitflags-used-by-specific-commands.md)참조)

 pvOptions

[in] 소스 제어 플러그 인 관련 옵션입니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|체크 아웃이 성공했습니다.|
|SCC_E_FILENOTCONTROLLED|선택한 파일이 소스 코드 제어에 있지 않습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 소스 제어 시스템에 액세스하는 데 문제가 있었습니다. 다시 시도 하는 것이 좋습니다.|
|SCC_E_NOTAUTHORIZED|사용자가 이 작업을 수행할 수 없습니다.|
|SCC_E_NONSPECIFICERROR|지정되지 않은 오류입니다. 파일이 체크 아웃되지 않았습니다.|
|SCC_E_ALREADYCHECKEDOUT|사용자가 이미 체크 아웃한 파일이 있습니다.|
|SCC_E_FILEISLOCKED|파일이 잠겨 새 버전 생성이 금지됩니다.|
|SCC_E_FILEOUTEXCLUSIVE|다른 사용자가 이 파일에 대한 단독 체크 아웃을 수행했습니다.|
|SCC_I_OPERATIONCANCELED|작업이 완료되기 전에 취소되었습니다.|

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [특정 명령에서 사용되는 비트 플래그](../extensibility/bitflags-used-by-specific-commands.md)
