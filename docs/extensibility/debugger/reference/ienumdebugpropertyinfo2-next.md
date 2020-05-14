---
title: IEnumDebugPropertyInfo2::다음 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2::Next
helpviewer_keywords:
- IEnumDebugPropertyInfo2::Next
ms.assetid: 4eb8c7c3-aadf-4187-abee-c0620308a3eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d8e714f281835adf7df8d7e96a910ca66f1949b4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715519"
---
# <a name="ienumdebugpropertyinfo2next"></a>IEnumDebugPropertyInfo2::Next
열거형에서 다음 요소 집합을 반환합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Next(
   ULONG                 celt,
   DEBUG_PROPERTY_INFO** rgelt,
   ULONG*                pceltFetched
);
```

```csharp
int Next(
   uint                  celt,
   DEBUG_PROPERTY_INFO[] rgelt,
   ref uint              pceltFetched
);
```

## <a name="parameters"></a>매개 변수
`celt`\
【인】 검색할 요소 수입니다. 또한 배열의 최대 크기를 `rgelt` 지정합니다.

`rgelt`\
【인, 아웃】 채워질 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 요소의 배열입니다.

`pceltFetched`\
【아웃】 에서 실제로 반환된 요소 `rgelt`수를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 `S_OK`를 반환합니다. 요청된 수보다 적은 수의 요소를 반환할 수 `S_FALSE` 있는 경우 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="see-also"></a>참조
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
