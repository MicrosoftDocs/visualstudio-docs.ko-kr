---
title: SccAddFilesFromSCC 함수 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701279"
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC 함수
이 함수는 소스 제어에서 현재 열려 있는 프로젝트에 파일 목록을 추가 합니다.

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

진행 소스 제어 플러그 인 컨텍스트 포인터입니다.

 hWnd

진행 소스 제어 플러그 인이 제공 하는 대화 상자의 부모로 사용할 수 있는 IDE 창에 대 한 핸들입니다.

 lpUser

[in, out] 사용자 이름입니다 (null 종결자를 포함 하 여 최대 SCC_USER_SIZE).

 lpAuxProjPath

[in, out] 프로젝트를 식별 하는 보조 문자열입니다 (null 종결자를 포함 하 여 최대 `SCC_PRJPATH_` 크기).

 cFiles

진행 에서 지정 된 파일 수입니다 `lpFilePaths` .

 lpFilePaths

[in, out] 현재 프로젝트에 추가할 파일 이름 배열입니다.

 lpDestination

진행 파일을 쓸 대상 경로입니다.

 lpComment

진행 추가 되는 각 파일에 적용할 설명입니다.

 Presults

[in, out] 각 파일에 대 한 성공 (0이 아닌 또는 TRUE) 또는 실패 (0 또는 FALSE)를 표시 하도록 설정 된 플래그의 배열입니다 (배열의 크기는 적어도 이상 이어야 함) `cFiles` .

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_E_PROJNOTOPEN|프로젝트가 열려 있지 않습니다.|
|SCC_E_OPNOTPERFORMED|에서 지정한 것과 동일한 프로젝트에 대 한 연결이 아닙니다. `lpAuxProjPath.`|
|SCC_E_NOTAUTHORIZED|사용자에 게 데이터베이스를 업데이트할 수 있는 권한이 없습니다.|
|SCC_E_NONSPECIFICERROR|알 수 없는 오류입니다.|
|SCC_I_RELOADFILE|파일이 나 프로젝트를 다시 로드 해야 합니다.|

## <a name="see-also"></a>추가 정보
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
