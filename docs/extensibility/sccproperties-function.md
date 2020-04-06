---
title: SccProperties 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf2dd87efbb50346093144db6e069eea30138e37
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700501"
---
# <a name="sccproperties-function"></a>SccProperties 함수
이 함수는 파일 또는 프로젝트에 대한 소스 제어 속성을 표시합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccProperties (
   LPVOID pvContext,
   HWND   hWnd,
   LPCSTR lpFileName
);
```

#### <a name="parameters"></a>매개 변수
 pvContext

【인】 소스 제어 플러그인 컨텍스트 구조입니다.

 Hwnd

【인】 소스 제어 플러그인이 제공하는 모든 대화 상자에 대한 상위로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 lpFileName

【인】 파일 또는 프로젝트의 정규화된 경로 이름입니다.

## <a name="return-value"></a>Return Value
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|속성이 성공적으로 표시되었습니다.|
|SCC_I_RELOADFILE|버전 제어 시스템이 파일 속성을 수정했기 때문에 IDE가 이 파일을 다시 로드해야 합니다.|
|SCC_E_PROJNOTOPEN|소스 제어에서 지정된 프로젝트가 열리지 않았습니다.|
|SCC_E_NOTAUTHORIZED|사용자는 이 파일 이나 프로젝트의 속성을 볼 권한이 없습니다.|
|SCC_E_FILENOTCONTROLLED|지정된 파일 또는 프로젝트가 소스 제어를 받지 않습니다.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|알 수 없거나 일반적인 오류가 발생했습니다.|

## <a name="remarks"></a>설명
 소스 제어 플러그인은 자체 대화 상자에 속성을 표시합니다.

 속성은 소스 제어 플러그인에 의해 정의되며 플러그인에서 플러그인까지 다를 수 있습니다. 플러그인을 통해 사용자가 파일의 소스 제어 속성을 변경할 수 있는 `SCC_I_RELOAD` 경우 이 파일 또는 프로젝트를 다시 로드해야 한다는 IDE 신호를 다시 보내야 합니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
