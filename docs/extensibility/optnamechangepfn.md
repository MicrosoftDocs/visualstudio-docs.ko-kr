---
title: 옵트네임 체인지PFN | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 603bd08c1ec3832bf732e0b33101076738d009e3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702243"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
이 콜백 함수는 [SccSetOption(옵션](../extensibility/sccsetoption-function.md) `SCC_OPT_NAMECHANGEPFN`사용)에 대한 호출에 지정된 콜백 함수이며 소스 제어 플러그인에 의해 변경된 이름을 IDE로 다시 전달하는 데 사용됩니다.

## <a name="signature"></a>서명

```cpp
typedef void (*OPTNAMECHANGEPFN)(
   LPVOID pvCallerData,
   LPCSTR pszOldName,
   LPCSTR pszNewName
);
```

## <a name="parameters"></a>매개 변수
 pvCallerData

【인】 [SccSetOption에](../extensibility/sccsetoption-function.md) 대한 이전 호출에서 지정한 `SCC_OPT_USERDATA`사용자 값입니다(옵션 사용).

 pszOldName

【인】 파일의 원래 이름입니다.

 pszNewName

【인】 파일이름이 바뀌었습니다.

## <a name="return-value"></a>반환 값
 없음

## <a name="remarks"></a>설명
 소스 제어 작업 중에 파일이름이 변경되면 소스 제어 플러그인은 이 콜백을 통해 이름 변경에 대해 IDE에 알릴 수 있습니다.

 IDE가 이 콜백을 지원하지 않는 경우 [SccSetOption을](../extensibility/sccsetoption-function.md) 호출하여 지정하지 않습니다. 플러그인이 이 콜백을 지원하지 않으면 IDE가 `SCC_E_OPNOTSUPPORTED` `SccSetOption` 콜백을 설정하려고 할 때 함수에서 반환됩니다.

## <a name="see-also"></a>참조
- [IDE에서 구현한 콜백 함수](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
