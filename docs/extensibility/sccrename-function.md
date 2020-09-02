---
title: SccRename 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88a917e43729b3049e488264c260f8455ab08fe4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700425"
---
# <a name="sccrename-function"></a>SccRename 함수
이 함수는 소스 제어 시스템에서 파일의 이름을 바꿉니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccRename(
   LPVOID pvContext,
   HWND   hWnd,
   LPCSTR lpFileName,
   LPCSTR lpNewName
);
```

#### <a name="parameters"></a>매개 변수
 pvContext

진행 소스 제어 플러그 인 컨텍스트 구조입니다.

 hWnd

진행 소스 제어 플러그 인이 제공 하는 대화 상자의 부모로 사용할 수 있는 IDE 창에 대 한 핸들입니다.

 lpFileName

진행 이름을 바꿀 파일의 정규화 된 파일 이름입니다.

 lpNewName

진행 정규화 된 새 이름입니다. 디렉터리 경로가 다른 경우 파일은 한 하위 디렉터리에서 다른 하위 디렉터리로 이동 되었습니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|이름 바꾸기 작업이 성공적으로 완료 되었습니다.|
|SCC_E_PROJNOTOPEN|프로젝트가 소스 제어에서 열려 있지 않습니다.|
|SCC_E_FILENOTCONTROLLED|파일이 소스 제어에 있지 않습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 원본 제어 시스템에 액세스 하는 동안 문제가 발생 했습니다.|
|SCC_E_NOTAUTHORIZED|사용자에 게이 작업을 완료할 수 있는 권한이 없습니다.|
|SCC_E_COULDNOTCREATEPROJECT|이름 바꾸기 프로세스의 일부로 프로젝트를 만들 수 없습니다.|
|SCC_E_OPNOTPERFORMED|작업이 수행 되지 않았습니다.|
|SCC_E_NONSPECIFICERROR|지정 되지 않았거나 일반 오류가 발생 했습니다.|

## <a name="remarks"></a>설명
 이 함수를 사용 하 여 소스 제어 시스템에서 파일의 이름을 바꾸거나 한 위치에서 다른 위치로 이동할 수 있습니다. 원본 제어 플러그 인은 디스크의 파일에 액세스를 시도 하지 않아야 합니다. 로컬 파일의 이름을 바꾸는 것은 IDE의 책임입니다.

## <a name="see-also"></a>추가 정보
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
