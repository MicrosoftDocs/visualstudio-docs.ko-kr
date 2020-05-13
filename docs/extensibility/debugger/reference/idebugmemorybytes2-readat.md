---
title: 아이데버그메모리바이트2::ReadAt | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f909ac3d2e2993879e4c24140abbf23c2ee8d545
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727540"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
지정된 위치에서 시작하여 일련의 바이트를 읽습니다.

## <a name="syntax"></a>구문

```cpp
HRESULT ReadAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory,
   DWORD*                pdwRead,
   DWORD*                pdwUnreadable
);
```

```csharp
int ReadAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory,
   out uint             pdwRead,
   ref uint             pdwUnreadable
);
```

## <a name="parameters"></a>매개 변수
`pStartContext`\
【인】 바이트 읽기를 시작할 위치를 지정하는 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 개체입니다.

`dwCount`\
【인】 읽을 바이트 수입니다. 또한 배열의 길이를 `rgbMemory` 지정합니다.

`rgbMemory`\
【인, 아웃】 바이트로 채워진 배열은 실제로 읽습니다.

`pdwRead`\
【아웃】 실제로 읽은 연속 바이트 수를 반환합니다.

`pdwUnreadable`\
【인, 아웃】 읽을 수 없는 바이트 수를 반환합니다. 클라이언트가 읽을 수 없는 바이트 수에 관심이 없는 경우 null 값일 수 있습니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 100바이트가 요청되고 처음 50바이트를 읽을 수 있는 경우 다음 20개는 읽을 수 없으며 나머지 30개는 읽을 수 있는 경우 이 메서드는 반환합니다.

 *`pdwRead`= 50

 *`pdwUnreadable`= 20

 이 경우 `*pdwRead + *pdwUnreadable < dwCount`호출자는 원래 100개의 원래 100바이트의 나머지 30바이트를 읽기 위해 추가 호출을 수행해야 `pStartContext` 하며 매개 변수에 전달된 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 개체는 70으로 진행되어야 합니다.

## <a name="see-also"></a>참조
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
