---
description: 이 메서드는 정확한 형식의 변수를 반환 합니다.
title: 'IDebugBinder:: ResolveDynamicType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::ResolveDynamicType
helpviewer_keywords:
- IDebugBinder::ResolveDynamicType method
ms.assetid: 2c36ef92-5b44-4cfd-988e-54a2e5a6710c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 548ba7ed326de2310cdc6689088f72c7a97ade7d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102174036"
---
# <a name="idebugbinderresolvedynamictype"></a>IDebugBinder::ResolveDynamicType
이 메서드는 정확한 형식의 변수를 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT ResolveDynamicType (
   IDebugDynamicField *pDynamic,
   IDebugField       **ppResolved
);
```

```csharp
int ResolveDynamicType(
   IDebugDynamicField pDynamic,
   out IDebugField    ppResolved
);
```

## <a name="parameters"></a>매개 변수
`pDynamic`\
진행 변수의 형식을 나타내는 [Idebugdynamicfield](../../../extensibility/debugger/reference/idebugdynamicfield.md) 입니다.

`ppResolved`\
제한이 변수의 형식에 대 한 특정 정보를 제공 하는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참고 항목
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)
