---
description: 이 메서드는 개체 위치 또는 메모리 주소를 메모리 컨텍스트로 변환 합니다.
title: 'IDebugBinder:: GetMemoryContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetMemoryContext
helpviewer_keywords:
- IDebugBinder::GetMemoryContext method
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7e31df905c35fa81e3e56e32ef969f9663054dc5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102174096"
---
# <a name="idebugbindergetmemorycontext"></a>IDebugBinder::GetMemoryContext
이 메서드는 개체 위치 또는 메모리 주소를 메모리 컨텍스트로 변환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetMemoryContext( 
   IDebugField*           pField,
   DWORD                  dwConstant,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int GetMemoryContext(
   IDebugField              pField,
   uint                     dwConstant,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>매개 변수
`pField`\
진행 찾을 개체를 설명 하는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 입니다. 이면 `NULL` 를 대신 사용 `dwConstant` 합니다.

`dwConstant`\
진행 상수 메모리 주소 (예: 0x5000)입니다.

`ppMemCxt`\
제한이 개체의 주소 또는 메모리의 주소를 나타내는 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 인터페이스를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참고 항목
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
