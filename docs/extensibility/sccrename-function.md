---
description: 이 함수는 소스 제어 시스템의 파일 이름을 바꿉니다.
title: SccRename 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fb3fa392cd4ed31d907fe5913f8d7965a20df05b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900462"
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

[in] 소스 제어 플러그 인 컨텍스트 구조입니다.

 Hwnd

[in] 소스 제어 플러그 인이 제공하는 모든 대화 상자의 부모로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 lpFileName

[in] 이름을 바꿀 파일의 정규화된 파일 이름입니다.

 lpNewName

[in] 정규화된 새 이름입니다. 디렉터리 경로가 다르면 파일이 한 하위 디렉터리에서 다른 하위 디렉터리로 이동됩니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|이름 바꾸기 작업이 성공적으로 완료되었습니다.|
|SCC_E_PROJNOTOPEN|프로젝트가 소스 제어에서 열려 있지 않습니다.|
|SCC_E_FILENOTCONTROLLED|파일이 소스 제어에 있지 않습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 소스 제어 시스템에 액세스하는 데 문제가 있었습니다.|
|SCC_E_NOTAUTHORIZED|사용자에게 이 작업을 완료할 권한이 없습니다.|
|SCC_E_COULDNOTCREATEPROJECT|프로젝트 이름을 바꾸는 프로세스의 일부로 프로젝트를 만들 수 없습니다.|
|SCC_E_OPNOTPERFORMED|작업이 수행되지 않았습니다.|
|SCC_E_NONSPECIFICERROR|지정되지 않은 오류 또는 일반 오류가 발생했습니다.|

## <a name="remarks"></a>설명
 이 함수를 사용하여 파일 이름을 바꾸거나 소스 제어 시스템의 한 위치에서 다른 위치로 이동할 수 있습니다. 소스 제어 플러그 인은 디스크의 파일에 액세스하려고 시도하면 안 됩니다. 로컬 파일의 이름을 바꾸는 것은 IDE의 책임입니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
