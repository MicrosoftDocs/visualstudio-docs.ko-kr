---
description: 개체를이 개체와 비교 합니다.
title: 'IDebugObject:: IsEqual | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0907b72f2a0647fc6ff6181ecdc5c7fd8c2134cb
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151664"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
개체를이 개체와 비교 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT IsEqual( 
   IDebugObject* pObject,
   BOOL*         pfIsEqual
);
```

```csharp
int IsEqual(
   IDebugObject pObject,
   out int      pfIsEqual
);
```

## <a name="parameters"></a>매개 변수
`pObject`\
진행 비교할 개체를 나타내는 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 개체입니다.

`pfIsEqual`\
제한이 개체의 값이 같으면 0이 아닌 값을 반환 `TRUE` 하 고, 그렇지 않으면 0 ()을 반환 `FALSE` 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 일반적으로이 메서드는 `pObject` 매개 변수와이 [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 개체가 나타내는 값의 주소를 비교할 수 있습니다. 주소가 같으면 개체는 같은 것으로 간주할 수 있습니다.

## <a name="see-also"></a>참고 항목
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
