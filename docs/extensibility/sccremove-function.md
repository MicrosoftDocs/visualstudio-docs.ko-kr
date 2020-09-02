---
title: SccRemove 함수 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700449"
---
# <a name="sccremove-function"></a>SccRemove 함수
이 함수는 소스 제어 시스템에서 파일을 삭제 합니다.

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

진행 소스 제어 플러그 인 컨텍스트 구조입니다.

 hWnd

진행 소스 제어 플러그 인이 제공 하는 대화 상자의 부모로 사용할 수 있는 IDE 창에 대 한 핸들입니다.

 n

진행 배열에 지정 된 파일 수 `lpFileNames` 입니다.

 lpFileNames 이름

진행 제거할 파일의 정규화 된 로컬 경로 이름 배열입니다.

 lpComment

진행 제거 되는 각 파일에 적용할 설명입니다.

 fOptions

진행 명령 플래그 (사용 되지 않음).

 pvOptions

진행 원본 제어 플러그 인 관련 옵션입니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|제거 했습니다.|
|SCC_E_FILENOTCONTROLLED|선택한 파일은 소스 제어에서 관리 되지 않습니다.|
|SCC_E_OPNOTSUPPORTED|소스 제어 시스템에서이 작업을 지원 하지 않습니다.|
|SCC_E_ISCHECKEDOUT|현재 사용자가 체크 아웃 했으므로 파일을 제거할 수 없습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 원본 제어 시스템에 액세스 하는 동안 문제가 발생 했습니다.|
|SCC_E_NOTAUTHORIZED|사용자가이 작업을 수행할 수 없습니다.|
|SCC_E_NONSPECIFICERROR|일반 오류입니다. 파일이 제거 되지 않았습니다.|
|SCC_I_OPERATIONCANCELED|작업이 완료 되기 전에 취소 되었습니다.|

## <a name="remarks"></a>설명
 이 함수는 소스 제어 시스템에서 파일을 제거 하지만 사용자의 로컬 하드 드라이브에서 파일을 삭제 하지는 않습니다.

## <a name="see-also"></a>추가 정보
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
