---
description: 이 메서드는 개체의 런타임 형식을 결정 합니다.
title: 'IDebugBinder:: ResolveRuntimeType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 19e7285dd25009e7fe4aeb92974c70ce4109502c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143638"
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
이 메서드는 개체의 런타임 형식을 결정 합니다.

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
진행 확인할 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 입니다.

`ppResolved`\
제한이 개체의 형식을 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md)로 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 개체의 런타임 형식은 컴파일 타임에 항상 알려지지는 않습니다. 예를 들어, 다형성을 사용 하면 인수를 단추 클래스와 같은 기본 클래스로 함수에 전달할 수 있습니다. 실제 인수는 라디오 단추 클래스와 같은 파생 된 클래스 일 수 있습니다.

## <a name="see-also"></a>참고 항목
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
