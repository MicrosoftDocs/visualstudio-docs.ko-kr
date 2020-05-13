---
title: IDebugObject::이평등 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13018e31fb5f8bed89a0a290d687360a605a855d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726509"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
개체를 이 개체와 비교합니다.

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
【인】 비교할 개체를 나타내는 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 개체입니다.

`pfIsEqual`\
【아웃】 개체의 값이`TRUE`같으면 0이 아닌 () 을 반환합니다. 그렇지 않으면 0`FALSE`()을 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 일반적으로 이 메서드는 `pObject` 매개 변수와 이 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 개체로 표시되는 값의 주소를 비교할 수 있습니다. 주소가 같으면 개체가 같아질 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
