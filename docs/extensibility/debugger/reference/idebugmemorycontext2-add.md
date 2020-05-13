---
title: IDebugMemoryContext2::추가 | 마이크로 소프트 문서
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a21fa2ec6d48bb1d6bf17bbc0d2ebf0d90a25a9f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727475"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
지정된 값을 현재 컨텍스트에 추가하고 새 컨텍스트를 반환합니다.

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
【인】 현재 컨텍스트에 추가할 값입니다.

`ppMemCxt`\
【아웃】 새 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 메모리 컨텍스트는 주소이므로 주소에 값을 추가하면 새 컨텍스트 인터페이스가 필요한 새 주소가 생성됩니다.

 이 메서드는 결과 주소가 이 컨텍스트와 연결된 메모리 공간 외부에 있더라도 항상 새 컨텍스트를 생성해야 합니다. 이에 대한 유일한 예외는 새 컨텍스트에 대한 메모리를 `ppMemCxt` 할당할 수 없거나 null 값(오류)인 경우입니다.

## <a name="see-also"></a>참조
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
