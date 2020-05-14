---
title: IEnumDebugPrograms2::다음 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::Next
helpviewer_keywords:
- IEnumDebugPrograms2::Next
ms.assetid: 9120e263-e97c-4a40-ab2c-e9264ce3d6c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 035af638b9504318a39e01f34ed32719d957896e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715630"
---
# <a name="ienumdebugprograms2next"></a>IEnumDebugPrograms2::Next
열거형에서 다음 요소 집합을 반환합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Next(
   ULONG            celt,
   IDebugProgram2** rgelt,
   ULONG*           pceltFetched
);
```

```csharp
int Next(
   uint             celt,
   IDebugProgram2[] rgelt,
   ref uint         pceltFetched
);
```

## <a name="parameters"></a>매개 변수
`celt`\
【인】 검색할 요소 수입니다. 또한 배열의 최대 크기를 `rgelt` 지정합니다.

`rgelt`\
【인, 아웃】 입력할 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 요소의 배열입니다.

`pceltFetched`\
【아웃】 에서 실제로 반환된 요소 `rgelt`수를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 `S_OK`를 반환합니다. 요청된 수보다 적은 수의 요소를 반환할 수 `S_FALSE` 있는 경우 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="see-also"></a>참조
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
