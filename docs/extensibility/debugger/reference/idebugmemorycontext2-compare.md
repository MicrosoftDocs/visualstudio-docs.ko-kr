---
title: 'IDebugMemoryContext2:: Compare | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727498"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
비교 플래그에 지정 된 방식으로 지정 된 배열의 각 컨텍스트와 메모리 컨텍스트를 비교 하 여와 일치 하는 첫 번째 컨텍스트의 인덱스를 반환 합니다.

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
진행 비교 유형을 결정 하는 [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) 열거형의 값입니다.

`rgpMemoryContextSet`\
진행 비교할 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 개체에 대 한 참조의 배열입니다.

`dwMemoryContextSetLen`\
진행 배열의 컨텍스트 수 `rgpMemoryContextSet` 입니다.

`pdwMemoryContext`\
제한이 비교를 만족 하는 첫 번째 메모리 컨텍스트의 인덱스를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. `E_COMPARE_CANNOT_COMPARE`두 컨텍스트를 비교할 수 없으면를 반환 합니다.

## <a name="remarks"></a>설명
 DE (디버그 엔진)는 모든 형식의 비교를 지원 하지 않아도 되지만 `CONTEXT_EQUAL` ,, 및 이상을 지원 해야 합니다 `CONTEXT_LESS_THAN` `CONTEXT_GREATER_THAN` `CONTEXT_SAME_SCOPE` .

## <a name="see-also"></a>추가 정보
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)
