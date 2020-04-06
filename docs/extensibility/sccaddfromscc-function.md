---
title: SccAddFromScc 기능 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701242"
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc 기능
이 기능을 사용하면 사용자가 소스 제어 시스템에 이미 있는 파일을 찾아보고 해당 파일을 현재 프로젝트의 일부로 만들 수 있습니다. 예를 들어 이 함수는 파일을 복사하지 않고 현재 프로젝트에 공통 헤더 파일을 가져옵니다. 파일의 반환 배열은 `lplpFileNames`사용자가 IDE 프로젝트에 추가하려는 파일 목록을 포함합니다.

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

【인】 소스 제어 플러그인 컨텍스트 구조입니다.

 Hwnd

【인】 소스 제어 플러그인이 제공하는 모든 대화 상자에 대한 상위로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 lpn파일

【인, 아웃】 추가되는 파일 수에 대한 버퍼입니다. (가리키는 `NULL` 메모리를 해제하는 `lplpFileNames` 경우입니다. 자세한 내용은 비고를 참조하십시오.)

 lplpFile 이름

【인, 아웃】 디렉터리 경로가 없는 모든 파일 이름에 대한 포인터 배열입니다. 이 배열은 소스 제어 플러그인에 의해 할당되고 해제됩니다. = `lpnFiles` 1이 `lplpFileNames` 아닌 `NULL`경우 가리키는 배열의 첫 `lplpFileNames` 번째 이름에 대상 폴더가 포함됩니다.

## <a name="return-value"></a>Return Value
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|파일이 성공적으로 배치되어 프로젝트에 추가되었습니다.|
|SCC_I_OPERATIONCANCELED|아무런 효과 없이 작업이 취소되었습니다.|
|SCC_I_RELOADFILE|파일 또는 프로젝트를 다시 로드해야 합니다.|

## <a name="remarks"></a>설명
 IDE는 이 함수를 호출합니다. 소스 제어 플러그인이 로컬 대상 폴더 지정을 지원하는 경우 `lpnFiles` IDE는 = 1을 `lplpFileNames`전달하고 로컬 폴더 이름을 에 전달합니다.

 함수에 대한 호출이 반환되면 플러그인은 필요에 `lpnFiles` 따라 `lplpFileNames`파일 이름 배열에 대한 메모리를 할당하는 값을 할당합니다(이 `lplpFileNames`할당은 포인터를 대체합니다). `SccAddFromScc` 소스 제어 플러그인은 모든 파일을 사용자의 디렉터리 또는 지정된 지정 폴더에 배치할 책임이 있습니다. 그런 다음 IDE는 파일을 IDE 프로젝트에 추가합니다.

 마지막으로 IDE는 이 함수를 두 번째로 `NULL` `lpnFiles`호출하여 에 전달합니다. 이는 소스 제어 플러그인이 파일 이름 배열에 할당된 메모리를 해제하는 특별한 신호로 해석됩니다.`lplpFileNames``.`

 `lplpFileNames`는 `char ***` 포인터입니다. 소스 제어 플러그인은 파일 이름에 대한 포인터 배열에 대한 포인터를 배치하므로 이 API에 대한 표준 방식으로 목록을 전달합니다.

> [!NOTE]
> VSSCI API의 초기 버전은 추가된 파일에 대한 대상 프로젝트를 나타내는 방법을 제공하지 않았습니다. 이를 수용하기 위해 `lplpFIleNames` 매개 변수의 의미 체계가 향상되어 출력 매개 변수가 아닌 인/아웃 매개변수로 변경되었습니다. 단일 파일만 지정하면 즉 = 1로 `lpnFiles` 가리키는 값이 대상 폴더를 `lplpFileNames` 포함합니다. 이러한 새 의미 체계를 사용 하려면 IDE `SccSetOption` `nOption`매개 변수가 `SCC_OPT_SHARESUBPROJ`설정 된 함수를 호출 합니다. 소스 제어 플러그인이 의미 체계를 지원하지 않으면 반환됩니다. `SCC_E_OPTNOTSUPPORTED` 이렇게 하면 **소스 제어에서 추가** 기능의 사용을 비활성화합니다. 플러그인이 **소스 제어에서 추가** 기능 ()을`SCC_CAP_ADDFROMSCC`지원하는 경우 새 의미 체계를 `SCC_I_SHARESUBPROJOK`지원하고 반환해야합니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그인 API 기능](../extensibility/source-control-plug-in-api-functions.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
