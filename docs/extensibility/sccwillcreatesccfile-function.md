---
description: 이 함수는 소스 제어 플러그 인에서 MSSCCPRJ.SCC 생성을 지원 하는지 여부를 확인 합니다. 지정 된 각 파일에 대 한 SCC 파일
title: SccWillCreateSccFile 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ee01478858615aad135d07a5c10d5d6c58280926
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221290"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile 함수
이 함수는 소스 제어 플러그 인에서 MSSCCPRJ.SCC 생성을 지원 하는지 여부를 확인 합니다. 지정 된 각 파일에 대 한 SCC 파일

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

진행 소스 제어 플러그 인 컨텍스트 포인터입니다.

 n

진행 배열에 포함 된 파일 이름 수 `lpFileNames` 및 `pbSccFiles` 배열 길이입니다.

 lpFileNames 이름

진행 확인할 정규화 된 파일 이름의 배열입니다 (배열은 호출자가 할당 해야 함).

 pbSccFiles

[in, out] 결과를 저장할 배열입니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|성공했습니다.|
|SCC_E_INVALIDFILEPATH|배열의 경로 중 하나가 잘못 되었습니다.|
|SCC_E_NONSPECIFICERROR|일반 오류입니다.|

## <a name="remarks"></a>설명
 이 함수는 소스 제어 플러그 인이 MSSCCPRJ.SCC에서 지원을 제공 하는지 여부를 확인 하기 위해 파일 목록과 함께 호출 됩니다. 지정 된 각 파일에 대 한 SCC 파일 (MSSCCPRJ.SCC에 대 한 자세한 내용) SCC 파일 Mssccprj.scc을 참조 [하세요. SCC 파일](../extensibility/mssccprj-scc-file.md)). 원본 제어 플러그 인은 MSSCCPRJ.SCC를 만드는 기능이 있는지 여부를 선언할 수 있습니다. 초기화 중에를 선언 하 여 SCC 파일 `SCC_CAP_SCCFILE` 플러그 인은 지정 된 `TRUE` `FALSE` `pbSccFiles` 파일 중 mssccprj.scc가 있는 파일을 나타내기 위해 배열에서 또는 파일 단위로 반환 됩니다. SCC 지원. 플러그 인이 함수에서 성공 코드를 반환 하는 경우 반환 배열의 값이 적용 됩니다. 오류가 발생 하면 배열이 무시 됩니다.

## <a name="see-also"></a>참고 항목
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [MSSCCPRJ.SCC 파일](../extensibility/mssccprj-scc-file.md)
