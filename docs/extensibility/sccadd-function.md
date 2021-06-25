---
description: 이 함수는 소스 제어 시스템에 새 파일을 추가합니다.
title: SccAdd 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7f73a91f7f801ca89a633f1722e0c4d1183fb3dc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904853"
---
# <a name="sccadd-function"></a>SccAdd 함수
이 함수는 소스 제어 시스템에 새 파일을 추가합니다.

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

[in] 소스 제어 플러그 인 컨텍스트 구조입니다.

 Hwnd

[in] 소스 제어 플러그 인이 제공하는 모든 대화 상자의 부모로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 nFiles

[in] 배열에 지정된 대로 현재 프로젝트에 추가하도록 선택한 파일 `lpFileNames` 수입니다.

 lpFileNames

[in] 추가할 파일의 정규화된 로컬 이름 배열입니다.

 lpComment

[in] 추가되는 모든 파일에 적용할 주석입니다.

 pfOptions

[in] 파일 단위로 제공되는 명령 플래그의 배열입니다.

 pvOptions

[in] 소스 제어 플러그 인 관련 옵션입니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|추가 작업이 성공했습니다.|
|SCC_E_FILEALREADYEXISTS|선택한 파일이 이미 소스 제어에 있습니다.|
|SCC_E_TYPENOTSUPPORTED|파일 형식(예: 이진)은 소스 제어 시스템에서 지원되지 않습니다.|
|SCC_E_OPNOTSUPPORTED|소스 제어 시스템에서 이 작업을 지원하지 않습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 소스 제어 시스템에 액세스하는 데 문제가 있었습니다. 다시 시도 하는 것이 좋습니다.|
|SCC_E_NOTAUTHORIZED|사용자가 이 작업을 수행할 수 없습니다.|
|SCC_E_NONSPECIFICERROR|지정되지 않은 오류; add가 수행되지 않았습니다.|
|SCC_I_OPERATIONCANCELED|작업이 완료되기 전에 취소되었습니다.|
|SCC_I_RELOADFILE|파일 또는 프로젝트를 다시 로드해야 합니다.|
|SCC_E_FILENOTEXIST|로컬 파일을 찾을 수 없습니다.|

## <a name="remarks"></a>설명
 여기서 일반적인 `fOptions` 는 `pfOptions` 파일당 하나의 옵션 사양으로 배열로 `LONG` 대체됩니다. 파일 형식이 파일마다 다를 수 있기 때문입니다.

> [!NOTE]
> 동일한 파일에 대해 및 옵션을 둘 다 지정하는 `SCC_FILETYPE_TEXT` `SCC_FILETYPE_BINARY` 것은 유효하지 않지만 둘 다 지정하는 것은 유효하지 않습니다. 둘 다 설정은 설정과 동일하지 않습니다. `SCC_FILETYPE_AUTO` 이 경우 소스 제어 플러그 인은 파일 형식을 자동으로 검색합니다.

 다음은 배열에 사용되는 플래그 목록입니다. `pfOptions`

|옵션|값|의미|
|------------|-----------|-------------|
|SCC_FILETYPE_AUTO|0x00|소스 제어 플러그 인은 파일 형식을 검색해야 합니다.|
|SCC_FILETYPE_TEXT|0x01|ASCII 텍스트 파일을 나타냅니다.|
|SCC_FILETYPE_BINARY|0x02|ASCII 텍스트 이외의 파일 형식을 나타냅니다.|
|SCC_ADD_STORELATEST|0x04|파일의 최신 복사본만 저장하고 델타는 저장하지 않습니다.|
|SCC_FILETYPE_TEXT_ANSI|0x08|파일을 ANSI 텍스트로 처리합니다.|
|SCC_FILETYPE_UTF8|0x10|파일을 UTF8 형식의 유니코드 텍스트로 처리합니다.|
|SCC_FILETYPE_UTF16LE|0x20|파일을 UTF16 Little Endian 형식의 유니코드 텍스트로 처리합니다.|
|SCC_FILETYPE_UTF16BE|0x40|파일을 UTF16 Big Endian 형식의 유니코드 텍스트로 처리합니다.|

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
