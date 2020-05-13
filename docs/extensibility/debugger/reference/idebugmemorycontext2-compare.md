---
title: IDebugMemoryContext2::비교 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b2551f8554d96186b90a1eed97a5a48ec5f0405
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727498"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
비교 플래그로 표시된 방식으로 지정된 배열의 각 컨텍스트와 메모리 컨텍스트를 비교하여 일치하는 첫 번째 컨텍스트의 인덱스를 반환합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Compare( 
   CONTEXT_COMPARE        compare,
   IDebugMemoryContext2** rgpMemoryContextSet,
   DWORD                  dwMemoryContextSetLen,
   DWORD*                 pdwMemoryContext
);
```

```csharp
int Compare(
   enum_CONTEXT_COMPARE   compare,
   IDebugMemoryContext2[] rgpMemoryContextSet,
   uint                   dwMemoryContextSetLen,
   out uint               pdwMemoryContext
);
```

## <a name="parameters"></a>매개 변수
`compare`\
【인】 비교 유형을 결정하는 [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) 열거형의 값입니다.

`rgpMemoryContextSet`\
【인】 비교할 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 개체에 대한 참조 배열입니다.

`dwMemoryContextSetLen`\
【인】 배열의 컨텍스트 수입니다. `rgpMemoryContextSet`

`pdwMemoryContext`\
【아웃】 비교를 제공하는 첫 번째 메모리 컨텍스트의 인덱스를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다. 두 `E_COMPARE_CANNOT_COMPARE` 컨텍스트를 비교할 수 없는 경우 반환합니다.

## <a name="remarks"></a>설명
 디버그 엔진(DE)은 모든 유형의 비교를 지원할 필요는 없지만 최소한 `CONTEXT_EQUAL` `CONTEXT_LESS_THAN`. `CONTEXT_GREATER_THAN` `CONTEXT_SAME_SCOPE`및 을 지원해야 합니다.

## <a name="see-also"></a>참조
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)
