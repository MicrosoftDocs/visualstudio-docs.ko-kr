---
description: 이 함수는 이전에 체크 아웃된 파일을 소스 제어 시스템에 체크 인하여 변경 내용을 저장하고 새 버전을 만듭니다.
title: SccCheckin 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d324c03096df5178decd6f6954928df3f2c6b9aa
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904749"
---
# <a name="scccheckin-function"></a>SccCheckin 함수
이 함수는 이전에 체크 아웃된 파일을 소스 제어 시스템에 체크 인하여 변경 내용을 저장하고 새 버전을 만듭니다. 이 함수는 체크 인할 파일 이름 배열과 개수로 호출됩니다.

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

[in] 소스 제어 플러그 인 컨텍스트 구조입니다.

 Hwnd

[in] SCC 플러그 인이 제공하는 모든 대화 상자의 부모로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 nFiles

[in] 체크 인할 파일 수입니다.

 lpFileNames

[in] 체크 인할 파일의 정규화된 로컬 경로 이름 배열입니다.

 lpComment

[in] 체크 인할 선택한 각 파일에 적용할 주석입니다. 이 매개 변수는 `NULL` 소스 제어 플러그 인에서 주석을 묻는 메시지를 표시해야 하는 경우 입니다.

 fOptions

[in] 명령 플래그(0 또는 `SCC_KEEP_CHECKEDOUT` )입니다.

 pvOptions

[in] SCC 플러그 인 관련 옵션입니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|파일이 성공적으로 체크 인되었습니다.|
|SCC_E_FILENOTCONTROLLED|선택한 파일이 소스 코드 제어에 있지 않습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 소스 제어 시스템에 액세스하는 데 문제가 있었습니다. 다시 시도 하는 것이 좋습니다.|
|SCC_E_NONSPECIFICERROR|지정되지 않은 오류입니다. 파일이 체크 인되지 않았습니다.|
|SCC_E_NOTCHECKEDOUT|사용자가 파일을 체크 아웃하지 않았으므로 체크 인할 수 없습니다.|
|SCC_E_CHECKINCONFLICT|다음과 같은 이유로 체크 인을 수행할 수 없습니다.<br /><br /> - 다른 사용자가 미리 체크 인했으며 `bAutoReconcile` false입니다.<br /><br /> 또는<br /><br /> - 자동 병합을 수행할 수 없습니다(예: 파일이 이진 파일인 경우).|
|SCC_E_VERIFYMERGE|파일이 자동으로 병합되었지만 보류 중인 사용자 확인에서 체크 인되지 않았습니다.|
|SCC_E_FIXMERGE|파일이 자동으로 병합되었지만 수동으로 해결해야 하는 병합 충돌로 인해 체크 인되지 않았습니다.|
|SCC_E_NOTAUTHORIZED|사용자가 이 작업을 수행할 수 없습니다.|
|SCC_I_OPERATIONCANCELED|작업이 완료되기 전에 취소되었습니다.|
|SCC_I_RELOADFILE|파일 또는 프로젝트를 다시 로드해야 합니다.|
|SCC_E_FILENOTEXIST|로컬 파일을 찾을 수 없습니다.|

## <a name="remarks"></a>설명
 주석은 체크 인되는 모든 파일에 적용됩니다. comment 인수는 문자열일 수 `null` 있으며, 이 경우 소스 제어 플러그 인은 사용자에게 각 파일에 대한 주석 문자열을 입력하라는 메시지를 표시할 수 있습니다.

 `fOptions`인수에 플래그 값을 `SCC_KEEP_CHECKEDOUT` 지정하여 파일을 체크 인하고 다시 체크 아웃하려는 사용자의 의도를 나타낼 수 있습니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
