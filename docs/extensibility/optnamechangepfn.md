---
title: OPTNAMECHANGEPFN | Microsoft Docs
description: 소스 제어 플러그 인에서 Visual Studio IDE로 이름 변경 내용을 전달하는 OPTNAMECHANGEPFN 콜백 함수에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 340012663ad7d21c0b5c2ef81283f5d780d6011c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901528"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
이 함수는 [SccSetOption](../extensibility/sccsetoption-function.md) 호출에 지정된 콜백 `SCC_OPT_NAMECHANGEPFN` 함수(옵션 사용)이며 소스 제어 플러그 인에서 변경한 이름을 IDE에 다시 전달하는 데 사용됩니다.

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

[in] [SccSetOption에](../extensibility/sccsetoption-function.md) 대한 이전 호출에서 지정한 사용자 값입니다(옵션 `SCC_OPT_USERDATA` 사용).

 pszOldName

[in] 파일의 원래 이름입니다.

 pszNewName

[in] 파일 이름을 바꾼 이름입니다.

## <a name="return-value"></a>반환 값
 없음

## <a name="remarks"></a>설명
 소스 제어 작업 중에 파일 이름이 바뀐 경우 소스 제어 플러그 인은 이 콜백을 통해 이름 변경에 대해 IDE에 알릴 수 있습니다.

 IDE가 이 콜백을 지원하지 않는 경우 [SccSetOption을](../extensibility/sccsetoption-function.md) 호출하여 지정하지 않습니다. 플러그 인이 이 콜백을 지원하지 않는 경우 `SCC_E_OPNOTSUPPORTED` `SccSetOption` IDE가 콜백을 설정하려고 할 때 함수에서 반환됩니다.

## <a name="see-also"></a>참조
- [IDE에서 구현하는 콜백 함수](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
