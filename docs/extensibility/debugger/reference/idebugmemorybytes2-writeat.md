---
title: 'IDebugMemoryBytes2:: WriteAt | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727524"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
지정 된 주소에서 시작 하 여 지정 된 바이트 수의 메모리를 씁니다.

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
진행 바이트 쓰기를 시작할 위치를 지정 하는 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 개체입니다.

`dwCount`\
진행 쓸 바이트 수입니다.

`rgbMemory`\
진행 쓸 바이트입니다. 이 배열의 크기는 최소한 바이트 이상으로 가정 `dwCount` 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면를 반환 하 고, 그렇지 않으면를 반환 `S_FALSE` `E_FAIL` 합니다.

## <a name="remarks"></a>설명
 시작 주소가이 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) 개체로 표시 되는 메모리 창 내에 없는 경우 쓰기가 발생 하지 않으며의 오류 코드가 `E_FAIL` 반환 됩니다 .이 값이 메모리 공간에 겹칠 경우에도 마찬가지입니다.

## <a name="see-also"></a>추가 정보
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
