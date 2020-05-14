---
title: SccEnum변경파일 함수 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b1826a87b20d6bc92254fc4a86b8e0b756400ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700913"
---
# <a name="sccenumchangedfiles-function"></a>SccEnum변함없파일 함수
로컬 파일 목록이 주어지면 이 함수는 소스 코드 제어 데이터베이스의 해당 버전과 다른 파일을 결정합니다.

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

【인】 소스 제어 플러그인 컨텍스트 포인터입니다.

 Hwnd

【인】 소스 제어 플러그인이 제공하는 모든 대화 상자에 대한 상위로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 c파일

【인】 배열에 지정된 파일 `lpFileNames` 이름 수입니다. 또한 배열의 `plIsFileDifferent` 크기를 지정합니다.

 lpFile 이름

【인】 확인할 로컬 파일 이름 배열입니다.

 plIsFile다른

【인, 아웃】 각 파일의 차이 상태를 나타내는 값 의 배열(배열에는 최소한 `cFiles` 항목이 있어야 함). 비영은 파일이 다르다는 것을 의미합니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|작업이 완료되었습니다.|
|SCC_UNSPECIFIEDERROR|일반 오류.|

## <a name="see-also"></a>참조
- [소스 제어 플러그인 API 기능](../extensibility/source-control-plug-in-api-functions.md)
