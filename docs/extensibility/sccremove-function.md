---
title: 스크리지 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17889d50dbdcf68dd4cca161d6703b8b6d69ad47
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700449"
---
# <a name="sccremove-function"></a>SccRemove 함수
이 함수는 소스 제어 시스템에서 파일을 삭제합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccRemove(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>매개 변수
 pvContext

【인】 소스 제어 플러그인 컨텍스트 구조입니다.

 Hwnd

【인】 소스 제어 플러그인이 제공하는 모든 대화 상자에 대한 상위로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 n파일

【인】 배열에 지정된 파일 `lpFileNames` 수입니다.

 lpFile 이름

【인】 제거할 파일의 정규화된 로컬 경로 이름 배열입니다.

 lpComment

【인】 제거되는 각 파일에 적용할 주석입니다.

 f옵션

【인】 명령 플래그(사용되지 않는).

 pv옵션

【인】 소스 제어 플러그인 관련 옵션.

## <a name="return-value"></a>Return Value
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|제거에 성공했습니다.|
|SCC_E_FILENOTCONTROLLED|선택한 파일이 소스 제어하에 있지 않습니다.|
|SCC_E_OPNOTSUPPORTED|소스 제어 시스템은 이 작업을 지원하지 않습니다.|
|SCC_E_ISCHECKEDOUT|사용자가 현재 파일을 체크 아웃했기 때문에 파일을 제거할 수 없습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 소스 제어 시스템에 액세스하는 데 문제가 있었습니다.|
|SCC_E_NOTAUTHORIZED|사용자는 이 작업을 수행할 수 없습니다.|
|SCC_E_NONSPECIFICERROR|비특이적 오류; 제거되지 않았습니다.|
|SCC_I_OPERATIONCANCELED|작업이 완료되기 전에 취소되었습니다.|

## <a name="remarks"></a>설명
 이 기능은 소스 제어 시스템에서 파일을 제거하지만 사용자의 로컬 하드 드라이브에서 파일을 삭제하지는 않습니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
