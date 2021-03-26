---
description: 모듈이 사용자 코드를 나타내는지 여부에 대 한 정보를 검색 합니다.
title: 'IDebugModule3:: IsUserCode | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::IsUserCode
helpviewer_keywords:
- IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cbc56943574cc5549e96e3281b4398df7d486f7d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065608"
---
# <a name="idebugmodule3isusercode"></a>IDebugModule3::IsUserCode
모듈이 사용자 코드를 나타내는지 여부에 대 한 정보를 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT IsUserCode(
   BOOL* pfUser
);
```

```csharp
int IsUserCode(
   out int pfUser
);
```

## <a name="parameters"></a>매개 변수
`pfUser`\
제한이 `TRUE`모듈이 사용자 코드를 나타내는 경우 0이 아닌 ()이 고, `FALSE` 그렇지 않으면 0 ()입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참조
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
