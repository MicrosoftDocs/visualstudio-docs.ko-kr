---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13018e31fb5f8bed89a0a290d687360a605a855d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726509"
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

## <a name="see-also"></a>추가 정보
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
