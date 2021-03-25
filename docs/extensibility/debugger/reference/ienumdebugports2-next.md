---
description: 포트 열거에서 다음 요소 집합을 반환 합니다.
title: 'IEnumDebugPorts2:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2::Next
helpviewer_keywords:
- IEnumDebugPorts2::Next
ms.assetid: 3f43d18c-6bd1-4ddd-95ef-9550abd2ad09
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e5972a5676c0e7859886578cb871c9a25846a4dc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105052816"
---
# <a name="ienumdebugports2next"></a>IEnumDebugPorts2::Next
열거형에서 다음 요소 집합을 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Next(
   ULONG         celt,
   IDebugPort2** rgelt,
   ULONG*        pceltFetched
);
```

```csharp
int Next(
   uint          celt,
   IDebugPort2[] rgelt,
   ref uint      pceltFetched
);
```

## <a name="parameters"></a>매개 변수
`celt`\
진행 검색할 요소의 수입니다. 또한 배열의 최대 크기를 지정 합니다 `rgelt` .

`rgelt`\
[in, out] 채워질 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 요소의 배열입니다.

`pceltFetched`\
제한이 에서 실제로 반환 된 요소의 수를 반환 합니다 `rgelt` .

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. `S_FALSE`요청 된 수의 요소를 반환할 수 있으면를 반환 하 고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참조
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
