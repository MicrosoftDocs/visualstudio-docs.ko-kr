---
title: 'IDebugReference2:: GetMemoryContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetMemoryContext
helpviewer_keywords:
- IDebugReference2::GetMemoryContext
ms.assetid: 47fc3827-07a0-4eee-b7f4-fc1c62e6b25c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d34684be7a08199bfc434b62600b9d1287d0354
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909629"
---
# <a name="idebugreference2getmemorycontext"></a>IDebugReference2::GetMemoryContext
참조의 메모리 컨텍스트를 가져옵니다. 다음에 사용하도록 예약됩니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetMemoryContext ( 
   IDebugMemoryContext2** ppMemory
);
```

```csharp
int GetMemoryContext ( 
   out IDebugMemoryContext2 ppMemory
);
```

## <a name="parameters"></a>매개 변수
`ppMemory`\
제한이 참조의 값과 연결 된 메모리를 나타내는 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 개체를 반환 합니다.

## <a name="return-value"></a>Return Value
 항상 `E_NOTIMPL`를 반환합니다.

## <a name="see-also"></a>참고 항목
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
