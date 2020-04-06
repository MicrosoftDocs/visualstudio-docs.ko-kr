---
title: 아이데버그메모리바이트2::쓰기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ac9113424c6cd5cce230774a6e5335ffa4d4ba77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727524"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
지정된 주소에서 시작하여 지정된 수의 메모리 바이트를 씁니다.

## <a name="syntax"></a>구문

```cpp
HRESULT WriteAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory
);
```

```csharp
int WriteAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory
);
```

## <a name="parameters"></a>매개 변수
`pStartContext`\
【인】 바이트 작성을 시작할 위치를 지정하는 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 개체입니다.

`dwCount`\
【인】 쓸 바이트 수입니다.

`rgbMemory`\
【인】 쓸 바이트입니다. 이 배열은 크기가 `dwCount` 적어도 바이트인 것으로 가정합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 `S_FALSE` 모든 바이트를 작성할 수 없는 경우 `E_FAIL`반환하거나 오류 코드(일반적으로)를 반환합니다.

## <a name="remarks"></a>설명
 시작 주소가 이 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) 개체로 표시되는 메모리 창 내에 없는 경우 `E_FAIL` 쓰기 양이 메모리 공간에 겹치더라도 쓰기가 발생하지 않고 오류 코드가 반환됩니다.

## <a name="see-also"></a>참조
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
