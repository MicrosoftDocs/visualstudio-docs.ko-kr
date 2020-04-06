---
title: SccRename 기능 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700425"
---
# <a name="sccrename-function"></a>SccRename 함수
이 함수는 소스 제어 시스템의 파일 이름을 바꿉니다.

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

【인】 소스 제어 플러그인 컨텍스트 구조입니다.

 Hwnd

【인】 소스 제어 플러그인이 제공하는 모든 대화 상자에 대한 상위로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 lpFileName

【인】 이름이 바뀌는 파일의 정규화된 파일 이름입니다.

 lpNewName

【인】 정규화된 새 이름입니다. 디렉터리 경로가 다른 경우 파일이 한 하위 디렉터리에서 다른 하위 디렉터리로 이동했습니다.

## <a name="return-value"></a>Return Value
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|이름 바꾸기 작업이 성공적으로 완료되었습니다.|
|SCC_E_PROJNOTOPEN|프로젝트는 소스 제어하에 열려 있지 않습니다.|
|SCC_E_FILENOTCONTROLLED|파일이 소스 제어를 받지 않습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 소스 제어 시스템에 액세스하는 데 문제가 있었습니다.|
|SCC_E_NOTAUTHORIZED|사용자가 이 작업을 완료할 권한이 없습니다.|
|SCC_E_COULDNOTCREATEPROJECT|이름 바꾸기 프로세스의 일부로 프로젝트를 만들 수 없습니다.|
|SCC_E_OPNOTPERFORMED|작업이 수행되지 않았습니다.|
|SCC_E_NONSPECIFICERROR|지정되지 않았거나 일반적인 오류가 발생했습니다.|

## <a name="remarks"></a>설명
 이 함수는 파일의 이름을 바꾸거나 소스 제어 시스템에서 한 위치에서 다른 위치로 이동할 수 있습니다. 소스 제어 플러그인은 디스크의 파일에 액세스하려고 시도해서는 안 됩니다. 로컬 파일의 이름을 변경하려면 IDE의 책임입니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
