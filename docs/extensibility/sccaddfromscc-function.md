---
title: SccAddFromScc 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1dd32e31330cdce958e463a40a4d92f88b09afb2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701242"
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc 함수
사용자는이 함수를 사용 하 여 소스 제어 시스템에 이미 있는 파일을 찾은 다음 해당 파일을 현재 프로젝트의 일부로 만들 수 있습니다. 예를 들어이 함수는 파일을 복사 하지 않고 공용 헤더 파일을 현재 프로젝트로 가져올 수 있습니다. 파일의 반환 배열에는 `lplpFileNames` 사용자가 IDE 프로젝트에 추가 하려는 파일 목록이 포함 되어 있습니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccAddFromScc (
   LPVOID   pvContext,
   HWND     hWnd,
   LPLONG   lpnFiles,
   LPCSTR** lplpFileNames
);
```

### <a name="parameters"></a>매개 변수
 pvContext

진행 소스 제어 플러그 인 컨텍스트 구조입니다.

 hWnd

진행 소스 제어 플러그 인이 제공 하는 대화 상자의 부모로 사용할 수 있는 IDE 창에 대 한 핸들입니다.

 lpnFiles

[in, out] 에 추가 되는 파일 수에 대 한 버퍼입니다. 이는가 `NULL` 가리키는 메모리를 `lplpFileNames` 해제 하는 경우입니다. 자세한 내용은 설명 부분을 참조 하세요.)

 lplpFileNames 이름

[in, out] 디렉터리 경로 없이 모든 파일 이름에 대 한 포인터의 배열입니다. 소스 제어 플러그 인이이 배열을 할당 하 고 해제 합니다. `lpnFiles`가 1이 고 `lplpFileNames` 가이 아니면 `NULL` 에서 가리키는 배열의 첫 번째 이름에 `lplpFileNames` 대상 폴더가 포함 됩니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|파일이 성공적으로 배치 되어 프로젝트에 추가 되었습니다.|
|SCC_I_OPERATIONCANCELED|작업을 취소 했지만 아무런 효과가 없습니다.|
|SCC_I_RELOADFILE|파일이 나 프로젝트를 다시 로드 해야 합니다.|

## <a name="remarks"></a>설명
 IDE는이 함수를 호출 합니다. 원본 제어 플러그 인에서 로컬 대상 폴더 지정을 지 원하는 경우 IDE는 `lpnFiles` = 1을 전달 하 고 로컬 폴더 이름을에 전달 `lplpFileNames` 합니다.

 함수에 대 한 호출이 반환 되 면 플러그 인에서 `SccAddFromScc` 및에 값을 할당 하 고 `lpnFiles` 필요에 `lplpFileNames` 따라 파일 이름 배열의 메모리를 할당 합니다 .이 할당은의 포인터를 대체 `lplpFileNames` 합니다. 소스 제어 플러그 인은 모든 파일을 사용자의 디렉터리 또는 지정 된 지정 폴더에 배치 합니다. 그런 다음 ide 프로젝트에 파일을 추가 합니다.

 마지막으로, IDE는에 대해를 전달 하 여이 함수를 두 번 호출 `NULL` `lpnFiles` 합니다. 이는에서 파일 이름 배열에 할당 된 메모리를 해제 하기 위해 소스 제어 플러그 인에서 특수 신호로 해석 됩니다. `lplpFileNames``.`

 `lplpFileNames` 는 `char ***` 포인터입니다. 소스 제어 플러그 인은 파일 이름에 대 한 포인터의 배열에 대 한 포인터를 배치 하므로이 API에 대 한 표준 방식으로 목록을 전달 합니다.

> [!NOTE]
> VSSCI API의 초기 버전에서는 추가 된 파일에 대 한 대상 프로젝트를 지정 하는 방법을 제공 하지 않았습니다. 이를 수용 하기 위해 `lplpFIleNames` 매개 변수의 의미 체계가 출력 매개 변수가 아니라 in/out 매개 변수로 만들기 위해 향상 되었습니다. 단일 파일만 지정 하는 경우, 즉 = 1이 가리키는 값은 `lpnFiles` 의 첫 번째 요소에 `lplpFileNames` 대상 폴더가 포함 됩니다. 이러한 새 의미 체계를 사용 하기 위해 IDE는 `SccSetOption` `nOption` 매개 변수를로 설정 하 여 함수를 호출 합니다 `SCC_OPT_SHARESUBPROJ` . 소스 제어 플러그 인이 의미 체계를 지원 하지 않는 경우를 반환 `SCC_E_OPTNOTSUPPORTED` 합니다. 이렇게 하면 **소스 제어에서 추가** 기능을 사용할 수 없습니다. 플러그 인에서 **원본 제어에서 추가** 기능 ()을 지 원하는 경우에는 `SCC_CAP_ADDFROMSCC` 새 의미 체계를 지원 하 고를 반환 해야 합니다 `SCC_I_SHARESUBPROJOK` .

## <a name="see-also"></a>추가 정보
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
