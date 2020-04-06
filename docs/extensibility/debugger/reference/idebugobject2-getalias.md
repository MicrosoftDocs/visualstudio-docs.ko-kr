---
title: 아이데버그오브젝트2::겟알리아스 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 53c72182b497e2b24d41a784c405d169c3db195f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726280"
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
이 개체와 연결된 별칭(있는 경우)을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetAlias(
   IDebugAlias** ppAlias
);
```

```csharp
int GetAlias(
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>매개 변수
`ppAlias`\
【아웃】 이 개체의 별칭을 나타내는 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) 개체를 반환합니다. 그렇지 않으면 null 값을 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 개체에 대한 별칭은 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) 메서드를 호출하여 만들어집니다.

## <a name="see-also"></a>참조
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
