---
title: SccAddFilesFromSCC 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d22527644edbf1697112f5cf8b73b8a3f72b774
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701279"
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC 기능
이 함수는 소스 제어의 파일 목록을 현재 열려 있는 프로젝트에 추가합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccAddFilesFromSCC(
   LPVOID  pContext,
   HWND    hWnd,
   LPSTR   lpUser,
   LPSTR   lpAuxProjPath,
   LONG    cFiles,
   LPCSTR* lpFilePaths,
   LPCSTR  lpDestination,
   LPCSTR  lpComment,
   LPBOOL  pbResults
);
```

### <a name="parameters"></a>매개 변수
 pContext

【인】 소스 제어 플러그인 컨텍스트 포인터입니다.

 Hwnd

【인】 소스 제어 플러그인이 제공하는 모든 대화 상자에 대한 상위로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 lpUser

【인, 아웃】 사용자 이름(null 종기자를 포함하여 최대 SCC_USER_SIZE).

 lpAuxProjPath

【인, 아웃】 프로젝트를 식별하는 보조 문자열(널 터미네이터를 포함하여 `SCC_PRJPATH_`최대 SIZE).

 c파일

【인】 에 의해 `lpFilePaths`주어진 파일의 수

 lpFilePaths

【인, 아웃】 현재 프로젝트에 추가할 파일 이름 배열입니다.

 lpDestination

【인】 파일을 작성할 대상 경로입니다.

 lpComment

【인】 추가되는 각 파일에 적용할 주석입니다.

 pb결과

【인, 아웃】 각 파일에 대한 성공(0또는 TRUE이 아닌) 또는 실패(0 또는 FALSE)를 나타내도록 설정된 `cFiles` 플래그 배열(배열의 크기는 최소한 길어야 합니다).

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_E_PROJNOTOPEN|프로젝트가 열려 있지 않습니다.|
|SCC_E_OPNOTPERFORMED|연결이 지정한 것과 동일한 프로젝트에 연결되지 않습니다.`lpAuxProjPath.`|
|SCC_E_NOTAUTHORIZED|사용자가 데이터베이스를 업데이트할 권한이 없습니다.|
|SCC_E_NONSPECIFICERROR|알 수 없는 오류입니다.|
|SCC_I_RELOADFILE|파일 또는 프로젝트를 다시 로드해야 합니다.|

## <a name="see-also"></a>참조
- [소스 제어 플러그인 API 기능](../extensibility/source-control-plug-in-api-functions.md)
