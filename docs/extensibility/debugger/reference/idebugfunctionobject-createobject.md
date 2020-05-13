---
title: IDebugFunctionObject::오브젝트 만들기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: beb00bcf932b19ed4e489456236957c55d909ce4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728604"
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
생성자 사용 하 여 개체를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CreateObject( 
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject(
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   out IDebugObject     ppObject
);
```

## <a name="parameters"></a>매개 변수
`pConstructor`\
【인】 생성할 개체의 생성자인 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 개체입니다.

`dwArgs`\
【인】 배열의 매개 변수 `pArg` 수입니다. 생성자에게 전달된 매개 변수 수를 나타냅니다.

`pArg`\
【인】 생성자에게 전달된 매개 변수를 나타내는 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 개체의 배열입니다.

`ppObject`\
【아웃】 새로 `IDebugObject` 만든 개체를 나타내는 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 인터페이스로 표현되는 함수의 매개 변수인 클래스(또는 생성자가 필요한 다른 복잡한 형식)의 인스턴스를 나타내는 개체를 만들기 위해 이 메서드를 호출합니다.

 개체 매개 변수에 생성자가 필요하지 않은 경우 [CreateObjectNo생성기](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) 메서드를 호출합니다.

## <a name="see-also"></a>참조
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)
