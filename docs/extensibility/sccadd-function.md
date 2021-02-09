---
title: SccAdd 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e7fc3a2a6fbf362d58ddd1bfe25c905354d1ebdb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926862"
---
# <a name="sccadd-function"></a>SccAdd 함수
이 함수는 소스 제어 시스템에 새 파일을 추가 합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccAdd(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG*     pfOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>매개 변수
 pvContext

진행 소스 제어 플러그 인 컨텍스트 구조입니다.

 hWnd

진행 소스 제어 플러그 인이 제공 하는 대화 상자의 부모로 사용할 수 있는 IDE 창에 대 한 핸들입니다.

 n

진행 배열에 지정 된 대로 현재 프로젝트에 추가 되도록 선택한 파일 수입니다 `lpFileNames` .

 lpFileNames 이름

진행 추가할 파일의 정규화 된 로컬 이름 배열입니다.

 lpComment

진행 추가 되는 모든 파일에 적용 될 설명입니다.

 pfOptions

진행 파일 별로 제공 되는 명령 플래그의 배열입니다.

 pvOptions

진행 원본 제어 플러그 인 관련 옵션입니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|추가 작업이 성공 했습니다.|
|SCC_E_FILEALREADYEXISTS|선택한 파일은 이미 소스 제어에 있습니다.|
|SCC_E_TYPENOTSUPPORTED|파일의 형식 (예: 이진)은 소스 제어 시스템에서 지원 되지 않습니다.|
|SCC_E_OPNOTSUPPORTED|소스 제어 시스템에서이 작업을 지원 하지 않습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 원본 제어 시스템에 액세스 하는 동안 문제가 발생 했습니다. 다시 시도 하는 것이 좋습니다.|
|SCC_E_NOTAUTHORIZED|사용자가이 작업을 수행할 수 없습니다.|
|SCC_E_NONSPECIFICERROR|일반 오류입니다. 추가를 수행 하지 않습니다.|
|SCC_I_OPERATIONCANCELED|작업이 완료 되기 전에 취소 되었습니다.|
|SCC_I_RELOADFILE|파일이 나 프로젝트를 다시 로드 해야 합니다.|
|SCC_E_FILENOTEXIST|로컬 파일을 찾을 수 없습니다.|

## <a name="remarks"></a>설명
 일반적인는 `fOptions` `pfOptions` 파일 마다 하나의 옵션 사양을 사용 하 여 배열에 의해 여기로 바뀝니다 `LONG` . 이는 파일 형식이 파일에 따라 다를 수 있기 때문입니다.

> [!NOTE]
> `SCC_FILETYPE_TEXT`동일한 파일에 대해 및 옵션을 모두 지정할 수는 없으며 `SCC_FILETYPE_BINARY` , 둘 다 지정할 수는 없습니다. 둘 다 설정 하는 것은 설정과 동일 하지 않습니다 `SCC_FILETYPE_AUTO` .이 경우 소스 제어 플러그 인에서 파일 형식을 자동으로 검색 합니다.

 다음은 배열에서 사용 된 플래그 목록입니다 `pfOptions` .

|옵션|값|의미|
|------------|-----------|-------------|
|SCC_FILETYPE_AUTO|0x00|소스 제어 플러그 인에서 파일 형식을 검색 해야 합니다.|
|SCC_FILETYPE_TEXT|0x01|ASCII 텍스트 파일을 나타냅니다.|
|SCC_FILETYPE_BINARY|0x02|ASCII 텍스트가 아닌 파일 형식을 나타냅니다.|
|SCC_ADD_STORELATEST|0x04|파일의 최신 복사본만 저장 하 고 델타는 저장 하지 않습니다.|
|SCC_FILETYPE_TEXT_ANSI|0x08|는 파일을 ANSI 텍스트로 처리 합니다.|
|SCC_FILETYPE_UTF8|0x10|는 파일을 UTF8 형식의 유니코드 텍스트로 처리 합니다.|
|SCC_FILETYPE_UTF16LE|0x20|는 파일을 UTF16 작은 Endian 형식의 유니코드 텍스트로 처리 합니다.|
|SCC_FILETYPE_UTF16BE|0x40|는 파일을 UTF16 Big Endian 형식의 유니코드 텍스트로 처리 합니다.|

## <a name="see-also"></a>참고 항목
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
