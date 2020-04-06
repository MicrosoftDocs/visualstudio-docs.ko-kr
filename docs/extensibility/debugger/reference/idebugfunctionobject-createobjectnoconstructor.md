---
title: IDebugFunctionObject::만들기 개체No생성자 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor
helpviewer_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor method
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad95f9273276830b59ebc77214f3920a687d41ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728567"
---
# <a name="idebugfunctionobjectcreateobjectnoconstructor"></a>IDebugFunctionObject::CreateObjectNoConstructor
생성자가 없는 개체를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CreateObjectNoConstructor( 
   IDebugField*   pClassObject,
   IDebugObject** ppObject
);
```

```csharp
int CreateObjectNoConstructor(
   IDebugField      pClassField,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>매개 변수
`pClassObject`\
【인】 만들 개체의 형식을 나타내는 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 개체입니다.

`ppObject`\
【아웃】 새로 만든 개체를 나타내는 [IDebugObject를](../../../extensibility/debugger/reference/idebugobject.md) 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 인터페이스로 표현되는 함수의 매개 변수인 구조체 또는 복잡한 형식(생성자가 필요하지 않음)의 인스턴스를 나타내는 개체를 만들기 위해 이 메서드를 호출합니다.

 개체 매개 변수에 생성자가 필요한 경우 CreateObject 메서드를 [호출합니다.](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)

## <a name="see-also"></a>참조
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)
