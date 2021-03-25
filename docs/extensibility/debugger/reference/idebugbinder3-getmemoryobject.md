---
description: 이 메서드는이 개체가 바인딩된 메모리를 나타내는 메모리 개체를 검색 합니다.
title: 'IDebugBinder3:: GetMemoryObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetMemoryObject
helpviewer_keywords:
- IDebugBinder3::GetMemoryObject method
ms.assetid: 71d959c7-45df-485f-b0ee-f1c0439d54fb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 10518db1aca373d749858855730cee458649cb5f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067363"
---
# <a name="idebugbinder3getmemoryobject"></a>IDebugBinder3::GetMemoryObject
이 메서드는이 개체가 바인딩된 메모리를 나타내는 메모리 개체를 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetMemoryObject(
   IDebugField*   pField,
   UINT64         uConstant,
   IDebugObject** ppObject
);
```

```csharp
int GetMemoryObject(
   IDebugField      pField,
   long             uConstant,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>매개 변수
`pField`\
진행 메모리 개체를 가져올 필드를 지정 합니다.

`uConstant`\
진행 상수 값에 대 한 메모리 주소 또는 값을 나타냅니다.

`ppObject`\
제한이 이 개체가 바인딩되는 메모리를 나타내는 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참조
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
