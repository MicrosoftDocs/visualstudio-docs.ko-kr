---
title: IDebugMemoryContext2::빼기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c858beb8c3f9f587633dbae8b3b1fe73fd789663
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727440"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
현재 컨텍스트에서 지정된 값을 빼고 새 컨텍스트를 반환합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Subtract( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Subtract(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>매개 변수
`dwCount`\
【인】 감소할 메모리 바이트 수입니다.

`ppMemCxt`\
【아웃】 새 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 메모리 컨텍스트는 주소이므로 주소에서 값을 빼면 새 컨텍스트 인터페이스가 필요한 새 주소가 생성됩니다.

 이 메서드는 결과 주소가 이 컨텍스트와 연결된 메모리 공간 외부에 있더라도 항상 새 컨텍스트를 생성해야 합니다. 이에 대한 유일한 예외는 새 컨텍스트에 대한 메모리를 `ppMemCxt` 할당할 수 없거나 null 값(오류)인 경우입니다.

## <a name="see-also"></a>참조
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
