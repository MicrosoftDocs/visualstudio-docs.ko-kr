---
title: SccCheckin 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5ba512642e1a63d9d39856f96194d717583d44f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701178"
---
# <a name="scccheckin-function"></a>SccCheckin 기능
이 함수는 이전에 체크 아웃된 파일을 소스 제어 시스템에 체크 인하여 변경 내용을 저장하고 새 버전을 만듭니다. 이 함수는 체크 인할 파일의 개수 및 이름 배열로 호출됩니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccCheckin (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPSTR*    lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>매개 변수
 pvContext

【인】 소스 제어 플러그인 컨텍스트 구조입니다.

 Hwnd

【인】 SCC 플러그인이 제공하는 모든 대화 상자에 대한 상위로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 n파일

【인】 체크 인할 파일 수입니다.

 lpFile 이름

【인】 체크 인할 파일의 정규화된 로컬 경로 이름 배열입니다.

 lpComment

【인】 체크 인중인 선택한 각 파일에 적용할 주석입니다. 이 매개 `NULL` 변수는 소스 제어 플러그인이 주석을 묻는 메시지를 표시해야 하는 경우입니다.

 f옵션

【인】 명령 플래그(0 `SCC_KEEP_CHECKEDOUT`또는 .

 pv옵션

【인】 SCC 플러그인 관련 옵션.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|파일이 성공적으로 체크 인되었습니다.|
|SCC_E_FILENOTCONTROLLED|선택한 파일이 소스 코드 제어하에 있지 않습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 소스 제어 시스템에 액세스하는 데 문제가 있었습니다. 다시 시도하는 것이 좋습니다.|
|SCC_E_NONSPECIFICERROR|비특정 오류입니다. 파일이 체크 인되지 않았습니다.|
|SCC_E_NOTCHECKEDOUT|사용자가 파일을 체크 아웃하지 않았기 때문에 체크 인할 수 없습니다.|
|SCC_E_CHECKINCONFLICT|다음과 같은 이유로 체크 인을 수행할 수 없습니다.<br /><br /> - 다른 사용자가 미리 `bAutoReconcile` 체크인하고 거짓되었습니다.<br /><br /> 또는<br /><br /> - 자동 병합은 수행할 수 없습니다(예: 파일이 바이너리인 경우).|
|SCC_E_VERIFYMERGE|파일이 자동으로 병합되었지만 보류 중인 사용자 확인에서 확인되지 않았습니다.|
|SCC_E_FIXMERGE|파일이 자동으로 병합되었지만 수동으로 해결해야 하는 병합 충돌로 인해 체크 인되지 않았습니다.|
|SCC_E_NOTAUTHORIZED|사용자는 이 작업을 수행할 수 없습니다.|
|SCC_I_OPERATIONCANCELED|작업이 완료되기 전에 취소되었습니다.|
|SCC_I_RELOADFILE|파일 또는 프로젝트를 다시 로드해야 합니다.|
|SCC_E_FILENOTEXIST|로컬 파일을 찾을 수 없습니다.|

## <a name="remarks"></a>설명
 주석은 체크 인중인 모든 파일에 적용됩니다. 주석 인수는 `null` 문자열일 수 있으며, 이 경우 소스 제어 플러그인은 각 파일에 대한 주석 문자열을 사용자에게 프롬프트할 수 있습니다.

 인수를 `fOptions` `SCC_KEEP_CHECKEDOUT` 플래그 값으로 지정하여 파일을 체크 인하고 다시 체크 아웃하려는 사용자의 의도를 나타낼 수 있습니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그인 API 기능](../extensibility/source-control-plug-in-api-functions.md)
