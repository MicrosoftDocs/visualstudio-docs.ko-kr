---
description: 이 메서드는 필드 열거에서 다음 요소 집합을 반환 합니다.
title: 'IEnumDebugFields:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Next
helpviewer_keywords:
- IEnumDebugFields::Next method
ms.assetid: 22c177a2-af81-4234-812b-f9b47be245a2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6b1705c1f07ce17df0d09c8b3036c639b6fe829a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073471"
---
# <a name="ienumdebugfieldsnext"></a>IEnumDebugFields::Next
이 메서드는 열거형에서 다음 요소 집합을 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Next(
   ULONG         celt,
   IDebugField** rgelt,
   ULONG*        pceltFetched
);
```

```csharp
int Next(
   uint          celt,
   IDebugField[] rgelt,
   ref uint      pceltFetched
);
```

## <a name="parameters"></a>매개 변수
`celt`\
진행 검색할 요소의 수입니다. 또한 배열의 최대 크기를 지정 합니다 `rgelt` .

`rgelt`\
[in, out] 채워질 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 요소의 배열입니다.

`pceltFetched`\
제한이 에서 실제로 반환 된 요소의 수를 반환 합니다 `rgelt` .

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. `S_FALSE`요청 된 수의 요소를 반환할 수 있으면를 반환 하 고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참조
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
