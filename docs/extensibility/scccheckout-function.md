---
title: SccCheckout 함수 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701101"
---
# <a name="scccheckout-function"></a>SccCheckout 함수
정규화 된 파일 이름 목록이 지정 된 경우이 함수는 로컬 드라이브를 검사 합니다. 주석은 체크 아웃 중인 모든 파일에 적용 됩니다. 주석 인수는 문자열일 수 있습니다 `null` .

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

진행 소스 제어 플러그 인 컨텍스트 구조입니다.

 hWnd

진행 소스 제어 플러그 인이 제공 하는 대화 상자의 부모로 사용할 수 있는 IDE 창에 대 한 핸들입니다.

 n

진행 체크 아웃 하도록 선택한 파일 수입니다.

 lpFileNames 이름

진행 체크 아웃할 파일의 정규화 된 로컬 경로 이름 배열입니다.

 lpComment

진행 체크 아웃 중인 선택한 각 파일에 적용할 설명입니다.

 fOptions

진행 명령 플래그 ( [특정 명령에 사용 되는 Bitflags](../extensibility/bitflags-used-by-specific-commands.md)참조)

 pvOptions

진행 원본 제어 플러그 인 관련 옵션입니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|체크 아웃 했습니다.|
|SCC_E_FILENOTCONTROLLED|선택한 파일은 소스 코드 제어에 있지 않습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 원본 제어 시스템에 액세스 하는 동안 문제가 발생 했습니다. 다시 시도 하는 것이 좋습니다.|
|SCC_E_NOTAUTHORIZED|사용자가이 작업을 수행할 수 없습니다.|
|SCC_E_NONSPECIFICERROR|일반 오류입니다. 파일이 체크 아웃 되지 않았습니다.|
|SCC_E_ALREADYCHECKEDOUT|사용자가 파일을 이미 체크 아웃 했습니다.|
|SCC_E_FILEISLOCKED|파일이 잠겨 있으므로 새 버전을 만들 수 없습니다.|
|SCC_E_FILEOUTEXCLUSIVE|다른 사용자가이 파일에 대 한 단독 체크 아웃을 완료 했습니다.|
|SCC_I_OPERATIONCANCELED|작업이 완료 되기 전에 취소 되었습니다.|

## <a name="see-also"></a>추가 정보
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [특정 명령에 사용 되는 bitflags](../extensibility/bitflags-used-by-specific-commands.md)
