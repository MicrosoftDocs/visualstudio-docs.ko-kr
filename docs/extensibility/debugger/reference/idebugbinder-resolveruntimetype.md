---
title: 아이디버그바인더::해결런타임타입 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4bdbff651618365f3b68a142a6cb1e76836876a3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735960"
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
이 메서드는 개체의 런타임 형식을 결정합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT ResolveRuntimeType( 
   IDebugObject* pObject,
   IDebugField** ppResolved
);
```

```csharp
int ResolveRuntimeType(
   IDebugObject     pObject,
   out IDebugField  ppResolved
);
```

## <a name="parameters"></a>매개 변수
`pObject`\
【인】 해결될 [IDebugObject입니다.](../../../extensibility/debugger/reference/idebugobject.md)

`ppResolved`\
【아웃】 개체 형식을 [IDebugField로](../../../extensibility/debugger/reference/idebugfield.md)반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 개체의 런타임 형식이 컴파일 타임에 항상 알려진 것은 아닙니다. 예를 들어 다형성을 사용하면 인수가 단추 클래스와 같은 기본 클래스로 함수에 전달될 수 있습니다. 실제 인수는 라디오 단추 클래스와 같은 파생 클래스일 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
