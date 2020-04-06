---
title: SccWillCreateSccFile 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0694fd6b4ba82faf8b05354765fc5734efe2ef4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700204"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile 함수
이 함수는 소스 제어 플러그인이 MSSCCPRJ 생성을 지원하는지 여부를 결정합니다. 지정된 각 파일에 대한 SCC 파일입니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccWillCreateSccFile(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPBOOL  pbSccFiles
);
```

#### <a name="parameters"></a>매개 변수
 pContext

【인】 소스 제어 플러그인 컨텍스트 포인터입니다.

 n파일

【인】 배열에 `lpFileNames` 포함된 파일 이름 수와 배열 의 `pbSccFiles` 길이입니다.

 lpFile 이름

【인】 확인할 수 있는 정규화된 파일 이름 배열(배열은 호출자에게 할당되어야 합니다).

 pbScc파일

【인, 아웃】 결과를 저장할 배열입니다.

## <a name="return-value"></a>Return Value
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|성공했습니다.|
|SCC_E_INVALIDFILEPATH|배열의 경로 중 하나가 잘못되었습니다.|
|SCC_E_NONSPECIFICERROR|비특정 오류입니다.|

## <a name="remarks"></a>설명
 이 함수는 소스 제어 플러그인이 MSSCCPRJ에서 지원을 제공하는지 확인하기 위해 파일 목록과 함께 호출됩니다. 주어진 각 파일에 대한 SCC 파일(MSSCCPRJ에 대한 자세한 내용은) SCC 파일, [MSSCCPRJ를 참조하십시오. SCC 파일)을](../extensibility/mssccprj-scc-file.md)참조하십시오. 소스 제어 플러그인은 MSSCCPRJ를 만드는 기능이 있는지 여부를 선언할 수 있습니다. 초기화 하는 동안 `SCC_CAP_SCCFILE` 선언 하 여 SCC 파일입니다. 플러그인은 `TRUE` `pbSccFiles` MSSCCPRJ가 있는 지정된 파일을 나타내기 위해 배열의 파일또는 `FALSE` 파일당 반환합니다. SCC 지원. 플러그인이 함수에서 성공 코드를 반환하면 반환 배열의 값이 적용됩니다. 오류가 나면 배열이 무시됩니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [MSSCCPRJ.SCC 파일](../extensibility/mssccprj-scc-file.md)
