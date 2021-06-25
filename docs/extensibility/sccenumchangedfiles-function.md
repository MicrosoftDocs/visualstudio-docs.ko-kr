---
description: 로컬 파일 목록이 제공되면 이 함수는 소스 코드 제어 데이터베이스의 해당 버전과 다른 파일을 결정합니다.
title: SccEnumChangedFiles 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2b0707c049013fd3a0272d1f024e4fdbc342bab1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904541"
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles 함수
로컬 파일 목록이 제공되면 이 함수는 소스 코드 제어 데이터베이스의 해당 버전과 다른 파일을 결정합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccEnumChangedFiles(
   LPVOID  pContext,
   HWND    hWnd,
   LONG    cFiles,
   LPCSTR* lpFileNames,
   LONG*   plIsFileDifferent
);
```

### <a name="parameters"></a>매개 변수
 pContext

[in] 소스 제어 플러그 인 컨텍스트 포인터입니다.

 Hwnd

[in] 소스 제어 플러그 인이 제공하는 모든 대화 상자의 부모로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 cFiles

[in] 배열에 지정된 파일 이름 `lpFileNames` 수입니다. 배열의 크기도 `plIsFileDifferent` 지정합니다.

 lpFileNames

[in] 확인할 로컬 파일 이름의 배열입니다.

 plIsFileDifferent

[in, out] 각 파일의 차이 상태를 나타내는 값의 배열입니다(배열에는 최소한 항목이 있어야 `cFiles` 합니다). 0이 아닌 경우 파일이 다르다는 의미입니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|작업이 완료되었습니다.|
|SCC_UNSPECIFIEDERROR|일반 오류.|

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
