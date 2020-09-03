---
title: OPTNAMECHANGEPFN | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702243"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
이 함수는 [Sccsetoption](../extensibility/sccsetoption-function.md) (옵션 사용)에 대 한 호출에 지정 된 콜백 함수 `SCC_OPT_NAMECHANGEPFN` 이며, 소스 제어 플러그 인의 이름 변경을 IDE에 다시 전달 하는 데 사용 됩니다.

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

진행 [Sccsetoption](../extensibility/sccsetoption-function.md) (옵션 사용)에 대 한 이전 호출에 지정 된 사용자 값 `SCC_OPT_USERDATA` 입니다.

 pszOldName

진행 파일의 원래 이름입니다.

 pszNewName

진행 파일의 이름을 바꾼 이름입니다.

## <a name="return-value"></a>반환 값
 없음

## <a name="remarks"></a>설명
 소스 제어 작업을 수행 하는 동안 파일의 이름을 바꾸면 소스 제어 플러그 인에서이 콜백을 통해 이름 변경을 IDE에 알릴 수 있습니다.

 IDE에서이 콜백을 지원 하지 않는 경우 [Sccsetoption](../extensibility/sccsetoption-function.md) 를 호출 하 여 지정 하지 않습니다. 플러그 인이이 콜백을 지원 하지 않는 경우 `SCC_E_OPNOTSUPPORTED` `SccSetOption` IDE가 콜백을 설정 하려고 하면 함수에서 반환 됩니다.

## <a name="see-also"></a>추가 정보
- [IDE에서 구현 하는 콜백 함수](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
