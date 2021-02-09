---
title: 'IDebugMemoryContext2:: Add | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4ddba5665ead15bb623193412bafa7d6eaa8aa16
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851220"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
현재 컨텍스트에 지정 된 값을 추가 하 고 새 컨텍스트를 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Add( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Add(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>매개 변수
`dwCount`\
진행 현재 컨텍스트에 추가할 값입니다.

`ppMemCxt`\
제한이 새 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 개체를 반환 합니다.

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 메모리 컨텍스트는 주소 이므로 주소에 값을 추가 하면 새 컨텍스트 인터페이스가 필요한 새 주소가 생성 됩니다.

 결과 주소가이 컨텍스트와 연결 된 메모리 공간을 벗어난 경우에도이 메서드는 항상 새 컨텍스트를 생성 해야 합니다. 이에 대 한 유일한 예외는 새 컨텍스트에 대해 메모리를 할당할 수 없는 경우이 고 `ppMemCxt` 가 null 값 (오류) 인 경우입니다.

## <a name="see-also"></a>참고 항목
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
