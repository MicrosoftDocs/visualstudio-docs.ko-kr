---
title: SccCheckin 함수 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701178"
---
# <a name="scccheckin-function"></a>SccCheckin 함수
이 함수는 이전에 체크 아웃 한 파일을 소스 제어 시스템으로 체크 인하고 변경 내용을 저장 하 고 새 버전을 만듭니다. 이 함수는 체크 인할 파일의 개수 및 이름 배열을 사용 하 여 호출 됩니다.

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

진행 소스 제어 플러그 인 컨텍스트 구조입니다.

 hWnd

진행 SCC 플러그 인이 제공 하는 대화 상자의 부모로 사용할 수 있는 IDE 창에 대 한 핸들입니다.

 n

진행 체크 인 되도록 선택한 파일 수입니다.

 lpFileNames 이름

진행 체크 인할 파일의 정규화 된 로컬 경로 이름 배열입니다.

 lpComment

진행 체크 인 되는 선택한 각 파일에 적용할 설명입니다. 이 매개 변수는 `NULL` 소스 제어 플러그 인에서 주석을 요청 해야 하는 경우입니다.

 fOptions

진행 명령 플래그 (0 또는) `SCC_KEEP_CHECKEDOUT` 입니다.

 pvOptions

진행 SCC 플러그 인 관련 옵션입니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|파일이 체크 인 되었습니다.|
|SCC_E_FILENOTCONTROLLED|선택한 파일은 소스 코드 제어에 있지 않습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 원본 제어 시스템에 액세스 하는 동안 문제가 발생 했습니다. 다시 시도 하는 것이 좋습니다.|
|SCC_E_NONSPECIFICERROR|일반 오류입니다. 파일이 체크 인 되지 않았습니다.|
|SCC_E_NOTCHECKEDOUT|사용자가 파일을 체크 아웃 하지 않았으므로 체크 인할 수 없습니다.|
|SCC_E_CHECKINCONFLICT|다음 이유로 인해 체크 인을 수행할 수 없습니다.<br /><br /> -다른 사용자가 미리 체크 인하고 `bAutoReconcile` false 였습니다.<br /><br /> 또는<br /><br /> -자동 병합을 수행할 수 없습니다 (예: 파일이 이진 인 경우).|
|SCC_E_VERIFYMERGE|파일이 자동으로 병합 되었지만 사용자 확인 보류 중에 체크 인 되지 않았습니다.|
|SCC_E_FIXMERGE|파일이 자동으로 병합 되었지만 수동으로 해결 해야 하는 병합 충돌로 인해 체크 인 되지 않았습니다.|
|SCC_E_NOTAUTHORIZED|사용자가이 작업을 수행할 수 없습니다.|
|SCC_I_OPERATIONCANCELED|작업이 완료 되기 전에 취소 되었습니다.|
|SCC_I_RELOADFILE|파일이 나 프로젝트를 다시 로드 해야 합니다.|
|SCC_E_FILENOTEXIST|로컬 파일을 찾을 수 없습니다.|

## <a name="remarks"></a>설명
 주석은 체크 인 된 모든 파일에 적용 됩니다. 주석 인수는 문자열일 수 있습니다 `null` .이 경우 소스 제어 플러그 인은 각 파일에 대 한 주석 문자열을 사용자에 게 표시할 수 있습니다.

 `fOptions`인수에 플래그 값을 지정 `SCC_KEEP_CHECKEDOUT` 하 여 파일을 확인 하 고 다시 체크 아웃할 사용자의 의도를 나타낼 수 있습니다.

## <a name="see-also"></a>추가 정보
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
