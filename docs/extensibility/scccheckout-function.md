---
title: Scc체크아웃 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ed809e33a80bf2903c88550e97b28b1e0178bcd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701101"
---
# <a name="scccheckout-function"></a>Scc체크아웃 기능
정규화된 파일 이름 목록이 주어지면 이 함수는 해당 파일을 로컬 드라이브로 체크 아웃합니다. 주석은 체크 아웃중인 모든 파일에 적용됩니다. 주석 인수는 문자열일 `null` 수 있습니다.

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

【인】 소스 제어 플러그인 컨텍스트 구조입니다.

 Hwnd

【인】 소스 제어 플러그인이 제공하는 모든 대화 상자에 대한 상위로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 n파일

【인】 체크 아웃할 파일 수입니다.

 lpFile 이름

【인】 체크 아웃할 파일의 정규화된 로컬 경로 이름 배열입니다.

 lpComment

【인】 체크 아웃중인 선택한 각 파일에 적용할 주석입니다.

 f옵션

【인】 명령 [플래그(특정 명령에서 사용되는 비트 플래그](../extensibility/bitflags-used-by-specific-commands.md)참조).

 pv옵션

【인】 소스 제어 플러그인 관련 옵션.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|체크 아웃이 성공했습니다.|
|SCC_E_FILENOTCONTROLLED|선택한 파일이 소스 코드 제어하에 있지 않습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 소스 제어 시스템에 액세스하는 데 문제가 있었습니다. 다시 시도하는 것이 좋습니다.|
|SCC_E_NOTAUTHORIZED|사용자는 이 작업을 수행할 수 없습니다.|
|SCC_E_NONSPECIFICERROR|비특정 오류입니다. 파일이 체크 아웃되지 않았습니다.|
|SCC_E_ALREADYCHECKEDOUT|사용자가 이미 파일을 체크 아웃했습니다.|
|SCC_E_FILEISLOCKED|파일이 잠겨 새 버전을 만들 수 없습니다.|
|SCC_E_FILEOUTEXCLUSIVE|다른 사용자가 이 파일에 대한 단독 체크 아웃을 수행했습니다.|
|SCC_I_OPERATIONCANCELED|작업이 완료되기 전에 취소되었습니다.|

## <a name="see-also"></a>참조
- [소스 제어 플러그인 API 기능](../extensibility/source-control-plug-in-api-functions.md)
- [특정 명령에서 사용되는 비트 플래그](../extensibility/bitflags-used-by-specific-commands.md)
